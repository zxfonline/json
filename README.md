# json
this is a go json tool like encode/json(golang 1.6) but allow you to use camelName/CamelName or under_score name style
and implement method map[key]interface{},the map's key more than "string",now added "bool","float64","float32","int","int8","int16","int32","int64","uint","uint8","uint16","uint32","uint64" 
and implement `encoding.TextMarshaler`'s method MarshalText() (text []byte, err error) and `encoding.TextUnmarshaler`'s method UnmarshalText(text []byte) error

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
    	json.UnderScoreStyle()
    	b, _ := json.Marshal(&p)
    	fmt.Println(string(b))
    }

output

> {"id":1,"first_name":"FirstName","name":"LastName"}


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
     	b, _ := json.Marshal(&p)
     	fmt.Println(string(b))
     }

output

> {"id":1,"firstName":"FirstName","name":"LastName"}


    package main
    
     import (
     	"fmt"
    
     	"github.com/zxfonline/json"
     )
    
	
     	func main() {
     	     	m := make(map[*EE]bool)
     	     	point := new(EE)
		//or
		//	point := &EE{}
		point.name = "aaa"
		m[point] = true
		b, err := json.Marshal(m)
		if err != nil {
			panic(err)
		}
		fmt.Println(string(b))
		a1 := make(map[*EE]bool)
		err = json.Unmarshal(b, &a1)
		if err != nil {
			panic(err)
		}
		b, err = json.Marshal(&a1)
		if err != nil {
			panic(err)
		}
		fmt.Println(string(b))
	}
	
	type EE struct {
		name string
	}
	
	func (n *EE) MarshalText() ([]byte, error) {
		return []byte(n.name), nil
	}
	
	func (n *EE) UnmarshalText(text []byte) error {
		n.name = string(text)
		return nil
	}
	
output

> {"aaa":true}
> {"aaa":true}
