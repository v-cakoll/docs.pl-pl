---
title: Interfejsy ogólne — przewodnik programowania języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic interfaces
- generics [C#], interfaces
ms.assetid: a8fa49a1-6e78-4a09-87e5-84a0b9f5ffbe
ms.openlocfilehash: 4cce23da7579e30ecff80b3afb92a5a58795c1bd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712211"
---
# <a name="generic-interfaces-c-programming-guide"></a>Interfejsy ogólne (Przewodnik programowania w języku C#)
Często jest przydatne do definiowania interfejsów dla klas kolekcji rodzajowej lub dla klas ogólnych, które reprezentują elementy w kolekcji. Preferencja dla klas ogólnych jest użycie <xref:System.IComparable%601> ogólnych <xref:System.IComparable>interfejsów, takich jak zamiast , w celu uniknięcia operacji bokserskich i rozpakowywania na typy wartości. Biblioteka klas .NET Framework definiuje kilka ogólnych interfejsów do <xref:System.Collections.Generic> użytku z klasami kolekcji w przestrzeni nazw.  
  
 Gdy interfejs jest określony jako ograniczenie parametru typu, można użyć tylko typy, które implementują interfejs. Poniższy przykład kodu `SortedList<T>` pokazuje klasę, która `GenericList<T>` pochodzi od klasy. Aby uzyskać więcej informacji, zobacz [Wprowadzenie do leków ogólnych](./index.md). `SortedList<T>`dodaje ograniczenie `where T : IComparable<T>`. Dzięki temu `BubbleSort` metoda `SortedList<T>` w do <xref:System.IComparable%601.CompareTo%2A> korzystania z metody ogólnej na elementy listy. W tym przykładzie elementy listy są `Person`prostą klasą, która implementuje `IComparable<Person>`.  
  
 [!code-csharp[csProgGuideGenerics#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics2.cs#29)]  
  
 Wiele interfejsów można określić jako ograniczenia dla jednego typu, w następujący sposób:  
  
 [!code-csharp[csProgGuideGenerics#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#30)]  
  
 Interfejs można zdefiniować więcej niż jeden parametr typu, w następujący sposób:  
  
 [!code-csharp[csProgGuideGenerics#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#31)]  
  
 Reguły dziedziczenia, które mają zastosowanie do klas, mają również zastosowanie do interfejsów:  
  
 [!code-csharp[csProgGuideGenerics#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#32)]  
  
 Interfejsy ogólne można dziedziczyć z interfejsów nieogólnych, jeśli interfejs ogólny jest kontrawariantny, co oznacza, że używa tylko jego parametr typu jako wartość zwracaną. W <xref:System.Collections.Generic.IEnumerable%601> bibliotece klas .NET Framework <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601> dziedziczy z, ponieważ używa `T` tylko w wartości zwracanej <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> i w getter <xref:System.Collections.Generic.IEnumerator%601.Current%2A> właściwości.  
  
 Klasy betonowe mogą implementować zamknięte skonstruowane interfejsy w następujący sposób:  
  
 [!code-csharp[csProgGuideGenerics#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#33)]  
  
 Klasy ogólne można zaimplementować interfejsy ogólne lub zamknięte skonstruowane interfejsy tak długo, jak lista parametrów klasy dostarcza wszystkie argumenty wymagane przez interfejs, w następujący sposób:  
  
 [!code-csharp[csProgGuideGenerics#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#34)]  
  
 Reguły, które kontrolują przeciążenie metody są takie same dla metod w ramach klas ogólnych, struktur ogólnych lub interfejsów ogólnych. Aby uzyskać więcej informacji, zobacz [Metody ogólne](./generic-methods.md).  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Wprowadzenie do typów ogólnych](./index.md)
- [Interfejs](../../language-reference/keywords/interface.md)
- [Typy ogólne](../../../standard/generics/index.md)
