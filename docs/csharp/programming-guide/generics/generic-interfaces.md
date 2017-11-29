---
title: "Interfejsy ogólne (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, generic interfaces
- generics [C#], interfaces
ms.assetid: a8fa49a1-6e78-4a09-87e5-84a0b9f5ffbe
caps.latest.revision: "28"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0326a7bc459c641cbfafe39fe36525a947051c16
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="generic-interfaces-c-programming-guide"></a>Interfejsy ogólne (Przewodnik programowania w języku C#)
Często jest przydatne do definiowania interfejsów dla klasy rodzajowej kolekcji lub dla klasy ogólne, które reprezentują elementów w kolekcji. Preferencje dla klas ogólnych jest używać interfejsów ogólnych, takich jak <xref:System.IComparable%601> zamiast <xref:System.IComparable>, aby uniknąć konwersja boxing i rozpakowywanie operacji w typach wartości. Biblioteka klas programu .NET Framework definiuje kilku interfejsach służących do klasy kolekcji w <xref:System.Collections.Generic> przestrzeni nazw.  
  
 Gdy interfejs jest określony jako ograniczenia dla parametru typu, może służyć tylko typy, które implementują interfejs. Poniższy kod przedstawia przykład `SortedList<T>` klasą pochodzącą z `GenericList<T>` klasy. Aby uzyskać więcej informacji, zobacz [wprowadzenie do typów ogólnych](../../../csharp/programming-guide/generics/introduction-to-generics.md). `SortedList<T>`dodaje ograniczenie `where T : IComparable<T>`. Dzięki temu `BubbleSort` metody w `SortedList<T>` do ogólnego użycia <xref:System.IComparable%601.CompareTo%2A> metody dla elementów listy. W tym przykładzie elementy listy są prostą klasę `Person`, który implementuje `IComparable<Person>`.  
  
 [!code-csharp[csProgGuideGenerics#29](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_1.cs)]  
  
 Wiele interfejsów można określić jako ograniczeń na jednym typie, w następujący sposób:  
  
 [!code-csharp[csProgGuideGenerics#30](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_2.cs)]  
  
 Interfejs można zdefiniować więcej niż jeden parametr typu, w następujący sposób:  
  
 [!code-csharp[csProgGuideGenerics#31](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_3.cs)]  
  
 Reguły dziedziczenia, które są stosowane do klasy dotyczą także interfejsów:  
  
 [!code-csharp[csProgGuideGenerics#32](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_4.cs)]  
  
 Interfejsy ogólne dziedziczenie z interfejsów nierodzajową ogólny interfejs jest ma przeciwwskazań variant, co oznacza, że jej parametr typu jest stosowana tylko jako do wartości zwracanej. W bibliotece klas programu .NET Framework <xref:System.Collections.Generic.IEnumerable%601> dziedziczy <xref:System.Collections.IEnumerable> ponieważ <xref:System.Collections.Generic.IEnumerable%601> używa tylko `T` w zwracanej wartości <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> i <xref:System.Collections.Generic.IEnumerator%601.Current%2A> metody pobierającej właściwości.  
  
 Klasy mogą zawierać zamkniętego interfejsy skonstruowane, w następujący sposób:  
  
 [!code-csharp[csProgGuideGenerics#33](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_5.cs)]  
  
 Klasy ogólne można zaimplementować ogólnego lub zamkniętych interfejsów skonstruowane tak długo, jak lista parametrów klasy udostępnia wszystkie argumenty wymagane przez interfejs, w następujący sposób:  
  
 [!code-csharp[csProgGuideGenerics#34](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_6.cs)]  
  
 Reguły określające przeciążenie metody są takie same dla metod w ogólny klasy, struktury ogólne lub interfejsy ogólne. Aby uzyskać więcej informacji, zobacz [metody rodzajowe](../../../csharp/programming-guide/generics/generic-methods.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Wprowadzenie do typów ogólnych](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [Interfejs](../../../csharp/language-reference/keywords/interface.md)  
 [Typy ogólne](~/docs/standard/generics/index.md)
