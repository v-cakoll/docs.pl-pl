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
ms.openlocfilehash: 566a2e5e8587dc6d6d2259a5f79f5c59c2e60c90
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="generic-delegates-for-manipulating-arrays-and-lists"></a>Delegaty ogólne do manipulowania tablicami i listami
Ten temat zawiera omówienie delegatów konwersje, predykatów wyszukiwania i działań podejmowanych w przypadku elementów tablicy lub kolekcji.  
  
## <a name="generic-delegates-for-manipulating-arrays-and-lists"></a>Delegaty ogólne do manipulowania tablicami i listami  
 <xref:System.Action%601> Delegat ogólny reprezentuje metodę, która wykonuje akcję na element o określonym typie. Można utworzyć metody, która wykonuje żądanej akcji dla elementu, Utwórz wystąpienie <xref:System.Action%601> delegata do reprezentowania tej metody, a następnie przekazać tablicy a obiektem delegowanym do <xref:System.Array.ForEach%2A?displayProperty=nameWithType> statycznej metody rodzajowej. Metoda jest wywoływana dla każdego elementu tablicy.  
  
 <xref:System.Collections.Generic.List%601> Udostępnia ogólne klasy <xref:System.Collections.Generic.List%601.ForEach%2A> metody, która używa <xref:System.Action%601> delegowanie. Ta metoda nie jest rodzajowa.  
  
> [!NOTE]
>  Dzięki temu interesujące punktu dotyczące typów ogólnych i metod. <xref:System.Array.ForEach%2A?displayProperty=nameWithType> Metody muszą być statyczne (`Shared` w języku Visual Basic) i rodzajowy ponieważ <xref:System.Array> ogólnego nie jest typu; tylko Przyczyna, można określić typ dla <xref:System.Array.ForEach%2A?displayProperty=nameWithType> do działania na się, że metoda ma własną listy parametrów typu. Przez kontrast, nongeneric <xref:System.Collections.Generic.List%601.ForEach%2A?displayProperty=nameWithType> metoda należy do klasy ogólnej <xref:System.Collections.Generic.List%601>, więc po prostu używa parametr typu w klasie. Klasa jest silnie typizowane, dlatego metoda może być metodą wystąpienia.  
  
 <xref:System.Predicate%601> Delegat ogólny reprezentuje metodę, która określa, czy dany element spełnia kryteria, należy zdefiniować. Korzystając z następujących ogólnych metod statycznych <xref:System.Array> do wyszukiwania element lub zbiór elementów: <xref:System.Array.Exists%2A>, <xref:System.Array.Find%2A>, <xref:System.Array.FindAll%2A>, <xref:System.Array.FindIndex%2A>, <xref:System.Array.FindLast%2A>, <xref:System.Array.FindLastIndex%2A>, i <xref:System.Array.TrueForAll%2A>.  
  
 <xref:System.Predicate%601> współdziała również z odpowiedniej metody wystąpienia nierodzajowe <xref:System.Collections.Generic.List%601> klasy ogólnej.  
  
 <xref:System.Comparison%601> Delegat ogólny umożliwia zapewnienie porządek sortowania dla tablicy lub listę elementów, które nie mają macierzysty sortowania lub zmiana kolejności sortowania macierzystego. Tworzenie metody, która przeprowadza porównanie, Utwórz wystąpienie <xref:System.Comparison%601> pełnomocnika, aby reprezentować metodę, a następnie przekazać tablicy a obiektem delegowanym do <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Comparison%7B%60%600%7D%29?displayProperty=nameWithType> statycznej metody rodzajowej. <xref:System.Collections.Generic.List%601> Klasy ogólnej zawiera odpowiednie przeciążenie metody wystąpienia <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29?displayProperty=nameWithType>.  
  
 <xref:System.Converter%602> Delegat ogólny umożliwia definiowanie konwersji między dwoma typami i konwertowanie tablicy typu jeden na tablicę innych lub przekonwertować listę jeden typ innych listę. Tworzenie metody, która konwertuje na nowy typ elementów listy, Utwórz wystąpienie obiektu delegowanego będzie odpowiadać metoda i użyj <xref:System.Array.ConvertAll%2A?displayProperty=nameWithType> statycznej metody ogólnej do utworzenia tablicy nowego typu z oryginalnego tablicy lub <xref:System.Collections.Generic.List%601.ConvertAll%60%601%28System.Converter%7B%600%2C%60%600%7D%29?displayProperty=nameWithType> ogólne wystąpienie metody do tworzenia listy nowy typ z oryginalnej listy.  
  
### <a name="chaining-delegates"></a>Łączenie w łańcuchy delegatów  
 Wiele metod, korzystających z tych obiektów delegowanych zwracać tablicy lub listy, które mogą zostać przekazane do innej metody. Na przykład, jeśli chcesz wybrać określone elementy tablicy, konwersji tych elementów do nowego typu i zapisać je w nowej tablicy można przekazać tablica zwrócona przez <xref:System.Array.FindAll%2A> metody ogólnej do <xref:System.Array.ConvertAll%2A> metody rodzajowej. Jeśli nowy typ elementu nie ma fizycznych sortowania, można przekazać tablica zwrócona przez <xref:System.Array.ConvertAll%2A> metody ogólnej do <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Comparison%7B%60%600%7D%29> metody rodzajowej.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
 <xref:System.Collections.ObjectModel?displayProperty=nameWithType>  
 [Typy ogólne](../../../docs/standard/generics/index.md)  
 [Kolekcje ogólne w oprogramowaniu .NET Framework](../../../docs/standard/generics/collections.md)  
 [Interfejsy ogólne](../../../docs/standard/generics/interfaces.md)  
 [Kowariancja i kontrawariancja](../../../docs/standard/generics/covariance-and-contravariance.md)
