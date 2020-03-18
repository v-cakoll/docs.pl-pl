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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708387"
---
# <a name="generic-delegates-for-manipulating-arrays-and-lists"></a>Delegaty ogólne do manipulowania tablicami i listami
Ten temat zawiera omówienie ogólnych delegatów dla konwersji, predykatów wyszukiwania i akcji, które należy podjąć na elementach tablicy lub kolekcji.  
  
## <a name="generic-delegates-for-manipulating-arrays-and-lists"></a>Delegaty ogólne do manipulowania tablicami i listami  
 Ogólny <xref:System.Action%601> delegat reprezentuje metodę, która wykonuje niektóre działania na element określonego typu. Można utworzyć metodę, która wykonuje żądaną akcję na element, <xref:System.Action%601> utworzyć wystąpienie delegata do reprezentowania tej metody, <xref:System.Array.ForEach%2A?displayProperty=nameWithType> a następnie przekazać tablicy i delegata do statycznej metody ogólnej. Metoda jest wywoływana dla każdego elementu tablicy.  
  
 Klasa <xref:System.Collections.Generic.List%601> ogólna zapewnia <xref:System.Collections.Generic.List%601.ForEach%2A> również metodę, która używa delegata. <xref:System.Action%601> Ta metoda nie jest ogólna.  
  
> [!NOTE]
> To sprawia, że interesujący punkt o typy ogólne i metody. Metoda <xref:System.Array.ForEach%2A?displayProperty=nameWithType> musi być`Shared` statyczna (w języku Visual Basic) i ogólna, ponieważ <xref:System.Array> nie jest typem ogólnym; Jedynym powodem, dla którego <xref:System.Array.ForEach%2A?displayProperty=nameWithType> można określić typ do pracy na jest to, że metoda ma własną listę parametrów typu. Natomiast metoda nierodzajowa <xref:System.Collections.Generic.List%601.ForEach%2A?displayProperty=nameWithType> należy do klasy <xref:System.Collections.Generic.List%601>ogólnej, więc po prostu używa parametru typu jego klasy. Klasa jest silnie typizowany, więc metoda może być metoda wystąpienia.  
  
 Delegat <xref:System.Predicate%601> ogólny reprezentuje metodę, która określa, czy określony element spełnia kryteria, które definiujesz. Można go używać z następującymi statycznymi <xref:System.Array> metodami ogólnymi wyszukiwania <xref:System.Array.Exists%2A> <xref:System.Array.Find%2A>elementu <xref:System.Array.FindAll%2A> <xref:System.Array.FindIndex%2A>lub zestawu elementów: , , , <xref:System.Array.FindLast%2A>, , <xref:System.Array.FindLastIndex%2A>i <xref:System.Array.TrueForAll%2A>.  
  
 <xref:System.Predicate%601>współpracuje również z odpowiednimi metodami <xref:System.Collections.Generic.List%601> wystąpienia nierodzajowego klasy ogólnej.  
  
 Ogólny <xref:System.Comparison%601> delegat umożliwia podanie kolejności sortowania dla elementów tablicy lub listy, które nie mają natywnej kolejności sortowania, lub zastąpienie kolejności sortowania macierzystego. Utwórz metodę, która wykonuje porównanie, utwórz wystąpienie <xref:System.Comparison%601> pełnomocnika do reprezentowania metody, a następnie <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Comparison%7B%60%600%7D%29?displayProperty=nameWithType> przekaż tablicę i delegata do statycznej metody ogólnej. Klasa <xref:System.Collections.Generic.List%601> ogólna zapewnia odpowiednie przeciążenie metody wystąpienia, <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29?displayProperty=nameWithType>.  
  
 Ogólny <xref:System.Converter%602> delegat umożliwia zdefiniowanie konwersji między dwoma typami i konwertowanie tablicy jednego typu na tablicę drugiego lub konwertowanie listy jednego typu na listę innych typów. Utwórz metodę, która konwertuje elementy istniejącej listy na nowy typ, utwórz <xref:System.Array.ConvertAll%2A?displayProperty=nameWithType> wystąpienie delegata do reprezentowania metody i użyj ogólnej <xref:System.Collections.Generic.List%601.ConvertAll%60%601%28System.Converter%7B%600%2C%60%600%7D%29?displayProperty=nameWithType> metody statycznej do utworzenia tablicy nowego typu z oryginalnej tablicy lub metody wystąpienia ogólnego do utworzenia listy nowego typu z oryginalnej listy.  
  
### <a name="chaining-delegates"></a>Łańcuchowe delegatów  
 Wiele metod, które używają tych delegatów zwrócić tablicy lub listy, które mogą być przekazywane do innej metody. Na przykład jeśli chcesz zaznaczyć niektóre elementy tablicy, przekonwertować te elementy na nowy typ i zapisać je <xref:System.Array.FindAll%2A> w nowej <xref:System.Array.ConvertAll%2A> tablicy, można przekazać tablicy zwrócone przez metodę rodzajową do metody ogólnej. Jeśli nowy typ elementu nie ma naturalnej kolejności sortowania, <xref:System.Array.ConvertAll%2A> można przekazać <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Comparison%7B%60%600%7D%29> tablicy zwrócone przez metodę rodzajową do metody ogólnej.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [Typy ogólne](../../../docs/standard/generics/index.md)
- [Kolekcje ogólne w oprogramowaniu .NET Framework](../../../docs/standard/generics/collections.md)
- [Interfejsy ogólne](../../../docs/standard/generics/interfaces.md)
- [Kowariancja i kontrawariancja](../../../docs/standard/generics/covariance-and-contravariance.md)
