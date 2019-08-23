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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f37f55f5af70a232952bdb94f0c111a27fcbab1d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948782"
---
# <a name="generic-delegates-for-manipulating-arrays-and-lists"></a>Delegaty ogólne do manipulowania tablicami i listami
Ten temat zawiera przegląd ogólnych delegatów dla konwersji, predykatów wyszukiwania i akcji, które mają być podejmowane w elementach tablicy lub kolekcji.  
  
## <a name="generic-delegates-for-manipulating-arrays-and-lists"></a>Delegaty ogólne do manipulowania tablicami i listami  
 Delegat <xref:System.Action%601> generyczny reprezentuje metodę wykonującą pewne działania na elemencie określonego typu. Można utworzyć metodę, która wykonuje żądaną akcję dla elementu, utworzyć wystąpienie <xref:System.Action%601> delegata do reprezentowania tej metody, a następnie przekazać tablicę i delegata <xref:System.Array.ForEach%2A?displayProperty=nameWithType> do statycznej metody ogólnej. Metoda jest wywoływana dla każdego elementu tablicy.  
  
 Klasa generyczna <xref:System.Collections.Generic.List%601.ForEach%2A> udostępnia również metodę, która używa <xref:System.Action%601> delegata. <xref:System.Collections.Generic.List%601> Ta metoda nie jest rodzajowa.  
  
> [!NOTE]
> Pozwala to na interesujący punkt dotyczący typów ogólnych i metod. Metoda musi być statyczna (`Shared` w Visual Basic) i generyczna <xref:System.Array> , ponieważ nie jest typem ogólnym. <xref:System.Array.ForEach%2A?displayProperty=nameWithType> jedyną przyczyną, którą można określić typ do działania, jest to, że metoda ma własną listę parametrów typu. <xref:System.Array.ForEach%2A?displayProperty=nameWithType> Z kolei Metoda niegeneryczna <xref:System.Collections.Generic.List%601.ForEach%2A?displayProperty=nameWithType> należy do klasy <xref:System.Collections.Generic.List%601>generycznej, dlatego po prostu używa parametru typu klasy. Klasa jest silnie wpisana, dlatego metoda może być metodą wystąpienia.  
  
 Delegat <xref:System.Predicate%601> ogólny reprezentuje metodę, która określa, czy konkretny element spełnia zdefiniowane kryteria. Można go użyć z następującymi statycznymi metodami <xref:System.Array> ogólnymi, aby wyszukać element lub zestaw elementów: <xref:System.Array.Exists%2A> <xref:System.Array.Find%2A> <xref:System.Array.FindAll%2A> <xref:System.Array.FindLastIndex%2A>,, <xref:System.Array.FindIndex%2A> <xref:System.Array.FindLast%2A>,,, i <xref:System.Array.TrueForAll%2A>.  
  
 <xref:System.Predicate%601>działa również z odpowiednimi nieogólnymi metodami <xref:System.Collections.Generic.List%601> wystąpień klasy generycznej.  
  
 Delegat <xref:System.Comparison%601> ogólny umożliwia podanie kolejności sortowania dla elementów tablicy lub listy, które nie mają natywnej kolejności sortowania ani przesłaniania natywnej kolejności sortowania. Utwórz metodę, która wykonuje porównanie, Utwórz wystąpienie <xref:System.Comparison%601> delegata reprezentujące metodę, a następnie Przekaż tablicę i delegata <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Comparison%7B%60%600%7D%29?displayProperty=nameWithType> do statycznej metody ogólnej. Klasa generyczna zapewnia odpowiednie Przeciążenie metody wystąpienia, <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29?displayProperty=nameWithType>. <xref:System.Collections.Generic.List%601>  
  
 Delegat <xref:System.Converter%602> generyczny umożliwia zdefiniowanie konwersji między dwoma typami, a także konwersję tablicy jednego typu na tablicę lub konwersję listy jednego typu na listę innych. Utwórz metodę, która konwertuje elementy istniejącej listy na nowy typ, Utwórz wystąpienie delegata reprezentujące metodę i Użyj <xref:System.Array.ConvertAll%2A?displayProperty=nameWithType> generycznej metody statycznej, aby utworzyć tablicę nowego typu z oryginalnej tablicy <xref:System.Collections.Generic.List%601.ConvertAll%60%601%28System.Converter%7B%600%2C%60%600%7D%29?displayProperty=nameWithType> lub ogólnego Metoda wystąpienia służąca do tworzenia listy nowych typów z listy pierwotnej.  
  
### <a name="chaining-delegates"></a>Tworzenie łańcuchów obiektów delegowanych  
 Wiele metod, które używają tych delegatów, zwraca tablicę lub listę, które mogą być przesyłane do innej metody. Na przykład jeśli chcesz wybrać niektóre elementy tablicy, przekonwertuj te elementy na nowy typ i Zapisz je w nowej tablicy, możesz przekazać tablicę zwracaną przez <xref:System.Array.FindAll%2A> metodę rodzajową <xref:System.Array.ConvertAll%2A> do metody ogólnej. Jeśli typ nowego elementu nie ma naturalnej kolejności sortowania, można przekazać tablicę zwracaną przez <xref:System.Array.ConvertAll%2A> metodę rodzajową <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Comparison%7B%60%600%7D%29> do metody ogólnej.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [Typy ogólne](../../../docs/standard/generics/index.md)
- [Kolekcje ogólne w oprogramowaniu .NET Framework](../../../docs/standard/generics/collections.md)
- [Interfejsy ogólne](../../../docs/standard/generics/interfaces.md)
- [Kowariancja i kontrawariancja](../../../docs/standard/generics/covariance-and-contravariance.md)
