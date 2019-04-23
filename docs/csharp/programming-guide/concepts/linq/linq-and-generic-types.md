---
title: LINQ i typy ogólne (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], generic types
- generic types [LINQ]
- generics [LINQ]
ms.assetid: 660e3799-25ca-462c-8c4a-8bce04fbb031
ms.openlocfilehash: cd0fae0c7d99491f21e5e1fb265e4aabafaa63c4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59332696"
---
# <a name="linq-and-generic-types-c"></a>LINQ i typy ogólne (C#)
[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania są oparte na typach ogólnych, które zostały wprowadzone w wersji 2.0 programu [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Nie potrzebujesz dogłębnej znajomości ogólne przed rozpoczęciem pisania zapytań. Jednak warto zrozumieć dwa podstawowe pojęcia:  
  
1. Podczas tworzenia wystąpienia klasy kolekcji generycznej takich jak <xref:System.Collections.Generic.List%601>, Zamień "T" na typ obiektów, które będzie przechowywać listę. Na przykład listę ciągów jest wyrażona jako `List<string>`oraz listę `Customer` obiektów jest wyrażona jako `List<Customer>`. Listy ogólnej zdecydowanie jest wpisane i udostępnia wiele korzyści w porównaniu z kolekcji, które przechowują elementów jako <xref:System.Object>. Jeśli użytkownik próbuje dodać `Customer` do `List<string>`, otrzymają komunikat o błędzie w czasie kompilacji. Jest łatwa w użyciu ogólnych kolekcji, ponieważ nie trzeba wykonać rzutowanie typów środowiska wykonawczego.  
  
2. <xref:System.Collections.Generic.IEnumerable%601> to interfejs, który umożliwia klasy kolekcji rodzajowej do wyliczenia przy użyciu `foreach` instrukcji. Klasy ogólne kolekcji pomocy technicznej <xref:System.Collections.Generic.IEnumerable%601> takich jak klasy, po prostu jako nieogólna Kolekcja <xref:System.Collections.ArrayList> obsługuje <xref:System.Collections.IEnumerable>.  
  
 Aby uzyskać więcej informacji na temat typów ogólnych, zobacz [ogólne](../../../../csharp/programming-guide/generics/index.md).  
  
## <a name="ienumerablet-variables-in-linq-queries"></a>Interfejs IEnumerable < T\> zmiennych w zapytaniach LINQ  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] Zmienne zapytania o typach <xref:System.Collections.Generic.IEnumerable%601> lub typ pochodny, takie jak <xref:System.Linq.IQueryable%601>. Po wyświetleniu zmienna zapytania, który jest `IEnumerable<Customer>`, oznacza jedynie, że zapytania, gdy jest wykonywany dadzą Sekwencja zero lub więcej `Customer` obiektów.  
  
 [!code-csharp[csLINQGettingStarted#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#34)]  
  
 Aby uzyskać więcej informacji, zobacz [relacje typu w operacjach zapytań LINQ](../../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).  
  
## <a name="letting-the-compiler-handle-generic-type-declarations"></a>Umożliwienie deklaracje typu ogólnego uchwyt kompilatora  
 Jeśli wolisz, możesz uniknąć ogólna składnia przy użyciu [var](../../../../csharp/language-reference/keywords/var.md) — słowo kluczowe. `var` — Słowo kluczowe nakazuje kompilatorowi wywnioskowania typu zmiennej zapytania, analizując źródło danych określone w `from` klauzuli. Poniższy przykład generuje ten sam kod skompilowany, jak w poprzednim przykładzie:  
  
 [!code-csharp[csLINQGettingStarted#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#35)]  
  
 `var` — Słowo kluczowe jest przydatne w przypadku, gdy typ zmiennej jest oczywisty lub gdy nie jest to ważne, jawnie określić zagnieżdżonych typów ogólnych, takich jak te, które są produkowane przez grupy zapytań. Ogólnie rzecz biorąc, zalecamy użycie `var`, należy pamiętać, że może sprawić, że Twój kod trudniejsze dla innych użytkowników. Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienne lokalne](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do korzystania z LINQ w C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Typy ogólne](../../../../csharp/programming-guide/generics/index.md)
