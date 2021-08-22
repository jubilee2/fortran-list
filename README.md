fortran-list
============

Generic list implementation in Fortran 2003. Uses unlimited polymorphics.

## How to use
```fortran
program name
    use gen_lists, only: list
    implicit none

    type foo
        real bar
    end type foo

    type(foo) :: f1
    type(list) :: lt

    class(*),pointer :: d1
    type(foo),pointer :: d2

    f1%bar = 97

    call lt%add(44)
    call lt%add(f1)

    print *, f1

    select type(d1 => lt%get_last())
    type is (foo)
        d2 => d1
    class default
        stop 'printLink : unexepted type for link'
    end select

    print *, d2

end program name
```