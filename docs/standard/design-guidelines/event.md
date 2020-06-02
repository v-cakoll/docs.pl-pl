---
title: Projekt zdarzenia
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- pre-events
- events [.NET Framework], design guidelines
- member design guidelines, events
- event handlers [.NET Framework], event design guidelines
- post-events
- signatures, event handling
ms.assetid: 67b3c6e2-6a8f-480d-a78f-ebeeaca1b95a
ms.openlocfilehash: 852c99b1a41691911f7ae82d3b8104526811757d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289827"
---
# <a name="event-design"></a>Projekt zdarzenia
Zdarzenia są najczęściej używane w formie wywołań zwrotnych (konstrukcje, które umożliwiają platformie Wywoływanie kodu użytkownika). Inne mechanizmy wywołania zwrotnego obejmują członków, którzy korzystają z delegatów, wirtualnych elementów członkowskich i wtyczek opartych na interfejsie. dane z badań użyteczności wskazują, że większość deweloperów jest bardziej wygodna przy użyciu zdarzeń, niż korzystają z innych mechanizmów wywołania zwrotnego. Zdarzenia są dobrze zintegrowane z programem Visual Studio i wieloma językami.

 Należy pamiętać, że istnieją dwie grupy zdarzeń: zdarzenia wywoływane przed zmianą systemu, zwane przed zdarzeniami i zdarzenia zgłoszone po zmianie stanu, nazywanego po wprowadzeniu zdarzeń. Przykładem przed zdarzeniem jest `Form.Closing` , który jest wywoływany przed zamknięciem formularza. Przykładem zdarzenia po zdarzeniu może być `Form.Closed` , które jest wywoływane po zamknięciu formularza.

 ✔️ należy używać terminu "Zgłoś" dla zdarzeń, a nie "ognia" lub "wyzwalacza".

 ✔️ używać <xref:System.EventHandler%601?displayProperty=nameWithType> zamiast ręcznego tworzenia nowych delegatów, które mają być używane jako programy obsługi zdarzeń.

 ✔️ ROZWAŻYĆ użycie podklasy <xref:System.EventArgs> jako argumentu zdarzenia, o ile nie masz absolutnej pewności, że zdarzenie nigdy nie będzie wymagało przeprowadzenia jakichkolwiek danych do metody obsługi zdarzeń, w takim przypadku można użyć `EventArgs` typu bezpośrednio.

 Jeśli interfejs API jest dostarczany `EventArgs` bezpośrednio, nigdy nie będzie można dodawać żadnych danych, które mają być przenoszone ze zdarzeniem bez przerywania zgodności. Jeśli używasz podklasy, nawet jeśli początkowo całkowicie jest pusta, możesz w razie potrzeby dodać właściwości do podklasy.

 Aby zgłosić każde zdarzenie, ✔️ użyj chronionej metody wirtualnej. Ma to zastosowanie tylko do zdarzeń niestatycznych dla niezapieczętowanych klas, nie do struktur, klas zapieczętowanych lub zdarzeń statycznych.

 Celem metody jest zapewnienie metodu do obsługi zdarzenia przy użyciu przesłonięcia klasy pochodnej. Zastępowanie jest bardziej elastyczne, szybsze i bardziej naturalne w przypadku obsługi zdarzeń klasy podstawowej w klasach pochodnych. Według Konwencji, nazwa metody powinna zaczynać się od "on" i następować nazwą zdarzenia.

 Klasa pochodna może zrezygnować z implementacji podstawowej metody w jej zastępowaniu. Przygotowuje się do tego przez nie uwzględniając żadnego przetwarzania w metodzie, która jest wymagana do poprawnego działania klasy bazowej.

 ✔️ przyjmuje jeden parametr do metody chronionej, która wywołuje zdarzenie.

 Parametr powinien mieć nazwę `e` i powinien być typem klasy argumentu zdarzenia.

 ❌NIE przekazuj wartości null jako nadawcy podczas podnoszenia niestatycznego zdarzenia.

 ✔️ przekazywać wartości null jako nadawcy podczas podnoszenia zdarzenia statycznego.

 ❌NIE przekazuj wartości null jako parametru danych zdarzenia podczas podnoszenia zdarzenia.

 Należy przekazać, `EventArgs.Empty` Jeśli nie chcesz przekazać żadnych danych do metody obsługi zdarzeń. Deweloperzy oczekują, że ten parametr nie ma wartości null.

 ✔️ ROZWAŻYĆ podnoszenie poziomu zdarzeń, które użytkownik końcowy może anulować. Dotyczy to przede wszystkim zdarzeń.

 Użyj <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> lub jej podklasy jako argumentu zdarzenia, aby umożliwić użytkownikowi końcowemu anulowanie zdarzeń.

### <a name="custom-event-handler-design"></a>Projekt programu obsługi zdarzeń niestandardowych
 Istnieją przypadki, w których `EventHandler<T>` nie można ich użyć, na przykład gdy struktura musi działać we wcześniejszych wersjach środowiska CLR, które nie obsługują typów ogólnych. W takich przypadkach może być konieczne zaprojektowanie i opracowanie niestandardowego delegata obsługi zdarzeń.

 ✔️ używać zwracanego typu void dla programów obsługi zdarzeń.

 Procedura obsługi zdarzeń może wywoływać wiele metod obsługi zdarzeń, prawdopodobnie na wielu obiektach. Jeśli metody obsługi zdarzeń mogły zwrócić wartość, dla każdego wywołania zdarzenia może istnieć wiele wartości zwracanych.

 ✔️ użyć `object` jako typu pierwszego parametru programu obsługi zdarzeń i wywołać go `sender` .

 ✔️ używać <xref:System.EventArgs?displayProperty=nameWithType> lub jej podklasy jako typu drugiego parametru programu obsługi zdarzeń i wywoływać `e` .

 ❌W obsłudze zdarzeń nie ma więcej niż dwa parametry.

 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*

## <a name="see-also"></a>Zobacz także

- [Wskazówki dotyczące projektowania elementów członkowskich](member.md)
- [Wskazówki dotyczące projektowania struktury](index.md)
