# Debugging Commands Scenarios

## Basic Debugging Commands

### Steps (into, over, through)

```Smalltalk
| o |
o := OrderedCollection new.
"step on :do message"
#(1 2 3) do: [ :number | o add:number ].
^ o.
```

### Proceed

#### Without exception

```Smalltalk
| a b c |
a := 1.
"Proceed here"
b := 2.
c := a + b.
^ c + b.
```

#### With exception

```Smalltalk
| a b c |
a := 1.
"Proceed here"
b := 2.
c := a + b.
b := b + (1 / 0).
^ c + b.
```


### Run to

```Smalltalk
| a block |
a := 1.
"Here, run to `a+2` "
block := [ a := a + 1 ].
a := a + 2.
^ a * 42.
```

### Restart

```Smalltalk
| o |
"Let's imagine we want to debug the `do:` loop (the block, not the method `do:` itself)"
"Perform step-overs until you get to `do:` and then you want to step through"
o := OrderedCollection new.
#(1 2 3) do: [ :number | o add:number ].
"But oups, you did an extra step-over instead of step-through: RESTART"
^ o.
```

### Step to Next Instance Creation

```Smalltalk
SindarinDebuggerTest new testTopStack.
"| a dbg|
Step to Next instance creation
a := 1.
dbg := SindarinDebugger debug: [ a := 2 ].
dbg step.
self assert: dbg topStack equals: 2."
```

### Step to next call in receiver / step to next call in class

```Smalltalk
OrderedCollectionTest compile: 'testBeginsWithAnyOf2
	"We can''t test SequenceableCollection directly. However, we can test a sampling of its descendants."

	| la oc |
	la := OrderedCollection new addAll: #(1 2 3 4 5 6); yourself.
	oc := OrderedCollection new.
	oc add: 1.

	self assert: (la beginsWithAnyOf: #((17) (1) (42))).
	oc add: 2.
	self assert: (la beginsWithAnyOf: #((17) (1 2) (42))).
	oc add: 3.
	self assert: (la beginsWithAnyOf: #((17) (1 2 3) (42))).
	self deny: (la beginsWithAnyOf: #()).
	self assert: (la beginsWithAnyOf: #(())).
	self deny: (la beginsWithAnyOf: #((42)))'.
OrderedCollectionTest new testBeginsWithAnyOf2.
"testBeginsWithAnyOf2
	""We can't test SequenceableCollection directly. However, we can test a sampling of its descendants.""

	| la oc |
	la := #(1 2 3 4 5 6).
	oc := OrderedCollection new addAll: #(1 2 3 4 5 6); yourself.
	Here: Step into + step over + step next receiver
	oc add: 1.
	
	self assert: (la beginsWithAnyOf: #((17) (1) (42))).
	oc add: 2.
	self assert: (la beginsWithAnyOf: #((17) (1 2) (42))).
	oc add: 3.
	self assert: (la beginsWithAnyOf: #((17) (1 2 3) (42))).
	self deny: (la beginsWithAnyOf: #()).
	self assert: (la beginsWithAnyOf: #(())).
	self deny: (la beginsWithAnyOf: #((42)))"
```

### Step to return

#### Basic scenario

```Smalltalk
| o |
"Step to return here"
o := OrderedCollection new.
#(1 2 3) do: [ :number | o add:number ].
^ o.
```

#### Scenario with no return

```Smalltalk
| o |
"Step to return here"
o := OrderedCollection new.
#(1 2 3) do: [ :number | o add:number ].
o.
```

#### Scenario with non-local return 

```Smalltalk
SindarinDebuggerTest new methodNonLocalReturn 
"methodNonLocalReturn
	| block |
	Step to return here
	block := [ ^ 42 ].
	block value.
	^ 43"
```

### Step to method entry

TODO

### Skip / SkipUpTo

TODO

### Jump to caret

TODO
