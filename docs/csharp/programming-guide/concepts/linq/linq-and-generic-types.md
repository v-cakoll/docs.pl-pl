---
title: LINQ i typy ogólne (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], generic types
- generic types [LINQ]
- generics [LINQ]
ms.assetid: 660e3799-25ca-462c-8c4a-8bce04fbb031
ms.openlocfilehash: 9a2d1ac72f70e7cd314d349e81ab2bc815a5bf13
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635577"
---
# <a name="linq-and-generic-types-c"></a>LINQ i typy ogólne (C#)
Zapytania LINQ są oparte na typach ogólnych, które zostały wprowadzone w wersji 2.0 .NET Framework. Nie trzeba dogłębnej wiedzy na temat ogólnych przed rozpoczęciem pisania zapytań. Warto jednak zrozumieć dwa podstawowe pojęcia:  
  
1. Podczas tworzenia wystąpienia ogólnej klasy kolekcji, takich jak <xref:System.Collections.Generic.List%601>, można zastąpić "T" z typem obiektów, które będzie posiadać listy. Na przykład lista ciągów jest wyrażona jako `List<string>`, `Customer` a lista `List<Customer>`obiektów jest wyrażona jako . Lista ogólna jest silnie typizowane i zapewnia wiele <xref:System.Object>korzyści w stosunku do kolekcji, które przechowują swoje elementy jako . Jeśli spróbujesz `Customer` dodać `List<string>`do , pojawi się błąd w czasie kompilacji. Jest łatwy w użyciu kolekcje ogólne, ponieważ nie trzeba wykonywać rzutowanie typu w czasie wykonywania.  
  
2. <xref:System.Collections.Generic.IEnumerable%601>jest interfejsem, który umożliwia klas kolekcji ogólnej, `foreach` które mają być wyliczone przy użyciu instrukcji. Ogólne klasy <xref:System.Collections.Generic.IEnumerable%601> kolekcji obsługują tak samo klasy <xref:System.Collections.ArrayList> <xref:System.Collections.IEnumerable>kolekcji nierodzajowych, takich jak obsługa.  
  
 Aby uzyskać więcej informacji na temat leków generycznych, zobacz [Generyk .](../../generics/index.md)  
  
## <a name="ienumerablet-variables-in-linq-queries"></a>Zmienne IEnumerable\><T w kwerendach LINQ  
 Zmienne kwerendy LINQ są <xref:System.Collections.Generic.IEnumerable%601> wpisywane jako lub <xref:System.Linq.IQueryable%601>typu pochodnego, takiego jak . Po wyświetleniu zmiennej kwerendy, `IEnumerable<Customer>`która jest wpisana jako , oznacza to po prostu, `Customer` że kwerenda, gdy jest wykonywana, będzie produkować sekwencję zero lub więcej obiektów.  
  
 [!code-csharp[csLINQGettingStarted#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#34)]  
  
 Aby uzyskać więcej informacji, zobacz [Wpisywanie relacji w operacjach kwerend LINQ](./type-relationships-in-linq-query-operations.md).  
  
## <a name="letting-the-compiler-handle-generic-type-declarations"></a>Zezwalanie kompilatorowi obsługiwać deklaracje typów ogólnych  
 Jeśli wolisz, możesz uniknąć składni rodzajowej za pomocą słowa kluczowego [var.](../../../language-reference/keywords/var.md) Słowo `var` kluczowe instruuje kompilator, aby wywnioskować typ zmiennej `from` kwerendy, patrząc na źródło danych określone w klauzuli. Poniższy przykład daje ten sam skompilowany kod jak w poprzednim przykładzie:  
  
 [!code-csharp[csLINQGettingStarted#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#35)]  
  
 Słowo `var` kluczowe jest przydatne, gdy typ zmiennej jest oczywiste lub gdy nie jest tak ważne, aby jawnie określić zagnieżdżone typy ogólne, takie jak te, które są tworzone przez zapytania grupowe. Ogólnie rzecz biorąc, zaleca `var`się, że jeśli używasz , sobie sprawę, że może to utrudnić kod dla innych do odczytania. Aby uzyskać więcej informacji, zobacz [Niejawnie wpisane zmienne lokalne](../../classes-and-structs/implicitly-typed-local-variables.md).  
  
## <a name="see-also"></a>Zobacz też

- [Typy ogólne](../../generics/index.md)
