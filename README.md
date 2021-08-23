
## Correr

```bash
npm run dev
```

- enviar las cabezeras

content-type: application/json
x-hasura-admin-secret: irOX9JWHWCH8gPvzrePQ6OtUawRC29kiN95QPN1XzZxF2f7v4csByIK1ZyH0mdiz

- Query identificationType tipos de identification

```
query identificationType {
  identificationType {
    id
    name
  }
}


```
- Query tipos de de documentos

```
query ownersType {
  ownersType {
    id
    name
  }
}

```

- Query tipos de construccion

```
query buildingsType {
  buildingsType {
    id
    name
  }
}


```

- Query obtener predios
```

query estates{
  estates{
    appraisalIdentifier
    department
    id
    municipality
    name
  }
}
```

- Mutacion insertar un predio
```
mutation insert_estates_one($object:estates_insert_input!){
  insert_estates_one(object: $object){
    appraisalIdentifier
    department
    id
    municipality
    name
  }
}

----------

variables
{
  "object": {
    "name": "Mi predio en flandes",
    "department": "Cundinamarca",
    "municipality": "Flandes"
  }
}

```

- Mutacion insertar terrero

```
mutation insert_terrains_one ($object:terrains_insert_input!){ 
  insert_terrains_one(object: $object){
    areaSquareMeters
    commercialValue
    estate
    hasBuildings
    id
    isNearWater
    isUrban
  }
}

-----------------------
variables

{
  "object": {
"estate": "af82d4a0-d0da-43de-95b6-9708b2f0e22b",
    "areaSquareMeters": 100,
    "commercialValue": 10000000,
    "hasBuildings": false,
    "isNearWater": false,
    "isUrban": false
  }
}

```
- Query obtener terreros

```
query terrains($where:terrains_bool_exp){
  terrains(where:$where) {
    areaSquareMeters
    commercialValue
    estate
    hasBuildings
    id
    isNearWater
    isUrban
  }
}
___________-
variables
{
  "where": {
"estate": {
  "_eq": "af82d4a0-d0da-43de-95b6-9708b2f0e22b"
}
}
}
```

- Mutacion Insertar construcciones

```
mutation insert_buildings_one($object:buildings_insert_input!){
  insert_buildings_one(object: $object, ){
    address
    buildingType
    estate
    floors
    id
    totalAreaSquareMeters
  }
}
```
- Query obtener construcciones

```
query buildings($where:buildings_bool_exp){
 buildings(where:$where) {
   address
   buildingType
   estate
   floors
   id
   totalAreaSquareMeters
 }
}

___________
variables
{
  "where": {
"estate": {
  "_eq": "af82d4a0-d0da-43de-95b6-9708b2f0e22b"
}
}
}

```

