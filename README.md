# json
this is a go json tool like encode/json(golang 1.6) but allow you to use camelName/CamelName or under_score name style
and implement method map[key]interface{},the map's key more than "string",now added "bool","float64","float32","int","int8","int16","int32","int64","uint","uint8","uint16","uint32","uint64"

    package main
    
    import (
    	"fmt"
    
    	"github.com/zxfonline/json"
    )
    
    type Person struct {
    	Id        int
    	FirstName string
    	LastName  string `json:"name"`
    }
    
    func main() {
    	p := Person{
    		Id:        1,
    		FirstName: "FirstName",
    		LastName:  "LastName",
    	}
    	jsun.UnderScoreStyle()
    	b, _ := jsun.Marshal(&p)
    	fmt.Println(string(b))
    }

output

> {"id":1,"first_name":"FirstName","name":"LastName"}


    package main
    
     import (
     	"fmt"
    
     	"github.com/JessonChan/jsun"
     )
    
     type Person struct {
     	Id        int
     	FirstName string
     	LastName  string `json:"name"`
     }
    
     func main() {
     	p := Person{
     		Id:        1,
     		FirstName: "FirstName",
     		LastName:  "LastName",
     	}
     	b, _ := jsun.Marshal(&p)
     	fmt.Println(string(b))
     }

output

> {"id":1,"firstName":"FirstName","name":"LastName"}
