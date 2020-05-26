# Jisp
Jisp Programming Language

## Examples

[HelloWorld.jisp](Examples/HelloWorld.jisp)
```
print-str-ln "Hello, world!"
```

[Call-CC.jisp](Examples/Call-CC.jisp)
```
;; Basiclly Call-CC
($_ (print (+ 1 (call-cc (λ cc (cc 1))))))

;; loop
($_ (print-str-ln ""))
($_ (loop 10 (λ break continue state 
	(($_ (? (% state 2) () (continue (- state 1))))
		($_ (print state))
		($next-state (- state 1))
		(? (> next-state 0) next-state (break 0)) ))))
		
;; while
($_ (print-str-ln ""))
($_ (while 10 (λ s (> s 0)) (λ break continue s 
	(($_ (? (% s 2) () (continue (- s 1))))
		($_ (print s))
		(- s 1) ))))
		
;; do-while
($_ (print-str-ln ""))
($_ (do-while 10 (λ s (false)) (λ break continue s 
	(($_ (print s))
		(- s 1) ))))

;; Non local exit
($_ (print-str-ln ""))
($_ (call-cc (λ exit 
	(($_ (exit ()))
		(failwith "No!!!!!!") ) )))

()

```

[Fibonacci.jisp](Examples/Fibonacci.jisp)
```
($fibo (Y (λ self n 
    (? (| (= n 0) (= n 1)) 
        1
        (+ (self (- n 1)) (self (- n 2)))))))


generate 20 fibo
```

[PrintCommandLineArguments.jisp](Examples/PrintCommandLineArguments.jisp)
```
ignore (map print-str-ln argv)
```

[stdlib.jisp](Jisp/stdlib.jisp)
