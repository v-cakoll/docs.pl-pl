---
title: Metody rozszerzenia
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 5de945cb-88f4-49d7-b0e6-f098300cf357
ms.openlocfilehash: 2578fbacecd9fe790f72e828b455e8983b1298d3
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709364"
---
# <a name="extension-methods"></a>Metody rozszerzenia
Metody rozszerzające są funkcją języka, która umożliwia wywoływanie metod statycznych przy użyciu składni wywołania metody wystąpienia. Te metody muszą przyjmować co najmniej jeden parametr, który reprezentuje wystąpienie, na którym ma działać Metoda.  
  
 Klasa, która definiuje takie metody rozszerzenia, jest określana jako Klasa "sponsora" i musi być zadeklarowana jako statyczna. Aby można było użyć metod rozszerzających, należy zaimportować przestrzeń nazw definiującą klasę sponsora.  
  
 **X AVOID** frivolously definiowania metod rozszerzenia, szczególnie w przypadku typów nie jesteś właścicielem.  
  
 Jeśli używasz kodu źródłowego typu, rozważ użycie zwykłych metod wystąpienia. Jeśli nie jesteś własnością, i chcesz dodać metodę, należy zachować ostrożność. Zliberalizowane korzystanie z metod rozszerzających ma możliwość bałaganu interfejsów API typów, które nie zostały zaprojektowane w taki sposób, aby miały te metody.  
  
 **✓ CONSIDER** przy użyciu metod rozszerzenia w jednym z następujących scenariuszy:  
  
- Aby zapewnić funkcje pomocnika odpowiednie dla każdej implementacji interfejsu, jeśli powyższe funkcje mogą być zapisywane w postaci podstawowego interfejsu. Wynika to z tego, że w przeciwnym razie nie można przypisać konkretnych implementacji do interfejsów. Na przykład operatory `LINQ to Objects` są implementowane jako metody rozszerzające dla wszystkich typów <xref:System.Collections.Generic.IEnumerable%601>. W ten sposób wszystkie implementacje `IEnumerable<>` są automatycznie obsługiwane w języku LINQ.  
  
- Gdy metoda wystąpienia wprowadzi zależność od pewnego typu, ale taka zależność spowoduje przerwanie reguł zarządzania zależnościami. Na przykład zależność od <xref:System.String> do <xref:System.Uri?displayProperty=nameWithType> prawdopodobnie nie jest pożądana, a więc `String.ToUri()` metoda wystąpienia zwraca `System.Uri` być niewłaściwym projektem z perspektywy zarządzania zależnościami. Statyczna metoda rozszerzająca `Uri.ToUri(this string str)` zwracać `System.Uri` byłoby znacznie lepszym projektem.  
  
 **X AVOID** definiowanie metody rozszerzenia na <xref:System.Object?displayProperty=nameWithType>.  
  
 Visual Basic użytkownicy nie będą mogli wywoływać takich metod w odwołaniach do obiektów przy użyciu składni metody rozszerzenia. Visual Basic nie obsługuje wywoływania takich metod, ponieważ, w Visual Basic, deklarując odwołanie jako obiekt wymusza, że wszystkie wywołania metody na nim mają być późne (rzeczywista nazwa elementu członkowskiego jest określana w czasie wykonywania), podczas gdy powiązania z metodami rozszerzenia są określane na czas kompilowania (Wczesna granica).  
  
 Należy zauważyć, że wytyczne dotyczą innych języków, w których występuje takie samo zachowanie dotyczące powiązań lub których metody rozszerzające nie są obsługiwane.  
  
 **X DO NOT** umieszczenia metod rozszerzenia w tej samej przestrzeni nazw jako typ rozszerzony, chyba że jest dodanie metody interfejsów lub zarządzania zależności.  
  
 **X AVOID** zdefiniowania co najmniej dwie metody rozszerzenia o tej samej sygnaturze, nawet jeśli są one przechowywane w różnych przestrzeniach nazw.  
  
 **✓ CONSIDER** definiowanie metody rozszerzenia w tej samej przestrzeni nazw jako typ rozszerzonej, jeśli typ jest interfejsem i metody rozszerzenia są przeznaczone do użycia w przypadku większości lub wszystkim.  
  
 **X DO NOT** definiować metody rozszerzenia wdrożenie funkcją w przestrzeniach nazw zwykle skojarzone z innymi funkcjami. Zamiast tego należy je zdefiniować w przestrzeni nazw skojarzonej z funkcją, do której należą.  
  
 **X AVOID** ogólnego nazewnictwa przestrzeni nazw przeznaczona do metody rozszerzenia (np. "rozszerzenia"). Zamiast tego użyj nazwy opisowej (np. "routingu").  
  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*  
  
## <a name="see-also"></a>Zobacz także

- [Element członkowski — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/member.md)
- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
