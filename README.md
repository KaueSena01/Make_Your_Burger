<div align="center">
<img src="https://github.com/KaueSena01/Make_Your_Burguer/blob/master/assets/logo.png"/>
<h1>Make Your Burger 🍔</h1>
</div>


<p>📷 Demo video</p>
<img src="https://github.com/KaueSena01/Make_Your_Burguer/blob/master/assets/video1.gif" width="100%"/>
<img src="https://github.com/KaueSena01/Make_Your_Burguer/blob/master/assets/video2.gif" width="100%"/>

### API Settings
```
npm install json-server
```

### Creating the file
* It is necessary that you create a folder in the root of the project with the name of db and inside the folder create a file with the name of db.json.

### Creating the command to run the API
* Then you will go to the package.json file and under build type the following command:
```
"backend":  "json-server --watch db/db.json"
```

### API 
* Copy and paste the json code below into the db.json file.
```
{
  "ingredientes": {
    "paes": [
      {
        "id": 1,
        "tipo": "Italiano Branco"
      },
      {
        "id": 2,
        "tipo": "3 Queijos"
      },
      {
        "id": 3,
        "tipo": "Parmesão e Orégano"
      },
      {
        "id": 4,
        "tipo": "Integral"
      }
    ],
    "carnes": [
      {
        "id": 1,
        "tipo": "Maminha"
      },
      {
        "id": 2,
        "tipo": "Alcatra"
      },
      {
        "id": 3,
        "tipo": "Picanha"
      },
      {
        "id": 4,
        "tipo": "Veggie burger"
      }
    ],
    "opcionais": [
      {
        "id": 1,
        "tipo": "Bacon"
      },
      {
        "id": 2,
        "tipo": "Cheddar"
      },
      {
        "id": 3,
        "tipo": "Salame"
      },
      {
        "id": 4,
        "tipo": "Tomate"
      },
      {
        "id": 4,
        "tipo": "Cebola roxa"
      },
      {
        "id": 4,
        "tipo": "Pepino"
      }
    ]
  },
  "status": [
    {
      "id": 1,
      "tipo": "Solicitado"
    },
    {
      "id": 2,
      "tipo": "Em produção"
    },
    {
      "id": 3,
      "tipo": "Finalizado"
    }
  ],
  "burgers": []
}
```

### Command to start the file
```
npm run backend
```

More about [Json server](https://www.npmjs.com/package/json-server).
