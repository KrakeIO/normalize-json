# Normalize Json

A simple library that flattens JSON objects with multi nested attributes into a JSON object with only single level attributes.
In the event there nested arrays as attribute values, splits the JSON object into multiple JSON objects

## Example 1
Flattens nested address attribute

#### Input
```javascript
{
  name: "something",
  phone: "is",
  address: {
    street:   "San Mateo",
    unit:     10,
    zipcode:  95122
  }
}
```

#### Output
```javascript
[
  {
    name:             "something",
    phone:            "is",
    address_street:   "San Mateo",
    address_unit:     10,
    address_zipcode:  95122  
  }
]
```

## Example 2
Flattens nested employee attribute into multiple different entries

#### Input
```javascript
{
  company_name: "iss",
  employee: [{
    first_name:   "Joseph",
    last_name:    "Crane"
  },{
    first_name:   "Abel",
    last_name:    "Picchu"
  }]
}
```

#### Output
```javascript
[
  {
    company_name: "iss",
    employee_first_name:   "Joseph",
    employee_last_name:    "Crane"
  },
  {
    company_name: "iss",
    employee_first_name:   "Abel",
    employee_last_name:    "Picchu"
  }  
]
```

## Example 3
If array of JSON object is input, returns as is

#### Input
```javascript
[
  {
    name:             "something",
    phone:            "is",
    address_street:   "San Mateo",
    address_unit:     10,
    address_zipcode:  95122  
  }
]
```

#### Output
```javascript
[
  {
    name:             "something",
    phone:            "is",
    address_street:   "San Mateo",
    address_unit:     10,
    address_zipcode:  95122  
  }
]
```

## Example 4

#### Input
```javascript
{
  name:             "something",
  phone:            "is",
  address: {
    street:   "San Mateo",
    unit:     10,
    zipcode:  95122,
    price_history: [
      10, 20, 30, 40
    ]
  }
}
```

#### Output
```javascript
[
  {
    name:             "something",
    phone:            "is",
    address_street:   "San Mateo",
    address_unit:     10,
    address_zipcode:  95122,
    address_price_history: 10  

  },
  {
    name:             "something",
    phone:            "is",
    address_street:   "San Mateo",
    address_unit:     10,
    address_zipcode:  95122,
    address_price_history: 20
  },
  {
    name:             "something",
    phone:            "is",
    address_street:   "San Mateo",
    address_unit:     10,
    address_zipcode:  95122,
    address_price_history: 30
  }
]
```