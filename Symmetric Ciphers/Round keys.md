```
state = [
    [206, 243, 61, 34],
    [171, 11, 93, 31],
    [16, 200, 91, 108],
    [150, 3, 194, 51],
]

round_key = [
    [173, 129, 68, 82],
    [223, 100, 38, 109],
    [32, 189, 53, 8],
    [253, 48, 187, 78],
]


def add_round_key(s, k):
    return [[state[row][col] ^ round_key[row][col] for col in range(4)] for row in range(4)]


a=add_round_key(state, round_key)
def matrix2bytes(a):
    """ Converts a 4x4 matrix into a 16-byte array.  """
    for i in range(0,4):
        for j in range(0,4):
            print(chr(a[i][j]),end="")

print(matrix2bytes(a))
```
