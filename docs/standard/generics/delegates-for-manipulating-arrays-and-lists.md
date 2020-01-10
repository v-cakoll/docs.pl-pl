---
title: Delegaty ogólne do manipulowania tablicami i listami
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- delegates [.NET Framework], generic delegates
- chaining delegates
- arrays [.NET Framework], generic delegates
- generic delegates [.NET Framework]
- lists [.NET Framework], generic delegates
- generics [.NET Framework], delegates
ms.assetid: 416be383-cc61-4102-9b1b-88b51adb963e
ms.openlocfilehash: baf8497289ee71c2dbdc544607212de90928289c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708387"
---
# <a name="generic-delegates-for-manipulating-arrays-and-lists"></a>Delegaty ogólne do manipulowania tablicami i listami
Ten temat zawiera przegląd ogólnych delegatów dla konwersji, predykatów wyszukiwania i akcji, które mają być podejmowane w elementach tablicy lub kolekcji.  
  
## <a name="generic-delegates-for-manipulating-arrays-and-lists"></a>Delegaty ogólne do manipulowania tablicami i listami  
 Delegat ogólny <xref:System.Action%601> reprezentuje metodę wykonującą pewne działania na elemencie określonego typu. Można utworzyć metodę, która wykonuje odpowiednią akcję dla elementu, utworzyć wystąpienie delegata <xref:System.Action%601> do reprezentowania tej metody, a następnie przekazać tablicę i delegata do <xref:System.Array.ForEach%2A?displayProperty=nameWithType> statycznej metody ogólnej. Metoda jest wywoływana dla każdego elementu tablicy.  
  
 Klasa ogólna <xref:System.Collections.Generic.List%601> również udostępnia metodę <xref:System.Collections.Generic.List%601.ForEach%2A>, która używa delegata <xref:System.Action%601>. Ta metoda nie jest rodzajowa.  
  
> [!NOTE]
> Pozwala to na interesujący punkt dotyczący typów ogólnych i metod. Metoda <xref:System.Array.ForEach%2A?displayProperty=nameWithType> musi być statyczna (`Shared` w Visual Basic) i ogólna, ponieważ <xref:System.Array> nie jest typem ogólnym; jedyną przyczyną, aby można było określić typ <xref:System.Array.ForEach%2A?displayProperty=nameWithType>, na którym operuje Metoda ma własną listę parametrów typu. Z kolei Metoda nieogólna <xref:System.Collections.Generic.List%601.ForEach%2A?displayProperty=nameWithType> należy do klasy generycznej <xref:System.Collections.Generic.List%601>, dlatego po prostu używa parametru typu klasy. Klasa jest silnie wpisana, dlatego metoda może być metodą wystąpienia.  
  
 Delegat ogólny <xref:System.Predicate%601> reprezentuje metodę, która określa, czy konkretny element spełnia zdefiniowane kryteria. Można go użyć z następującymi statycznymi metodami <xref:System.Array>, aby wyszukać element lub zestaw elementów: <xref:System.Array.Exists%2A>, <xref:System.Array.Find%2A>, <xref:System.Array.FindAll%2A>, <xref:System.Array.FindIndex%2A>, <xref:System.Array.FindLast%2A>, <xref:System.Array.FindLastIndex%2A>i <xref:System.Array.TrueForAll%2A>.  
  
 <xref:System.Predicate%601> działa również z odpowiednimi nieogólnymi metodami wystąpień klasy generycznej <xref:System.Collections.Generic.List%601>.  
  
 Delegat ogólny <xref:System.Comparison%601> umożliwia podanie porządku sortowania dla elementów tablicy lub listy, które nie mają natywnej kolejności sortowania lub przesłaniania natywnej kolejności sortowania. Utwórz metodę, która wykonuje porównanie, Utwórz wystąpienie delegata <xref:System.Comparison%601>, aby reprezentować metodę, a następnie Przekaż tablicę i delegata do <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Comparison%7B%60%600%7D%29?displayProperty=nameWithType> statycznej metody ogólnej. Klasa generyczna <xref:System.Collections.Generic.List%601> udostępnia odpowiednie Przeciążenie metody wystąpienia, <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29?displayProperty=nameWithType>.  
  
 Delegat ogólny <xref:System.Converter%602> umożliwia zdefiniowanie konwersji między dwoma typami, a także konwersję tablicy jednego typu na tablicę lub konwersję listy jednego typu na listę innych. Utwórz metodę, która konwertuje elementy istniejącej listy na nowy typ, Utwórz wystąpienie delegata reprezentujące metodę, a następnie użyj <xref:System.Array.ConvertAll%2A?displayProperty=nameWithType> ogólnej metody statycznej, aby utworzyć tablicę nowego typu z oryginalnej tablicy, lub metodę <xref:System.Collections.Generic.List%601.ConvertAll%60%601%28System.Converter%7B%600%2C%60%600%7D%29?displayProperty=nameWithType> wystąpienie ogólne, aby utworzyć listę nowych typów z listy pierwotnej.  
  
### <a name="chaining-delegates"></a>Tworzenie łańcuchów obiektów delegowanych  
 Wiele metod, które używają tych delegatów, zwraca tablicę lub listę, które mogą być przesyłane do innej metody. Na przykład, jeśli chcesz wybrać niektóre elementy tablicy, przekonwertuj te elementy na nowy typ i Zapisz je w nowej tablicy, możesz przekazać tablicę zwracaną przez metodę <xref:System.Array.FindAll%2A> Generic do <xref:System.Array.ConvertAll%2A> metody ogólnej. Jeśli typ nowego elementu nie ma naturalnej kolejności sortowania, można przekazać tablicę zwróconą przez metodę rodzajową <xref:System.Array.ConvertAll%2A> do <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Comparison%7B%60%600%7D%29> metody ogólnej.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [Typy ogólne](../../../docs/standard/generics/index.md)
- [Kolekcje ogólne w oprogramowaniu .NET Framework](../../../docs/standard/generics/collections.md)
- [Interfejsy ogólne](../../../docs/standard/generics/interfaces.md)
- [Kowariancja i kontrawariancja](../../../docs/standard/generics/covariance-and-contravariance.md)
