---
title: Operatory dopuszczające wartość null
description: Dowiedz się więcej o operatory dopuszczające wartość null, które są dostępne w F# języka programowania.
ms.date: 05/16/2016
ms.openlocfilehash: b17c0de2d81a1ef88b31d833a49ff9e3f9d34e8d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61960462"
---
# <a name="nullable-operators"></a>Operatory dopuszczające wartość null

Operatory dopuszczające wartość null są operatory dwuargumentowe arytmetycznych lub porównaniach, współpracujących z typami zerowalnymi arytmetyczne na jednej lub obu stronach. Typy dopuszczające wartości zerowe pojawiają się często, podczas pracy z danymi ze źródeł, takich jak bazy danych, które dopuszcza wartości null, zamiast rzeczywistych wartości. Operatory dopuszczające wartość null są często używane w wyrażeniach zapytań. Oprócz operatory dopuszczające wartość null dla operacji arytmetycznych i porównanie operatory konwersji może służyć do konwersji między typy dopuszczające wartości null. Istnieją również nullable wersje niektórych operatorów zapytań.

## <a name="table-of-nullable-operators"></a>Tabela operatory dopuszczające wartość null

W poniższej tabeli wymieniono operatory dopuszczające wartość null, obsługiwane w F# języka.

|Dopuszcza wartości null po lewej stronie|Dopuszcza wartości null w prawo|Obie strony dopuszczającego wartość null|
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

Operatory dopuszczające wartość null znajdują się w [NullableOperators](https://msdn.microsoft.com/library/2c3633c5-3f31-4d62-a9f8-272ad6b19007) modułu w przestrzeni nazw [Microsoft.fsharp.LINQ —](https://msdn.microsoft.com/library/4765b4e8-4006-4d8c-a405-39c218b3c82d). Typ danych dopuszczających wartość null jest `System.Nullable<'T>`.

Typy dopuszczające wartości null w wyrażeniach zapytań pojawiają się podczas wybierania danych ze źródła danych, które umożliwia wartości null, zamiast wartości. W bazie danych programu SQL Server każdą kolumnę danych w tabeli ma atrybut, który wskazuje, czy są dozwolone wartości null. Jeśli wartości null są dozwolone, dane zwrócone z bazy danych może zawierać wartości null, niemożliwe do przedstawienia przez typ danych pierwotnych takich jak `int`, `float`i tak dalej. W związku z tym, dane są zwracane jako `System.Nullable<int>` zamiast `int`, i `System.Nullable<float>` zamiast `float`. Można uzyskać wartości rzeczywistej `System.Nullable<'T>` obiektu za pomocą `Value` właściwości, na które można określić, czy `System.Nullable<'T>` obiekt ma wartość, przez wywołanie metody `HasValue` metody. Inną metodą przydatne jest `System.Nullable<'T>.GetValueOrDefault` metody, która umożliwia uzyskanie wartość lub wartość domyślną odpowiedniego typu. Wartość domyślna to pewnego rodzaju wartość "zero", np. 0, 0.0, lub `false`.

Typy dopuszczające wartości zerowe może zostać przekonwertowana na dopuszcza typy pierwotne, takie jak korzystanie z operatorów konwersji zwykle `int` lub `float`. Istnieje również możliwość konwersji z jednego typu dopuszczającego wartość null do innego typu dopuszczającego wartość null, przy użyciu operatorów konwersji dla typów dopuszczających wartości null. Operatory konwersji odpowiednie mają taką samą nazwę jak to standardowe, ale są one oddzielny moduł [Nullable](https://msdn.microsoft.com/library/e7a4ea13-28cc-462e-bc3a-33131ace976e) modułu w [Microsoft.fsharp.LINQ —](https://msdn.microsoft.com/library/4765b4e8-4006-4d8c-a405-39c218b3c82d) przestrzeni nazw. Zazwyczaj, możesz otworzyć ten obszar nazw podczas pracy z wyrażenia zapytania. W takim przypadku można używać operatorów konwersji dopuszczającego wartość null, dodając prefiks `Nullable.` operatora odpowiedniej konwersji, jak pokazano w poniższym kodzie.

```fsharp
open Microsoft.FSharp.Linq

let nullableInt = new System.Nullable<int>(10)

// Use the Nullable.float conversion operator to convert from one nullable type to another nullable type.
let nullableFloat = Nullable.float nullableInt

// Use the regular non-nullable float operator to convert to a non-nullable float.
printfn "%f" (float nullableFloat)
```

Dane wyjściowe są `10.000000`.

Zapytanie operatorów w polach danych dopuszczających wartość null, takie jak `sumByNullable`, dostępne są także do użycia w wyrażeniach zapytań. Operatory zapytań dla typów innych niż null nie są typu zgodnego z typami zerowalnymi, więc nullable wersję operator odpowiednich zapytań należy użyć podczas pracy z wartościami danych dopuszczających wartość null. Aby uzyskać więcej informacji, zobacz [wyrażenia zapytań](../query-expressions.md).

Poniższy przykład pokazuje użycie operatory dopuszczające wartość null w F# wyrażeniu zapytania. Pierwsze zapytanie pokazuje, jak należy napisać zapytanie bez operatora dopuszczającego wartość null; drugie zapytanie zawiera równoważne zapytanie, które używa operatora dopuszczającego wartość null. Dla pełnego kontekstu, w tym sposób konfigurowania bazy danych, aby użyć przykładowego kodu, zobacz [instruktażu: Uzyskiwanie dostępu do bazy danych SQL za pomocą dostawców typów](../../tutorials/type-providers/accessing-a-sql-database.md).

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

## <a name="see-also"></a>Zobacz także

- [Dostawcy typów](../../tutorials/type-providers/index.md)
- [Wyrażenia zapytania](../query-expressions.md)