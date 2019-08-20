---
title: Interfejsy ogólne — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic interfaces
- generics [C#], interfaces
ms.assetid: a8fa49a1-6e78-4a09-87e5-84a0b9f5ffbe
ms.openlocfilehash: fb2c570b251979adb76ad2af1a3b6f54b75a15ff
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589716"
---
# <a name="generic-interfaces-c-programming-guide"></a>Interfejsy ogólne (Przewodnik programowania w języku C#)
Często warto zdefiniować interfejsy dla klas kolekcji generycznej lub dla klas ogólnych, które reprezentują elementy w kolekcji. Preferencją dla klas ogólnych jest użycie interfejsów ogólnych, takich jak <xref:System.IComparable%601> <xref:System.IComparable>zamiast, aby uniknąć pakowania i rozpakowywania operacji na typach wartości. Biblioteka klas .NET Framework definiuje kilka ogólnych interfejsów do użycia z klasami kolekcji w <xref:System.Collections.Generic> przestrzeni nazw.  
  
 Gdy interfejs jest określony jako ograniczenie dla parametru typu, można użyć tylko typów, które implementują interfejs. Poniższy przykład kodu pokazuje `SortedList<T>` klasę, która dziedziczy `GenericList<T>` z klasy. Aby uzyskać więcej informacji, zobacz [wprowadzenie do typów ogólnych](./index.md). `SortedList<T>`dodaje ograniczenie `where T : IComparable<T>`. Dzięki `BubbleSort` temu Metoda w programie `SortedList<T>` może używać metody ogólnej <xref:System.IComparable%601.CompareTo%2A> dla elementów listy. W tym przykładzie elementy list są prostą klasą `Person`, która implementuje. `IComparable<Person>`  
  
 [!code-csharp[csProgGuideGenerics#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics2.cs#29)]  
  
 Można określić wiele interfejsów jako ograniczenia dotyczące pojedynczego typu w następujący sposób:  
  
 [!code-csharp[csProgGuideGenerics#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#30)]  
  
 Interfejs może definiować więcej niż jeden parametr typu w następujący sposób:  
  
 [!code-csharp[csProgGuideGenerics#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#31)]  
  
 Reguły dziedziczenia stosowane do klas dotyczą również interfejsów:  
  
 [!code-csharp[csProgGuideGenerics#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#32)]  
  
 Interfejsy generyczne mogą dziedziczyć z interfejsów innych niż ogólne, jeśli interfejs generyczny jest kontrawariantne, co oznacza, że używa jego parametru typu jako wartości zwracanej. W bibliotece klas .NET Framework dziedziczy z <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.IEnumerable> , ponieważ <xref:System.Collections.Generic.IEnumerable%601> używa `T` tylko w wartości <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> zwracanej i w <xref:System.Collections.Generic.IEnumerator%601.Current%2A> metodzie pobierającej właściwości.  
  
 Konkretne klasy mogą zaimplementować zamknięte interfejsy skonstruowane w następujący sposób:  
  
 [!code-csharp[csProgGuideGenerics#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#33)]  
  
 Klasy generyczne mogą implementować interfejsy ogólne lub zamknięte skonstruowane interfejsy, o ile lista parametrów klasy dostarcza wszystkie argumenty wymagane przez interfejs, w następujący sposób:  
  
 [!code-csharp[csProgGuideGenerics#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#34)]  
  
 Reguły przeciążania metody kontrolującej są takie same dla metod w klasach ogólnych, strukturach ogólnych lub w interfejsach ogólnych. Aby uzyskać więcej informacji, zobacz [metody ogólne](./generic-methods.md).  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Wprowadzenie do typów ogólnych](./index.md)
- [interface](../../language-reference/keywords/interface.md)
- [Typy ogólne](~/docs/standard/generics/index.md)
