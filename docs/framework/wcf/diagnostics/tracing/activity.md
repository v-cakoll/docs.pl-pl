---
title: Działanie
ms.date: 03/30/2017
ms.assetid: 70471705-f55f-4da1-919f-4b580f172665
ms.openlocfilehash: 41de6b9458feb4e1898eeac6635b74c4617885d6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602144"
---
# <a name="activity"></a>Działanie
W tym temacie opisano ślady działania w modelu śledzenia Windows Communication Foundation (WCF). Działania to jednostki przetwarzania, które pomagają użytkownikowi zawęzić zakres błędu. Błędy występujące w tym samym działaniu są bezpośrednio powiązane. Na przykład operacja nie powiedzie się, ponieważ odszyfrowywanie komunikatu nie powiodło się. Ślady w przypadku niepowodzenia odszyfrowywania operacji i komunikatów są wyświetlane w tym samym działaniu, pokazując bezpośrednia korelacja między błędem odszyfrowywania i błędem żądania.  
  
## <a name="configuring-activity-tracing"></a>Konfigurowanie śledzenia działań  
 Funkcja WCF udostępnia wstępnie zdefiniowane działania dotyczące przetwarzania aplikacji (zobacz [listę działań](activity-list.md)). Możesz również programowo definiować działania, aby grupować ślady użytkowników. Aby uzyskać więcej informacji, zobacz [emitowanie śladów kodu użytkownika](emitting-user-code-traces.md).  
  
 Aby emitować ślady aktywności w czasie wykonywania, użyj `ActivityTracing` Ustawienia dla `System.ServiceModel` źródła śledzenia lub innych źródeł programu WCF lub niestandardowych śledzenia, jak pokazano w poniższym kodzie konfiguracyjnym.  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
 Aby dowiedzieć się więcej na temat elementu konfiguracji i używanych atrybutów, zobacz temat [Konfigurowanie śledzenia](configuring-tracing.md) .  
  
## <a name="viewing-activities"></a>Wyświetlanie działań  
 Możesz wyświetlić działania i ich narzędzia w [narzędziu Podgląd śledzenia usług (SvcTraceViewer. exe)](../../service-trace-viewer-tool-svctraceviewer-exe.md). Gdy ActivityTracing jest włączona, to narzędzie pobiera ślady i sortuje je na podstawie działania. Możesz również zobaczyć transfery śledzenia. Transfer śledzenia wskazuje, w jaki sposób różne działania są ze sobą powiązane. Można zobaczyć, że określone działanie jest inne do uruchomienia. Na przykład żądanie komunikatu rozpoczęło uzgadnianie zabezpieczeń w celu uzyskania tokenu bezpiecznej konwersacji.  
  
### <a name="correlating-activities-in-service-trace-viewer"></a>Korelacja działań w przeglądarce śledzenia usługi  
 Narzędzie Podgląd śledzenia usług zawiera dwa widoki działań:  
  
- Widok **listy** , w którym identyfikator działania jest używany do bezpośredniego skorelowania śladów między procesami. Ślady z różnych procesów, na przykład klient i usługa, ale z tym samym IDENTYFIKATORem działania są pogrupowane w tym samym działaniu. W związku z tym wystąpił błąd w usłudze, która powoduje, że błąd na kliencie zostanie wyświetlony w tym samym widoku działania w narzędziu.  
  
- Widok **wykresu** , w którym działania są pogrupowane według procesów. W tym widoku klient i usługa o tym samym IDENTYFIKATORze działania mają swoje ślady w różnych działaniach. Aby skorelować działania z tym samym IDENTYFIKATORem działania w różnych procesach, narzędzie wyświetla przepływy komunikatów między powiązanymi działaniami.  
  
 Aby uzyskać więcej informacji i wyświetlić widok graficzny narzędzia Podgląd śledzenia usług, zobacz [narzędzie Podgląd śledzenia usług (SvcTraceViewer. exe)](../../service-trace-viewer-tool-svctraceviewer-exe.md) i [Używanie przeglądarki śledzenia usługi do wyświetlania skorelowanych śladów i rozwiązywania problemów](using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
## <a name="defining-the-scope-of-an-activity"></a>Definiowanie zakresu działania  
 Działanie jest definiowane w czasie projektowania i oznacza jednostkę logiczną pracy. Emitowane ślady z tym samym identyfikatorem działania są bezpośrednio powiązane, są częścią tego samego działania. Ponieważ działanie może przekroczyć granice punktu końcowego (żądanie), definiowane są dwa zakresy dla działania.  
  
- `Global`zakres, na aplikację. W tym zakresie działanie jest identyfikowane przez 128-bitowy globalnie unikatowy identyfikator działania, gAId. GAid jest rozmnożony przez punkty końcowe.  
  
- `Local`zakres, na punkt końcowy. W tym zakresie działanie jest identyfikowane przez gAId wraz z nazwą źródła śledzenia emitującą ślady aktywności i identyfikator procesu. Ten tryplet stanowi identyfikator działania lokalnego. Ta wartość jest używana do definiowania granic (lokalnych) działania.  
  
## <a name="trace-schema"></a>Schemat śledzenia  
 Ślady mogą być emitowane przy użyciu dowolnego schematu i między platformami firmy Microsoft. "E2E" (dla "end to end") jest często używanym schematem. Ten schemat zawiera identyfikator 128 bitowy (gAId), nazwę źródła śledzenia i identyfikator procesu. W kodzie zarządzanym program <xref:System.Diagnostics.XmlWriterTraceListener> emituje ślady w schemacie E2E.  
  
 Deweloperzy mogą ustawić pomoc, która jest emitowana przy użyciu śledzenia przez ustawienie <xref:System.Diagnostics.CorrelationManager.ActivityId%2A> właściwości z identyfikatorem GUID w lokalnym magazynie wątków (TLS). Poniższy przykład ilustruje to.  
  
```csharp
// set the current Activity ID to a new GUID.  
CorrelationManager.ActivityId = Guid.NewGuid();  
```
  
 Ustawienie gAId w protokole TLS będzie oczywiste, gdy ślady są emitowane przy użyciu źródła śledzenia, jak pokazano w poniższym przykładzie.  
  
```csharp
TraceSource traceSource = new TraceSource("myTraceSource");  
traceSource.TraceEvent(TraceEventType.Warning, eventId, "Information");  
```  
  
 Wyemitowane ślady będą zawierać gAId aktualnie w protokole TLS, nazwę źródła śledzenia przekazaną jako parametr do konstruktora źródła śledzenia i identyfikator bieżącego procesu.  
  
## <a name="activity-lifetime"></a>Okres istnienia działania  
 W najrygorystycznych warunkach dowody działania są uruchamiane przy pierwszym użyciu identyfikatora działania w wyemitowanym śledzeniu i kończą się ostatnim razem, gdy jest on używany w wyemitowanym śledzeniu. Wstępnie zdefiniowany zestaw typów śledzenia jest dostarczany przez <xref:System.Diagnostics> , włącznie z rozpoczęciem i zatrzymywaniem, aby jawnie oznaczyć granice okresu istnienia działania.  
  
- Początek: wskazuje początek działania. Ślad "Start" zawiera rekord rozpoczynający się od nowego punktu kontrolnego przetwarzania. Zawiera nowy identyfikator działania dla danego źródła śledzenia w danym procesie, z wyjątkiem sytuacji, gdy identyfikator działania jest propagowany między punktami końcowymi, w tym przypadku zobaczysz jeden "Początek" na punkt końcowy. Przykłady uruchamiania nowego działania obejmują tworzenie nowego wątku do przetwarzania lub wprowadzanie nowej metody publicznej.  
  
- Zatrzymaj: wskazuje koniec działania. Ślad "Stop" zawiera rekord kończący istniejący punkt kontrolny przetwarzania. Zawiera istniejący identyfikator działania dla danego źródła śledzenia w danym procesie, z wyjątkiem sytuacji, gdy identyfikator działania jest propagowany między punktami końcowymi, w tym przypadku zobaczysz jeden "Stop" na punkt końcowy.  Przykłady zatrzymywania działania obejmują zakończenie wątku przetwarzania lub wyjście z metody, której początkowa została oznaczona jako "Start".  
  
- Wstrzymaj: wskazuje zawieszenie przetwarzania działania. Ślad "Suspend" zawiera istniejący identyfikator działania, którego przetwarzanie powinno zostać wznowione w późniejszym czasie. Nie są emitowane żadne ślady z tym IDENTYFIKATORem między zdarzeniami wstrzymywania i wznawiania z bieżącego źródła śledzenia. Przykłady obejmują wstrzymywanie działania podczas wywoływania funkcji zewnętrznej biblioteki lub podczas oczekiwania na zasób, taki jak Port zakończenia we/wy.  
  
- Wznów: wskazuje wznowienie przetwarzania działania. Ślad "Wznów" zawiera istniejący identyfikator działania, którego ostatni wygenerowany ślad z bieżącego źródła śledzenia to ślad "Suspend". Przykłady obejmują zwracanie z wywołania do zewnętrznej funkcji biblioteki lub po zasygnalizowaniu wznowienia przetwarzania przez zasób, taki jak Port zakończenia we/wy.  
  
- Transfer: ponieważ niektóre działania są spowodowane przez inne osoby lub odnoszą się do innych, działania mogą być powiązane z innymi działaniami za pomocą śladów "Transfer". Transfer rejestruje bezpośrednią relację jednego działania z inną  
  
 Śledzenie uruchamiania i zatrzymywania nie ma znaczenia dla korelacji. Mogą jednak pomóc zwiększyć wydajność, profilowanie i weryfikację zakresu działania.  
  
 Korzystając z tych typów, narzędzia mogą zoptymalizować przechodzenie do dzienników śledzenia w celu znalezienia bezpośrednio powiązanych zdarzeń tego samego działania lub zdarzeń w powiązanych działaniach, jeśli narzędzie postępuje zgodnie z transferem danych śledzenia. Na przykład narzędzia przestają przeanalizować dzienniki dla danego działania, gdy zobaczy wynik śledzenia uruchamiania/zatrzymywania.  
  
 Te typy śledzenia mogą być również używane do profilowania. Zasoby używane między znacznikami początkowymi i końcowymi reprezentują łączny czas działania, w tym zawarte działania logiczne. Odjęcie przedziałów czasu między śladami wstrzymania i wznowienia zapewnia rzeczywisty czas działania.  
  
 Śledzenie zatrzymania jest również szczególnie przydatne do walidacji zakresu implementowanych działań. Jeśli niektóre ślady przetwarzania są wyświetlane po zatrzymaniu śledzenia zamiast wewnątrz danego działania, może to zasugerować wady kodu.  
  
## <a name="guidelines-for-using-activity-tracing"></a>Wskazówki dotyczące korzystania ze śledzenia działań  
 Poniżej przedstawiono wskazówki dotyczące używania ActivityTracing śledzenia (uruchamianie, zatrzymywanie, wstrzymywanie, wznawianie i transfer).  
  
- Śledzenie jest bezpośrednim wykresem cyklicznym, a nie drzewem. Można zwrócić kontrolę do działania, które duplikuje działanie.  
  
- Działanie oznacza granicę przetwarzania, która może być zrozumiała dla administratora systemu lub do zapewnienia obsługi.  
  
- Każda metoda WCF, zarówno na kliencie, jak i serwerze, jest ograniczona przez rozpoczęcie nowego działania, a następnie (po zakończeniu pracy) kończące nowe działanie i zwracając do działania otoczenia.  
  
- Długotrwałe działania (na bieżąco), takie jak nasłuchiwanie połączeń lub oczekiwanie na komunikaty, są reprezentowane przez odpowiadające im znaczniki uruchamiania/zatrzymywania.  
  
- Działania wyzwalane przez potwierdzenie lub przetworzenie komunikatu są reprezentowane przez granice śledzenia.  
  
- Działania reprezentują działania, niekoniecznie obiekty. Działanie powinno być interpretowane jako "dzieje się tak. . . (wystąpił znacząca emisja śledzenia). "  
  
## <a name="see-also"></a>Zobacz też

- [Konfigurowanie śledzenia](configuring-tracing.md)
- [Używanie przeglądarki danych śledzenia usługi do wyświetlania skorelowanych danych śledzenia i rozwiązywania problemów](using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [Scenariusze kompleksowego śledzenia](end-to-end-tracing-scenarios.md)
- [Narzędzie do przeglądania danych śledzenia usług (SvcTraceViewer.exe)](../../service-trace-viewer-tool-svctraceviewer-exe.md)
- [Emitowanie danych śledzenia elementu User-Code](emitting-user-code-traces.md)
