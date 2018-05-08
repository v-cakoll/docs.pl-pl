---
title: Projekt zdarzeń
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- pre-events
- events [.NET Framework], design guidelines
- member design guidelines, events
- event handlers [.NET Framework], event design guidelines
- post-events
- signatures, event handling
ms.assetid: 67b3c6e2-6a8f-480d-a78f-ebeeaca1b95a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 48d1ad0f02ae34675c0a910d7651d718c060db60
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="event-design"></a>Projekt zdarzeń
Zdarzenia są najczęściej używane formę wywołania zwrotne (konstrukcji umożliwiających framework do wywołania do kodu użytkownika). Inne mechanizmy wywołania zwrotnego zawierać elementów członkowskich delegatów, wirtualne elementy członkowskie i oparty na używanie dodatków. Dane z badań użyteczność wskazania, że większość deweloperów wygodniejsze za pomocą zdarzeń, nie są one za pomocą innych mechanizmów wywołania zwrotnego. Zdarzenia są dobrze zintegrowane z usługą Visual Studio i wielu języków.  
  
 Należy pamiętać, że istnieją dwie grupy zdarzeń: zdarzenia wywoływane przed wykonaniem stan zmian w systemie, nazywanych zdarzeń poprzedzających i zdarzenia wywoływane po zmianie stanu, wywoływana po zdarzenia. Przykładem zdarzenia wstępnej może być `Form.Closing`, które jest wywoływane przed zamknięciem formularza. Przykładem zdarzenia po może być `Form.Closed`, które jest wywoływane po zamknięciu formularza.  
  
 **CZY ✓** używany jest termin "raise" dla zdarzenia, a nie "fire" lub "wyzwolenia".  
  
 **CZY ✓** użyj <xref:System.EventHandler%601?displayProperty=nameWithType> zamiast ręcznego tworzenia nowych delegatów, które mają być używane jako procedury obsługi zdarzeń.  
  
 **ROZWAŻ ✓** przy użyciu podklasą <xref:System.EventArgs> jako argument zdarzenia, jeśli nie masz pewności absolutnie zdarzenie nie będzie trzeba do przenoszenia danych do obsługi metody zdarzeń w takim przypadku można zastosować `EventArgs` wpisać bezpośrednio.  
  
 Jeśli dostarczany za pomocą interfejsu API `EventArgs` bezpośrednio, nigdy nie będą mogli dodawać żadnych danych do ze zdarzeniem bez przerywania zgodności. Jeśli używasz podklasy, nawet jeśli pierwotnie pusty, można dodać właściwości do podklasy w razie potrzeby.  
  
 **CZY ✓** Użyj chronione metody wirtualnej, aby wywołać każdego zdarzenia. To ma zastosowanie tylko do niestatycznego zdarzeń w klasach niezapieczętowany, aby nie struktury, zapieczętowane klasy lub zdarzenia statyczne.  
  
 Celem metody jest sposób dla klasy pochodnej w celu obsługi zdarzeń za pomocą zastąpienia. Zastępowanie jest bardziej elastyczne, szybszy i bardziej naturalny sposób obsługi zdarzeń klasy podstawowej w klasach pochodnych. Konwencja Nazwa metody powinna zaczynać się znakiem "On" i występować o nazwie zdarzenia.  
  
 Klasa pochodna można zrezygnować z wywoływać implementację podstawową metody w jego zastąpienie. Należy przygotować to w tym wszystkie metody, która jest wymagana dla klasy podstawowej działać poprawnie.  
  
 **CZY ✓** przyjmować jeden parametr do metody chronionych, która wywołuje zdarzenie.  
  
 Parametr powinno być nazwanym `e` , należy wpisać jako klasa argumentów zdarzenia.  
  
 **X nie** należy przekazać wartość null jako nadawcę podczas wywołaniem Niestatyczne zdarzenia.  
  
 **CZY ✓** przekazać wartości null jako nadawcę, gdy wywołaniem zdarzenia statyczne.  
  
 **X nie** przekazać wartości null jako parametr danych zdarzenia, gdy wywołanie zdarzenia.  
  
 Należy przekazać `EventArgs.Empty` Jeśli nie chcesz przekazać żadnych danych do obsługi metody zdarzeń. Deweloperzy oczekiwać, że ten parametr nie powinien być pusty.  
  
 **ROZWAŻ ✓** wywoływanie zdarzeń, które użytkownik końcowy może anulować. Dotyczy to tylko zdarzeń poprzedzających.  
  
 Użyj <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> ani jej podklasy jako argument zdarzenia, aby umożliwić użytkownikom końcowym Anulowanie zdarzenia.  
  
### <a name="custom-event-handler-design"></a>Projekt programu obsługi zdarzeń niestandardowych  
 Istnieją przypadki, w którym `EventHandler<T>` nie można użyć, np. gdy platformę potrzebuje do pracy z wcześniejszych wersji środowiska CLR, która nie obsługuje typów ogólnych. W takich przypadkach może być konieczne do projektowania i opracowywania delegata obsługi zdarzeń niestandardowych.  
  
 **CZY ✓** zwracany typ void na użytek obsługi zdarzeń.  
  
 Program obsługi zdarzeń może wywołać obsługi metod, prawdopodobnie na wiele obiektów wiele zdarzeń. Jeśli metody obsługi zdarzeń zostały może zwracać wartości, może to być wiele wartości zwrotnych dla każdego wywołania zdarzenia.  
  
 **CZY ✓** użyj `object` jako typ pierwszego parametru metody obsługi zdarzeń i nadaj mu `sender`.  
  
 **CZY ✓** użyj <xref:System.EventArgs?displayProperty=nameWithType> ani jej podklasy jako typ drugiego parametru obsługi zdarzeń i nadaj mu `e`.  
  
 **X nie** ma więcej niż dwa parametry dotyczące programu obsługi zdarzeń.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 [Element członkowski — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/member.md)  
 [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
