---
title: Działanie
ms.date: 03/30/2017
ms.assetid: 70471705-f55f-4da1-919f-4b580f172665
ms.openlocfilehash: 3100d5bb60dc1b11d23b0705f4d6f23a3675ac51
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806835"
---
# <a name="activity"></a>Działanie
W tym temacie opisano działania śledzenia w modelu śledzenia usług Windows Communication Foundation (WCF). Działania są przetwarzania jednostki, które pomagają użytkownikowi zawęzić zakres awarii. Błędy występujące w tej samej działania są bezpośrednio powiązane. Na przykład kończy się niepowodzeniem, ponieważ odszyfrowywania wiadomości nie powiodło się. Ślady za działanie i błąd odszyfrowywania wiadomości są wyświetlane w to samo działanie przedstawiający bezpośredniego korelacja błędu odszyfrowywania Błąd żądania.  
  
## <a name="configuring-activity-tracing"></a>Konfigurowanie śledzenia działania  
 Usługi WCF udostępnia wstępnie zdefiniowane działań do przetwarzania aplikacji (zobacz [lista działania](../../../../../docs/framework/wcf/diagnostics/tracing/activity-list.md)). Działania można również definiować programowo do grupy użytkowników śladów. Aby uzyskać więcej informacji, zobacz [emitowanie danych śledzenia User-Code](../../../../../docs/framework/wcf/diagnostics/tracing/emitting-user-code-traces.md).  
  
 Aby wysyłać ślady działania w czasie wykonywania, należy użyć `ActivityTracing` ustawienie `System.ServiceModel` śledzenia źródła, lub inne WCF lub źródła śledzenia niestandardowych, jak pokazano w następującym kodem konfiguracji.  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
 Aby dowiedzieć się więcej o elementem konfiguracji i atrybuty używany, zobacz [Konfigurowanie śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) tematu.  
  
## <a name="viewing-activities"></a>Wyświetlanie działań  
 Można wyświetlić działań i ich narzędzie w [narzędzia podglądu śledzenia usług (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Po włączeniu ActivityTracing to narzędzie ma dane śledzenia i sortuje zależnie od aktywności. Można również sprawdzić transferów śledzenia. Wskazuje, jak różnych działań transferu śledzenia są ze sobą powiązane. Widać określone działanie spowodowało innego można uruchomić. Na przykład żądanie komunikatu uruchomiona uzgadniania zabezpieczeń, aby uzyskać bezpieczny konwersacji tokenu.  
  
### <a name="correlating-activities-in-service-trace-viewer"></a>Korelowanie działań w podglądzie śledzenia usługi  
 To narzędzie przeglądarki danych śledzenia usługi zawiera dwa widoki działań:  
  
-   **Lista** widok, w którym identyfikator działania jest używany do bezpośrednio korelowanie śladów między procesami. Ślady z różnych procesów, na przykład klienta i usługi, ale o tym samym identyfikatorze działania są grupowane w tym samym działaniu. W związku z tym błędów występujących na usługę, która następnie powoduje błąd na komputerze klienckim zarówno pojawi się w jednym widoku działania w narzędziu.  
  
-   **Wykres** widok, w których działania są pogrupowane według procesów. W tym widoku klienta i usługę mających taki sam identyfikator działania ma swoje dane śledzenia w różnych działań. Służące do skorelowania działań mających taki sam identyfikator działania w różnych procesów, narzędzie zawiera przepływów wiadomości między powiązanych działań.  
  
 Aby uzyskać więcej informacji i aby zobaczyć widoku graficznego narzędzia podglądu śledzenia usługi, zobacz [narzędzia podglądu śledzenia usług (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) i [przy użyciu przeglądarki śledzenia usługi do wyświetlania skorelowanych danych śledzenia i Rozwiązywanie problemów z](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
## <a name="defining-the-scope-of-an-activity"></a>Definiowanie zakresu działania  
 Działanie jest definiowany w czasie projektowania i oznacza jednostkę logiczną pracy. Ślady emitowany z tego samego identyfikatora działania są bezpośrednio powiązane, są częścią tego samego działania. Ponieważ działania mogą przechodzić przez granice punktu końcowego (żądanie), są zdefiniowane dwa zakresy dla działania.  
  
-   `Global` zakres na aplikację. W tym zakresie działanie jest identyfikowane przez jego działania globalnie unikatowy identyfikator 128-bitowego gAId. GAid to, co to są propagowane w obrębie punktów końcowych.  
  
-   `Local` zakres na punkt końcowy. W tym zakresie działanie jest identyfikowane przez jego gAId, oraz nazwę źródła śledzenia śledzenia działań i identyfikator procesu. Ta Trzykolumnowa stanowi identyfikator działania lokalnych, którego układ określa. Ustalonymi służy do definiowania (local) granice działania.  
  
## <a name="trace-schema"></a>Schemat śledzenia  
 Dane śledzenia może być wysyłany przy użyciu dowolnego schematu i na platformach firmy Microsoft. "e2e" (dla "pełny") jest często używane schematu. Ten schemat zawiera identyfikator 128-bitowego (gAId), nazwa źródła śledzenia i identyfikatora procesu. W kodzie zarządzanym <xref:System.Diagnostics.XmlWriterTraceListener> emituje dane śledzenia w schemacie E2E.  
  
 Deweloperzy mogą ustawić pomocy emitowanego śledzenia przez ustawienie <xref:System.Diagnostics.CorrelationManager.ActivityId%2A> właściwości za pomocą identyfikatora Guid w wątku lokalnego magazynu (TLS). W poniższym przykładzie pokazano to.  
  
```  
// set the current Activity ID to a new GUID.  
CorrelationManager.ActivityId = Guid.NewGuid();  
```  
  
 Ustawienie gAId w protokole TLS będą widoczne podczas śledzenia są emitowane przy użyciu źródła śledzenia, jak pokazano na poniższym przykładzie.  
  
```  
TraceSource traceSource = new TraceSource("myTraceSource");  
traceSource.TraceEvent(TraceEventType.Warning, eventId, "Information");  
```  
  
 Śledzenie wysyłanego będzie zawierać gAId obecnie w protokół TLS, nazwę źródła śledzenia przekazany jako parametr do konstruktora źródła śledzenia i identyfikator bieżącego procesu.  
  
## <a name="activity-lifetime"></a>Okres istnienia działania  
 W najbardziej rygorystyczne warunki dowód działanie uruchamia się po raz pierwszy identyfikator działania jest używana w emitowanym śledzenia i kończy się czasu, gdy jest on używany w emitowanym śledzenia. Zestaw wstępnie zdefiniowanych typów śledzenia są dostarczane przez <xref:System.Diagnostics>, w tym uruchamianie i zatrzymywanie, aby jawnie oznaczyć granice okres istnienia działania.  
  
-   Start: Wskazuje początek działania. Śledzenia "Start" zawiera rekord początkowego nowego punktu kontrolnego przetwarzania. Zawiera nowy identyfikator działania dla danego źródła w ramach danego procesu, z wyjątkiem przypadków, gdy identyfikator działania są propagowane w obrębie punktów końcowych, w tym przypadku widzimy na punkt końcowy jeden "Start". Uruchamianie nowego działania przykładem tworzenia nowego wątku przetwarzania lub wprowadzenie nowych publiczną metodę.  
  
-   Zatrzymaj: Wskazuje koniec działania. Śledzenia "Stop" zawiera rekord końcowy istniejący punkt kontrolny przetwarzania. Zawiera istniejącego Identyfikatora aktywności dla danego źródła w ramach danego procesu, z wyjątkiem przypadków, gdy identyfikator działania są propagowane w obrębie punktów końcowych, w tym przypadku widzimy jeden "Stop" na punkt końcowy.  Zatrzymywanie działania przykładami przerywanie wątku przetwarzania lub zamykanie metody, której początek zostało oznaczone symbolem śledzenia "Start".  
  
-   Wstrzymanie: Wskazuje zawieszenie przetwarzania działania. Śledzenia "Wstrzymaj" zawiera oczekuje się wznowić w późniejszym czasie, których przetwarzanie istniejący identyfikator działania. Ślady są emitowane o tym identyfikatorze między zdarzeniami wstrzymywanie i wznawianie z bieżącego źródła śledzenia. Przykładami wstrzymanie działania podczas wywoływania metody do funkcji zewnętrznej biblioteki lub podczas oczekiwania na zasobów, takich jak portu zakończenia We/Wy.  
  
-   Wznów: Wskazuje na wznowienie przetwarzania działania. Śledzenie "Resume" zawiera istniejący identyfikator działania którego ostatniego śledzenia wyemitowanego z bieżącego źródła śledzenia został śledzenia "Wstrzymaj". Przykładami powrotem z wywołania funkcji zewnętrznej biblioteki lub gdy sygnalizowane wznowienia przetwarzania przez zasób, takich jak portu zakończenia We/Wy.  
  
-   Transfer: Ponieważ niektóre działania są powodowane przez innych użytkowników lub odnoszą się do innych użytkowników, działania mogą związane z innych działań za pośrednictwem "Transfer" śladów. Przeniesienie rejestruje ukierunkowanej relacji z jednego działania do drugiego  
  
 Uruchomienia i zatrzymania śledzenia nie są krytyczne dla korelacji. Jednak może pomóc w zwiększenie wydajności, profilowania i weryfikacji zakresu działania.  
  
 Używanie tych typów, narzędzi można zoptymalizować Nawigacja dzienniki śledzenia do znalezienia natychmiast powiązanych zdarzeń tego samego działania, lub zdarzenia w działań związanych z Jeśli narzędzie transferu danych śledzenia. Na przykład narzędzi spowoduje zatrzymanie analizy dzienników dla danego działania, po zgłoszeniu śledzenia uruchamiania i zatrzymywania.  
  
 Te typy śledzenia mogą służyć do profilowania. Zasoby używane między znacznikami rozpoczęcie i zakończenie reprezentują całkowity czas działania tym zawarte działania logiczne. Odejmowanie interwałów czasu między śladów wstrzymywanie i wznawianie zapewnia czasu rzeczywistego działania.  
  
 Zatrzymaj śledzenie też jest szczególnie przydatne podczas sprawdzania poprawności zakres zaimplementowanym czynności. Jeśli niektóre przetwarzania śladów pojawią się po Zatrzymaj śledzenie zamiast w obrębie danego działania, może to sugeruje wad kodu.  
  
## <a name="guidelines-for-using-activity-tracing"></a>Wskazówki dotyczące używania działania śledzenia  
 Poniżej znajduje się wskazówek dotyczących używania śladów ActivityTracing (Start, Stop, wstrzymania, wznowienia i Transfer).  
  
-   Śledzenie jest ukierunkowanego wykresu cykliczne nie drzewa. Kontrolki można wrócić do działania, która zduplikowany działania.  
  
-   Działanie oznacza granic przetwarzania, który może być istotnych dla administratora systemu lub obsługi.  
  
-   Każda metoda WCF, zarówno na kliencie i serwerze, jest ograniczona przez od nowego działania, a następnie (po zakończeniu pracy) kończy nowe działanie i powrót do działania otoczenia.  
  
-   Czas uruchamiania (ciągłe) działania, takie jak nasłuchiwania dla połączeń lub Oczekiwanie na komunikaty są reprezentowane przez odpowiednie znaczniki uruchamiania i zatrzymywania.  
  
-   Działania wyzwalane przez przyjęcie lub przetwarzania komunikatów są reprezentowane przez granice śledzenia.  
  
-   Działania reprezentują działania, niekoniecznie obiektów. Działanie powinny być rozumiane jako "ten został występować po. . . (emisji znaczący śledzenia wystąpił)."  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [Używanie przeglądarki danych śledzenia usługi do wyświetlania skorelowanych danych śledzenia i rozwiązywania problemów](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [Scenariusze kompleksowego śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)  
 [Narzędzie do przeglądania danych śledzenia usług (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)  
 [Emitowanie danych śledzenia elementu User-Code](../../../../../docs/framework/wcf/diagnostics/tracing/emitting-user-code-traces.md)
