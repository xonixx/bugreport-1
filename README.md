
### Gawk 5.2.1

Crash

```
$ ./soft/gawk521 -f makesure.awk 27_parameterized_goals_10_errors.sh -l
gawk521: makesure.awk:674: (FILENAME=tests/27_parameterized_goals_10_errors.sh FNR=23) fatal error: internal error
Aborted (core dumped)
```

### Gawk 5.1.1

Good

```
$ ./soft/gawk511 -f makesure.awk 27_parameterized_goals_10_errors.sh -l
Goal 'a' has unknown dependency 'unknown1':
tests/27_parameterized_goals_10_errors.sh:10: @depends_on unknown1             # err unknown dep
Goal 'a' has unknown dependency 'unknown2':
tests/27_parameterized_goals_10_errors.sh:11: @depends_on unknown2 @args 'arg2' # err unknown dep
wrong args count for 'b':
tests/27_parameterized_goals_10_errors.sh:5: @depends_on b                    # err missing args
wrong args count for 'e':
tests/27_parameterized_goals_10_errors.sh:19: @depends_on e @args WRONG3 WRONG4 # multiple errors
wrong args count for 'b':
tests/27_parameterized_goals_10_errors.sh:6: @depends_on b @args              # err missing args
wrong args count for 'b':
tests/27_parameterized_goals_10_errors.sh:7: @depends_on b @args 'hello' 'hi' # err more args than params
wrong args count for 'e':
tests/27_parameterized_goals_10_errors.sh:9: @depends_on e @args 'arg1'       # err args for non-PG
```