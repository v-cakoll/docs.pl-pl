---
title: Metody rozszerzania
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 5de945cb-88f4-49d7-b0e6-f098300cf357
ms.openlocfilehash: 77c012d7838ae2fa1f62163bc58520db67c64ce5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289762"
---
# <a name="extension-methods"></a>Metody rozszerzeń

Metody rozszerzające są funkcją języka, która umożliwia wywoływanie metod statycznych przy użyciu składni wywołania metody wystąpienia. Te metody muszą przyjmować co najmniej jeden parametr, który reprezentuje wystąpienie, na którym ma działać Metoda.

 Klasa, która definiuje metodę rozszerzenia, jest określana jako Klasa "sponsora" i musi być zadeklarowana jako `static` . Aby użyć metod rozszerzających, należy zaimportować przestrzeń nazw, która definiuje klasę sponsora.

 ❌UNIKAj nadmiernego użycia metod rozszerzających, szczególnie w przypadku typów, które nie są posiadane.

 Jeśli używasz kodu źródłowego typu, rozważ użycie zwykłych metod wystąpienia. Jeśli nie jesteś własnością kodu źródłowego i chcesz dodać metodę, należy zachować ostrożność. Zliberalizowane korzystanie z metod rozszerzających ma możliwość bałaganu interfejsów API typów, które nie zostały zaprojektowane w taki sposób, aby miały te metody.

 ✔️ ROZWAŻYĆ użycie metod rozszerzających w jednym z następujących scenariuszy:

- Aby zapewnić funkcje pomocnika odpowiednie dla każdej implementacji interfejsu, jeśli powyższe funkcje mogą być zapisywane w postaci podstawowego interfejsu. Wynika to z tego, że w przeciwnym razie nie można przypisać konkretnych implementacji do interfejsów. Na przykład operatory LINQ to Objects są implementowane jako metody rozszerzające dla wszystkich <xref:System.Collections.Generic.IEnumerable%601> typów. W rezultacie każda `IEnumerable<>` implementacja jest automatycznie włączona w LINQ.

- Gdy metoda wystąpienia wprowadzi zależność od pewnego typu, ale taka zależność spowoduje przerwanie reguł zarządzania zależnościami. Na przykład zależność od do elementu <xref:System.String> <xref:System.Uri?displayProperty=nameWithType> prawdopodobnie nie jest pożądana, a więc `String.ToUri()` metoda wystąpienia zwraca `System.Uri` niewłaściwy projekt z perspektywy zarządzania zależnościami. Zwracana Metoda rozszerzenia statycznego będzie `Uri.ToUri(this string str)` `System.Uri` znacznie lepszym projektem.

 ❌Należy unikać definiowania metod rozszerzających <xref:System.Object?displayProperty=nameWithType> .

 Visual Basic użytkownicy nie będą mogli wywoływać takich metod w odwołaniach do obiektów przy użyciu składni metody rozszerzenia. W Visual Basic, deklarując odwołanie jako `Object` wymusza późne wywołania wszystkich metod na tym etapie, co oznacza, że rzeczywista wywołana składowa jest określana w czasie wykonywania. Powiązania z metodami rozszerzania są określane w czasie kompilacji (Wczesna granica).

 Niniejsze wytyczne dotyczą innych języków, w których występuje takie samo zachowanie dotyczące powiązań lub których metody rozszerzające nie są obsługiwane.

 ❌NIE należy umieszczać metod rozszerzających w tej samej przestrzeni nazw co typ rozszerzony, chyba że służy do dodawania metod do interfejsów ani do zarządzania zależnościami.

 ❌Należy unikać definiowania dwóch lub więcej metod rozszerzających o tej samej sygnaturze, nawet jeśli znajdują się one w różnych przestrzeniach nazw.

 ✔️ ROZWAŻYĆ zdefiniowanie metod rozszerzenia w tej samej przestrzeni nazw, co typ rozszerzony, jeśli typ jest interfejsem i jeśli metody rozszerzające mają być używane w większości lub we wszystkich przypadkach.

 ❌NIE należy definiować metod rozszerzających implementujących funkcję w przestrzeniach nazw zwykle skojarzonych z innymi funkcjami. Zamiast tego należy je zdefiniować w przestrzeni nazw skojarzonej z funkcją, do której należą.

 ❌UNIKAj ogólnego nazewnictwa przestrzeni nazw przeznaczonych dla metod rozszerzających (np. "rozszerzeń"). Zamiast tego użyj nazwy opisowej (np. "routingu").

 *Fragmenty &copy; 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*

## <a name="see-also"></a>Zobacz także

- [Wskazówki dotyczące projektowania elementów członkowskich](member.md)
- [Wskazówki dotyczące projektowania struktury](index.md)
