---
title: Konfigurowanie śledzenia
ms.date: 03/30/2017
helpviewer_keywords:
- tracing [WCF]
ms.assetid: 82922010-e8b3-40eb-98c4-10fc05c6d65d
ms.openlocfilehash: c5079237ff4c97dd9ef164061dc5e7499c1d6e38
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/03/2020
ms.locfileid: "80636001"
---
# <a name="configuring-tracing"></a>Konfigurowanie śledzenia
W tym temacie opisano, jak włączyć śledzenie, skonfigurować źródła śledzenia do emitowania śladów i ustawić poziomy śledzenia, ustawić śledzenie aktywności i propagację do obsługi korelacji śledzenia end-to-end i ustawić detektory śledzenia, aby uzyskać dostęp do śledzenia.  
  
 Informacje na temat śledzenia zaleceń dotyczących ustawień w środowisku produkcyjnym lub debugowania można znaleźć w [sekcji Zalecane ustawienia śledzenia i rejestrowania wiadomości](../../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md).  
  
> [!IMPORTANT]
> W systemie Windows 8 należy uruchomić aplikację z podwyższonym poziomem uprawnień (Uruchom jako administrator), aby aplikacja wygenerowała dzienniki śledzenia.  
  
## <a name="enabling-tracing"></a>Włączenie debugowania  
 Windows Communication Foundation (WCF) wyprowadza następujące dane do śledzenia diagnostycznego:  
  
- Ślady dla punktów kontrolnych procesu we wszystkich składnikach aplikacji, takich jak wywołania operacji, wyjątki kodu, ostrzeżenia i inne znaczące zdarzenia przetwarzania.  
  
- Zdarzenia błędu systemu Windows, gdy funkcja śledzenia działa nieprawidłowo. Zobacz [Rejestrowanie zdarzeń](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md).  
  
 Śledzenie WCF jest zbudowany <xref:System.Diagnostics>na szczycie . Aby użyć śledzenia, należy zdefiniować źródła śledzenia w pliku konfiguracyjnym lub w kodzie. WCF definiuje źródło śledzenia dla każdego zestawu WCF. Źródło `System.ServiceModel` śledzenia jest najbardziej ogólne źródło śledzenia WCF i rekordy przetwarzania punktów kontrolnych w stosie komunikacji WCF, od wprowadzania/opuszczania transportu do wprowadzania/opuszczania kodu użytkownika. Źródło `System.ServiceModel.MessageLogging` śledzenia rejestruje wszystkie komunikaty, które przepływają przez system.  
  
 Śledzenie nie jest domyślnie włączone. Aby aktywować śledzenie, należy utworzyć odbiornik śledzenia i ustawić poziom śledzenia inny niż "Off" dla wybranego źródła śledzenia w konfiguracji; w przeciwnym razie WCF nie generuje żadnych śladów. Jeśli odbiornik nie zostanie określony, śledzenie zostanie automatycznie wyłączone. Jeśli odbiornik jest zdefiniowany, ale nie określono poziomu, poziom jest domyślnie ustawiony na "Off", co oznacza, że nie jest emitowany żaden ślad.  
  
 Jeśli używasz punktów rozszerzalności WCF, takich jak wywoływania operacji niestandardowych, należy emitować własne ślady. Dzieje się tak, ponieważ jeśli zaimplementujesz punkt rozszerzalności, WCF nie może już emitować standardowych śladów w ścieżce domyślnej. Jeśli nie implementujesz obsługi śledzenia ręcznego przez emitowanie śladów, możesz nie widzieć oczekiwanych śladów.  
  
 Śledzenie można skonfigurować, edytując plik konfiguracyjny aplikacji — plik Web.config dla aplikacji hostowanych w sieci Web lub appname.exe.config dla aplikacji hostowanych samodzielnie. Poniżej przedstawiono przykład takiej edycji. Aby uzyskać więcej informacji na temat tych ustawień, zobacz sekcję "Konfigurowanie odbiorników śledzenia do wykorzystania śladów".  
  
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
> Aby edytować plik konfiguracyjny projektu usługi WCF w programie Visual Studio, kliknij prawym przyciskiem myszy plik konfiguracyjny aplikacji — web.config dla aplikacji hostowanych w sieci Web lub Appname.exe.config dla aplikacji hostowanych samodzielnie w **Eksploratorze rozwiązań**. Następnie wybierz element menu kontekstowego **Edytuj konfigurację WCF.** Spowoduje to uruchomienie [narzędzia Edytor konfiguracji (SvcConfigEditor.exe),](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)które umożliwia modyfikowanie ustawień konfiguracji usług WCF przy użyciu graficznego interfejsu użytkownika.  
  
## <a name="configuring-trace-sources-to-emit-traces"></a>Konfigurowanie źródeł śledzenia w celu emitowania śladów  
 WCF definiuje źródło śledzenia dla każdego zestawu. Ślady generowane w ramach zestawu są dostępne dla odbiorników zdefiniowanych dla tego źródła. Zdefiniowano następujące źródła śledzenia:  
  
- System.ServiceModel: Rejestruje wszystkie etapy przetwarzania WCF, gdy konfiguracja jest odczytywana, komunikat jest przetwarzany w transporcie, przetwarzania zabezpieczeń, wiadomość jest wywoływana w kodzie użytkownika i tak dalej.  
  
- System.ServiceModel.MessageLogging: Rejestruje wszystkie komunikaty, które przepływają przez system.  
  
- System.identitymodel.  
  
- System.ServiceModel.Activation.  
  
- System.IO.Log: Rejestrowanie interfejsu programu .NET Framework do wspólnego systemu plików dziennika (CLFS).  
  
- System.Runtime.Serialization: Rejestruje, gdy obiekty są odczytywane lub zapisywane.  
  
- Cardspace.  
  
 Można skonfigurować każde źródło śledzenia, aby używało tego samego (udostępnionego) odbiornika, jak wskazano w poniższym przykładzie konfiguracji.  
  
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
  
 Ponadto można dodać źródła śledzenia zdefiniowane przez użytkownika, jak pokazano w poniższym przykładzie, aby emitować ślady kodu użytkownika.  
  
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
  
 Aby uzyskać więcej informacji na temat tworzenia źródeł śledzenia zdefiniowanych przez użytkownika, zobacz [Rozszerzanie śledzenia](../../../../../docs/framework/wcf/samples/extending-tracing.md).  
  
## <a name="configuring-trace-listeners-to-consume-traces"></a>Konfigurowanie odbiorników śledzenia do wykorzystania śladów  
 W czasie wykonywania WCF dostarcza dane śledzenia do odbiorników, które przetwarzają dane. WCF zapewnia kilka wstępnie zdefiniowanych <xref:System.Diagnostics>odbiorników dla , które różnią się formatem, którego używają do wyjścia. Można również dodać niestandardowe typy odbiorników.  
  
 Można użyć `add` określić nazwę i typ odbiornik śledzenia ma być używany. W naszej konfiguracji przykładowej nazwaliśmy odbiornik `traceListener` i dodaliśmy standardowy`System.Diagnostics.XmlWriterTraceListener`odbiornik śledzenia programu .NET Framework ( ) jako typ, którego chcemy użyć. Można dodać dowolną liczbę odbiorników śledzenia dla każdego źródła. Jeśli odbiornik śledzenia emituje śledzenie do pliku, należy określić lokalizację pliku wyjściowego i nazwę w pliku konfiguracyjnym. Odbywa się to `initializeData` przez ustawienie nazwy pliku dla tego odbiornika. Jeśli nazwa pliku nie zostanie określona, zostanie wygenerowana losowa nazwa pliku na podstawie używanego typu odbiornika. Jeśli <xref:System.Diagnostics.XmlWriterTraceListener> jest używany, nazwa pliku bez rozszerzenia jest generowany. Jeśli zaimplementujesz odbiornik niestandardowy, można również użyć tego atrybutu do odbierania danych inicjowania innych niż nazwa pliku. Na przykład można określić identyfikator bazy danych dla tego atrybutu.  
  
 Można skonfigurować niestandardowy odbiornik śledzenia, aby wysyłał ślady w sieci, na przykład do zdalnej bazy danych. Jako wdrażający aplikację należy wymusić właściwą kontrolę dostępu na dziennikach śledzenia na komputerze zdalnym.  
  
 Można również skonfigurować odbiornik śledzenia programowo. Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie i inicjowanie odbiorników śledzenia](../../../debug-trace-profile/how-to-create-and-initialize-trace-listeners.md) i [tworzenie niestandardowego listy śledzenia](https://docs.microsoft.com/archive/msdn-magazine/2006/april/clr-inside-out-extending-system-diagnostics).  
  
> [!CAUTION]
> Ponieważ `System.Diagnostics.XmlWriterTraceListener` nie jest bezpieczne dla wątków, źródło śledzenia może zablokować zasoby wyłącznie podczas wyprowadzania śladów. Gdy wiele wątków danych danych śledzenia śledzenia źródła skonfigurowanego do korzystania z tego odbiornika, rywalizacja o zasoby może wystąpić, co powoduje znaczący problem z wydajnością. Aby rozwiązać ten problem, należy zaimplementować niestandardowy odbiornik, który jest bezpieczny dla wątków.  
  
## <a name="trace-level"></a>Poziom śledzenia  
 Poziom śledzenia jest kontrolowany `switchValue` przez ustawienie źródła śledzenia. Dostępne poziomy śledzenia są opisane w poniższej tabeli.  
  
|Poziom śledzenia|Charakter śledzonych wydarzeń|Zawartość śledzonych zdarzeń|Śledzone zdarzenia|Obiekt docelowy użytkownika|  
|-----------------|----------------------------------|-----------------------------------|--------------------|-----------------|  
|Wyłączone|Nie dotyczy|Nie dotyczy|Nie są emitowane żadne ślady.|Nie dotyczy|  
|Krytyczny|Zdarzenia "negatywne": zdarzenia wskazujące nieoczekiwane przetwarzanie lub warunek błędu.||Rejestrowane są nieobsługiwalne wyjątki, w tym następujące:<br /><br /> - OutOfMemoryException<br />- ThreadAbortException (CLR wywołuje wszelkie ThreadAbortExceptionHandler)<br />- StackOverflowException (nie można złapać)<br />- KonfiguracjaErrorsException<br />- SEHException<br />- Błędy uruchamiania aplikacji<br />- Nieudane zdarzenia<br />- Zawiesza się system<br />- Trujące wiadomości: ślady wiadomości, które powodują niepowodzenie aplikacji.|Administratorzy<br /><br /> Deweloperzy aplikacji|  
|Błąd|Zdarzenia "negatywne": zdarzenia wskazujące nieoczekiwane przetwarzanie lub warunek błędu.|Nieoczekiwane przetwarzanie miało miejsce. Aplikacja nie była w stanie wykonać zadania zgodnie z oczekiwaniami. Jednak aplikacja jest nadal uruchomiona.|Wszystkie wyjątki są rejestrowane.|Administratorzy<br /><br /> Deweloperzy aplikacji|  
|Ostrzeżenie|Zdarzenia "negatywne": zdarzenia wskazujące nieoczekiwane przetwarzanie lub warunek błędu.|Wystąpił lub może wystąpić możliwy problem, ale aplikacja nadal działa poprawnie. Jednak może nie działać poprawnie.|- Aplikacja otrzymuje więcej żądań niż pozwalają na to jej ustawienia ograniczania przepustowości.<br />- Kolejka odbiorcza znajduje się w pobliżu maksymalnej skonfigurowaną pojemności.<br />- Przekroczony limit czasu.<br />- Poświadczenia są odrzucane.|Administratorzy<br /><br /> Deweloperzy aplikacji|  
|Informacje|"Pozytywne" wydarzenia: wydarzenia, które oznaczają udane kamienie milowe|Ważne i pomyślne punkty kontrolne wykonania aplikacji, niezależnie od tego, czy aplikacja działa poprawnie, czy nie.|Ogólnie rzecz biorąc, generowane są komunikaty przydatne do monitorowania i diagnozowania stanu systemu, pomiaru wydajności lub profilowania. Takie informacje można wykorzystać do planowania pojemności i zarządzania wydajnością:<br /><br /> - Kanały są tworzone.<br />- Odbiorniki punktów końcowych są tworzone.<br />- Wiadomość wchodzi / opuszcza transport.<br />- Token zabezpieczający jest pobierany.<br />- Odczytanie ustawienia konfiguracji.|Administratorzy<br /><br /> Deweloperzy aplikacji<br /><br /> Deweloperzy produktów.|  
|Pełny|"Pozytywne" wydarzenia: wydarzenia, które oznaczają udane kamienie milowe.|Emitowane są zdarzenia niskiego poziomu zarówno dla kodu użytkownika, jak i obsługi.|Ogólnie rzecz biorąc można użyć tego poziomu do debugowania lub optymalizacji aplikacji.<br /><br /> - Zrozumiałe nagłówek wiadomości.|Administratorzy<br /><br /> Deweloperzy aplikacji<br /><br /> Deweloperzy produktów.|  
|Activitytracing||Zdarzenia przepływu między działaniami przetwarzania i składnikami.|Ten poziom umożliwia administratorom i deweloperom skorelowanie aplikacji w tej samej domenie aplikacji:<br /><br /> - Ślady dla granic działania, takie jak start/stop.<br />- Ślady transferów.|Wszystkie|  
|Wszystkie||Aplikacja może działać prawidłowo. Wszystkie zdarzenia są emitowane.|Wszystkie poprzednie wydarzenia.|Wszystkie|  
  
 Poziomy z pełnej do krytycznej są ułożone jeden na drugim, oznacza to, że każdy poziom śledzenia zawiera wszystkie poziomy powyżej z wyjątkiem Off poziom. Na przykład odbiornik nasłuchiwania na poziomie ostrzeżenie odbiera krytyczne, błędy i ostrzeżenia śledzenia. Poziom Wszystkie zawiera zdarzenia z pełne do krytycznych i zdarzeń śledzenia aktywności.  
  
> [!CAUTION]
> Poziomy Informacje, Pełne i ActivityTracing generują wiele śladów, które mogą negatywnie wpłynąć na przepływność komunikatów, jeśli zostały wykorzystane wszystkie dostępne zasoby na komputerze.  
  
## <a name="configuring-activity-tracing-and-propagation-for-correlation"></a>Konfigurowanie śledzenia i propagacji działań dla korelacji  
 Wartość `activityTracing` określona `switchValue` dla atrybutu jest używana do włączania śledzenia działania, które emituje ślady dla granic działania i transferów w punktach końcowych.  
  
> [!NOTE]
> Korzystając z niektórych funkcji rozszerzalności w WCF, może pojawić <xref:System.NullReferenceException> się, gdy śledzenie aktywności jest włączone. Aby rozwiązać ten problem, sprawdź plik konfiguracyjny aplikacji i upewnij się, że `switchValue` atrybut źródła śledzenia nie jest ustawiony na `activityTracing`.  
  
 Atrybut `propagateActivity` wskazuje, czy działanie powinno być propagowane do innych punktów końcowych, które uczestniczą w wymianie wiadomości. Ustawiając tę `true`wartość na , można wziąć pliki śledzenia generowane przez dowolne dwa punkty końcowe i obserwować, jak zestaw śladów w jednym punkcie końcowym przepływał do zestawu śladów w innym punkcie końcowym.  
  
 Aby uzyskać więcej informacji na temat śledzenia i propagacji aktywności, zobacz [Propagacja](../../../../../docs/framework/wcf/diagnostics/tracing/propagation.md).  
  
 Zarówno `propagateActivity` `ActivityTracing` wartości logiczne i logiczne mają zastosowanie do System.ServiceModel TraceSource. Wartość `ActivityTracing` dotyczy również dowolnego źródła śledzenia, w tym WCF lub zdefiniowanych przez użytkownika.  
  
 Nie można `propagateActivity` użyć atrybutu ze źródłami śledzenia zdefiniowanymi przez użytkownika. W przypadku propagacji identyfikatora działania kodu użytkownika upewnij `ActivityTracing`się, że nie `propagateActivity` ustawiono servicemodelu, podczas gdy atrybut ServiceModel jest ustawiony na `true`.  
  
## <a name="see-also"></a>Zobacz też

- [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Administracja i diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
- [Porady: tworzenie i inicjowanie obiektów nasłuchujących śledzenia](../../../debug-trace-profile/how-to-create-and-initialize-trace-listeners.md)
- [Tworzenie niestandardowego listy śledzenia](https://docs.microsoft.com/archive/msdn-magazine/2006/april/clr-inside-out-extending-system-diagnostics)
