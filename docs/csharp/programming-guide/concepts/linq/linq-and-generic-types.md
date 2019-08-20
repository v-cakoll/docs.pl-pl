---
title: LINQ i typy ogólne (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], generic types
- generic types [LINQ]
- generics [LINQ]
ms.assetid: 660e3799-25ca-462c-8c4a-8bce04fbb031
ms.openlocfilehash: 8ec2a599a6762d62d101f7660892a6d85a100794
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591942"
---
# <a name="linq-and-generic-types-c"></a>LINQ i typy ogólne (C#)
[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]zapytania są oparte na typach ogólnych, które zostały wprowadzone w wersji 2,0 .NET Framework. Przed rozpoczęciem pisania zapytań nie jest potrzebna Szczegółowa wiedza o typach ogólnych. Jednak warto zrozumieć dwa podstawowe koncepcje:  
  
1. Podczas tworzenia wystąpienia klasy kolekcji ogólnej, takiej jak <xref:System.Collections.Generic.List%601>, należy zastąpić "T" typem obiektów, które będą przechowywane na liście. Na przykład lista ciągów jest wyrażona jako `List<string>`, a `Customer` lista obiektów jest wyrażana jako `List<Customer>`. Lista ogólna jest silnie wpisana i oferuje wiele korzyści w stosunku do kolekcji, które przechowują ich elementy jako <xref:System.Object>. Jeśli spróbujesz dodać `Customer` `List<string>`do, pojawi się błąd w czasie kompilacji. Korzystanie z kolekcji ogólnych jest proste, ponieważ nie jest konieczne wykonywanie rzutowania typu w czasie wykonywania.  
  
2. <xref:System.Collections.Generic.IEnumerable%601>jest interfejsem, który umożliwia Wyliczenie ogólnych klas kolekcji przy użyciu `foreach` instrukcji. Klasy kolekcji generycznej <xref:System.Collections.Generic.IEnumerable%601> obsługują klasy kolekcji inne niż ogólne, takie jak <xref:System.Collections.ArrayList> obsługa <xref:System.Collections.IEnumerable>.  
  
 Aby uzyskać więcej informacji na temat typów ogólnych, zobacz [typy ogólne](../../generics/index.md).  
  
## <a name="ienumerablet-variables-in-linq-queries"></a>Zmienne interfejsu IEnumerable\> < T w zapytaniach LINQ  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]zmienne zapytania są wpisywane jako <xref:System.Collections.Generic.IEnumerable%601> lub typu pochodnego, takiego <xref:System.Linq.IQueryable%601>jak. Gdy zostanie wyświetlona zmienna zapytania, która jest `IEnumerable<Customer>`wpisana jako, oznacza to, że zapytanie, gdy jest wykonywane, spowoduje utworzenie sekwencji zero lub więcej `Customer` obiektów.  
  
 [!code-csharp[csLINQGettingStarted#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#34)]  
  
 Aby uzyskać więcej informacji, zobacz temat [relacje typu w operacjach zapytań LINQ](./type-relationships-in-linq-query-operations.md).  
  
## <a name="letting-the-compiler-handle-generic-type-declarations"></a>Zezwalanie kompilatorowi na obsługę deklaracji typów ogólnych  
 Jeśli wolisz, możesz uniknąć składni generycznej za pomocą słowa kluczowego [var](../../../language-reference/keywords/var.md) . Słowo kluczowe instruuje kompilator do wywnioskowania typu zmiennej zapytania, sprawdzając źródło danych określone `from` w klauzuli. `var` Poniższy przykład generuje ten sam skompilowany kod, jak w poprzednim przykładzie:  
  
 [!code-csharp[csLINQGettingStarted#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#35)]  
  
 `var` Słowo kluczowe jest przydatne, gdy typ zmiennej jest oczywisty lub jeśli nie jest istotny do jawnego określenia zagnieżdżonych typów ogólnych, takich jak te, które są tworzone przez zapytania grupowe. Ogólnie rzecz biorąc, zaleca się, aby w `var`przypadku korzystania z programu pamiętać, że kod może być trudniejszy do odczytania przez inne osoby. Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienne lokalne](../../classes-and-structs/implicitly-typed-local-variables.md).  
  
## <a name="see-also"></a>Zobacz także

- [Typy ogólne](../../generics/index.md)
