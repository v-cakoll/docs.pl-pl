---
title: Metody rozszerzeń
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 5de945cb-88f4-49d7-b0e6-f098300cf357
author: KrzysztofCwalina
ms.openlocfilehash: bd5f67c3bd766625e7c22b3ca9986cfbca8854bf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54621763"
---
# <a name="extension-methods"></a>Metody rozszerzeń
Metody rozszerzenia są funkcją języka, umożliwiająca metody statyczne, które można wywoływać za pomocą składni wywołania metody wystąpienia. Te metody musi mieć co najmniej jeden parametr, który reprezentuje wystąpienie, którego metoda jest używana w ramach operacji.  
  
 Klasa, która definiuje takie metody rozszerzenia jest określany jako klasy "sponsora", a musi być zadeklarowana jako statyczna. Można użyć metod rozszerzających, jeden zaimportować Definiowanie klasy sponsora przestrzeni nazw.  
  
 **X AVOID** frivolously definiowania metod rozszerzenia, szczególnie w przypadku typów nie jesteś właścicielem.  
  
 Jeśli jesteś właścicielem kodu źródłowego typu, metody regularnego wystąpienia zamiast tego Rozważ użycie. Jeśli nie jesteś właścicielem, i chcesz dodać metodę, należy zwrócić szczególną uwagę. Liberalne stosowanie metod rozszerzenia stwarza możliwość potencjalnego zaśmiecania interfejsów API, typów, które nie zostały zaprojektowane do mieć tych metod.  
  
 **✓ CONSIDER** przy użyciu metod rozszerzenia w jednym z następujących scenariuszy:  
  
-   Zapewnienie pomocy funkcji, które dotyczą każdej implementacji interfejsu, w przypadku funkcji mogą być napisane pod kątem interfejsu core. Jest to spowodowane konkretnych implementacji, w przeciwnym razie nie można przypisać do interfejsów. Na przykład `LINQ to Objects` operatory są implementowane jako metody rozszerzenia dla wszystkich <xref:System.Collections.Generic.IEnumerable%601> typów. W związku z dowolnego `IEnumerable<>` implementacja jest włączane automatycznie LINQ.  
  
-   Gdy metoda wystąpienia spowodowałoby to powstanie zależności pewnego typu, ale takie zależności zaburzyłaby reguły zarządzania zależności. Na przykład zależność od <xref:System.String> do <xref:System.Uri?displayProperty=nameWithType> prawdopodobnie nie jest pożądane, a tym samym `String.ToUri()` metodę wystąpienia, zwracając `System.Uri` będzie niewłaściwy projekt z punktu widzenia zarządzania zależności. Metody statyczne rozszerzenie `Uri.ToUri(this string str)` zwracanie `System.Uri` będzie znacznie lepiej projektu.  
  
 **X AVOID** definiowanie metody rozszerzenia na <xref:System.Object?displayProperty=nameWithType>.  
  
 Użytkownicy VB nie będzie wywoływać tych metod w odwołania do obiektu za pomocą składni metody rozszerzenia. VB nie obsługuje wywoływania takich metod, ponieważ w języku Visual Basic, deklaruje odwołanie, jako obiekt wymusza wszystkich wywołań metod w celu Spóźnię się powiązany (rzeczywistego elementu członkowskiego, wywoływana jest określana w czasie wykonywania), podczas gdy powiązania z metody rozszerzenia są określane w czasie kompilacji (wcześnie powiązany).  
  
 Należy pamiętać, że wytyczna ma zastosowanie do innych języków, w którym znajduje się takie samo zachowanie powiązania, lub gdy metody rozszerzenia nie są obsługiwane.  
  
 **X DO NOT** umieszczenia metod rozszerzenia w tej samej przestrzeni nazw jako typ rozszerzony, chyba że jest dodanie metody interfejsów lub zarządzania zależności.  
  
 **X AVOID** zdefiniowania co najmniej dwie metody rozszerzenia o tej samej sygnaturze, nawet jeśli są one przechowywane w różnych przestrzeniach nazw.  
  
 **✓ CONSIDER** definiowanie metody rozszerzenia w tej samej przestrzeni nazw jako typ rozszerzonej, jeśli typ jest interfejsem i metody rozszerzenia są przeznaczone do użycia w przypadku większości lub wszystkim.  
  
 **X DO NOT** definiować metody rozszerzenia wdrożenie funkcją w przestrzeniach nazw zwykle skojarzone z innymi funkcjami. Zamiast tego zdefiniuj je w przestrzeni nazw skojarzonego z funkcją, które należą do.  
  
 **X AVOID** ogólnego nazewnictwa przestrzeni nazw przeznaczona do metody rozszerzenia (np. "rozszerzenia"). Użyj nazwy opisowej (np. "Routing") zamiast tego.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Przedrukowano za uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams publikowane 22 Oct 2008 przez Addison Wesley Professional w ramach serii rozwoju Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz także

- [Element członkowski — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/member.md)
- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
