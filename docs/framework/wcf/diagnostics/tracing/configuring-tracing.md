---
title: Konfigurowanie śledzenia
ms.date: 03/30/2017
helpviewer_keywords:
- tracing [WCF]
ms.assetid: 82922010-e8b3-40eb-98c4-10fc05c6d65d
ms.openlocfilehash: f80d89d66253df310395cdfa3139e8765da24edb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54584915"
---
# <a name="configuring-tracing"></a>Konfigurowanie śledzenia
W tym temacie opisano, jak możesz włączyć śledzenie, skonfigurować źródła śledzenia emitowanie danych śledzenia i zestaw poziomów śledzenia, śledzenie aktywności zestawu oraz propagacji do obsługi śledzenia end-to-end korelacji i ustawić detektorów śledzenia do dostępu do danych śledzenia.  
  
 Zalecenia ustawienia śledzenia w produkcji lub w środowisku debugowania, można znaleźć [zalecane ustawienia śledzenia i rejestrowania komunikatów](../../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md).  
  
> [!IMPORTANT]
>  W systemie Windows 8 należy uruchomić aplikację podniesionych uprawnień (Uruchom jako Administrator), w kolejności dla swojej aplikacji w celu generowania dzienników śledzenia.  
  
## <a name="enabling-tracing"></a>Włączenie debugowania  
 Windows Communication Foundation (WCF) wyświetla następujące dane śledzenia diagnostycznego:  
  
-   Śledzenie procesu punktów kontrolnych, dotyczące wszystkich składników aplikacji, takich jak wywołania operacji kodu, wyjątki, ostrzeżenia i inne zdarzenia przetwarzania.  
  
-   Zdarzenia błędu Windows działa funkcja śledzenia. Zobacz [rejestrowania zdarzeń](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md).  
  
 Śledzenie programu WCF jest wbudowana w górnej części <xref:System.Diagnostics>. Aby użyć śledzenia, należy zdefiniować źródła śledzenia w pliku konfiguracji lub w kodzie. Usługi WCF definiuje źródła śledzenia dla każdego zestawu WCF. `System.ServiceModel` Źródła śledzenia jest najbardziej ogólnym źródła śledzenia WCF i rejestruje przetwarzania punkty kontrolne w stos komunikacji WCF z wprowadzania opuszczania transportu do wprowadzania/wyłączanych kod użytkownika. `System.ServiceModel.MessageLogging` Źródła śledzenia rejestruje wszystkie komunikaty, które będą działać przez system.  
  
 Śledzenie nie jest włączone domyślnie. Aby uaktywnić śledzenie, musisz utworzyć odbiornik śledzenia i ustawić poziom śledzenia, innego niż "Off" dla źródła śledzenia wybranego w konfiguracji; w przeciwnym razie WCF nie generuje żadnych śladów. Jeśli odbiornik nie jest określona, śledzenie zostanie automatycznie usunięte. Jeśli odbiornik jest zdefiniowany, ale poziom nie zostanie określony, poziom ustawiono na "Wyłączone" Domyślnie, co oznacza, że bez śledzenia jest emitowane.  
  
 Jeśli używasz usługi WCF punkty rozszerzeń, takich jak invokers operacji niestandardowej, powinny wysyłać własne dane śledzenia. Jest to spowodowane w przypadku zaimplementowania punktu rozszerzalności usługi WCF nie jest już może emitować standardowa ślady w domyślnej ścieżce. Jeśli implementuje obsługę ręcznego śledzenia przez emitowanie danych śledzenia, może być niewidoczna ślady, których oczekujesz.  
  
 Można skonfigurować śledzenie, edytując plik konfiguracji aplikacji — albo plik Web.config dla aplikacji hostowanych w sieci Web lub Appname.exe.config samodzielnie hostowanej aplikacji. Oto przykład takiego edycji. Aby uzyskać więcej informacji na temat tych ustawień zobacz sekcję "Konfigurowanie śledzenia obiektów nasłuchujących na używanie Traces".  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <sources>  
            <source name="System.ServiceModel"   
                    switchValue="Information, ActivityTracing"  
                    propagateActivity="true">  
            <listeners>  
               <add name="traceListener"   
                   type="System.Diagnostics.XmlWriterTraceListener"   
                   initializeData= "c:\log\Traces.svclog" />  
            </listeners>  
         </source>  
      </sources>  
   </system.diagnostics>  
</configuration>  
```  
  
> [!NOTE]
>  Aby edytować plik konfiguracji projektu usługi WCF w programie Visual Studio, kliknij prawym przyciskiem myszy plik konfiguracji aplikacji — albo plik Web.config dla aplikacji hostowanych w sieci Web lub Appname.exe.config samodzielnie hostowanej aplikacji w **Eksploratora rozwiązań** . Następnie wybierz **Edycja konfiguracji usługi WCF** element menu kontekstowego. Spowoduje to uruchomienie [narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md), co umożliwia modyfikowanie ustawień konfiguracji dla usług WCF za pomocą graficznego interfejsu użytkownika.  
  
## <a name="configuring-trace-sources-to-emit-traces"></a>Konfigurowanie źródła śledzenia emitowanie danych śledzenia  
 Usługi WCF definiuje źródła śledzenia dla każdego zestawu. Dane śledzenia generowane w zestawie uzyskują odbiorników zdefiniowane dla tego źródła. Następujące źródła śledzenia są zdefiniowane:  
  
-   System.ServiceModel: Rejestruje wszystkie etapy przetwarzania WCF, zawsze, gdy odczyt konfiguracji, komunikat jest przetwarzany transportu, zabezpieczeń, przetwarzanie, komunikat jest wysyłany w kodzie użytkownika i tak dalej.  
  
-   System.ServiceModel.MessageLogging: Rejestruje wszystkie komunikaty, które będą działać przez system.  
  
-   System.IdentityModel.  
  
-   System.ServiceModel.Activation.  
  
-   System.IO.Log: Rejestrowanie interfejsu .NET Framework do wspólnego Log File System (CLFS).  
  
-   System.Runtime.Serialization: Dzienniki, gdy obiekty są odczytywane lub zapisywane.  
  
-   CardSpace.  
  
 Każde źródło śledzenia, aby użyć tego samego odbiornika (współużytkowane), można skonfigurować, jak wskazano w poniższym przykładzie konfiguracji.  
  
```xml  
<configuration>  
    <system.diagnostics>  
        <sources>  
            <source name="System.ServiceModel"   
                    switchValue="Information, ActivityTracing"  
                    propagateActivity="true">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="CardSpace">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="System.IO.Log">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="System.Runtime.Serialization">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="System.IdentityModel">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
        </sources>  
  
        <sharedListeners>  
            <add name="xml"  
                 type="System.Diagnostics.XmlWriterTraceListener"  
                 initializeData="c:\log\Traces.svclog" />  
        </sharedListeners>  
    </system.diagnostics>  
</configuration>  
```  
  
 Ponadto możesz dodać źródła śledzenia zdefiniowanych przez użytkownika, jak pokazano na poniższym przykładzie emitowanie danych śledzenia kodu użytkownika.  
  
```xml  
<system.diagnostics>  
   <sources>  
       <source name="UserTraceSource" switchValue="Warning, ActivityTracing" >  
          <listeners>  
              <add name="xml"  
                 type="System.Diagnostics.XmlWriterTraceListener"  
                 initializeData="C:\logs\UserTraces.svclog" />  
          </listeners>  
       </source>  
   </sources>  
   <trace autoflush="true" />   
</system.diagnostics>  
```  
  
 Aby uzyskać więcej informacji na temat tworzenia źródła śledzenia zdefiniowanych przez użytkownika, zobacz [rozszerzanie śledzenia](../../../../../docs/framework/wcf/samples/extending-tracing.md).  
  
## <a name="configuring-trace-listeners-to-consume-traces"></a>Konfigurowanie śledzenia słuchaczy korzystanie z danych śledzenia  
 W czasie wykonywania WCF źródeł danych śledzenia do odbiorników, które przetwarzają dane. Usługi WCF zawiera kilka wstępnie zdefiniowanych obiektów nasłuchujących dla <xref:System.Diagnostics>, które różnią się w formacie korzystają z danych wyjściowych. Można również dodać niestandardowe odbiornika typów.  
  
 Można użyć `add` określić nazwę i typ odbiornik śledzenia ma być używany. W naszym przykładzie konfiguracji nasze konto nazywa się odbiornik `traceListener` i dodać standardowy odbiornik śledzenia .NET Framework (`System.Diagnostics.XmlWriterTraceListener`) jako typ chcemy do użycia. Możesz dodać dowolną liczbę obiektów nasłuchujących śledzenia dla każdego źródła. Odbiornik śledzenia emituje śledzenia do pliku, w pliku konfiguracji należy określić lokalizację pliku danych wyjściowych i nazwę. Jest to realizowane przez ustawienie `initializeData` do nazwy pliku dla tego odbiornika. Jeśli nie określisz nazwy pliku, nazwę pliku losowe jest generowany na podstawie typu odbiornika używane. Jeśli <xref:System.Diagnostics.XmlWriterTraceListener> jest używany, nazwę pliku bez rozszerzenia jest generowany. W przypadku zastosowania niestandardowych odbiornik umożliwia także tego atrybutu na odbieranie danych inicjowania inne niż nazwa pliku. Na przykład można określić identyfikatora bazy danych dla tego atrybutu.  
  
 Można skonfigurować odbiornik śledzenia niestandardowych do wysyłania danych śledzenia w sieci, na przykład ze zdalną bazą danych. Jako narzędzia do wdrażania aplikacji powinien wymuszać kontrolę dostępu do dzienników śledzenia w komputerze zdalnym.  
  
 Odbiornik śledzenia można również skonfigurować programowo. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie i Inicjowanie obiektów nasłuchujących śledzenia](https://go.microsoft.com/fwlink/?LinkId=94648) i [tworzenia niestandardowych zdarzeń TraceListener](https://go.microsoft.com/fwlink/?LinkId=96239).  
  
> [!CAUTION]
>  Ponieważ `System.Diagnostics.XmlWriterTraceListener` jest nie metodą o bezpiecznych wątkach, źródła śledzenia może zablokować zasobów wyłącznie w przypadku, gdy dane są wyprowadzane ślady. Gdy wiele wątków, dane wyjściowe śledzenia do źródła śledzenia skonfigurowany do używania tego odbiornika, może wystąpić, rywalizacji o zasoby, które powoduje problem istotnie poprawiającą wydajność. Aby rozwiązać ten problem, należy zaimplementować niestandardowy odbiornik, który jest bezpieczna dla wątków.  
  
## <a name="trace-level"></a>Poziom śledzenia  
 Poziom śledzenia jest kontrolowane przez `switchValue` ustawienia źródła śledzenia. Poziomy śledzenia dostępne są opisane w poniższej tabeli.  
  
|Poziom śledzenia|Rodzaj rejestrowanych zdarzeń.|Zawartość rejestrowanych zdarzeń.|Śledzone zdarzenia|Użytkownik docelowy|  
|-----------------|----------------------------------|-----------------------------------|--------------------|-----------------|  
|Off|Brak|Brak|Ślady są emitowane.|Brak|  
|Krytyczny|"Ujemne" zdarzeń: zdarzenia, które wskazują przetwarzania lub warunek błędu.||Rejestrowane są nieobsługiwane wyjątki, takie jak następujące:<br /><br /> — OutOfMemoryException<br />-ThreadAbortException (Środowisko CLR wywołuje wszystkie ThreadAbortExceptionHandler)<br />-Stackoverflowexception — (nie można przechwycić)<br />— ConfigurationErrorsException<br />-Sehexception —<br />— Błędy uruchomienia aplikacji<br />-Failfast zdarzenia<br />-System zawiesza się<br />-Skażonymi komunikatami: komunikat śledzenia, które powodują awarię aplikacji.|Administratorzy<br /><br /> Deweloperzy aplikacji|  
|Błąd|"Ujemne" zdarzeń: zdarzenia, które wskazują przetwarzania lub warunek błędu.|Wykonano przetwarzania. Aplikacja nie był w stanie wykonać zadanie, zgodnie z oczekiwaniami. Jednak aplikacja jest nadal uruchomiona.|Wszystkie wyjątki są rejestrowane.|Administratorzy<br /><br /> Deweloperzy aplikacji|  
|Ostrzeżenie|"Ujemne" zdarzeń: zdarzenia, które wskazują przetwarzania lub warunek błędu.|Możliwy problem wystąpił lub może wystąpić, ale nadal funkcje aplikacji poprawnie. Jednak może nie nadal działała poprawnie.|— Aplikacja odbiera więcej żądań, niż jest dozwolone w ustawieniach ograniczania przepustowości.<br />-Odbieranie kolejki zbliża się skonfigurowanego pojemności maksymalnej.<br />— Przekroczony został limit czasu.<br />-Poświadczenia są odrzucane.|Administratorzy<br /><br /> Deweloperzy aplikacji|  
|Informacje|"Dodatnią" zdarzeń: zdarzenia, oznaczające pomyślne punkty kontrolne|Ważne, jak i pomyślnie punktów kontrolnych wykonywania aplikacji, niezależnie od tego, czy aplikacja działa poprawnie.|Ogólnie rzecz biorąc komunikaty przydatne do monitorowania i diagnozowania stanu systemu, pomiaru wydajności lub profilowania są generowane. Można użyć takich informacji do pojemności planowanie i zarządzanie wydajnością:<br /><br /> -Kanały są tworzone.<br />-Odbiorniki endpoint są tworzone.<br />-Komunikat przechodzi/pozostawia transportu.<br />— Token zabezpieczający są pobierane.<br />— Ustawienie konfiguracji jest do odczytu.|Administratorzy<br /><br /> Deweloperzy aplikacji<br /><br /> Deweloperzy produktów.|  
|Pełny|"Dodatnią" zdarzeń: zdarzenia, oznaczające pomyślne punktów kontrolnych.|Niski poziom zdarzenia kod użytkownika i obsługi są emitowane.|Ogólnie rzecz biorąc można użyć ten poziom optymalizacji aplikacji lub debugowania.<br /><br /> — Nagłówek rozpoznawanych wiadomości.|Administratorzy<br /><br /> Deweloperzy aplikacji<br /><br /> Deweloperzy produktów.|  
|ActivityTracing||Zdarzenia przepływ między działaniami przetwarzania i składników.|Ten poziom umożliwia administratorów i deweloperów skorelować aplikacji w tej samej domenie aplikacji:<br /><br /> -Śladów granice działania, takie jak uruchamianie i zatrzymywanie.<br />-Ślady transferów.|Wszystkie|  
|Wszystkie||Aplikacja może działać poprawnie. Wszystkie zdarzenia są emitowane.|Wszystkie poprzednie zdarzenia.|Wszystkie|  
  
 Poziomy pełne krytyczny są ułożone jeden na drugim, oznacza to, że każdy poziom śledzenia zawiera wszystkie poziomy nad nim, z wyjątkiem poziom Off. Na przykład odbiornik nasłuchuje na poziom ostrzeżeń odbiera ślady krytyczny, błąd i ostrzeżenie. Poziom wszystkich zawiera zdarzenia z pełne do zdarzenia śledzenia krytyczne i działania.  
  
> [!CAUTION]
>  Poziomy informacje, pełne i ActivityTracing generuje dużą liczbę śladów, które mogą mieć negatywny wpływ na przepływność komunikatów, jeśli zostały zużyte wszystkie dostępne zasoby na komputerze.  
  
## <a name="configuring-activity-tracing-and-propagation-for-correlation"></a>Konfigurowanie śledzenia działań i Propagacja dla korelacji  
 `activityTracing` Wartość określona dla `switchValue` atrybut służy do monitorowania zdarzeń zachodzących działań, który emituje ślady działania granic i transfery w obrębie punktów końcowych.  
  
> [!NOTE]
>  Gdy używasz pewnych funkcji rozszerzalności programu WCF możesz otrzymać <xref:System.NullReferenceException> podczas czynność śledzenia jest włączona. Aby rozwiązać ten problem, sprawdź plik konfiguracji aplikacji i upewnij się, że `switchValue` atrybutu źródła śledzenia nie jest ustawiony na `activityTracing`.  
  
 `propagateActivity` Atrybut wskazuje, czy działanie powinno propagowane do innych punktów końcowych, które uczestniczą w wymianie wiadomości. Ustawiając tę wartość na `true`, możesz pobrać pliki śledzenia generowanych przez wszystkie dwa punkty końcowe i obserwuj, jak zestaw danych śledzenia w jednym punkcie końcowym przekazane do zestawu danych śledzenia w innym punkcie końcowym.  
  
 Aby uzyskać więcej informacji na temat śledzenie aktywności i propagację zobacz [propagacji](../../../../../docs/framework/wcf/diagnostics/tracing/propagation.md).  
  
 Zarówno `propagateActivity` i `ActivityTracing` wartościami logicznymi dotyczą System.ServiceModel TraceSource. `ActivityTracing` Wartość ma zastosowanie również do dowolnego źródła śledzenia, w tym usługi WCF i te zdefiniowane przez użytkownika.  
  
 Nie można użyć `propagateActivity` atrybut o źródła śledzenia zdefiniowanych przez użytkownika. W przypadku Propagacja Identyfikatora działania kodu użytkownika, upewnij się, nie należy ustawiać elementu ServiceModel `ActivityTracing`, przy zachowaniu ServiceModel `propagateActivity` ustawioną wartość atrybutu `true`.  
  
## <a name="see-also"></a>Zobacz także
- [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Administracja i diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
- [Instrukcje: Tworzenie i Inicjowanie obiektów nasłuchujących śledzenia](https://go.microsoft.com/fwlink/?LinkId=94648)
- [Tworzenie niestandardowych zdarzeń TraceListener](https://go.microsoft.com/fwlink/?LinkId=96239)
