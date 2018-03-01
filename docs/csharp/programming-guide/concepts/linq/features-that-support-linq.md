---
title: "Funkcje C# obsługujące LINQ"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- LINQ [C#], features supporting LINQ
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2f5accb188e54e0d3e2b941832637ec33afc26b2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="c-features-that-support-linq"></a>Funkcje C# obsługujące LINQ
Poniższa sekcja wprowadza nowe konstrukcje języka wprowadzono w języku C# 3.0. Chociaż te nowe funkcje są używane w stopniu z [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytań, nie są one ograniczone do [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] i mogą być używane w dowolnym kontekście gdzie użyteczna je.  
  
## <a name="query-expressions"></a>Wyrażenia zapytań  
 Wyrażenia zapytań użyj składni deklaratywnej podobne do bazy danych SQL lub XQuery zapytania za pośrednictwem interfejsu IEnumerable kolekcji. W kompilacji czasu Składnia kwerendy jest konwertowana na wywołania metody do [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dostawcy implementacja metody rozszerzenia operator standardowej kwerendy. Aplikacje kontroli standardowych operatorów zapytań, które znajdują się w zakresie, określając odpowiedni obszar nazw z `using` dyrektywy. Poniższe wyrażenie zapytania pobiera tablicę ciągów, grupy, zgodnie z pierwszego znaku w ciągu i porządkuje grup.  
  
```  
var query = from str in stringArray  
            group str by str[0] into stringGroup  
            orderby stringGroup.Key  
            select stringGroup;  
```  
  
 Aby uzyskać więcej informacji, zobacz [wyrażenia zapytań LINQ](../../../../csharp/programming-guide/linq-query-expressions/index.md).  
  
## <a name="implicitly-typed-variables-var"></a>Niejawnie wpisane zmienne (var)  
 Zamiast jawne określenie typu, gdy zadeklarować i zainicjuj zmienną, możesz użyć [var](../../../../csharp/language-reference/keywords/var.md) modyfikator nakazać kompilatora wnioskować i przypisać ten typ, jak pokazano poniżej:  
  
```  
var number = 5;  
var name = "Virginia";  
var query = from str in stringArray  
            where str[0] == 'm'  
            select str;  
```  
  
 Zmienne zadeklarowane jako `var` są po prostu jako silnie typizowaną jako zmienne o typie, określ w sposób jawny. Korzystanie z `var` sprawia, że można tworzyć typy anonimowe, ale może służyć do dowolnej zmiennej lokalnej. Ponadto można deklarować tablic w trakcie pisania niejawne.  
  
 Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienne lokalne](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
## <a name="object-and-collection-initializers"></a>Inicjatory obiektów i kolekcji  
 Inicjatory obiektów i kolekcji umożliwiają inicjowanie obiektów bez jawnego wywołania konstruktora dla obiekt. Inicjatory są zazwyczaj używane w wyrażeniach zapytań do ich projektu źródło danych do nowego typu danych. Zakładając, że klasa o nazwie `Customer` z publicznych `Name` i `Phone` można używać właściwości, inicjatora obiektu zgodnie z poniższym kodem:  
  
```  
Customer cust = new Customer { Name = "Mike", Phone = "555-1212" };  
```  
  
 Aby uzyskać więcej informacji, zobacz [inicjatory obiektów i kolekcji](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
## <a name="anonymous-types"></a>Typy anonimowe  
 Typ anonimowy jest tworzony przez kompilator i nazwa typu jest dostępna tylko dla kompilatora. Typy anonimowe zapewnić wygodny sposób grupowania zestawu właściwości tymczasowo w wyniku zapytania bez konieczności zdefiniuj oddzielnej o nazwie typu. Typy anonimowe są inicjowane z nowym wyrażeniu i inicjatora obiektów, jak pokazano poniżej:  
  
```  
select new {name = cust.Name, phone = cust.Phone};  
```  
  
 Aby uzyskać więcej informacji, zobacz [typy anonimowe](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
## <a name="extension-methods"></a>Metody rozszerzeń  
 Metody rozszerzenia jest statyczną metodę, która może być skojarzony z typem, dzięki czemu można wywołać, tak jakby był on metodę wystąpienia typu. Ta funkcja umożliwia, w efekcie "Dodaj" nowych metod do istniejących typów nie modyfikując je. Standardowe operatory zapytań to zbiór metody rozszerzenia, które zapewniają [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania funkcji dla dowolnego typu, który implementuje <xref:System.Collections.Generic.IEnumerable%601>.  
  
 Aby uzyskać więcej informacji, zobacz [metody rozszerzenia](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).  
  
## <a name="lambda-expressions"></a>Wyrażenia lambda  
 Wyrażenie lambda jest wbudowanej funkcji, która używa = > operator do rozdzielenia parametrów z treści funkcji wejściowych i mogą być przekonwertowane na delegata lub drzewo wyrażeń w czasie kompilacji. W [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] programowania, można napotkać wyrażenia lambda po wprowadzeniu wywołania metody bezpośrednio do standardowych operatorów zapytań.  
  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [Funkcje anonimowe](../../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)  
  
-   [Wyrażenia lambda](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
  
-   [Drzewa wyrażeń (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)  
  
## <a name="auto-implemented-properties"></a>Właściwości zaimplementowane automatycznie  
 Właściwości zaimplementowane automatycznie należy bardziej zwięzły deklaracji właściwości. Jak pokazano w poniższym przykładzie w deklaracji właściwości, kompilator utworzy polem zapasowym prywatne i anonimowy, który nie jest dostępny z wyjątkiem za pośrednictwem metody pobierającej i ustawiającej.  
  
```  
public string Name {get; set;}  
```  
  
 Aby uzyskać więcej informacji, zobacz [Auto-Implemented właściwości](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zapytanie o języku zintegrowanym (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)
