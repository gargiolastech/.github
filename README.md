<!-- ⚠️ AUTO-GENERATED FILE. DO NOT EDIT DIRECTLY. -->
# 🌐 Hub Organizzazione

Questo README aggrega automaticamente i contenuti dai repository elencati in `.config/repos.json`.

---

## 📚 Indice
- [Engineering Snippets](#engineering-snippets)

---

### Engineering Snippets

<!-- INCLUDE: gargiolastech/engineering-snippets@main:README.md -->
<!-- BEGIN INCLUDE: gargiolastech/engineering-snippets@main:README.md -->

> Fonte: `gargiolastech/engineering-snippets@main:README.md`

# engineering-snippets
Snippet mirati e piccoli esempi


All'interno troverai codice da utilizzare per implementare all'interno della applicazioni

- [specification-pattern](https://github.com/gargiolastech/engineering-snippets/tree/main/snippets/csharp/specification-pattern)

# Gestione dati sensibili

Non bisogna mai rilasciare informazioni sensibili all'interno dei repository in modo da evitare data leakage.


Bisogna stabilire una “strategia di sorgenti” per ambiente

## Dev locale

La scelta migliore è utilizzare gli User Secrets o eventualmente .env (solo se non versionato)

### Configurazione

 - Posizionarsi all'interno della folder del progetto in cui desideriamo gestire i Secrets
 - Da terminale effettuare l'inizializzazione mediante: dotnet user-secrets init
    
   all'interno del .csproj troviamo la nuova sezione *UserSecretsId* che conterrà una chiave
   identificativa che potrà essere tranquillamente pushata sul repos in quanto non è un secret
   
``` xml
	<PropertyGroup>
	  <TargetFramework>net9.0</TargetFramework>
	  *<UserSecretsId>ecs-api-dev</UserSecretsId>*
	</PropertyGroup>
```

  - Aggiungere una chiave all'interno dei Secrets
    
	dotnet user-secrets set "LaunchDarkly:SdkKey" "sdk-xxxxxxxxxxxxxxxx"
	
  - Visualizzare tutti i secret
  
    dotnet user-secrets list
	
  E' possibile anche restare in src e specificare il progetto:
  
``` powershell
    dotnet user-secrets init --project .\Ecs.Api\Ecs.Api.csproj
```

  e poi:

``` powershell
	dotnet user-secrets set "LaunchDarkly:SdkKey" "sdk-xxx" --project .\Ecs.Api\Ecs.Api.csproj
```
	
 NB. I secrets non stanno nel progetto.

	Percorso tipico:

	Windows
	%APPDATA%\Microsoft\UserSecrets\<UserSecretsId>\secrets.json

	macOS/Linux
	~/.microsoft/usersecrets/<UserSecretsId>/secrets.json

In Development, l’ordine tipico è:

- appsettings.json
- appsettings.Development.json
- User Secrets
- Environment Variables

👉 User Secrets sovrascrivono i file JSON.


## CI/CD

Environment Variables (iniettate da pipeline)


# utility

- [flow-launcher](https://github.com/gargiolastech/engineering-snippets/tree/main/snippets/utility/README.md)

<!-- END INCLUDE: gargiolastech/engineering-snippets@main:README.md -->

---
