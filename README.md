# kexpr-nim
nim wrapper for Heng Li's kexpr math expression library

```Nim
var e = expression("5*6+x > 20")
echo e.get_int({"x": 10}.newTable)
echo e.get_int({"x": -20}.newTable)
assert e.error() == 0

e = expression("(sample1 > 20 & sample2 > 10 & sample3 < 40")
# missing paren
assert e.error() != 0
e.clear()

e = expression("(sample1 > 20) & (sample2 > 10) & (sample3 < 40)")
echo e.get_int({"sample1": 21, "sample2": 65, "sample3": 20}.newTable) # 1
echo e.get_int({"sample1": 0, "sample2": 0, "sample3": 0}.newTable) # 0
assert e.error() == 0
```