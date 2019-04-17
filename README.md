# learnNS2

## Assign value
```
set a 10
set b "this"
set c 2.3

// set with no assigned value return the value
set a       
```

## Expression
```
// [] executes first
set r [expr $a + 12]        
```


## Output
```
puts $a

// by default every puts starts new line
puts -nonewline "this is"
// with -nonewline the out stream not go to new line
puts "demo"
```

## flow control
```
// if { must on the same line
if { $a > 10 } {
// if [expr $a > 10]
    puts "a is greater than 10"
} else {
    puts "a is smaller than 10"
}
```

## while loop
```
set a 0
while { $a < 101} {
    puts $a
    set a [expr $a + 2]
}
```

## for loop
```
for {set a 1} {$a < 11} {incr a} {
    puts $a
}
```

## array(map)
```
set a(0) 21
set a(1) 33
set a(2) 45

put $a(0)

set salary("john") 2000
set salary("raj") 3000

puts $salary("raj")
```

## procedure
```
proc max {a b} {
    if {$a > $b} {
        puts $a
    } else {
        puts $b
    }
}

max 23 45

// proc with return
proc add {a b c} {
    set c [expr $a + $b + $c]
    return $c
}

set x [sum 12 23 24]
print $x

// proc with multiple return
proc fun {} {
    return [list 12 23 34 45]
}

set x [fun]
```

## local and global variable
```
set x 10

proc fun {} {
    // to use variable as global
    global x
    set x 12
}

puts $x
// output 10
fun
puts $x
// still 10
```

## file handling
```
// file mode: r(read) w(write) a(append) r+ w+
set f [open "one.txt" w+]

puts $f "welcome to ns2"

close $f

// read file
set f [open "one.txt" r]

gets $f d

puts $d

close $f
```

## class and object
```
Class Student

Student instproc show {} {
    // declear variables to use
    $self instvar name roll city
    puts "Name: $name"
    puts "Roll: $roll"
    puts "City: $city"
}

// constructor for class
Student instproc init {} {
    $self instvar name roll city
    set name "default"
    set roll 0
    set city "NYC"
}

// destructor for class
Student instproc destroy {} {
    puts "destructor called"
}

Student ob1
ob1 set name "Yitao"
ob1 set roll 1234
ob1 se city "NYC"

puts [ob1 set name]
puts [ob1 set roll]
puts [ob1 set city]

// call to class func
ob1 show

// destroy obj, call to destructor
ob1 destroy
```