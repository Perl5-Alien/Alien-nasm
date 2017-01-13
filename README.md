# Alien::nasm [![Build Status](https://secure.travis-ci.org/plicease/Alien-nasm.png)](http://travis-ci.org/plicease/Alien-nasm)

Find or build nasm, the netwide assembler

# SYNOPSIS

    use Alien::nasm ();
    use Env qw( @PATH );
    
    unshift @ENV, Alien::nasm->bin_dir;
    system 'nasm', ...;

Or with [Alien::Build::ModuleBuild](https://metacpan.org/pod/Alien::Build::ModuleBuild):

    use Alien::Base::ModuleBuild;
    Alien::Base::ModuleBuild->new(
      ...
      alien_bin_requires => {
        'Alien::nasm' => '0.11',
      },
      alien_build_commands => {
        "%{nasm} ...",
      },
      ...
    )->create_build_script;

# DESCRIPTION

This Alien module provides Netwide Assembler (NASM).

This class is a subclass of [Alien::Base](https://metacpan.org/pod/Alien::Base), so all of the methods documented there
should work with this class.

# HELPERS

## nasm

    %{nasm}

Returns the name of the nasm executable.  As of this writing it is always
`nasm`, but in the future it may have a different value.

# CAVEATS

This version of [Alien::nasm](https://metacpan.org/pod/Alien::nasm) adds nasm to your path, if it isn't
already there when you use it, like this:

    use Alien::nasm;  # deprecated, issues a warning

This was a design mistake, and now **deprecated**.  When [Alien::nasm](https://metacpan.org/pod/Alien::nasm) was
originally written, it was one of the first Alien tool style modules on
CPAN.  As such, the author and the [Alien::Base](https://metacpan.org/pod/Alien::Base) team hadn't yet come up
with the best practices for this sort of module.  The author, and the
[Alien::Base](https://metacpan.org/pod/Alien::Base) team feel that for consistency and for readability it is
better use [Alien::nasm](https://metacpan.org/pod/Alien::nasm) without the automatic import:

    use Alien::nasm ();

and explicitly modify the `PATH` yourself (examples are above in the
synopsis).  The old style will issue a warning.  The old behavior will be
removed, but not before 31 January 2018.

# AUTHOR

Graham Ollis <plicease@cpan.org>

# COPYRIGHT AND LICENSE

This software is copyright (c) 2017 by Graham Ollis.

This is free software; you can redistribute it and/or modify it under
the same terms as the Perl 5 programming language system itself.
