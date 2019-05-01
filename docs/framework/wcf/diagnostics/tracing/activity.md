---
title: Działanie
ms.date: 03/30/2017
ms.assetid: 70471705-f55f-4da1-919f-4b580f172665
ms.openlocfilehash: b93960d4006499c935c27ee18e066d091632d3d9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61998026"
---
# <a name="activity"></a>Działanie
W tym temacie opisano ślady działania w modelu śledzenia usług Windows Communication Foundation (WCF). Działania to przetwarzania jednostek, które pomagają użytkownikowi zawęzić zakres awarii. Błędy w ramach tego samego działania są bezpośrednio powiązane. Na przykład kończy się niepowodzeniem, ponieważ odszyfrowywania wiadomości nie powiodło się. Śledzenie operacji i błędu odszyfrowywania wiadomości pojawiają się w tym samym działaniu, przedstawiający bezpośrednia korelacja między błąd odszyfrowywania i Błąd żądania.  
  
## <a name="configuring-activity-tracing"></a>Konfigurowanie śledzenia działań  
 Usługi WCF zapewnia wstępnie zdefiniowane działania związane z przetwarzaniem (zobacz [lista działań](../../../../../docs/framework/wcf/diagnostics/tracing/activity-list.md)). Działania można również zdefiniować programowo, aby śledzenie użytkowników grupy. Aby uzyskać więcej informacji, zobacz [emitowanie danych śledzenia User-Code](../../../../../docs/framework/wcf/diagnostics/tracing/emitting-user-code-traces.md).  
  
 Emitowanie danych śledzenia działań w czasie wykonywania, użyj `ActivityTracing` ustawienie `System.ServiceModel` śledzenia, lub inne usługi WCF lub niestandardowe śledzenia źródeł, jak pokazano w następującym kodem konfiguracji.  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
 Aby dowiedzieć się więcej na temat elementu konfiguracji i atrybuty są używane, zobacz [Konfigurowanie śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) tematu.  
  
## <a name="viewing-activities"></a>Wyświetlanie działań  
 Można przeglądać działania i ich użyteczność w [narzędzie śledzenia usług (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Po włączeniu ActivityTracing to narzędzie pobiera ślady i sortuje je na podstawie aktywności. Widać również transfery śledzenia. Transfer śledzenia wskazuje, jak różne działania są powiązane ze sobą. Możesz zobaczyć danego działania spowodowane innej, aby rozpocząć. Na przykład żądanie komunikatu uruchomione uzgadnianie zabezpieczeń w celu uzyskania bezpiecznego konwersacji tokenu.  
  
### <a name="correlating-activities-in-service-trace-viewer"></a>Korelowanie działań w przeglądarki danych śledzenia usługi  
 To narzędzie przeglądarki danych śledzenia usługi zawiera dwa widoki działania:  
  
- **Lista** widoku, gdy identyfikator działania jest używana w celu bezpośrednio korelowanie śladów procesów. Ślady z różnych procesów, na przykład, klienta i usługi, ale ten sam identyfikator działania są grupowane w ramach tego samego działania. W związku z tym błąd występujących na usługi, która powoduje błąd, na komputerze klienckim oba pojawią się w jednym widoku działań w narzędziu.  
  
- **Wykres** widok, w których działania są pogrupowane według procesów. W tym widoku klienta i usługi o tym samym identyfikatorze działanie ma ich ślady w różnych działaniach. Aby skorelować działań mających taki sam identyfikator działania w różnych procesach, w narzędziu jest wyświetlany komunikat przepływów różnych działań powiązanych z.  
  
 Aby uzyskać więcej informacji i wyświetlić graficznego narzędzia przeglądarki danych śledzenia usługi, zobacz [narzędzie śledzenia usług (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) i [za pomocą przeglądarki danych śledzenia usługi do wyświetlania skorelowanych danych śledzenia i Rozwiązywanie problemów z](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
## <a name="defining-the-scope-of-an-activity"></a>Definiowanie zakresu działania  
 Działanie jest zdefiniowana w czasie projektowania i oznacza jednostkę logiczną w pracy. Emitowany ślady za pomocą tego samego identyfikatora działania są bezpośrednio powiązane, są one częścią tego samego działania. Ponieważ działania mogą przechodzić granic punktu końcowego (żądanie), są zdefiniowane dwa zakresy dla działania.  
  
- `Global` zakres każdej aplikacji. W tym zakresie działanie jest identyfikowane przez jego działania globalnie unikatowy identyfikator 128-bitowego gAId. GAid to, co to są propagowane w obrębie punktów końcowych.  
  
- `Local` zakres za punkt końcowy. W tym zakresie działanie jest identyfikowane przez jego gAId wraz z nazwą źródła śledzenia emitowanie danych śledzenia działań i identyfikator procesu. Ta trójkę stanowi identyfikator działań lokalnych ustanowione. Ustalonymi służy do definiowania (local) granice tego działania.  
  
## <a name="trace-schema"></a>Schemat śledzenia  
 Może być emitowana danych śledzenia przy użyciu dowolnego schematu i na platformach firmy Microsoft. "e2e" (dla "End to End") to najczęściej używany schemat. Ten schemat obejmuje identyfikatorem 128-bitowego (gAId), nazwa źródła śledzenia i identyfikatora procesu. W kodzie zarządzanym <xref:System.Diagnostics.XmlWriterTraceListener> emituje ślady w schemacie E2E.  
  
 Deweloperzy mogą ustawić pomocy, który jest emitowane przy użyciu śledzenia, ustawiając <xref:System.Diagnostics.CorrelationManager.ActivityId%2A> właściwości przy użyciu identyfikatora Guid na wątku lokalnego magazynu (TLS). Poniższy przykład przedstawia to.  
  
```csharp
// set the current Activity ID to a new GUID.  
CorrelationManager.ActivityId = Guid.NewGuid();  
```
  
 Ustawienie gAId w protokole TLS będą widoczne podczas śledzenia są emitowane przy użyciu źródła śledzenia, jak pokazano na poniższym przykładzie.  
  
```csharp
TraceSource traceSource = new TraceSource("myTraceSource");  
traceSource.TraceEvent(TraceEventType.Warning, eventId, "Information");  
```  
  
 Informacje śledzenia emitowane będą zawierać gAId aktualnie w TLS, nazwa źródła śledzenia przekazany jako parametr do konstruktora źródła śledzenia i identyfikator bieżącego procesu.  
  
## <a name="activity-lifetime"></a>Okres istnienia działania  
 W sposób najbardziej rygorystyczne dowód działania uruchamiania po raz pierwszy identyfikator działania jest używana w emitowany śledzenia i kończy ostatniego, jest ono używane w emitowany śledzenia. Zestaw wstępnie zdefiniowanych typów śledzenia są dostarczane przez <xref:System.Diagnostics>, w tym uruchamianie i zatrzymywanie, aby wyraźnie oznaczyć granice okres istnienia działania.  
  
- Uruchamianie: Wskazuje początek działania. Śledzenie "Start" zawiera rejestr od nowego punktu kontrolnego przetwarzania. Zawiera nowy identyfikator działania śledzenia danego źródła danego procesu, z wyjątkiem sytuacji, gdy identyfikator działania są propagowane w obrębie punktów końcowych, w którym to przypadku widzimy za punkt końcowy jeden "Start". Uruchamianie nowego działania przykłady tworzenia nowego wątku przetwarzania lub wprowadzania nowej metody publiczne.  
  
- Zatrzymywanie: Oznacza koniec działania. Śledzenie "Zatrzymaj" zawiera rejestr zakończenia istniejący punkt kontrolny przetwarzania. Zawiera on istniejący identyfikator działania śledzenia danego źródła danego procesu, z wyjątkiem sytuacji, gdy identyfikator działania są propagowane w obrębie punktów końcowych, w którym to przypadku widzimy jeden "Stop" na punkt końcowy.  Zatrzymywanie działania przykładami zakończenie wątku przetwarzania lub Kończenie wykonywania metody, którego początek została oznaczona za pomocą śledzenia "Start".  
  
- Wstrzymywanie: Wskazuje zawieszenia przetwarzania działania. Śledzenie "Wstrzymaj" zawiera istniejący identyfikator działania przetwarzania, którego oczekuje się, aby wznowić w późniejszym czasie. Ślady są emitowane o tym identyfikatorze między zdarzeniami wstrzymywanie i wznawianie z bieżącego źródła śledzenia. Przykłady obejmują wstrzymywanie działania, gdy wywołanie do funkcji zewnętrznej biblioteki lub Oczekiwanie na zasób, taki jak port zakończenia operacji We/Wy.  
  
- Wznów: Wskazuje na wznowienie przetwarzania działania. Śledzenie "Resume" zawiera istniejący identyfikator działania, w których ostatni ślad emitowany z bieżącego źródła śledzenia został śledzenia "Wstrzymaj". Do przykładów należą, zwracając po wywołaniu do funkcji zewnętrznej biblioteki lub gdy sygnalizowane, aby wznowić przetwarzanie przez zasób, taki jak port zakończenia operacji We/Wy.  
  
- Transfer: Ponieważ niektóre działania są spowodowane przez inne osoby lub odnoszą się do innych osób, działania mogą dotyczyć innych działań za pośrednictwem "Przekazywać" ślady. Przeniesienie rejestruje kierowanych relacji jednego działania do innego  
  
 Uruchamiania i zatrzymania śledzenia nie są krytyczne dla korelacji. Jednak może pomóc w zwiększaniu wydajności, profilowanie i walidacji zakres działania.  
  
 Korzystając z tych typów, narzędzia można zoptymalizować przechodząc dzienniki śledzenia, aby znaleźć zdarzenia bezpośrednio powiązane z tego samego działania lub zdarzenia w działania powiązane z Jeśli narzędzie transferu danych śledzenia. Na przykład narzędzia zostanie zatrzymane, analizy dzienników dla danego działania, po zgłoszeniu śledzenia uruchomień/zatrzymań.  
  
 Te typy śledzenia może również używane na potrzeby profilowania. Zasoby używane między znacznikami uruchamianie i zatrzymywanie reprezentują całkowity czas działania, tym zawarte działania logiczne. Odejmowanie interwałami między ślady wstrzymywanie i wznawianie udostępnia w czasie działania rzeczywistych.  
  
 Zatrzymaj śledzenie również jest szczególnie przydatne w przypadku sprawdzania zakresu działalności zaimplementowane. Jeśli niektóre dane śledzenia przetwarzania pojawią się po Zatrzymaj śledzenie zamiast wewnątrz danego działania, może to sugeruje wady kodu.  
  
## <a name="guidelines-for-using-activity-tracing"></a>Wskazówki dotyczące używania śledzenie aktywności  
 Poniżej znajduje się wytyczne użycia ślady ActivityTracing (uruchamianie, Zatrzymaj, Wstrzymaj, Wznów i transferu).  
  
- Śledzenie jest directed graph cykliczne nie drzewa. Kontrolka możesz wrócić do działania, które zduplikowany działania.  
  
- Działanie oznacza granicy przetwarzania, który może być istotnych dla administratora systemu lub obsługi.  
  
- Każda metoda WCF, zarówno na kliencie i serwerze, jest ograniczony przez rozpoczęciem nowe działanie, a następnie (po zakończeniu pracy) Kończenie nowe działanie i powrocie do otoczenia działania.  
  
- Czas uruchamiania (ciągłe) działań, takich jak nasłuchiwać w poszukiwaniu połączeń lub Oczekiwanie na komunikaty są reprezentowane przez odpowiednie znaczników rozpoczęcia/zakończenia.  
  
- Działania wyzwolone przez przyjęcie lub przetwarzania komunikatów są reprezentowane przez granice śledzenia.  
  
- Działania reprezentują działań, niekoniecznie obiektów. Działanie powinno być interpretowane jako "to się dzieje po. . . (emisji śledzenia istotnych wystąpił)."  
  
## <a name="see-also"></a>Zobacz także

- [Konfigurowanie śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)
- [Używanie przeglądarki danych śledzenia usługi do wyświetlania skorelowanych danych śledzenia i rozwiązywania problemów](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [Scenariusze kompleksowego śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)
- [Narzędzie do przeglądania danych śledzenia usług (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
- [Emitowanie danych śledzenia elementu User-Code](../../../../../docs/framework/wcf/diagnostics/tracing/emitting-user-code-traces.md)
