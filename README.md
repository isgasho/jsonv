# jsonv: Get Value from JSON

```go
package main

import (
	"fmt"

	"github.com/chai2010/jsonv"
)

func main() {
	v0 := jsonv.Get(`{"value":"abc"}`, "value")
	fmt.Printf("%v\n", v0)

	v1, ok1 := jsonv.GetValue(`{"value":"abc"}`, "value")
	fmt.Printf("%[1]T: %[1]v, %v\n", v1, ok1)

	v2, ok2 := jsonv.GetValue(`{"value":{"abc":123}}`, "value", "abc")
	fmt.Printf("%[1]T: %[1]v, %v\n", v2, ok2)

	v3, ok3 := jsonv.GetValue(`{"value":{"abc":[11,22]}}`, "value", "abc", 1)
	fmt.Printf("%[1]T: %[1]v, %v\n", v3, ok3)

	v4, ok4 := jsonv.GetValue(`[{"value":{"abc":[11,22]}}]`, 0, "value", "abc", 0)
	fmt.Printf("%[1]T: %[1]v, %v\n", v4, ok4)

	v5 := jsonv.Get(`[{"value":{"abc":[11,22]}}]`, 0, "value", "abc", 0)
	fmt.Printf("%[1]T: %[1]v\n", v5)

	v6 := jsonv.Get(`[{"value":{"abc":[11,22]}}]`, 0, "value", "abc", 100)
	fmt.Printf("%[1]T: %[1]v\n", v6)
}
```

Output:

```
abc
string: abc, true
float64: 123, true
float64: 22, true
float64: 11, true
float64: 11
<nil>: <nil>
```
