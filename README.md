# MyOverload

Put @my_overload in front of some of the functions that
have the same name in the same module
but has different arg parameters,
such that when you call this function,
the first version of this function that fit the arg parameters will be called.

Mostly copied (and heavily inspired lol) from typing.overload.


# Usage

        @my_overload
        def my_func(a: int, b: int, c: int = 0) -> int:
            return a + b + c

        @my_overload
        def my_func(a: float, b: float, c: float) -> float:
            return a * b * c

        @my_overload
        def my_func(a: list[int], b: list[float]) -> str:
            return str(sum([a[i] * b[i] for i in range(len(a))]))

        print(my_func(1, 2))                               # 1 + 2 + 0 = 3
        print(my_func(3.0, 4.0, 5.1))                      # 3.0 * 4.0 * 5.1 = 61.199999999999996
        print(my_func([1, 3, 5], [10.0, 15.0, 12.3]))      # str(1*10.0 + 3*15.0 + 5*12.3) = "116.5"
        print(my_func("a"))                                # raise error because fulfill none of the arg parameters of my_func.