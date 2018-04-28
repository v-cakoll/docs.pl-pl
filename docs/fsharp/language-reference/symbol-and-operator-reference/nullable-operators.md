---
title: Operatory dopuszczające wartość null (F#)
description: 'Więcej informacji na temat operatory dopuszczające wartość null, które są dostępne w języku programowania w języku F #.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 37025e16768b949b51f6b9f0cff32e88da110ca8
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="nullable-operators"></a>Operatory dopuszczające wartość null

Operatory dopuszczające wartość null są operatorów binarnych arytmetycznego lub porównanie, które współpracują z typy dopuszczające wartości zerowe arytmetycznego na jednej lub obu stronach. Typy dopuszczające wartości zerowe pojawiają się często, podczas pracy z danymi ze źródeł, takich jak bazy danych, które dopuszcza wartości null zamiast wartości rzeczywistych. Operatory dopuszczające wartość null są często używane w wyrażeniach zapytań. Oprócz operatory dopuszczające wartość null dla arytmetyczne i porównanie operatory konwersji umożliwia konwertowanie typów dopuszczających wartości zerowe. Dostępne są również nullable wersje operatorów zapytania.


## <a name="table-of-nullable-operators"></a>Tabela operatory dopuszczające wartość null
W poniższej tabeli wymieniono obsługiwane w języku F # operatory dopuszczające wartość null.

|Wartości null po lewej stronie|Wartości null na prawo|Obie strony dopuszczające wartości zerowe|
|---|---|---|
|[?>=](https://msdn.microsoft.com/library/94d29e32-a204-4f60-a527-6b0af86268f3)|[>=?](https://msdn.microsoft.com/library/0a255d8e-8cae-4160-ae61-243a5d96583f)|[?>=?](https://msdn.microsoft.com/library/3051a50f-d276-4c84-9d73-bf2efeddef94)|
|[?>](https://msdn.microsoft.com/library/62dc0021-1312-4ac3-be87-798b60b81bb6)|[>?](https://msdn.microsoft.com/library/0ad1284b-de48-4a04-83d8-b6f13c9c8936)|[?>?](https://msdn.microsoft.com/library/dc18b6fa-30c4-47b0-9057-794439378a05)|
|[?<=](https://msdn.microsoft.com/library/56fddf0a-e4ca-4891-a3be-fad1876be3b6)|[<=?](https://msdn.microsoft.com/library/02454a0f-30ca-4e77-ad84-ee7837461804)|[?<=?](https://msdn.microsoft.com/library/5c37c28c-0b57-4da5-be11-5a123f7e8ee4)|
|[?<](https://msdn.microsoft.com/library/b71897f0-6e29-4c58-b0a7-a5bfa6f88917)|[<?](https://msdn.microsoft.com/library/be9ea40f-a67f-4e98-8067-a14046752e8b)|[?<?](https://msdn.microsoft.com/library/6f1962c8-5605-468c-94ae-f379ae98e17d)|
|[?=](https://msdn.microsoft.com/library/5cdc8ff6-244b-49cf-9376-69ecf249fd7c)|[=?](https://msdn.microsoft.com/library/d2102894-6a51-475d-890a-735568c31f87)|[?=?](https://msdn.microsoft.com/library/5f793f29-1084-4570-b1c1-17c1b7ef764b)|
|[?<>](https://msdn.microsoft.com/library/3643a5a8-2ea5-4ad6-82c4-83927c3884a0)|[<>?](https://msdn.microsoft.com/library/3179aace-70c4-4911-9258-619592214976)|[?<>?](https://msdn.microsoft.com/library/5da813d8-ee75-45b8-9ef4-146dcb6d394d)|
|[?+](https://msdn.microsoft.com/library/2e8ddd05-b3f3-41b3-9d73-938d9e540f3f)|[+?](https://msdn.microsoft.com/library/74772ea8-f010-493e-bdb5-ba347f2fd4f1)|[?+?](https://msdn.microsoft.com/library/57f28137-0f42-43d2-92af-cad8c6c9d05f)|
|[?-](https://msdn.microsoft.com/library/f237a7a6-89f2-48b2-a2fe-f0b98a2bedc2)|[-?](https://msdn.microsoft.com/library/4a345c07-314a-48f1-b557-ce072583589c)|[?-?](https://msdn.microsoft.com/library/e0024142-1d2a-4607-a39c-1eb1e86fa25a)|
|[?*](https://msdn.microsoft.com/library/519da708-5ad6-4075-9d74-d00441cd6078)|[*?](https://msdn.microsoft.com/library/04c47870-de7b-480d-98a0-f47593b4ffac)|[?*?](https://msdn.microsoft.com/library/e57057ba-9c3a-40ec-8401-150c2b25f75b)|
|[?/](https://msdn.microsoft.com/library/add02a42-f556-40a7-a168-fbf2053322e3)|[/?](https://msdn.microsoft.com/library/1de07646-3778-476d-8c61-5d37495d463c)|[?/?](https://msdn.microsoft.com/library/b17be0ac-bf98-4590-861d-a4dd6c6fa535)|
|[?%](https://msdn.microsoft.com/library/44297bba-1bd9-4ed2-a848-f1e1e598db87)|[%?](https://msdn.microsoft.com/library/a4c178e5-eec4-42e8-847f-90b24fc609fe)|[?%?](https://msdn.microsoft.com/library/dd555f20-1be3-4b8d-81f1-bf1921e62fda)|

## <a name="remarks"></a>Uwagi
Operatory dopuszczające wartość null są uwzględnione w [NullableOperators](https://msdn.microsoft.com/library/2c3633c5-3f31-4d62-a9f8-272ad6b19007) moduł w przestrzeni nazw [Microsoft.fsharp.LINQ —](https://msdn.microsoft.com/library/4765b4e8-4006-4d8c-a405-39c218b3c82d). Typ danych wartości null jest `System.Nullable<'T>`.

W wyrażeniach zapytań typy dopuszczające wartości zerowe wystąpić, gdy wybór danych ze źródła danych, umożliwiający zamiast wartości na wartości null. W bazie danych programu SQL Server każda kolumna danych w tabeli ma atrybut, który wskazuje, czy są dozwolone wartości null. Jeśli są dozwolone wartości null, danych zwróconych z bazy danych może zawierać wartości null, które nie może być reprezentowany przez typ danych pierwotnych takich jak `int`, `float`i tak dalej. W związku z tym dane są zwracane jako `System.Nullable<int>` zamiast `int`, i `System.Nullable<float>` zamiast `float`. Bieżąca wartość można uzyskać od `System.Nullable<'T>` obiektu za pomocą `Value` właściwości oraz można określić, czy `System.Nullable<'T>` obiekt ma wartość, wywołując `HasValue` — metoda. Inną metodą przydatne jest `System.Nullable<'T>.GetValueOrDefault` metody, dzięki czemu można uzyskać wartość lub wartość domyślną odpowiedniego typu. Wartość domyślna to jakiegoś typu "zero" wartość, na przykład 0, 0.0, lub `false`.

Typy dopuszczające wartości null, mogą być konwertowane na wartości null typy pierwotne, takie jak przy użyciu operatorów konwersji zwykle `int` lub `float`. Istnieje również możliwość do konwersji z jednego typu dopuszczającego wartości null do innego typu dopuszczającego wartości null przy użyciu operatorów konwersji na typy dopuszczające wartości zerowe. Operatory konwersji odpowiednie ma taką samą nazwę jak standardowe, ale są one w oddzielnych module [Nullable](https://msdn.microsoft.com/library/e7a4ea13-28cc-462e-bc3a-33131ace976e) modułu w [Microsoft.fsharp.LINQ —](https://msdn.microsoft.com/library/4765b4e8-4006-4d8c-a405-39c218b3c82d) przestrzeni nazw. Zazwyczaj możesz otworzyć ten obszar nazw, podczas pracy z wyrażenia zapytania. W takim przypadku można używać operatorów konwersji wartości null, dodając prefiks `Nullable.` operatora konwersji odpowiednie, jak pokazano w poniższym kodzie.

```fsharp
open Microsoft.FSharp.Linq

let nullableInt = new System.Nullable<int>(10)

// Use the Nullable.float conversion operator to convert from one nullable type to another nullable type.
let nullableFloat = Nullable.float nullableInt

// Use the regular non-nullable float operator to convert to a non-nullable float.
printfn "%f" (float nullableFloat)
```

Dane wyjściowe `10.000000`.

Zapytanie operatory na pola danych wartości null, takich jak `sumByNullable`, istnieją również do użycia w wyrażeniach zapytań. Operatory zapytań dla typów wartości null nie są typu zgodnego z typy dopuszczające wartości null, więc należy użyć wartości null wersji operator zapytania odpowiednie podczas pracy z wartościami danych o wartości null. Aby uzyskać więcej informacji, zobacz [wyrażenia zapytania](../query-expressions.md).

Poniższy przykład przedstawia użycie operatory dopuszczające wartość null w wyrażeniu kwerendy F #. Pierwsza kwerenda pokazuje, jak będzie napisać zapytanie bez operatora wartości null; drugiego zapytania zawiera równoważne zapytanie, które używa operatora wartości null. Pełna kontekstu, oraz o sposobie konfigurowania bazy danych, aby użyć tego przykładowego kodu, zobacz [wskazówki: uzyskiwanie dostępu do bazy danych SQL za pomocą dostawców typów](../../tutorials/type-providers/accessing-a-sql-database.md).

```fsharp
open System
open System.Data
open System.Data.Linq
open Microsoft.FSharp.Data.TypeProviders
open Microsoft.FSharp.Linq

[<Generate>]
type dbSchema = SqlDataConnection<"Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;">

let db = dbSchema.GetDataContext()

query {
    for row in db.Table2 do
    where (row.TestData1.HasValue && row.TestData1.Value > 2)
    select row
} |> Seq.iter (fun row -> printfn "%d %s" row.TestData1.Value row.Name)

query {
    for row in db.Table2 do
    // Use a nullable operator ?>
    where (row.TestData1 ?> 2)
    select row
} |> Seq.iter (fun row -> printfn "%d %s" (row.TestData1.GetValueOrDefault()) row.Name)
```

## <a name="see-also"></a>Zobacz też

[Dostawcy typów](../../tutorials/type-providers/index.md)

[Wyrażenia zapytania](../query-expressions.md)
