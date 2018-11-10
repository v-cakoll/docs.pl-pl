---
title: Interfejsy ogólne (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic interfaces
- generics [C#], interfaces
ms.assetid: a8fa49a1-6e78-4a09-87e5-84a0b9f5ffbe
ms.openlocfilehash: 4c7449568ff250c8de521e7afb71178536f52657
ms.sourcegitcommit: 4bca8f7e172fd019ef437a4803bf5895c6bc4781
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2018
ms.locfileid: "50980778"
---
# <a name="generic-interfaces-c-programming-guide"></a>Interfejsy ogólne (Przewodnik programowania w języku C#)
Często jest to przydatne do definiowania interfejsów dla klasy kolekcji rodzajowej lub dla klas ogólnych, które reprezentują elementy w kolekcji. Preferencje dla klas ogólnych jest używać interfejsów ogólnych, takich jak <xref:System.IComparable%601> zamiast <xref:System.IComparable>, aby unikać operacji pakowania, jak i rozpakowania dla typów wartości. Biblioteka klas .NET Framework definiuje kilka interfejsów ogólnych do użytku z klas kolekcji przestrzeni <xref:System.Collections.Generic> przestrzeni nazw.  
  
 Jeśli interfejs jest określony jako ograniczenia dla parametru typu, może służyć tylko typy, które implementują interfejs. Poniższy kod przedstawia przykład `SortedList<T>` klasę pochodzącą od `GenericList<T>` klasy. Aby uzyskać więcej informacji, zobacz [wprowadzenie do typów ogólnych](../../../csharp/programming-guide/generics/introduction-to-generics.md). `SortedList<T>` dodaje ograniczenie `where T : IComparable<T>`. Dzięki temu `BubbleSort` method in Class metoda `SortedList<T>` musieli używać ogólnych <xref:System.IComparable%601.CompareTo%2A> metody na liście elementów. W tym przykładzie, elementy listy są klasą prostą `Person`, która implementuje `IComparable<Person>`.  
  
 [!code-csharp[csProgGuideGenerics#29](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_1.cs)]  
  
 Wiele interfejsów można określić jako warunki ograniczające w jednego typu, w następujący sposób:  
  
 [!code-csharp[csProgGuideGenerics#30](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_2.cs)]  
  
 Interfejs można zdefiniować więcej niż jeden parametr typu, w następujący sposób:  
  
 [!code-csharp[csProgGuideGenerics#31](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_3.cs)]  
  
 Reguły dziedziczenia, które są stosowane do klasy, która jest również zastosowanie do interfejsów:  
  
 [!code-csharp[csProgGuideGenerics#32](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_4.cs)]  
  
 Interfejsy ogólne może dziedziczyć po elemencie nieogólnego interfejsów, jeśli ogólny interfejs jest kontrawariantny, co oznacza, że jej parametr typu jest stosowana tylko jako wartości zwracanej. W bibliotece klas programu .NET Framework <xref:System.Collections.Generic.IEnumerable%601> dziedziczy <xref:System.Collections.IEnumerable> ponieważ <xref:System.Collections.Generic.IEnumerable%601> używa tylko `T` w zwracanej wartości <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> i <xref:System.Collections.Generic.IEnumerator%601.Current%2A> metoda pobierająca właściwości.  
  
 Konkretnych klas można zaimplementować zamknięte interfejsów skonstruowany, w następujący sposób:  
  
 [!code-csharp[csProgGuideGenerics#33](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_5.cs)]  
  
 Klasy ogólne można zaimplementować interfejsów ogólnych lub zamkniętych skonstruowany interfejsów, tak długo, jak lista parametrów klasy dostarcza wszystkie argumenty wymagane przy użyciu interfejsu, w następujący sposób:  
  
 [!code-csharp[csProgGuideGenerics#34](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_6.cs)]  
  
 Reguły które kontrolują, przeciążenie metody są takie same dla metod w obrębie klasy ogólne, ogólny struktury lub interfejsów ogólnych. Aby uzyskać więcej informacji, zobacz [metod ogólnych](../../../csharp/programming-guide/generics/generic-methods.md).  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Wprowadzenie do typów ogólnych](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
- [interface](../../../csharp/language-reference/keywords/interface.md)  
- [Typy ogólne](~/docs/standard/generics/index.md)
