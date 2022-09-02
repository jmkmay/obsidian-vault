[[Two's complement]] is a way of representing signed numbers in binary such that addition operations are preserved when operating on two numbers.

The easiest way of thinking about [[Two's complement]] is that for an `n` bit signed number, you count up like you would normally, but once you hit 2<sup>n-1</sup> - 1, the next number starts negative and decreases to -1.

For example; n = 3

Bits | Unsigned value | Signed value
-- | -- | --
000 | 0 | 0
001 | 1 | 1
010 | 2 | 2
011 | 3 | 3
100 | 4| -4
101|5 | -3
110 |6|-2
111|7|-1



