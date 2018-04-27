---
title: Metody rozszerzeń
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5de945cb-88f4-49d7-b0e6-f098300cf357
caps.latest.revision: 4
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6247b6d1718f43d4b05d585cc12a05c5e0cc2035
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="extension-methods"></a>Metody rozszerzeń
Metody rozszerzenia są funkcją języka, która umożliwia metody statyczne do jej wywołać przy użyciu składni wywołanie metody wystąpienia. Te metody należy wykonać co najmniej jeden parametr, który reprezentuje wystąpienie, którego metoda ma działać na.  
  
 Klasa, która definiuje takich metod rozszerzenia jest określany jako klasa "sponsor", a musi być zadeklarowany jako statyczny. Aby używać metody rozszerzenia, jeden zaimportować definiujący klasę sponsor przestrzeni nazw.  
  
 **X należy UNIKAĆ** frivolously definiowania metod rozszerzenia, szczególnie w przypadku typów nie jesteś właścicielem.  
  
 Jeśli masz kod źródłowy typu metody wystąpienia regularnego zamiast tego Rozważ użycie. Jeśli nie jesteś właścicielem, i chcesz dodać metodę, trzeba zwrócić szczególną uwagę. Rozległych korzystanie z metod rozszerzenia stwarza możliwość potencjalnego przeładowania interfejsów API typów, które nie zostały zaprojektowane do mają tych metod.  
  
 **ROZWAŻ ✓** przy użyciu metod rozszerzenia w jednym z następujących scenariuszy:  
  
-   Zapewnienie pomocy funkcji zastosowanie w każdej implementacji interfejsu, w przypadku funkcji mogą być napisane pod względem interfejsu core. Jest to spowodowane konkretnych implementacji, w przeciwnym razie nie można przypisać do interfejsów. Na przykład `LINQ to Objects` operatory są zaimplementowane jako metody rozszerzenia dla wszystkich <xref:System.Collections.Generic.IEnumerable%601> typów. W związku z tym wszelkie `IEnumerable<>` implementacja jest włączane automatycznie LINQ.  
  
-   Gdy metodą wystąpienia spowodowałoby to powstanie zależności pewien typ, ale takie zależności spowoduje przerwanie zasady zarządzania zależności. Na przykład zależność od <xref:System.String> do <xref:System.Uri?displayProperty=nameWithType> prawdopodobnie nie jest pożądane i dlatego `String.ToUri()` metody wystąpienia zwracanie `System.Uri` jest niewłaściwy projekt z punktu widzenia zarządzania zależności. Metody statyczne rozszerzenie `Uri.ToUri(this string str)` zwracanie `System.Uri` będzie znacznie lepszą projektu.  
  
 **X należy UNIKAĆ** definiowanie metody rozszerzenia na <xref:System.Object?displayProperty=nameWithType>.  
  
 Użytkownicy VB nie będą mogli może wywołać metody te odwołania do obiektów przy użyciu składni metody rozszerzenia. VB nie obsługuje wywoływania takich metod, ponieważ w języku VB, deklarowanie odwołania, jak obiekt wymusza wszystkich wywołań metod na nim być opóźnione powiązany (faktycznego elementu członkowskiego o nazwie jest określana w czasie wykonywania), podczas gdy powiązania z metody rozszerzenia są określane w czasie kompilacji (wcześniej powiązany).  
  
 Należy pamiętać, że wytyczna ma zastosowanie do innych języków, w których ma takie samo zachowanie wiązania, lub gdy metody rozszerzenia nie są obsługiwane.  
  
 **X nie** umieszczenia metod rozszerzenia w tej samej przestrzeni nazw jako typ rozszerzony, chyba że jest dodanie metody interfejsów lub zarządzania zależności.  
  
 **X należy UNIKAĆ** zdefiniowania co najmniej dwie metody rozszerzenia o tej samej sygnaturze, nawet jeśli są one przechowywane w różnych przestrzeniach nazw.  
  
 **ROZWAŻ ✓** definiowanie metody rozszerzenia w tej samej przestrzeni nazw jako typ rozszerzonej, jeśli typ jest interfejsem i metody rozszerzenia są przeznaczone do użycia w przypadku większości lub wszystkim.  
  
 **X nie** definiować metody rozszerzenia wdrożenie funkcją w przestrzeniach nazw zwykle skojarzone z innymi funkcjami. Zamiast tego należy je zdefiniować w skojarzonych z funkcją, które należą do przestrzeni nazw.  
  
 **X należy UNIKAĆ** ogólnego nazewnictwa przestrzeni nazw przeznaczona do metody rozszerzenia (np. "rozszerzenia"). Użyj nazwy opisowej (np. "Routing") zamiast tego.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 [Element członkowski — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/member.md)  
 [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
