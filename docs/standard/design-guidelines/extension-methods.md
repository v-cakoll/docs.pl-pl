---
title: Metody rozszerzeń
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 5de945cb-88f4-49d7-b0e6-f098300cf357
ms.openlocfilehash: 13f92470b23d138e0d30bed947ff1932f2605d28
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741624"
---
# <a name="extension-methods"></a>Metody rozszerzeń
Metody rozszerzające są funkcją języka, która umożliwia wywoływanie metod statycznych przy użyciu składni wywołania metody wystąpienia. Te metody muszą przyjmować co najmniej jeden parametr, który reprezentuje wystąpienie, na którym ma działać Metoda.

 Klasa, która definiuje takie metody rozszerzenia, jest określana jako Klasa "sponsora" i musi być zadeklarowana jako statyczna. Aby można było użyć metod rozszerzających, należy zaimportować przestrzeń nazw definiującą klasę sponsora.

 ❌ uniknąć definiowania metod rozszerzających, szczególnie w przypadku typów, które nie są posiadane.

 Jeśli używasz kodu źródłowego typu, rozważ użycie zwykłych metod wystąpienia. Jeśli nie jesteś własnością, i chcesz dodać metodę, należy zachować ostrożność. Zliberalizowane korzystanie z metod rozszerzających ma możliwość bałaganu interfejsów API typów, które nie zostały zaprojektowane w taki sposób, aby miały te metody.

 ✔️ ROZWAŻYĆ użycie metod rozszerzających w jednym z następujących scenariuszy:

- Aby zapewnić funkcje pomocnika odpowiednie dla każdej implementacji interfejsu, jeśli powyższe funkcje mogą być zapisywane w postaci podstawowego interfejsu. Wynika to z tego, że w przeciwnym razie nie można przypisać konkretnych implementacji do interfejsów. Na przykład operatory `LINQ to Objects` są implementowane jako metody rozszerzające dla wszystkich typów <xref:System.Collections.Generic.IEnumerable%601>. W ten sposób wszystkie implementacje `IEnumerable<>` są automatycznie obsługiwane w języku LINQ.

- Gdy metoda wystąpienia wprowadzi zależność od pewnego typu, ale taka zależność spowoduje przerwanie reguł zarządzania zależnościami. Na przykład zależność od <xref:System.String> do <xref:System.Uri?displayProperty=nameWithType> prawdopodobnie nie jest pożądana, a więc `String.ToUri()` metoda wystąpienia zwraca `System.Uri` być niewłaściwym projektem z perspektywy zarządzania zależnościami. Statyczna metoda rozszerzająca `Uri.ToUri(this string str)` zwracać `System.Uri` byłoby znacznie lepszym projektem.

 ❌ uniknąć definiowania metod rozszerzenia na <xref:System.Object?displayProperty=nameWithType>.

 Visual Basic użytkownicy nie będą mogli wywoływać takich metod w odwołaniach do obiektów przy użyciu składni metody rozszerzenia. Visual Basic nie obsługuje wywoływania takich metod, ponieważ, w Visual Basic, deklarując odwołanie jako obiekt wymusza, że wszystkie wywołania metody na nim mają być późne (rzeczywista nazwa elementu członkowskiego jest określana w czasie wykonywania), podczas gdy powiązania z metodami rozszerzenia są określane na czas kompilowania (Wczesna granica).

 Należy zauważyć, że wytyczne dotyczą innych języków, w których występuje takie samo zachowanie dotyczące powiązań lub których metody rozszerzające nie są obsługiwane.

 ❌ nie należy umieszczać metod rozszerzających w tej samej przestrzeni nazw co typ rozszerzony, chyba że służy do dodawania metod do interfejsów ani do zarządzania zależnościami.

 ❌ uniknąć definiowania dwóch lub więcej metod rozszerzających o tej samej sygnaturze, nawet jeśli znajdują się one w różnych przestrzeniach nazw.

 ✔️ ROZWAŻYĆ zdefiniowanie metod rozszerzenia w tej samej przestrzeni nazw, co typ rozszerzony, jeśli typ jest interfejsem i jeśli metody rozszerzające mają być używane w większości lub we wszystkich przypadkach.

 ❌ nie definiują metod rozszerzających implementujących funkcję w przestrzeniach nazw zwykle skojarzonych z innymi funkcjami. Zamiast tego należy je zdefiniować w przestrzeni nazw skojarzonej z funkcją, do której należą.

 ❌ uniknąć ogólnego nazewnictwa przestrzeni nazw przeznaczonych dla metod rozszerzających (np. "rozszerzeń"). Zamiast tego użyj nazwy opisowej (np. "routingu").

 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*

## <a name="see-also"></a>Zobacz także

- [Element członkowski — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/member.md)
- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
