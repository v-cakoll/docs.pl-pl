---
title: Konfigurowanie śledzenia
ms.date: 03/30/2017
helpviewer_keywords:
- tracing [WCF]
ms.assetid: 82922010-e8b3-40eb-98c4-10fc05c6d65d
ms.openlocfilehash: 2fbe5b48a9405c9236923ffec268683bdf570831
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579010"
---
# <a name="configuring-tracing"></a>Konfigurowanie śledzenia
W tym temacie opisano sposób włączania śledzenia, konfigurowania źródeł śledzenia w celu emitowania śladów i ustawiania poziomów śledzenia, ustawiania śledzenia aktywności i propagacji w celu obsługi korelacji kompleksowych wyników śledzenia oraz ustawiania detektorów śledzenia dostępu do śladów.  
  
 W przypadku zaleceń dotyczących ustawień śledzenia w środowisku produkcyjnym lub debugowania zapoznaj się z [zalecanymi ustawieniami śledzenia i rejestrowania komunikatów](recommended-settings-for-tracing-and-message-logging.md).  
  
> [!IMPORTANT]
> W systemie Windows 8 należy uruchomić podniesiony poziom aplikacji (Uruchom jako administrator), aby aplikacja mogła generować dzienniki śledzenia.  
  
## <a name="enabling-tracing"></a>Włączenie debugowania  
 Windows Communication Foundation (WCF) wyprowadza następujące dane na potrzeby śledzenia diagnostycznego:  
  
- Ślady dla punktów kontrolnych procesu we wszystkich składnikach aplikacji, takich jak wywołania operacji, wyjątki kodu, ostrzeżenia i inne istotne zdarzenia przetwarzania.  
  
- Zdarzenia błędów systemu Windows, gdy funkcja śledzenia działa nieprawidłowo. Zobacz [Rejestrowanie zdarzeń](../event-logging/index.md).  
  
 Śledzenie WCF jest tworzone w oparciu o <xref:System.Diagnostics> . Aby użyć funkcji śledzenia, należy zdefiniować źródła śledzenia w pliku konfiguracyjnym lub w kodzie. Funkcja WCF definiuje Źródło śledzenia dla każdego zestawu WCF. `System.ServiceModel`Źródłem śledzenia jest najpopularniejsze Źródło śledzenia WCF oraz rejestruje punkty kontrolne przetwarzania w stosie komunikacji WCF, od wejścia/opuszczenia transportu w celu wprowadzenia/opuszczenia kodu użytkownika. `System.ServiceModel.MessageLogging`Źródło śledzenia rejestruje wszystkie komunikaty przesyłane przez system.  
  
 Śledzenie nie jest domyślnie włączone. Aby uaktywnić śledzenie, należy utworzyć odbiornik śledzenia i ustawić poziom śledzenia inny niż "off" dla wybranego źródła śledzenia w konfiguracji; w przeciwnym razie WCF nie generuje żadnych śladów. Jeśli nie określisz odbiornika, funkcja śledzenia zostanie automatycznie wyłączona. Jeśli odbiornik jest zdefiniowany, ale nie określono żadnego poziomu, poziom jest domyślnie ustawiony na wartość "off", co oznacza, że śledzenie nie jest emitowane.  
  
 W przypadku używania punktów rozszerzalności WCF, takich jak niestandardowe wywołania operacji, należy emitować własne dane śledzenia. Wynika to z faktu, że w przypadku zaimplementowania punktu rozszerzalności Funkcja WCF nie będzie już emitować standardowych śladów w ścieżce domyślnej. Jeśli obsługa śledzenia ręcznego nie zostanie wdrożona przez emitowanie śladów, mogą nie być widoczne dane śledzenia.  
  
 Śledzenie można skonfigurować, edytując plik konfiguracyjny aplikacji — Web. config dla aplikacji hostowanych w sieci Web lub nazwa_aplikacji. exe. config dla aplikacji samodzielnych. Poniżej przedstawiono przykład takiej edycji. Aby uzyskać więcej informacji na temat tych ustawień, zobacz sekcję "Konfigurowanie odbiorników śledzenia do korzystania ze śladów".  
  
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
> Aby edytować plik konfiguracji projektu usługi WCF w programie Visual Studio, kliknij prawym przyciskiem myszy plik konfiguracyjny aplikacji — Web. config dla aplikacji hostowanych w sieci Web, lub nazwa_aplikacji. exe. config dla aplikacji samohostowanej w **Eksplorator rozwiązań**. Następnie wybierz pozycję **Edytuj kontekst konfiguracji WCF** . Spowoduje to uruchomienie [Narzędzia Edytora konfiguracji (SvcConfigEditor. exe)](../../configuration-editor-tool-svcconfigeditor-exe.md), które pozwala modyfikować ustawienia konfiguracji usług WCF przy użyciu graficznego interfejsu użytkownika.  
  
## <a name="configuring-trace-sources-to-emit-traces"></a>Konfigurowanie źródeł śledzenia w celu emitowania śladów  
 Funkcja WCF definiuje Źródło śledzenia dla każdego zestawu. Ślady wygenerowane w zestawie są dostępne dla odbiorników zdefiniowanych dla tego źródła. Zdefiniowane są następujące źródła śledzenia:  
  
- System. ServiceModel: rejestruje wszystkie etapy przetwarzania w programie WCF, za każdym razem, gdy konfiguracja jest odczytywana, komunikat jest przetwarzany w transporcie, przetwarzanie zabezpieczeń, komunikat jest wysyłany w kodzie użytkownika i tak dalej.  
  
- System. ServiceModel. MessageLogging: rejestruje wszystkie komunikaty przesyłane przez system.  
  
- System. IdentityModel.  
  
- System. ServiceModel. Activation.  
  
- System. IO. log: rejestrowanie interfejsu .NET Framework do Common Log File System (CLFS).  
  
- System. Runtime. Serialization: rejestruje, kiedy obiekty są odczytywane lub zapisywane.  
  
- CardSpace.  
  
 Każde źródło śledzenia można skonfigurować tak, aby korzystało z tego samego odbiornika (udostępnionego), jak pokazano w poniższym przykładzie konfiguracji.  
  
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
  
 Ponadto można dodać zdefiniowane przez użytkownika źródła śledzenia, jak pokazano w poniższym przykładzie, aby emitować ślady kodu użytkownika.  
  
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
  
 Aby uzyskać więcej informacji na temat tworzenia źródeł śledzenia zdefiniowanych przez użytkownika, zobacz [Rozszerzanie śledzenia](../../samples/extending-tracing.md).  
  
## <a name="configuring-trace-listeners-to-consume-traces"></a>Konfigurowanie detektorów śledzenia do korzystania ze śladów  
 W czasie wykonywania usługa WCF zwraca dane śledzenia do odbiorników, które przetwarzają dane. Funkcja WCF udostępnia kilka wstępnie zdefiniowanych odbiorników <xref:System.Diagnostics> , które różnią się w formacie danych wyjściowych. Możesz również dodać typy odbiorników niestandardowych.  
  
 Można użyć `add` określić nazwę i typ odbiornik śledzenia ma być używany. W naszej przykładowej konfiguracji nazywamy odbiornik `traceListener` i dodałeś odbiornik standardowego .NET Framework śledzenia ( `System.Diagnostics.XmlWriterTraceListener` ) jako typ, który ma być używany. Można dodać dowolną liczbę detektorów śledzenia dla każdego źródła. Jeśli odbiornik śledzenia emituje ślad do pliku, należy określić lokalizację i nazwę pliku wyjściowego w pliku konfiguracji. Jest to realizowane przez ustawienie `initializeData` nazwy pliku dla tego odbiornika. Jeśli nie określisz nazwy pliku, zostanie wygenerowana losowa nazwa pliku na podstawie używanego typu odbiornika. Jeśli <xref:System.Diagnostics.XmlWriterTraceListener> jest używana, zostanie wygenerowana nazwa pliku bez rozszerzenia. W przypadku zaimplementowania odbiornika niestandardowego można także użyć tego atrybutu do odbierania danych inicjujących innych niż nazwa pliku. Na przykład można określić identyfikator bazy danych dla tego atrybutu.  
  
 Można skonfigurować odbiornik niestandardowego śledzenia do wysyłania śladów do sieci, na przykład do zdalnej bazy danych. Jako narzędzie do wdrażania aplikacji należy wymusić odpowiednią kontrolę dostępu w dziennikach śledzenia na maszynie zdalnej.  
  
 Można również programowo skonfigurować odbiornik śledzenia. Aby uzyskać więcej informacji, zobacz [How to: Create i Initialize detektory śledzenia](../../../debug-trace-profile/how-to-create-and-initialize-trace-listeners.md) i [Tworzenie niestandardowego TraceListener](https://docs.microsoft.com/archive/msdn-magazine/2006/april/clr-inside-out-extending-system-diagnostics).  
  
> [!CAUTION]
> Ponieważ `System.Diagnostics.XmlWriterTraceListener` nie jest bezpieczny wątkowo, Źródło śledzenia może blokować zasoby wyłącznie podczas wyprowadzania śladów. Gdy wiele wątków wyprowadza ślady do źródła śledzenia skonfigurowanego do korzystania z tego odbiornika, może wystąpić rywalizacja o zasoby, co powoduje znaczący problem z wydajnością. Aby rozwiązać ten problem, należy zaimplementować niestandardowy odbiornik, który jest bezpieczny dla wątków.  
  
## <a name="trace-level"></a>Poziom śledzenia  
 Poziom śledzenia jest kontrolowany przez `switchValue` ustawienie źródła śledzenia. Dostępne poziomy śledzenia są opisane w poniższej tabeli.  
  
|Poziom śledzenia|Charakter śledzonych zdarzeń|Zawartość śledzonych zdarzeń|Zdarzenia śledzone|Obiekt docelowy użytkownika|  
|-----------------|----------------------------------|-----------------------------------|--------------------|-----------------|  
|Wyłączone|Brak|Brak|Brak wyemitowanych śladów.|Brak|  
|Krytyczne|Zdarzenia "negatywne": zdarzenia wskazujące nieoczekiwane przetwarzanie lub warunek błędu.||Zarejestrowano Nieobsłużone wyjątki, w tym następujące:<br /><br /> -OutOfMemoryException<br />-ThreadAbortException (środowisko CLR wywołuje wszystkie ThreadAbortExceptionHandler)<br />-StackOverflowException (nie można przechwycić)<br />-ConfigurationErrorsException<br />-SEHException —<br />-Błędy uruchamiania aplikacji<br />-FailFast zdarzenia<br />— Zawiesza się system<br />-Trujące komunikaty: ślady komunikatów, które powodują niepowodzenie aplikacji.|Administratorzy<br /><br /> Deweloperzy aplikacji|  
|Błąd|Zdarzenia "negatywne": zdarzenia wskazujące nieoczekiwane przetwarzanie lub warunek błędu.|Nastąpiło nieoczekiwane przetwarzanie. Aplikacja nie mogła wykonać zadania zgodnie z oczekiwaniami. Aplikacja jest jednak nadal uruchomiona.|Wszystkie wyjątki są rejestrowane.|Administratorzy<br /><br /> Deweloperzy aplikacji|  
|Ostrzeżenie|Zdarzenia "negatywne": zdarzenia wskazujące nieoczekiwane przetwarzanie lub warunek błędu.|Wystąpił możliwy problem lub może wystąpić, ale aplikacja nadal działa poprawnie. Może jednak nadal nie funkcjonować prawidłowo.|-Aplikacja otrzymuje więcej żądań niż zezwala na to ustawienia ograniczenia przepustowości.<br />-Kolejka otrzymująca zbliża się do maksymalnej skonfigurowanej pojemności.<br />-Przekroczono limit czasu.<br />-Poświadczenia są odrzucane.|Administratorzy<br /><br /> Deweloperzy aplikacji|  
|Informacje|Zdarzenia "pozytywne": zdarzenia, które oznaczają pomyślne punkty kontrolne|Ważne i pomyślne punkty kontrolne wykonywania aplikacji, niezależnie od tego, czy aplikacja działa prawidłowo, czy nie.|Ogólnie rzecz biorąc komunikaty przydatne do monitorowania i diagnozowania stanu systemu, wygenerowania pomiaru wydajności lub profilowania. Tych informacji można użyć do planowania pojemności i zarządzania wydajnością:<br /><br /> -Kanały zostały utworzone.<br />-Są tworzone odbiorniki punktów końcowych.<br />-Komunikat przechodzi/opuszcza transport.<br />-Zostanie pobrany token zabezpieczający.<br />-Ustawienie konfiguracji jest odczytane.|Administratorzy<br /><br /> Deweloperzy aplikacji<br /><br /> Deweloperzy produktów.|  
|Pełny|Zdarzenia "pozytywne": zdarzenia, które oznaczają pomyślne punkty kontrolne.|Zdarzenia niskiego poziomu dla kodu użytkownika i obsługi są emitowane.|Ogólnie rzecz biorąc, można użyć tego poziomu na potrzeby debugowania lub optymalizacji aplikacji.<br /><br /> -Zrozumiały nagłówek wiadomości.|Administratorzy<br /><br /> Deweloperzy aplikacji<br /><br /> Deweloperzy produktów.|  
|ActivityTracing||Przepływ zdarzeń między działaniami przetwarzania i składnikami.|Na tym poziomie Administratorzy i deweloperzy mogą skorelować aplikacje w tej samej domenie aplikacji:<br /><br /> -Śledzi dla granic działania, takich jak uruchamianie/zatrzymywanie.<br />— Ślady dla transferów.|Wszystko|  
|Wszystko||Aplikacja może działać prawidłowo. Wszystkie zdarzenia są emitowane.|Wszystkie poprzednie zdarzenia.|Wszystko|  
  
 Poziomy od pełnych do krytyczne są ułożone na siebie nawzajem, to znaczy, że każdy poziom śledzenia obejmuje wszystkie poziomy powyżej, z wyjątkiem poziomu wyłączonego. Na przykład odbiornik nasłuchujący na poziomie ostrzeżeń odbiera dane śledzenia krytyczne, błąd i ostrzeżenie. Poziom wszystko obejmuje zdarzenia z pełnymi zdarzeniami śledzenia krytycznego i działania.  
  
> [!CAUTION]
> Informacje, pełne i ActivityTracing poziomy generują wiele śladów, co może negatywnie wpłynąć na przepływność komunikatów, jeśli wszystkie dostępne zasoby są używane na komputerze.  
  
## <a name="configuring-activity-tracing-and-propagation-for-correlation"></a>Konfigurowanie śledzenia działań i propagacji dla korelacji  
 `activityTracing`Wartość określona dla atrybutu służy `switchValue` do włączania śledzenia aktywności, która emituje ślady dla granic działań i transferów w punktach końcowych.  
  
> [!NOTE]
> W przypadku korzystania z pewnych funkcji rozszerzalności w programie WCF może wystąpić sytuacja, w której <xref:System.NullReferenceException> jest włączone śledzenie aktywności. Aby rozwiązać ten problem, sprawdź plik konfiguracyjny aplikacji i upewnij się, że `switchValue` Atrybut źródła śledzenia nie jest ustawiony na `activityTracing` .  
  
 Ten `propagateActivity` atrybut wskazuje, czy działanie powinno być propagowane do innych punktów końcowych, które uczestniczą w wymianie komunikatów. Ustawiając tę wartość na `true` , można pobrać pliki śledzenia wygenerowane przez dowolne dwa punkty końcowe i obserwować, jak zestaw śladów w jednym punkcie końcowym przepływa do zestawu śladów w innym punkcie końcowym.  
  
 Aby uzyskać więcej informacji na temat śledzenia działań i propagacji, zobacz [Propagacja](propagation.md).  
  
 Oba `propagateActivity` i `ActivityTracing` wartości logiczne są stosowane do elementu System. ServiceModel TraceSource. `ActivityTracing`Wartość ma zastosowanie również do każdego źródła śledzenia, w tym funkcji WCF lub zdefiniowanych przez użytkownika.  
  
 Nie można używać `propagateActivity` atrybutu ze źródłami śledzenia zdefiniowanymi przez użytkownika. W przypadku propagacji identyfikatora działania kodu użytkownika upewnij się, że nie ustawiono elementu ServiceModel `ActivityTracing` , podczas gdy nadal `propagateActivity` ma atrybut ServiceModel ustawiony na `true` .  
  
## <a name="see-also"></a>Zobacz też

- [Śledzenie](index.md)
- [Administracja i Diagnostyka](../index.md)
- [Porady: tworzenie i inicjowanie obiektów nasłuchujących śledzenia](../../../debug-trace-profile/how-to-create-and-initialize-trace-listeners.md)
- [Tworzenie niestandardowego TraceListener](https://docs.microsoft.com/archive/msdn-magazine/2006/april/clr-inside-out-extending-system-diagnostics)
