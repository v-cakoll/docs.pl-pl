---
title: "Wskazówki: uzyskiwanie dostępu do usługi OData za pomocą dostawców typów (F#)"
description: "Informacje o sposobie użycia dostawcy typów F # ODataService w F # 3.0 do generowania typów klienta do usługi OData i zapewnia zapytania danych źródeł usługi."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 0adae84c-b0fa-455f-994b-274ecdc6df30
ms.openlocfilehash: 28c2e9a405670f4e5f9512e99e0e6c3e3082856c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-accessing-an-odata-service-by-using-type-providers"></a>Wskazówki: uzyskiwanie dostępu do usługi OData za pomocą dostawców typów

> [!NOTE]
Ten przewodnik został napisany w języku F # 3.0 i zostanie zaktualizowany.  Zobacz [FSharp.Data](http://fsharp.github.io/FSharp.Data/) dla dostawców typów aktualne, między platformami.

> [!NOTE]
Linki odwołań interfejsu API spowoduje przejście do MSDN.  Dokumentacja interfejsu API docs.microsoft.com nie została ukończona.

OData, co oznacza Open Data Protocol, jest protokół transferu danych za pośrednictwem Internetu. Wielu dostawców danych udostępnić dostęp do swoich danych publikowania usługi sieci web OData. Dostęp do danych z dowolnego źródła OData w F # 3.0 używanie typów danych, które są automatycznie generowane przez `ODataService` typ dostawcy. Aby uzyskać więcej informacji na temat OData Zobacz https://msdn.microsoft.com/library/da3380cc-f6da-4c6c-bdb2-bb86afa59d62.

Ten przewodnik zawiera wygenerować typy klienta dla usługi OData przy użyciu dostawcy typów ODataService F # oraz zapytania danych źródeł usługi.

W tym przewodniku opisano następujące zadania, które trzeba wykonać, aby pomyślnie przerobić przewodnik:


- Konfigurowanie projekt klienta do usługi OData
<br />

- Uzyskiwanie dostępu do typów OData
<br />

- Zapytanie usługi OData
<br />

- Sprawdzanie żądań OData
<br />


## <a name="configuring-a-client-project-for-an-odata-service"></a>Konfigurowanie projekt klienta do usługi OData
W tym kroku należy skonfigurować projekt do używania dostawcy typów OData.


#### <a name="to-configure-a-client-project-for-an-odata-service"></a>Aby skonfigurować projekt klienta do usługi OData

- Otwórz projekt aplikacji konsoli F #, a następnie dodaj odwołanie do `System.Data.Services.Client` zestawu struktury.
<br />

- W obszarze `Extensions`, Dodaj odwołanie do `FSharp.Data.TypeProviders` zestawu.
<br />

## <a name="accessing-odata-types"></a>Uzyskiwanie dostępu do typów OData
W tym kroku utworzysz typ dostawcy, która zapewnia dostęp do danych i typów dla usługi OData.


#### <a name="to-access-odata-types"></a>Aby dostęp do tych typów OData

- W edytorze kodu Otwórz plik źródłowy języka F #, a następnie wprowadź poniższy kod.
<br />

```fsharp
open Microsoft.FSharp.Data.TypeProviders


type Northwind = ODataService<"http://services.odata.org/Northwind/Northwind.svc/">

let db = Northwind.GetDataContext()
let fullContext = Northwind.ServiceTypes.NorthwindEntities()
```

W tym przykładzie ma wywołać dostawcy typów F # i nakazał go w celu utworzenia zestawu typów, które są oparte na określonej identyfikatora URI OData. Dostępne są dwa obiekty zawierających informacje o danych; jeden z nich jest kontekst danych uproszczony, `db` w przykładzie. Ten obiekt zawiera tylko typy danych, które są skojarzone z bazy danych, które obejmują typy tabel i źródeł danych. Drugi obiekt `fullContext` w tym przykładzie jest wystąpieniem `System.Data.Linq.DataContext` i zawiera wiele dodatkowych właściwości, metod i zdarzeń.
<br />


## <a name="querying-an-odata-service"></a>Zapytanie usługi OData
W tym kroku wyrażenia zapytania F # służy do wysłać zapytania do usługi OData.


#### <a name="to-query-an-odata-service"></a>Kwerenda usługi OData

1. Teraz, gdy ustawiono typ dostawcy mogą wysyłać zapytania usługi OData.
<br />  OData obsługuje tylko operacje zapytań dostępne. Obsługiwane są następujące operacje oraz ich odpowiednich słów kluczowych:
<br />
  - Projekcja (`select`)
<br />

  - Filtrowanie (`where`, przez użycie ciągu i Data operations)
<br />

  - stronicowanie (`skip`, `take`)
<br />

  - kolejność (`orderBy`, `thenBy`)
<br />

  - `AddQueryOption`i `Expand`, które są zależne od OData operacji
<br />

  Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące LINQ &#40; Usługi danych WCF &#41; ](https://msdn.microsoft.com/library/ee622463.aspx).
<br />  Wszystkie pozycje źródła danych lub tabeli, użyć najprostszej formie wyrażenia zapytania, zgodnie z poniższym kodem:
<br />

```fsharp
query {
  for customer in db.Customers do
  select customer
} |> Seq.iter (fun customer ->
                  printfn "ID: %s\nCompany: %s" customer.CustomerID customer.CompanyName
                  printfn "Contact: %s\nAddress: %s" customer.ContactName customer.Address
                  printfn "         %s, %s %s" customer.City customer.Region customer.PostalCode
                  printfn "%s\n" customer.Phone)
```

2. Określ pola lub kolumny, które mają przy użyciu spójnych kolekcji po słowie kluczowym select.
<br />

```fsharp
  query { 
    for cat in db.Categories do
    select (cat.CategoryID, cat.CategoryName, cat.Description)
  } |> Seq.iter (fun (id, name, description) ->
                    printfn "ID: %d\nCategory: %s\nDescription: %s\n" id name description)
```

3. Określ warunki, używając `where` klauzuli.
<br />

```fsharp
query {
  for employee in db.Employees do
  where (employee.EmployeeID = 9)
  select employee
} |> Seq.iter (fun employee ->
                  printfn "Name: %s ID: %d" (employee.FirstName + " " + employee.LastName) (employee.EmployeeID))
```

4. Określ warunek podciąg do zapytania przy użyciu `System.String.Contains(System.String)` metody. Następujące zapytanie zwraca wszystkie produkty, które mają w nazwach "Chef". Ponadto użycie `System.Nullable<'T>.GetValueOrDefault()`. `UnitPrice` Jest wartość null, dzięki czemu możesz musi uzyskać wartość przy użyciu `Value` właściwości, lub należy wywołać `System.Nullable<'T>.GetValueOrDefault()`.
<br />

```fsharp
query { 
  for product in db.Products do
  where (product.ProductName.Contains("Chef"))
  select product
} |> Seq.iter (fun product ->
                  printfn "ID: %d Product: %s" product.ProductID product.ProductName
                  printfn "Price: %M\n" (product.UnitPrice.GetValueOrDefault()))
```

5. Użyj `System.String.EndsWith(System.String)` metodę, aby określić, że ciąg kończy się niektórych podciąg.
<br />

```fsharp
query {
  for product in db.Products do
  where (product.ProductName.EndsWith("u"))
  select product
} |> Seq.iter (fun product ->
                  printfn "ID: %d Product: %s" product.ProductID product.ProductName
                  printfn "Price: %M\n" (product.UnitPrice.GetValueOrDefault()))
```

6. Łączenie warunków w klauzuli where klauzuli przy użyciu `&&` operatora.
<br />

```fsharp
// Open this module to use the nullable operators ?> and ?<.
open Microsoft.FSharp.Linq.NullableOperators

let salesIn1997 = query { 
  for sales in db.Category_Sales_for_1997 do
  where (sales.CategorySales ?> 50000.00M && sales.CategorySales ?< 60000.0M)
  select sales }

salesIn1997
|> Seq.iter (fun sales ->
                printfn "Category: %s Sales: %M" sales.CategoryName (sales.CategorySales.GetValueOrDefault()))
```

Operatory `?>` i `?<` są operatory dopuszczające wartość null. Można użyć pełny zestaw Operatory równości i porównanie dopuszczające wartość null. Aby uzyskać więcej informacji, zobacz [LINQ.nullableoperators — moduł](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.nullableoperators-module-%5bfsharp%5d).
<br />

7. Użyj `sortBy` zapytań operatora, aby określić kolejność, użyj `thenBy` Aby określić inny poziom kolejności. Ponadto użycie spójnych kolekcji w części zapytania select. W związku z tym zapytanie ma krotka jako typ elementu.
<br />

```fsharp
printfn "Freight for some orders: "

query { 
  for order in db.Orders do
  sortBy (order.OrderDate.Value)
  thenBy (order.OrderID)
  select (order.OrderDate, order.OrderID, order.Customer.CompanyName)
} |> Seq.iter (fun (orderDate, orderID, company) ->
                  printfn "OrderDate: %s" (orderDate.GetValueOrDefault().ToString())
                  printfn "OrderID: %d Company: %s\n" orderID company)
```

8. Ignoruj określoną liczbę rekordów za pomocą operatora skip i użyj operatora podjęcia, aby określić liczbę zwracanych rekordów. W ten sposób można zaimplementować stronicowania na strumieniowych źródeł danych.
<br />

```fsharp
printfn "Get the first page of 2 employees."

query { 
  for employee in db.Employees do
  take 2
  select employee
} |> Seq.iter (fun employee ->
                  printfn "Name: %s ID: %d" (employee.FirstName + " " + employee.LastName) (employee.EmployeeID)) 

printfn "Get the next 2 employees."

query { 
  for employee in db.Employees do
  skip 2
  take 2
  select employee
} |> Seq.iter (fun employee ->
                  printfn "Name: %s ID: %d" (employee.FirstName + " " + employee.LastName) (employee.EmployeeID))
```

## <a name="verifying-the-odata-request"></a>Weryfikowanie żądania OData
Zapytania OData, co jest przetłumaczyć określonego identyfikatora URI żądania OData. Możesz sprawdzić, czy identyfikator URI, być może do debugowania w celach przez dodanie obsługi zdarzeń do `SendingRequest` zdarzenia dla obiekt kontekstu danych.


#### <a name="to-verify-the-odata-request"></a>Aby sprawdzić żądanie OData

- Aby sprawdzić identyfikator URI żądania OData, użyj następującego kodu:
<br />

```fsharp
// The DataContext property returns the full data context.
db.DataContext.SendingRequest.Add (fun eventArgs -> printfn "Requesting %A" eventArgs.Request.RequestUri)
```

Dane wyjściowe poprzedniego kodu to:
<br />`requesting http://services.odata.org/Northwind/Northwind.svc/Orders()?$orderby=ShippedDate&amp;$select=OrderID,ShippedDate`


## <a name="see-also"></a>Zobacz też
[Wyrażenia zapytań](../../language-reference/query-expressions.md)

[Zagadnienia dotyczące LINQ (usługi danych WCF)](https://msdn.microsoft.com/library/ee622463.aspx)

[Odataservice — dostawca typów (F #)](https://msdn.microsoft.com/visualfsharpdocs/conceptual/odataservice-type-provider-%5bfsharp%5d)
