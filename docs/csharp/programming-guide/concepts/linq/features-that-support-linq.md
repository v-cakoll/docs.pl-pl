---
title: Funkcje C# obsługujące LINQ
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], features supporting LINQ
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
ms.openlocfilehash: 9fc8adaa49d02f8b69c2db6e94a28b9fab36b3b0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635798"
---
# <a name="c-features-that-support-linq"></a>Funkcje C# obsługujące LINQ

W poniższej sekcji przedstawiono nowe konstrukcje języka wprowadzone w języku C# 3.0. Mimo że te nowe funkcje są używane w stopniu z zapytaniami LINQ, nie są one ograniczone do LINQ i mogą być używane w dowolnym kontekście, w którym można je znaleźć przydatne.

## <a name="query-expressions"></a>Wyrażenia kwerend

Wyrażenia kwerend y używają składni deklaratywnej podobnej do SQL lub XQuery do wykonywania zapytań za pomocą kolekcji Numerowanych. W kompie czas składnia kwerendy jest konwertowany na wywołania metody do implementacji dostawcy LINQ standardowych metod rozszerzenia operatora kwerendy. Aplikacje kontrolują standardowe operatory zapytań, które znajdują się `using` w zakresie, określając odpowiedni obszar nazw za pomocą dyrektywy. Następujące wyrażenie kwerendy przyjmuje tablicę ciągów, grupuje je według pierwszego znaku w ciągu i porządkuje grupy.

```csharp
var query = from str in stringArray
            group str by str[0] into stringGroup
            orderby stringGroup.Key
            select stringGroup;
```

Aby uzyskać więcej informacji, zobacz [WYRAŻENIA ZAPytań LINQ](../../../linq/index.md).

## <a name="implicitly-typed-variables-var"></a>Zmienne wpisane niejawnie (var)

Zamiast jawnie określać typ podczas deklarowania i inicjowania zmiennej, można użyć modyfikatora [var,](../../../language-reference/keywords/var.md) aby poinstruować kompilator, aby wywnioskować i przypisać typ, jak pokazano poniżej:

```csharp
var number = 5;
var name = "Virginia";
var query = from str in stringArray
            where str[0] == 'm'
            select str;
```

Zmienne zadeklarowane `var` jako są tak samo silnie typizowane jako zmienne, których typ określa się jawnie. Użycie `var` umożliwia tworzenie typów anonimowych, ale może służyć tylko dla zmiennych lokalnych. Tablice mogą być również deklarowane z niejawnym wpisywaniem.

Aby uzyskać więcej informacji, zobacz [Niejawnie wpisane zmienne lokalne](../../classes-and-structs/implicitly-typed-local-variables.md).

## <a name="object-and-collection-initializers"></a>Inicjatory obiektów i kolekcji

Inicjatory obiektów i kolekcji umożliwiają inicjowanie obiektów bez jawnego wywoływania konstruktora dla obiektu. Inicjatory są zwykle używane w wyrażeniach kwerend, gdy projektują dane źródłowe do nowego typu danych. Zakładając, że `Customer` klasa `Name` `Phone` o nazwie public i właściwości, inicjatora obiektu może służyć jak w następującym kodzie:

```csharp
var cust = new Customer { Name = "Mike", Phone = "555-1212" };
```

Kontynuując naszą `Customer` klasę, załóżmy, że `IncomingOrders`istnieje źródło danych o `OrderSize`nazwie , i że `Customer` dla każdego zamówienia z dużym , chcielibyśmy stworzyć nowy oparty na tej kolejności. Kwerenda LINQ mogą być wykonywane na tym źródle danych i używać inicjowania obiektu do wypełnienia kolekcji:

```csharp
var newLargeOrderCustomers = from o in IncomingOrders
                            where o.OrderSize > 5
                            select new Customer { Name = o.Name, Phone = o.Phone };
```

Źródło danych może mieć więcej właściwości leżących `Customer` pod `OrderSize`maską niż klasa, takich jak , ale z inicjowania obiektu, dane zwrócone z kwerendy jest formowane do żądanego typu danych; wybieramy dane, które są istotne dla naszej klasy. W rezultacie mamy teraz `IEnumerable` wypełnione nowym `Customer`s chcieliśmy. Powyższe można również zapisać w składni metody LINQ:

```csharp
var newLargeOrderCustomers = IncomingOrders.Where(x => x.OrderSize > 5).Select(y => new Customer { Name = y.Name, Phone = y.Phone });
```

Aby uzyskać więcej informacji, zobacz:

- [Inicjatory obiektów i kolekcji](../../classes-and-structs/object-and-collection-initializers.md)

- [Składnia wyrażeń dla standardowych operatorów zapytań](./query-expression-syntax-for-standard-query-operators.md)

## <a name="anonymous-types"></a>Typy anonimowe

Typ anonimowy jest konstruowany przez kompilator, a nazwa typu jest dostępna tylko dla kompilatora. Typy anonimowe zapewniają wygodny sposób grupowania zestawu właściwości tymczasowo w wyniku kwerendy bez konieczności definiowania oddzielnego typu o nazwie. Typy anonimowe są inicjowane z nowym wyrażeniem i inicjatorem obiektu, jak pokazano poniżej:

```csharp
select new {name = cust.Name, phone = cust.Phone};
```

Aby uzyskać więcej informacji, zobacz [Typy anonimowe](../../classes-and-structs/anonymous-types.md).

## <a name="extension-methods"></a>Metody rozszerzeń

Metoda rozszerzenia jest metodą statyczną, która może być skojarzona z typem, dzięki czemu może być wywoływana tak, jakby była metodą wystąpienia typu. Ta funkcja umożliwia, w efekcie, "dodawanie" nowych metod do istniejących typów bez ich modyfikowania. Standardowe operatory zapytań to zestaw metod rozszerzenia, które zapewniają funkcje kwerendy LINQ dla dowolnego typu, który implementuje <xref:System.Collections.Generic.IEnumerable%601>.

Aby uzyskać więcej informacji, zobacz [Metody rozszerzenia](../../classes-and-structs/extension-methods.md).

## <a name="lambda-expressions"></a>Wyrażenia lambda

Wyrażenie lambda jest funkcją inline, która używa => operatora do oddzielenia parametrów wejściowych od treści funkcji i może być konwertowane w czasie kompilacji do delegata lub drzewa wyrażeń. W programowaniu LINQ napotkasz wyrażenia lambda podczas wykonywania wywołań metody bezpośredniej do standardowych operatorów zapytań.

Aby uzyskać więcej informacji, zobacz:

- [Funkcje anonimowe](../../statements-expressions-operators/anonymous-functions.md)

- [Wyrażenia Lambda](../../statements-expressions-operators/lambda-expressions.md)

- [Drzewa wyrażeń (C#)](../expression-trees/index.md)

## <a name="see-also"></a>Zobacz też

- [Zapytanie zintegrowane z językiem (LINQ) (C#)](./index.md)
