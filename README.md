# Class::Tiny::ConstrainedAccessor - Generate Class::Tiny accessors that apply type constraints



[Class::Tiny](https://metacpan.org/pod/Class::Tiny) uses custom accessors if they are defined before the
`use Class::Tiny` statement in a package.  This module creates custom
accessors that behave as standard `Class::Tiny` accessors except that
they apply type constraints (`isa` relationships).  Type constraints
can come from TODO (e.g., [Type::Tiny](https://metacpan.org/pod/Type::Tiny)).

Example of a class using this package:

    package SampleClass;
    use Scalar::Util qw(looks_like_number);

    use Type::Tiny;

    my $MediumInteger = Type::Tiny->new(
        name => 'MediumInteger',
        constraint => sub { looks_like_number($_) and $_ >= 10 and $_ < 20 }
    );

    use Class::Tiny::ConstrainedAccessor {
        medint => $MediumInteger,           # create accessor sub medint()
        med_with_default => $MediumInteger,
    };

    # After using ConstrainedAccessor
    use Class::Tiny qw(medint regular), {
        med_with_default => 12,
    };

# SUBROUTINES

## import

Creates the accessors you have requested.

# AUTHOR

Christopher White, `<cxwembedded at gmail.com>`

# BUGS

Please report any bugs or feature requests through the GitHub Issues interface
at [https://github.com/cxw42/Class-Tiny-ConstrainedAccessor](https://github.com/cxw42/Class-Tiny-ConstrainedAccessor).  I will be
notified, and then you'll automatically be notified of progress on your bug as
I make changes.

# SUPPORT
# SUPPORT

You can find documentation for this module with the perldoc command.

    perldoc Class::Tiny::ConstrainedAccessor

You can also look for information at:

- GitHub (report bugs here)

    [https://github.com/cxw42/Class-Tiny-ConstrainedAccessor](https://github.com/cxw42/Class-Tiny-ConstrainedAccessor)

- RT: CPAN's request tracker

    [https://rt.cpan.org/NoAuth/Bugs.html?Dist=Class-Tiny-ConstrainedAccessor](https://rt.cpan.org/NoAuth/Bugs.html?Dist=Class-Tiny-ConstrainedAccessor)

- Search CPAN

    [https://metacpan.org/release/Class-Tiny-ConstrainedAccessor](https://metacpan.org/release/Class-Tiny-ConstrainedAccessor)

# LICENSE AND COPYRIGHT

Copyright 2019 Christopher White.

This program is free software; you can redistribute it and/or modify it
under the terms of the the Apache License (2.0). You may obtain a
copy of the full license at:

[https://www.apache.org/licenses/LICENSE-2.0](https://www.apache.org/licenses/LICENSE-2.0)

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.