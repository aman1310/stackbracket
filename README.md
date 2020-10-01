# stackbracket
#A program to check whether number of opening brackets being pushed into a stack is equal to the number of closing brackets being pushed into it.

# python3

from collections import namedtuple

Bracket = namedtuple("Bracket", ["char", "position"])


def are_matching(left, right):
    return (left + right) in ["()", "[]", "{}"]


def find_mismatch(text):
    opening_brackets_stack = []
    if len(text) == 1:
        return 1
    for i, next in enumerate(text):
        
        if next in "([{":
            opening_brackets_stack.append((i,next))
        if next in ")]}":
            if(len(opening_brackets_stack)) == 0:
                return i+1
            if are_matching(opening_brackets_stack[-1][1], next):
                opening_brackets_stack.pop()
                continue
            return i+1
    if len(opening_brackets_stack) == 0:
        return "Success"
    else:
        return opening_brackets_stack[-1][0] + 1



def main():
    text = input()
    mismatch = find_mismatch(text)
    print(mismatch)

if __name__ == "__main__":
    main()

