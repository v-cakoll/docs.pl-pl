---
title: LINQ i typy ogólne (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], generic types
- generic types [LINQ]
- generics [LINQ]
ms.assetid: 660e3799-25ca-462c-8c4a-8bce04fbb031
ms.openlocfilehash: f9bb4ec21685d21d0975529c7460944b5f0f9fc6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33327740"
---
# <a name="linq-and-generic-types-c"></a>LINQ i typy ogólne (C#)
[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania są oparte na typach ogólnych, które zostały wprowadzone w wersji 2.0 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Nie trzeba dogłębnej wiedzy typów ogólnych przed rozpoczęciem Pisanie zapytań. Można jednak poznać dwa podstawowe pojęcia:  
  
1.  Podczas tworzenia wystąpienia klasy rodzajowej kolekcji takich jak <xref:System.Collections.Generic.List%601>, zastąp "T" z typem obiektów zawierających listy. Na przykład lista ciągów jest wyrażony jako `List<string>`oraz listę `Customer` obiektów jest wyrażony jako `List<Customer>`. Ogólne listy są silnie typizowane i udostępnia wiele korzyści w porównaniu z kolekcji, w których są przechowywane ich elementów jako <xref:System.Object>. Jeśli próbujesz dodać `Customer` do `List<string>`, wystąpi błąd w czasie kompilacji. Jest łatwy w użyciu kolekcji, ponieważ nie trzeba wykonywać rzutowanie typów środowiska wykonawczego.  
  
2.  <xref:System.Collections.Generic.IEnumerable%601> to interfejs, który umożliwia kolekcji ogólnej klasy mają zostać wyliczone przy użyciu `foreach` instrukcji. Obsługa klasy rodzajowej kolekcji <xref:System.Collections.Generic.IEnumerable%601> tylko jako nieogólna kolekcja klas takich jak <xref:System.Collections.ArrayList> obsługuje <xref:System.Collections.IEnumerable>.  
  
 Aby uzyskać informacje ogólne, zobacz [ogólne](../../../../csharp/programming-guide/generics/index.md).  
  
## <a name="ienumerablet-variables-in-linq-queries"></a>Interfejs IEnumerable < T\> zmiennych w zapytaniach LINQ  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] Zmienne zapytania są wpisywane jako <xref:System.Collections.Generic.IEnumerable%601> ani typem pochodnym, takich jak <xref:System.Linq.IQueryable%601>. Po wyświetleniu zapytania zmiennej, która zostanie wpisany jako `IEnumerable<Customer>`, po prostu oznacza, że zapytanie po jego wykonaniu utworzy sekwencji zero lub więcej `Customer` obiektów.  
  
 [!code-csharp[csLINQGettingStarted#34](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/linq-and-generic-types_1.cs)]  
  
 Aby uzyskać więcej informacji, zobacz [relacje typu w operacjach zapytań LINQ](../../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).  
  
## <a name="letting-the-compiler-handle-generic-type-declarations"></a>Umożliwienie deklaracje typu ogólnego dojścia kompilatora  
 Jeśli wolisz, możesz uniknąć ogólna składnia przy użyciu [var](../../../../csharp/language-reference/keywords/var.md) — słowo kluczowe. `var` — Słowo kluczowe instruuje kompilator, aby wywnioskowania typu zmienną zapytania analizując źródłem danych określonym w `from` klauzuli. Poniższy przykład tworzy tego samego kodu skompilowanego co w poprzednim przykładzie:  
  
 [!code-csharp[csLINQGettingStarted#35](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/linq-and-generic-types_2.cs)]  
  
 `var` — Słowo kluczowe jest przydatne, gdy typ zmiennej jest widoczne, lub gdy nie jest to ważne jawnie określić zagnieżdżonych typów ogólnych, takich jak te, które są tworzone przez grupy zapytań. Ogólnie rzecz biorąc, zaleca się użycie `var`, należy pamiętać, że go kodu trudniejsze dla innych użytkowników. Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienne lokalne](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do korzystania z LINQ w C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [Typy ogólne](../../../../csharp/programming-guide/generics/index.md)
