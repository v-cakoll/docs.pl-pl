---
title: Funkcje C# obsługujące LINQ
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], features supporting LINQ
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
ms.openlocfilehash: c617b2d7b56618867fe92cbe1d9ee04aa4c3ab64
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44035934"
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
  
 Aby uzyskać więcej informacji, zobacz [inicjatory obiektów i kolekcji](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
## <a name="anonymous-types"></a>Typy anonimowe  
 Typ anonimowy jest tworzony przez kompilator i nazwę typu jest dostępna tylko dla kompilatora. Typy anonimowe zapewniają wygodny sposób grupowania zestawu właściwości tymczasowo w wyniku zapytania bez konieczności wcześniejszego definiowania oddzielnego typu nazwanego. Typy anonimowe są inicjowane za pomocą nowego wyrażenia i inicjatora obiektów, jak pokazano poniżej:  
  
```  
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
  
## <a name="auto-implemented-properties"></a>Właściwości zaimplementowane automatycznie  
 Właściwości zaimplementowane automatycznie wprowadzić bardziej zwięzły widok deklaracja właściwości. Kiedy Deklarujesz właściwości, jak pokazano w poniższym przykładzie, kompilator utworzy polem zapasowym prywatne i anonimowy, który nie jest dostępny z wyjątkiem za pośrednictwem właściwości getter i setter.  
  
```csharp  
public string Name {get; set;}  
```  
  
 Aby uzyskać więcej informacji, zobacz [implemented Properties](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).  
  
## <a name="see-also"></a>Zobacz też

- [Zapytanie o języku zintegrowanym (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)
