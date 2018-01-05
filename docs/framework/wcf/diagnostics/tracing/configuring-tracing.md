---
title: "Konfigurowanie śledzenia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: tracing [WCF]
ms.assetid: 82922010-e8b3-40eb-98c4-10fc05c6d65d
caps.latest.revision: "53"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3beeaec1ed9982fc49f6bf81e2717db862e7882f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-tracing"></a>Konfigurowanie śledzenia
W tym temacie opisano, jak można włączyć śledzenie, skonfigurować źródła śledzenia na emitowanie danych śledzenia i poziomy śledzenia zestawu, śledzenie działania zestawu i propagacji do obsługi korelacji śledzenia end-to-end i ustaw obiektów nasłuchujących śledzenia do śledzenia.  
  
 Zalecenia dotyczące ustawień śledzenia w środowisku debugowania i produkcji, można znaleźć w temacie [zalecane ustawienia śledzenia i rejestrowania komunikatów](../../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md).  
  
> [!IMPORTANT]
>  W systemie Windows 8 należy uruchomić aplikację podniesionych uprawnień (Uruchom jako Administrator) w kolejności dla aplikacji do wygenerowania dzienniki śledzenia.  
  
## <a name="enabling-tracing"></a>Włączenie debugowania  
 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]Wyświetla następujące dane śledzenia diagnostycznego:  
  
-   Ślady punktów kontrolnych procesu dotyczące wszystkich składników aplikacji, takie jak wywołania operacji kodu wyjątki, ostrzeżenia i inne istotne przetwarzanie zdarzeń.  
  
-   Zdarzenia błędu systemu Windows działa funkcja śledzenia. Zobacz [rejestrowanie zdarzeń](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md).  
  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]śledzenie jest oparty na <xref:System.Diagnostics>. Aby użyć śledzenia, należy zdefiniować źródła śledzenia w pliku konfiguracji lub w kodzie. [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]Określa źródło śladu dla każdego [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] zestawu. `System.ServiceModel` Źródła śledzenia jest najbardziej ogólnym [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] źródła śledzenia i rejestruje przetwarzania punkty kontrolne w [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] stosu komunikacji z wprowadzania pozostawienie transportu do wprowadzania/pozostawienia kodu użytkownika. `System.ServiceModel.MessageLogging` Źródło śladu rejestruje wszystkie komunikaty, które przepływać przez system.  
  
 Śledzenie nie jest włączone domyślnie. Aby uaktywnić śledzenie, należy utworzyć odbiornik śledzenia i ustawić poziom śledzenia innych niż "Off" dla źródła śledzenia wybranych w konfiguracji. w przeciwnym razie [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] nie generuje żadnych śladów. Jeśli nie określisz odbiornik, śledzenie jest automatycznie wyłączana. Jeśli jest określony odbiornik, ale poziom nie jest określony, "Wyłączone" po ustawieniu poziomu domyślnie, co oznacza emitowanego śladów.  
  
 Jeśli używasz [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] punktów rozszerzalności takich jak invokers operacja niestandardowa powinien Emituj własne dane śledzenia. To dlatego, jeśli implementuje punkt rozszerzeń [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] może nie są już emitowane standardowe dane śledzenia w domyślnej ścieżce. Jeśli nie implementuje obsługę ręcznego śledzenia przez ślady emisji nie widać oczekiwane dane śledzenia.  
  
 Można skonfigurować śledzenie, edytując plik konfiguracji aplikacji, albo plik Web.config dla aplikacji hostowanych w sieci Web lub Appname.exe.config własnym obsługiwanych aplikacji. Oto przykład takiego edycji. Aby uzyskać więcej informacji na temat tych ustawień zobacz sekcję "Konfigurowanie śledzenia odbiorników można korzystać z śladów".  
  
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
>  Na edycję pliku konfiguracyjnego z [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] projekt usługi w [!INCLUDE[vs_current_short](../../../../../includes/vs-current-short-md.md)], kliknij prawym przyciskiem myszy plik konfiguracji aplikacji — albo plik Web.config dla aplikacji hostowanych w sieci Web lub Appname.exe.config własnym hostowanej aplikacji w  **Eksplorator rozwiązań**. Następnie wybierz pozycję **Edycja konfiguracji WCF** elementu menu kontekstowego. Spowoduje to uruchomienie [narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md), co umożliwia modyfikowanie ustawień konfiguracyjnych [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] usług przy użyciu graficznego interfejsu użytkownika.  
  
## <a name="configuring-trace-sources-to-emit-traces"></a>Konfigurowanie źródeł śledzenia na emitowanie danych śledzenia  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]Określa źródło śladu dla każdego zestawu. Wygenerowane w zestawie danych śledzenia są dostępne dla odbiorników zdefiniowane dla tego źródła. Następujące źródła śledzenia są zdefiniowane:  
  
-   System.ServiceModel: Dzienników wszystkich etapach [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] przetwarzania, gdy odczytać konfiguracji, komunikat jest przetwarzany w transporcie, zabezpieczeń, przetwarzanie wiadomości jest wysyłane w kodzie użytkownika i tak dalej.  
  
-   Używająca elementu System.ServiceModel.MessageLogging jako: Rejestruje wszystkie komunikaty przepływać przez system.  
  
-   System.IdentityModel.  
  
-   System.ServiceModel.Activation.  
  
-   System.IO.Log: Rejestrowanie dla interfejsu programu .NET Framework do typowych dziennika File System (CLFS).  
  
-   System.Runtime.Serialization: Dzienniki gdy obiekty są odczytywane lub zapisywane.  
  
-   Program CardSpace.  
  
 Każdego źródło śledzenia, aby użyć tego samego odbiornika (udostępnione), można skonfigurować zgodnie z poniższym przykładzie konfiguracji.  
  
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
  
 Ponadto możesz dodać źródła śledzenia zdefiniowanych przez użytkownika, jak pokazano na poniższym przykładzie, aby emitować śladów kodu użytkownika.  
  
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
  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]Tworzenie użytkownika śledzenia źródeł, zobacz [rozszerzanie śledzenia](../../../../../docs/framework/wcf/samples/extending-tracing.md).  
  
## <a name="configuring-trace-listeners-to-consume-traces"></a>Konfigurowanie obiektów nasłuchujących śledzenia zużyje śledzenia  
 W czasie wykonywania [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] źródła danych do odbiorników, które przetwarzają dane śledzenia. [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]zawiera kilka wstępnie zdefiniowanych odbiorników dla <xref:System.Diagnostics>, które różnią się w formacie ich użycia dla danych wyjściowych. Można również dodać niestandardowe odbiornika typów.  
  
 Można użyć `add` określić nazwę i typ odbiornik śledzenia ma być używany. W naszym przykładzie konfiguracji, firma Microsoft o nazwie odbiornika `traceListener` i dodać standardowe nasłuchującego śledzenia .NET Framework (`System.Diagnostics.XmlWriterTraceListener`) jako typ chcemy użyć. Możesz dodać dowolną liczbę obiektów nasłuchujących śledzenia dla każdego źródła. Jeśli odbiornik śledzenia emituje śledzenia w pliku, należy określić dane wyjściowe lokalizację i nazwę pliku w pliku konfiguracji. Odbywa się przez ustawienie `initializeData` nazwę pliku dla tego odbiornika. Jeśli nie określisz nazwy pliku, nazwy pliku losowe jest generowany na podstawie typu odbiornika używane. Jeśli <xref:System.Diagnostics.XmlWriterTraceListener> jest używana, jest generowany nazwę pliku bez rozszerzenia. W przypadku zastosowania niestandardowych odbiornika, można również użyć tego atrybutu, aby odebrało danych inicjujących inne niż nazwa pliku. Na przykład można określić identyfikatora bazy danych dla tego atrybutu.  
  
 Można skonfigurować odbiornik śledzenia niestandardowych do wysyłania danych śledzenia w sieci, na przykład ze zdalną bazą danych. Jako wdrażania aplikacji należy wymusić kontrolę dostępu do dzienników śledzenia na maszynie zdalnej.  
  
 Można również skonfigurować odbiornik śledzenia programowo. [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)][Porady: tworzenie i Inicjowanie obiektów nasłuchujących śledzenia](http://go.microsoft.com/fwlink/?LinkId=94648) i [Tworzenie niestandardowego elementu TraceListener](http://go.microsoft.com/fwlink/?LinkId=96239).  
  
> [!CAUTION]
>  Ponieważ `System.Diagnostics.XmlWriterTraceListener` jest nie wątkowo, źródło śladu może zablokować zasobów wyłącznie podczas wyprowadzania danych śledzenia. Wiele wątków dane wyjściowe śledzenia źródła skonfigurowane do używania tego odbiornika rywalizacji może wystąpić, które powoduje problem znaczących wydajności. Aby rozwiązać ten problem, należy zaimplementować wątkowo niestandardowe odbiornik.  
  
## <a name="trace-level"></a>Poziom śledzenia  
 Poziom śledzenia jest kontrolowany przez `switchValue` ustawienie źródła śledzenia. Poziomy śledzenia dostępne są opisane w poniższej tabeli.  
  
|Poziom śledzenia|Rodzaj rejestrowane zdarzenia|Zawartość śledzonych zdarzeń|Rejestrowane zdarzenia|Miejsce docelowe użytkownika|  
|-----------------|----------------------------------|-----------------------------------|--------------------|-----------------|  
|Off|Brak|Brak|Ślady są emitowane.|Brak|  
|Krytyczny|"Ujemną" zdarzenia: zdarzenia, które wskazują podczas wykonywania operacji wystąpił nieoczekiwany lub warunek błędu.||Rejestrowane są nieobsługiwane wyjątki, takie jak następujące:<br /><br /> — OutOfMemoryException<br />-ThreadAbortException (żadnych ThreadAbortExceptionHandler wywołuje środowiska CLR)<br />-Stackoverflowexception — (nie można przechwycić)<br />-Configurationerrorsexception —<br />-Sehexception —<br />-Błędy uruchomienia aplikacji<br />-Natychmiastowy błąd zdarzeń<br />-System przestaje odpowiadać<br />-Zanieczyszczonych komunikatów: komunikatów śledzenia, które powodują awarię aplikacji.|Administratorzy<br /><br /> Deweloperzy aplikacji|  
|Błąd|"Ujemną" zdarzenia: zdarzenia, które wskazują podczas wykonywania operacji wystąpił nieoczekiwany lub warunek błędu.|Wystąpił nieoczekiwany przetwarzania. Aplikacja nie może wykonać zadanie, zgodnie z oczekiwaniami. Jednak aplikacja jest nadal uruchomiona.|Wszystkie wyjątki są rejestrowane.|Administratorzy<br /><br /> Deweloperzy aplikacji|  
|Ostrzeżenie|"Ujemną" zdarzenia: zdarzenia, które wskazują podczas wykonywania operacji wystąpił nieoczekiwany lub warunek błędu.|Możliwy problem wystąpił lub może wystąpić, ale nadal funkcje aplikacji poprawnie. Nie może ona jednak nadal działała poprawnie.|-Aplikacja odbiera żądania więcej niż dozwolone jego ustawienia ograniczenia przepustowości.<br />-Odbierania kolejki zbliża się swoją maksymalną pojemność skonfigurowany.<br />— Przekroczony został limit czasu.<br />-Poświadczenia są odrzucane.|Administratorzy<br /><br /> Deweloperzy aplikacji|  
|Informacje|Zdarzenia "Dodatnią": zdarzenia, oznaczające pomyślne punkty kontrolne|Ważne i pomyślne punktów kontrolnych wykonywania aplikacji, niezależnie od tego, czy aplikacja działa prawidłowo lub nie.|Ogólnie rzecz biorąc generowane są przydatne do monitorowania i diagnozowania stan systemu, pomiaru wydajności lub profilowania wiadomości. Można użyć takich informacji do pojemności planowania i zarządzanie wydajnością:<br /><br /> -Kanały są tworzone.<br />— Odbiorniki punktu końcowego są tworzone.<br />-Komunikat wprowadza/pozostawia transportu.<br />-Token zabezpieczający są pobierane.<br />— Ustawienie konfiguracji jest do odczytu.|Administratorzy<br /><br /> Deweloperzy aplikacji<br /><br /> Deweloperzy produktu.|  
|Pełny|Zdarzenia "Dodatnią": zdarzenia, oznaczające pomyślne punkty kontrolne.|Zdarzenia na poziomie niskim kod użytkownika i obsługi są emitowane.|Ogólnie rzecz biorąc można użyć ten poziom optymalizacji aplikacji lub debugowania.<br /><br /> -Nagłówek komunikatu rozpoznawanych.|Administratorzy<br /><br /> Deweloperzy aplikacji<br /><br /> Deweloperzy produktu.|  
|ActivityTracing||Przepływ zdarzenia między działaniami przetwarzania i składniki.|Ten poziom umożliwia Administratorzy i deweloperzy służące do skorelowania aplikacji w tej samej domenie aplikacji:<br /><br /> -Dane śledzenia granice działania, takie jak uruchomienie/zatrzymanie.<br />-Ślady transferów.|Wszystkie|  
|Wszystkie||Aplikacja może działać prawidłowo. Wszystkie zdarzenia są emitowane.|Wszystkie poprzednie zdarzenia.|Wszystkie|  
  
 Stos poziomów pełne krytyczne na siebie, to znaczy każdy poziom śledzenia zawiera wszystkie poziomy wyżej z wyjątkiem poziomu Off. Na przykład odbiornik nasłuchiwania na poziomie ostrzeżenia odbiera śladów krytyczny, błąd i ostrzeżenie. Wszystkie poziom obejmuje zdarzenia z pełne działanie i krytyczne zdarzenia śledzenia.  
  
> [!CAUTION]
>  Poziomy informacje pełne i ActivityTracing generuje dużą liczbę śladów, które może niekorzystnie wpłynąć na wydajność obsługi wiadomości Jeśli użyto wszystkich dostępnych zasobów na komputerze.  
  
## <a name="configuring-activity-tracing-and-propagation-for-correlation"></a>Konfigurowanie śledzenia działań i Propagacja dla korelacji  
 `activityTracing` Wartość określona dla `switchValue` atrybut służy do włączenia śledzenia działania, który emituje śladów granic działania i transferów w obrębie punktów końcowych.  
  
> [!NOTE]
>  Jeśli używasz pewnych funkcji rozszerzalności w [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)], może spowodować, że <xref:System.NullReferenceException> podczas działania śledzenie jest włączone. Aby rozwiązać ten problem, sprawdź plik konfiguracji aplikacji i upewnij się, że `switchValue` atrybutu źródła śledzenia nie jest ustawiony na `activityTracing`.  
  
 `propagateActivity` Atrybut wskazuje, czy działanie powinno propagowane do pozostałych punktów końcowych, które uczestniczą w wymianie wiadomości. Ustawiając tę wartość na `true`, możesz pobrać pliki śledzenia wygenerowane przez dwoma punktami końcowymi i obserwować, jak zestaw ślady na jeden punkt końcowy skierowana do zestawu danych śledzenia w innym punktem końcowym.  
  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]śledzenie działania i propagacji, zobacz [propagacji](../../../../../docs/framework/wcf/diagnostics/tracing/propagation.md).  
  
 Zarówno `propagateActivity` i `ActivityTracing` wartościami logicznymi dotyczą System.ServiceModel TraceSource. `ActivityTracing` Wartości mają zastosowanie również do dowolnego źródła śledzenia, łącznie z [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] lub zdefiniowanej przez użytkownika.  
  
 Nie można użyć `propagateActivity` atrybut o źródła śledzenia zdefiniowanych przez użytkownika. Dla Propagacja Identyfikatora działania kodu użytkownika, upewnij się, że nie należy ustawiać ServiceModel `ActivityTracing`, przy zachowaniu ServiceModel `propagateActivity` ustawić atrybutu `true`.  
  
## <a name="see-also"></a>Zobacz też  
 [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Administracja i diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [Instrukcje: Tworzenie i inicjowanie obiektów nasłuchujących śledzenie](http://go.microsoft.com/fwlink/?LinkId=94648)  
 [Tworzenie niestandardowego elementu TraceListener](http://go.microsoft.com/fwlink/?LinkId=96239)
