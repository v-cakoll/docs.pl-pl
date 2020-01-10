---
title: Interfejsy ogólne — C# Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic interfaces
- generics [C#], interfaces
ms.assetid: a8fa49a1-6e78-4a09-87e5-84a0b9f5ffbe
ms.openlocfilehash: 4cce23da7579e30ecff80b3afb92a5a58795c1bd
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712211"
---
# <a name="generic-interfaces-c-programming-guide"></a>Interfejsy ogólne (Przewodnik programowania w języku C#)
Często warto zdefiniować interfejsy dla klas kolekcji generycznej lub dla klas ogólnych, które reprezentują elementy w kolekcji. Preferencja dla klas ogólnych polega na użyciu interfejsów ogólnych, takich jak <xref:System.IComparable%601>, a nie <xref:System.IComparable>, aby uniknąć pakowania i rozpakowywania operacji na typach wartości. Biblioteka klas .NET Framework definiuje kilka ogólnych interfejsów do użycia z klasami kolekcji w przestrzeni nazw <xref:System.Collections.Generic>.  
  
 Gdy interfejs jest określony jako ograniczenie dla parametru typu, można użyć tylko typów, które implementują interfejs. Poniższy przykład kodu przedstawia klasę `SortedList<T>`, która pochodzi od klasy `GenericList<T>`. Aby uzyskać więcej informacji, zobacz [wprowadzenie do typów ogólnych](./index.md). `SortedList<T>` dodaje `where T : IComparable<T>`ograniczenia. Dzięki temu Metoda `BubbleSort` w `SortedList<T>` do używania metody ogólnej <xref:System.IComparable%601.CompareTo%2A> dla elementów listy. W tym przykładzie elementy list są prostą klasą `Person`, która implementuje `IComparable<Person>`.  
  
 [!code-csharp[csProgGuideGenerics#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics2.cs#29)]  
  
 Można określić wiele interfejsów jako ograniczenia dotyczące pojedynczego typu w następujący sposób:  
  
 [!code-csharp[csProgGuideGenerics#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#30)]  
  
 Interfejs może definiować więcej niż jeden parametr typu w następujący sposób:  
  
 [!code-csharp[csProgGuideGenerics#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#31)]  
  
 Reguły dziedziczenia stosowane do klas dotyczą również interfejsów:  
  
 [!code-csharp[csProgGuideGenerics#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#32)]  
  
 Interfejsy generyczne mogą dziedziczyć z interfejsów innych niż ogólne, jeśli interfejs generyczny jest kontrawariantne, co oznacza, że używa jego parametru typu jako wartości zwracanej. W bibliotece klas .NET Framework <xref:System.Collections.Generic.IEnumerable%601> dziedziczy po <xref:System.Collections.IEnumerable>, ponieważ <xref:System.Collections.Generic.IEnumerable%601> używa tylko `T` w wartości zwracanej przez <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> i we właściwości <xref:System.Collections.Generic.IEnumerator%601.Current%2A> pobierającej.  
  
 Konkretne klasy mogą zaimplementować zamknięte interfejsy skonstruowane w następujący sposób:  
  
 [!code-csharp[csProgGuideGenerics#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#33)]  
  
 Klasy generyczne mogą implementować interfejsy ogólne lub zamknięte skonstruowane interfejsy, o ile lista parametrów klasy dostarcza wszystkie argumenty wymagane przez interfejs, w następujący sposób:  
  
 [!code-csharp[csProgGuideGenerics#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#34)]  
  
 Reguły przeciążania metody kontrolującej są takie same dla metod w klasach ogólnych, strukturach ogólnych lub w interfejsach ogólnych. Aby uzyskać więcej informacji, zobacz [metody ogólne](./generic-methods.md).  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Wprowadzenie do typów ogólnych](./index.md)
- [interface](../../language-reference/keywords/interface.md)
- [Typy ogólne](../../../standard/generics/index.md)
