---
title: Funkcje C# obsługujące LINQ
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], features supporting LINQ
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
ms.openlocfilehash: 1029d34ae8823fe91c7e4bc92e168fcc1061c707
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594404"
---
# <a name="c-features-that-support-linq"></a>Funkcje C# obsługujące LINQ

W poniższej sekcji wprowadzono nowe konstrukcje języka wprowadzone w C# 3,0. Mimo że te nowe funkcje są używane do stopnia z [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytaniami, nie są ograniczone do [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] i mogą być używane w dowolnym kontekście, w którym są użyteczne.

## <a name="query-expressions"></a>Wyrażenia kwerend

Wyrażenia zapytań używają składni deklaracyjnej podobnej do SQL lub XQuery w celu wykonywania zapytań na kolekcjach IEnumerable. W czasie kompilacji Składnia zapytania jest konwertowana na wywołania metody do [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] implementacji dostawcy standardowych metod rozszerzenia operatora zapytania. Aplikacje kontrolują standardowe operatory zapytań, które znajdują się w zakresie przez określenie odpowiedniej przestrzeni `using` nazw z dyrektywą. Następujące wyrażenie zapytania pobiera tablicę ciągów, grupuje je według pierwszego znaku w ciągu i porządkuje grupy.

```csharp
var query = from str in stringArray
            group str by str[0] into stringGroup
            orderby stringGroup.Key
            select stringGroup;
```

Aby uzyskać więcej informacji, zobacz [wyrażenia zapytań LINQ](../../linq-query-expressions/index.md).

## <a name="implicitly-typed-variables-var"></a>Niejawnie wpisane zmienne (var)

Zamiast jawnie określić typ podczas deklarowania i inicjowania zmiennej, można użyć modyfikatora [var](../../../language-reference/keywords/var.md) , aby nakazać kompilatorowi wywnioskowanie i przypisanie typu, jak pokazano poniżej:

```csharp
var number = 5;
var name = "Virginia";
var query = from str in stringArray
            where str[0] == 'm'
            select str;
```

Zmienne zadeklarowane `var` jako są równie silnie wpisywane jako zmienne, których typ określa się jawnie. Użycie `var` systemu umożliwia tworzenie typów anonimowych, ale może być używane tylko dla zmiennych lokalnych. Tablice mogą być również deklarowane przy użyciu niejawnego wpisywania.

Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienne lokalne](../../classes-and-structs/implicitly-typed-local-variables.md).

## <a name="object-and-collection-initializers"></a>Inicjatory obiektów i kolekcji

Inicjatory obiektów i kolekcji umożliwiają inicjowanie obiektów bez jawnego wywoływania konstruktora dla obiektu. Inicjatory są zwykle używane w wyrażeniach zapytań, gdy projektują dane źródłowe do nowego typu danych. Przy założeniu klasy `Customer` o nazwie `Name` z `Phone` publiczną i właściwością inicjatora obiektów można używać tak jak w poniższym kodzie:

```csharp
var cust = new Customer { Name = "Mike", Phone = "555-1212" };
```

Kontynuując pracę `Customer` z naszą klasą, Załóżmy, że istnieje źródło `IncomingOrders`danych o nazwie i że dla każdego zamówienia z `OrderSize`dużą, chcemy utworzyć nową `Customer` wartość na podstawie tej kolejności. Zapytanie LINQ można wykonać w tym źródle danych i użyć inicjalizacji obiektu do wypełnienia kolekcji:

```csharp
var newLargeOrderCustomers = from o in IncomingOrders
                            where o.OrderSize > 5
                            select new Customer { Name = o.Name, Phone = o.Phone };
```

Źródło danych może mieć więcej właściwości znajdujących się pod okapem niż `Customer` Klasa, taka `OrderSize`jak, ale z inicjalizacją obiektu, dane zwrócone z zapytania są Molded do żądanego typu danych. wybieramy dane, które są istotne dla naszej klasy. W związku z tym mamy teraz `IEnumerable` wypełnioną nową, pożądaną nowością. `Customer` Powyższe dane można także napisać w składni metody LINQ:

```csharp
var newLargeOrderCustomers = IncomingOrders.Where(x => x.OrderSize > 5).Select(y => new Customer { Name = y.Name, Phone = y.Phone });
```

Aby uzyskać więcej informacji, zobacz:

- [Inicjatory obiektów i kolekcji](../../classes-and-structs/object-and-collection-initializers.md)

- [Składnia wyrażeń dla standardowych operatorów zapytań](./query-expression-syntax-for-standard-query-operators.md)

## <a name="anonymous-types"></a>Typy anonimowe

Typ anonimowy jest konstruowany przez kompilator, a nazwa typu jest dostępna tylko dla kompilatora. Typy anonimowe umożliwiają wygodne grupowanie zestawu właściwości w wyniku zapytania, bez konieczności definiowania oddzielnego nazwanego typu. Typy anonimowe są inicjowane za pomocą nowego wyrażenia i inicjatora obiektów, jak pokazano poniżej:

```csharp
select new {name = cust.Name, phone = cust.Phone};
```

Aby uzyskać więcej informacji, zobacz [Typy anonimowe](../../classes-and-structs/anonymous-types.md).

## <a name="extension-methods"></a>Metody rozszerzeń

Metoda rozszerzenia to metoda statyczna, która może być skojarzona z typem, tak aby można ją było wywołać tak, jakby była metodą wystąpienia w typie. Ta funkcja umożliwia, w efekcie, "dodać" nowe metody do istniejących typów bez ich faktycznego modyfikowania. Standardowe operatory zapytań to zestaw metod rozszerzających, które udostępniają [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] funkcje zapytania dla dowolnego typu, który <xref:System.Collections.Generic.IEnumerable%601>implementuje.

Aby uzyskać więcej informacji, zobacz [metody rozszerzenia](../../classes-and-structs/extension-methods.md).

## <a name="lambda-expressions"></a>Wyrażenia lambda

Wyrażenie lambda jest funkcją wbudowaną, która używa operatora = > do oddzielania parametrów wejściowych od treści funkcji i może być konwertowana w czasie kompilacji do delegata lub drzewa wyrażenia. W [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] programowaniu podczas tworzenia wywołań metod bezpośrednich do standardowych operatorów zapytań są wyświetlane wyrażenia lambda.

Aby uzyskać więcej informacji, zobacz:

- [Funkcje anonimowe](../../statements-expressions-operators/anonymous-functions.md)

- [Wyrażenia lambda](../../statements-expressions-operators/lambda-expressions.md)

- [Drzewa wyrażeń (C#)](../expression-trees/index.md)

## <a name="see-also"></a>Zobacz także

- [Zapytanie zintegrowane z językiem (LINQ)C#()](./index.md)
