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
ms.openlocfilehash: b0ecd8661b7c58645e49ca884ed0499e8c828af9
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287535"
---
# <a name="generic-delegates-for-manipulating-arrays-and-lists"></a>Delegaty ogólne do manipulowania tablicami i listami
Ten temat zawiera przegląd ogólnych delegatów dla konwersji, predykatów wyszukiwania i akcji, które mają być podejmowane w elementach tablicy lub kolekcji.  
  
## <a name="generic-delegates-for-manipulating-arrays-and-lists"></a>Delegaty ogólne do manipulowania tablicami i listami  
 <xref:System.Action%601>Delegat generyczny reprezentuje metodę wykonującą pewne działania na elemencie określonego typu. Można utworzyć metodę, która wykonuje żądaną akcję dla elementu, utworzyć wystąpienie <xref:System.Action%601> delegata do reprezentowania tej metody, a następnie przekazać tablicę i delegata do <xref:System.Array.ForEach%2A?displayProperty=nameWithType> statycznej metody ogólnej. Metoda jest wywoływana dla każdego elementu tablicy.  
  
 <xref:System.Collections.Generic.List%601>Klasa generyczna udostępnia również <xref:System.Collections.Generic.List%601.ForEach%2A> metodę, która używa <xref:System.Action%601> delegata. Ta metoda nie jest rodzajowa.  
  
> [!NOTE]
> Pozwala to na interesujący punkt dotyczący typów ogólnych i metod. <xref:System.Array.ForEach%2A?displayProperty=nameWithType>Metoda musi być statyczna ( `Shared` w Visual Basic) i generyczna, ponieważ <xref:System.Array> nie jest typem ogólnym. jedyną przyczyną, którą można określić typ <xref:System.Array.ForEach%2A?displayProperty=nameWithType> do działania, jest to, że metoda ma własną listę parametrów typu. Z kolei Metoda niegeneryczna <xref:System.Collections.Generic.List%601.ForEach%2A?displayProperty=nameWithType> należy do klasy generycznej <xref:System.Collections.Generic.List%601> , dlatego po prostu używa parametru typu klasy. Klasa jest silnie wpisana, dlatego metoda może być metodą wystąpienia.  
  
 <xref:System.Predicate%601>Delegat ogólny reprezentuje metodę, która określa, czy konkretny element spełnia zdefiniowane kryteria. Można go użyć z następującymi statycznymi metodami ogólnymi, <xref:System.Array> Aby wyszukać element lub zestaw elementów:,,,,, <xref:System.Array.Exists%2A> <xref:System.Array.Find%2A> <xref:System.Array.FindAll%2A> <xref:System.Array.FindIndex%2A> <xref:System.Array.FindLast%2A> <xref:System.Array.FindLastIndex%2A> i <xref:System.Array.TrueForAll%2A> .  
  
 <xref:System.Predicate%601>działa również z odpowiednimi nieogólnymi metodami wystąpień <xref:System.Collections.Generic.List%601> klasy generycznej.  
  
 <xref:System.Comparison%601>Delegat ogólny umożliwia podanie kolejności sortowania dla elementów tablicy lub listy, które nie mają natywnej kolejności sortowania ani przesłaniania natywnej kolejności sortowania. Utwórz metodę, która wykonuje porównanie, Utwórz wystąpienie <xref:System.Comparison%601> delegata reprezentujące metodę, a następnie Przekaż tablicę i delegata do <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Comparison%7B%60%600%7D%29?displayProperty=nameWithType> statycznej metody ogólnej. <xref:System.Collections.Generic.List%601>Klasa generyczna zapewnia odpowiednie Przeciążenie metody wystąpienia, <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29?displayProperty=nameWithType> .  
  
 <xref:System.Converter%602>Delegat generyczny umożliwia zdefiniowanie konwersji między dwoma typami, a także konwersję tablicy jednego typu na tablicę lub konwersję listy jednego typu na listę innych. Utwórz metodę, która konwertuje elementy istniejącej listy na nowy typ, Utwórz wystąpienie delegata reprezentujące metodę i Użyj <xref:System.Array.ConvertAll%2A?displayProperty=nameWithType> generycznej metody statycznej, aby utworzyć tablicę nowego typu z oryginalnej tablicy, lub <xref:System.Collections.Generic.List%601.ConvertAll%60%601%28System.Converter%7B%600%2C%60%600%7D%29?displayProperty=nameWithType> metodę wystąpienia ogólnego, aby utworzyć listę nowych typów z listy pierwotnej.  
  
### <a name="chaining-delegates"></a>Tworzenie łańcuchów obiektów delegowanych  
 Wiele metod, które używają tych delegatów, zwraca tablicę lub listę, które mogą być przesyłane do innej metody. Na przykład jeśli chcesz wybrać niektóre elementy tablicy, przekonwertuj te elementy na nowy typ i Zapisz je w nowej tablicy, możesz przekazać tablicę zwracaną przez <xref:System.Array.FindAll%2A> metodę rodzajową do <xref:System.Array.ConvertAll%2A> metody ogólnej. Jeśli typ nowego elementu nie ma naturalnej kolejności sortowania, można przekazać tablicę zwracaną przez <xref:System.Array.ConvertAll%2A> metodę rodzajową do <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Comparison%7B%60%600%7D%29> metody ogólnej.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [Typy ogólne](index.md)
- [Kolekcje ogólne w oprogramowaniu .NET Framework](collections.md)
- [Interfejsy ogólne](interfaces.md)
- [Kowariancja i kontrawariancja](covariance-and-contravariance.md)
