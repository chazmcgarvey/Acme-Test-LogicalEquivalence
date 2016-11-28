# NAME

Acme::Test::LogicalEquivalence - Test if expressions are logically equivalent

# VERSION

version 0.001

# SYNOPSIS

    use Test::More;
    use Acme::Test::LogicalEquivalence qw(is_logically_equivalent);

    # test two expressions with 2 variables using the special vars $a and $b
    is_logically_equivalent(2, sub { $a && $b }, sub { $b && $a });

    # same as above
    is_logically_equivalent(2, sub { $_[0] && $_[1] }, sub { $_[1] && $_[0] });

    # you can do as many vars as you like
    is_logically_equivalent(3, sub { $_[0] || ($_[1] && $_[2]) },
                               sub { ($_[0] || $_[1]) && ($_[0] || $_[2]) });

    done_testing;

# DESCRIPTION

Some expressions are "logically equivalent" to other expressions, but it may not be easy to tell if
one or both of the expressions are reasonably complicated. Or maybe you're like many other people
and are too lazy to go through the effort... Either way, why not let your computer prove logical
equivalence for you?

# FUNCTIONS

## is\_logically\_equivalent

Test logical equivalence of two subroutines.

    my $is_equivalent = is_logically_equivalent($numvars, &sub1, &sub2);

This will execute both of the subroutines one or more times (depending on how many variables you
specify) with different inputs. The subroutines shall be considered logically equivalent if, for all
combinations of inputs, they both return the same thing.

Returns true if the subroutines are logically equivalent, false otherwise.

# SEE ALSO

- What is logical equivalence? Start here: [https://en.wikipedia.org/wiki/Logical\_equivalence](https://en.wikipedia.org/wiki/Logical_equivalence)

# AUTHOR

Charles McGarvey <chazmcgarvey@brokenzipper.com>

# COPYRIGHT AND LICENSE

This software is copyright (c) 2016 by Charles McGarvey.

This is free software; you can redistribute it and/or modify it under
the same terms as the Perl 5 programming language system itself.
