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
ms.openlocfilehash: 78d765a7af77b1e6a6ecd483677cea2d4c6b0d5b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709429"
---
# <a name="event-design"></a>Projekt zdarzenia
Zdarzenia są najczęściej używane w formie wywołań zwrotnych (konstrukcje, które umożliwiają platformie Wywoływanie kodu użytkownika). Inne mechanizmy wywołania zwrotnego obejmują członków, którzy korzystają z delegatów, wirtualnych elementów członkowskich i wtyczek opartych na interfejsie. dane z badań użyteczności wskazują, że większość deweloperów jest bardziej wygodna przy użyciu zdarzeń, niż korzystają z innych mechanizmów wywołania zwrotnego . Zdarzenia są dobrze zintegrowane z programem Visual Studio i wieloma językami.  
  
 Należy pamiętać, że istnieją dwie grupy zdarzeń: zdarzenia wywoływane przed zmianą systemu, zwane przed zdarzeniami i zdarzenia zgłoszone po zmianie stanu, nazywanego po wprowadzeniu zdarzeń. Przykładem przedevent może być `Form.Closing`, który jest wywoływany przed zamknięciem formularza. Przykładem zdarzenia po zdarzeniu może być `Form.Closed`, które jest wywoływane po zamknięciu formularza.  
  
 **✓ DO** używany jest termin "raise" dla zdarzenia, a nie "fire" lub "wyzwolenia".  
  
 **✓ DO** użyj <xref:System.EventHandler%601?displayProperty=nameWithType> zamiast ręcznego tworzenia nowych delegatów, które mają być używane jako procedury obsługi zdarzeń.  
  
 **✓ CONSIDER** przy użyciu podklasą <xref:System.EventArgs> jako argument zdarzenia, jeśli nie masz pewności absolutnie zdarzenie nie będzie trzeba do przenoszenia danych do obsługi metody zdarzeń w takim przypadku można zastosować `EventArgs` wpisać bezpośrednio.  
  
 W przypadku dostarczania interfejsu API za pomocą `EventArgs` bezpośrednio nie będzie można dodawać żadnych danych, które mają być przenoszone ze zdarzeniem bez przerywania zgodności. Jeśli używasz podklasy, nawet jeśli początkowo całkowicie jest pusta, możesz w razie potrzeby dodać właściwości do podklasy.  
  
 **✓ DO** Użyj chronione metody wirtualnej, aby wywołać każdego zdarzenia. Ma to zastosowanie tylko do zdarzeń niestatycznych dla niezapieczętowanych klas, nie do struktur, klas zapieczętowanych lub zdarzeń statycznych.  
  
 Celem metody jest zapewnienie metodu do obsługi zdarzenia przy użyciu przesłonięcia klasy pochodnej. Zastępowanie jest bardziej elastyczne, szybsze i bardziej naturalne w przypadku obsługi zdarzeń klasy podstawowej w klasach pochodnych. Według Konwencji, nazwa metody powinna zaczynać się od "on" i następować nazwą zdarzenia.  
  
 Klasa pochodna może zrezygnować z implementacji podstawowej metody w jej zastępowaniu. Przygotowuje się do tego przez nie uwzględniając żadnego przetwarzania w metodzie, która jest wymagana do poprawnego działania klasy bazowej.  
  
 **✓ DO** przyjmować jeden parametr do metody chronionych, która wywołuje zdarzenie.  
  
 Parametr powinien mieć nazwę `e` i powinien być typem klasy argumentu zdarzenia.  
  
 **X DO NOT** należy przekazać wartość null jako nadawcę podczas wywołaniem Niestatyczne zdarzenia.  
  
 **✓ DO** przekazać wartości null jako nadawcę, gdy wywołaniem zdarzenia statyczne.  
  
 **X DO NOT** przekazać wartości null jako parametr danych zdarzenia, gdy wywołanie zdarzenia.  
  
 Należy przekazać `EventArgs.Empty`, jeśli nie chcesz przekazać żadnych danych do metody obsługi zdarzeń. Deweloperzy oczekują, że ten parametr nie ma wartości null.  
  
 **✓ CONSIDER** wywoływanie zdarzeń, które użytkownik końcowy może anulować. Dotyczy to przede wszystkim zdarzeń.  
  
 Użyj <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> lub jej podklasy jako argumentu zdarzenia, aby umożliwić użytkownikowi końcowemu anulowanie zdarzeń.  
  
### <a name="custom-event-handler-design"></a>Projekt programu obsługi zdarzeń niestandardowych  
 Istnieją przypadki, w których nie można użyć `EventHandler<T>`, na przykład gdy struktura musi działać we wcześniejszych wersjach środowiska CLR, które nie obsługują typów ogólnych. W takich przypadkach może być konieczne zaprojektowanie i opracowanie niestandardowego delegata obsługi zdarzeń.  
  
 **✓ DO** zwracany typ void na użytek obsługi zdarzeń.  
  
 Procedura obsługi zdarzeń może wywoływać wiele metod obsługi zdarzeń, prawdopodobnie na wielu obiektach. Jeśli metody obsługi zdarzeń mogły zwrócić wartość, dla każdego wywołania zdarzenia może istnieć wiele wartości zwracanych.  
  
 **✓ DO** użyj `object` jako typ pierwszego parametru metody obsługi zdarzeń i nadaj mu `sender`.  
  
 **✓ DO** użyj <xref:System.EventArgs?displayProperty=nameWithType> ani jej podklasy jako typ drugiego parametru obsługi zdarzeń i nadaj mu `e`.  
  
 **X DO NOT** ma więcej niż dwa parametry dotyczące programu obsługi zdarzeń.  
  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*  
  
## <a name="see-also"></a>Zobacz także

- [Element członkowski — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/member.md)
- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
