---
title: Funkcje C# obsługujące LINQ
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], features supporting LINQ
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
ms.openlocfilehash: 51cc24fd8054b87b6c92a02450420a9c4abef525
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50191093"
---
# <a name="c-features-that-support-linq"></a>Funkcje C# obsługujące LINQ
Poniższa sekcja wprowadza nowe konstrukcji językowych, wprowadzona w języku C# 3.0. Mimo że te nowe funkcje są używane w stopniu przy użyciu [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania, nie są one ograniczone do [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] i mogą być używane w dowolnym kontekście gdzie można je odnaleźć przydatne.  
  
## <a name="query-expressions"></a>Wyrażenia zapytań  
 Wyrażenia zapytań użyj składni deklaratywnej podobne do bazy danych SQL lub XQuery zapytania za pośrednictwem kolekcji interfejs IEnumerable. Podczas kompilacji czasu Składnia kwerendy jest konwertowany na wywołania metody do [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dostawcy implementację metody standardowego operatora zapytań rozszerzenia. Aplikacje kontrolować standardowych operatorów zapytań, które znajdują się w zakresie, określając odpowiedni obszar nazw z `using` dyrektywy. Poniższe wyrażenie zapytania pobiera tablicę ciągów, grupuje je zgodnie z pierwszego znaku w ciągu i porządkuje grup.  
  
```csharp  
var query = from str in stringArray  
            group str by str[0] into stringGroup  
            orderby stringGroup.Key  
            select stringGroup;  
```  
  
 Aby uzyskać więcej informacji, zobacz [wyrażenia zapytań LINQ](../../../../csharp/programming-guide/linq-query-expressions/index.md).  
  
## <a name="implicitly-typed-variables-var"></a>Niejawnie wpisane zmienne (var)  
 Zamiast jawnego określania typu, jeśli zadeklarujesz i zainicjalizujesz zmienną, możesz użyć [var](../../../../csharp/language-reference/keywords/var.md) modyfikator można nakazać kompilatorowi wywnioskowania i przypisać ten typ, jak pokazano poniżej:  
  
```csharp  
var number = 5;  
var name = "Virginia";  
var query = from str in stringArray  
            where str[0] == 'm'  
            select str;  
```  
  
 Zmienne zadeklarowane jako `var` są po prostu jako silnie typizowaną jako zmienne o typie należy jawnie określić. Korzystanie z `var` sprawia, że można utworzyć typy anonimowe, ale może służyć tylko dla zmiennych lokalnych. Tablice mogą być także zadeklarowane przy użyciu niejawnego wpisywania.  
  
 Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienne lokalne](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
## <a name="object-and-collection-initializers"></a>Inicjatory obiektów i kolekcji  
 Inicjatory obiektów i kolekcji umożliwiają inicjowanie obiektów bez jawnego wywołania konstruktora obiektu. Inicjatory są zwykle używane w wyrażeniach zapytań, gdy ich projektu źródła danych na nowy typ danych. Zakładając, że klasę o nazwie `Customer` z publicznych `Name` i `Phone` właściwości, inicjatora obiektów mogą być używane zgodnie z poniższym kodem:  
  
```csharp  
Customer cust = new Customer { Name = "Mike", Phone = "555-1212" };  
```  
Kontynuując nasze `Customer` klasy, założono, że jest źródło danych o nazwie `IncomingOrders`oraz że dla każdego zamówienia o dużej `OrderSize`, chcielibyśmy utworzyć nową `Customer` na podstawie tej kolejności. Zapytania LINQ mogą być wykonywane w tym źródle danych i użyj inicjowania obiektu, aby wypełnić kolekcję:
```csharp
var newLargeOrderCustomers = from o in IncomingOrders
                            where o.OrderSize > 5
                            select new Customer { Name = o.Name, Phone = o.Phone };
```
Źródło danych może mieć więcej właściwości leżącego kulisy niż `Customer` klasy takie jak `OrderSize`, ale przy użyciu inicjowania obiektu danych zwróconych przez kwerendę jest profilowany na typ danych żądany; Wybierzmy danych, która jest odpowiednia dla klasy Nasze. Co w efekcie mamy `IEnumerable` wypełnione przy użyciu nowego `Customer`Chcieliśmy s. Powyższe można, również będą zapisywane w składni metody LINQ firmy:
```csharp
var newLargeOrderCustomers = IncomingOrders.Where(x => x.OrderSize > 5).Select(y => new Customer { Name = y.Name, Phone = y.Phone });
```
 Aby uzyskać więcej informacji, zobacz:
 
 - [Inicjatory obiektów i kolekcji](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)

 - [Składnia wyrażeń dla standardowych operatorów zapytań](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)

## <a name="anonymous-types"></a>Typy anonimowe  
 Typ anonimowy jest tworzony przez kompilator i nazwę typu jest dostępna tylko dla kompilatora. Typy anonimowe zapewniają wygodny sposób grupowania zestawu właściwości tymczasowo w wyniku zapytania bez konieczności wcześniejszego definiowania oddzielnego typu nazwanego. Typy anonimowe są inicjowane za pomocą nowego wyrażenia i inicjatora obiektów, jak pokazano poniżej:  
  
```csharp
select new {name = cust.Name, phone = cust.Phone};  
```  
  
 Aby uzyskać więcej informacji, zobacz [typy anonimowe](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
## <a name="extension-methods"></a>Metody rozszerzeń  
 Metody rozszerzenia jest statycznej metody, które mogą być skojarzone z typem, dzięki czemu można wywołać, tak jakby był metodą wystąpienia typu. Ta funkcja umożliwia, w efekcie "add" nowych metod do istniejących typów bez faktycznie ich modyfikowania. Standardowe operatory zapytań są zestawem metody rozszerzenia, które zapewniają [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania funkcji dla dowolnego typu, który implementuje <xref:System.Collections.Generic.IEnumerable%601>.  
  
 Aby uzyskać więcej informacji, zobacz [metody rozszerzenia](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).  
  
## <a name="lambda-expressions"></a>Wyrażenia lambda  
 Wyrażenie lambda jest funkcją śródwierszową, który używa = > operator do oddzielania parametrów w treści funkcji wejściowych i mogą być konwertowane w czasie kompilacji do delegata lub drzewo wyrażenia. W [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] programowania, można napotkać wyrażenia lambda po wprowadzeniu wywołania metody bezpośredniej do standardowych operatorów zapytań.  
  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [Funkcje anonimowe](../../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)  
  
-   [Wyrażenia lambda](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
  
-   [Drzewa wyrażeń (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)  
   
## <a name="see-also"></a>Zobacz też

- [Zapytanie o języku zintegrowanym (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)
