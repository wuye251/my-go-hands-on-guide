1. var xx map和 xx:=区别(var定义是nil ， :=会初始化空间)
   ```
   	userIdMap := map[int][]int{}
   	var xxx map[int]string
   ```

2. 
   ```go
   // map中塞入一个切片，在后序修改这个切片时不会更新map中的切片，只有map切片存的切片地址时是可以变化的
   package logic_test
   
   import (
   	"fmt"
   	"testing"
   
   	"github.com/spf13/cast"
   )
   
   func TestExport(t *testing.T) {
   	tmpMap := []int{}
   	result := map[string][]int{
   		"asd": tmpMap,
   	}
   	tmp := result["asd"]
   	fmt.Printf("init %p\n", &(tmp))
   	for i := 0; i < 20; i++ {
   		tmpMap = append(tmpMap, i)
   		fmt.Printf("%p\n", &tmpMap)
   	}
   	fmt.Println(result)
   }
   
   ```

3. 