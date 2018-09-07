---
title: Konfigurowanie rejestrowania komunikatów
ms.date: 03/30/2017
helpviewer_keywords:
- message logging [WCF]
ms.assetid: 0ff4c857-8f09-4b85-9dc0-89084706e4c9
ms.openlocfilehash: 80d852dd08e935d4c06e9b6d2e52b0a075849ef5
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44085158"
---
# <a name="configuring-message-logging"></a>Konfigurowanie rejestrowania komunikatów
W tym temacie opisano, jak można skonfigurować rejestrowanie komunikatów dla różnych scenariuszy.  
  
## <a name="enabling-message-logging"></a>Włączanie rejestrowania komunikatów  
 Windows Communication Foundation (WCF) nie rejestruje komunikaty domyślnie. Aby włączyć rejestrowanie komunikatów, należy dodać odbiornik śledzenia do `System.ServiceModel.MessageLogging` Śledź źródło i ustaw atrybuty dla `<messagelogging>` elementu w pliku konfiguracji.  
  
 Poniższy przykład pokazuje, jak włączyć rejestrowanie i określić dodatkowe opcje.  
  
```xml  
<system.diagnostics>  
  <sources>  
    <source name="System.ServiceModel.MessageLogging">  
      <listeners>  
         <add name="messages"  
              type="System.Diagnostics.XmlWriterTraceListener"  
              initializeData="c:\logs\messages.svclog" />  
        </listeners>  
    </source>  
  </sources>  
</system.diagnostics>  
  
<system.serviceModel>  
  <diagnostics>  
    <messageLogging   
         logEntireMessage="true"   
         logMalformedMessages="false"  
         logMessagesAtServiceLevel="true"   
         logMessagesAtTransportLevel="false"  
         maxMessagesToLog="3000"  
         maxSizeOfMessageToLog="2000"/>  
  </diagnostics>  
</system.serviceModel>  
```  
  
 Aby uzyskać więcej informacji na temat ustawień rejestrowania wiadomości zobacz [zalecane ustawienia śledzenia i rejestrowania komunikatów](../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md).  
  
 Możesz użyć `add` Aby określić nazwę i typ odbiornik, którego chcesz użyć. W przykładzie konfiguracji, odbiornik o nazwie "komunikatów" i dodaje standardowy odbiornik śledzenia .NET Framework (`System.Diagnostics.XmlWriterTraceListener`) jako typ, który ma być używany. Jeśli używasz `System.Diagnostics.XmlWriterTraceListener`, należy określić dane wyjściowe lokalizację i nazwę pliku, które znajdują się w pliku konfiguracji. Jest to realizowane przez ustawienie `initializeData` do nazwy pliku dziennika. W przeciwnym razie system zgłasza wyjątek. Możesz również wdrożyć niestandardowy odbiornik, który emituje dzienniki, aby plik domyślny.  
  
> [!NOTE]
>  Ponieważ rejestrowanie komunikatów uzyskuje dostęp do miejsca na dysku, należy ograniczyć liczbę wiadomości, które są zapisywane na dysku dla określonej usługi. Po osiągnięciu limitu wiadomości śledzenia na poziomie informacje są generowane i Zatrzymaj wszystkie działania rejestrowania komunikatu.  
  
 Poziom rejestrowania, a także dodatkowe opcje zostały omówione w sekcji Opcje i poziomu rejestrowania.  
  
 `switchValue` Atrybutu `source` jest prawidłowy tylko dla śledzenia. Jeśli określisz `switchValue` atrybutu dla `System.ServiceModel.MessageLogging` źródła śledzenia jest zgodna, nie ma wpływu.  
  
```xml  
<source name="System.ServiceModel.MessageLogging" switchValue="Verbose">  
```  
  
 Jeśli chcesz wyłączyć źródła śledzenia, należy użyć `logMessagesAtServiceLevel`, `logMalformedMessages`, i `logMessagesAtTransportLevel` atrybuty `messageLogging` elementu zamiast tego. Należy ustawić te atrybuty `false`. Można to zrobić za pomocą pliku konfiguracji w poprzednim przykładzie kodu poprzez interfejs użytkownika edytora konfiguracji, lub przy użyciu usługi WMI. Aby uzyskać więcej informacji na temat narzędzie edytora konfiguracji zobacz [narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md). Aby uzyskać więcej informacji na temat usługi WMI, zobacz [przy użyciu Instrumentacji zarządzania Windows Diagnostics](../../../../docs/framework/wcf/diagnostics/wmi/index.md).  
  
## <a name="logging-levels-and-options"></a>Opcje i poziomy rejestrowania  
 Komunikaty przychodzące rejestrowanie odbywa się natychmiast po zakończeniu sformułowany komunikat bezpośrednio przed wykonaniem komunikat pobiera kodu użytkownika na poziomie usługi, a po wykryciu źle sformułowane komunikaty.  
  
 Komunikaty wychodzące rejestrowanie odbywa się natychmiast po zakończeniu wiadomość opuszcza kod użytkownika i natychmiast, zanim wiadomość jest wysyłana na łączu.  
  
 Usługi WCF rejestruje komunikaty w dwóch różnych poziomach, usług i mechanizm transportu. Źle sformułowane komunikaty są także rejestrowane. Trzy kategorie są niezależne od siebie nawzajem i można ją aktywować niezależnie w konfiguracji.  
  
 Możesz kontrolować poziom rejestrowania, ustawiając `logMessagesAtServiceLevel`, `logMalformedMessages`, i `logMessagesAtTransportLevel` atrybuty `messageLogging` elementu.  
  
### <a name="service-level"></a>Poziom usług  
 Komunikaty zarejestrowane w tej warstwie zamiar wprowadzić (na odbieranie) lub pozostaw (na wysłanie) kod użytkownika. Jeśli zostały zdefiniowane filtry, będą rejestrowane tylko komunikaty, które pasują do filtrów. W przeciwnym razie są rejestrowane wszystkie komunikaty na poziomie usługi. Komunikaty infrastruktury (transakcje, kanał elementu równorzędnego i zabezpieczeń) również są rejestrowane na tym poziomie, z wyjątkiem komunikaty niezawodnej obsługi komunikatów. W strumieniu wiadomości tylko nagłówki są rejestrowane. Ponadto zabezpieczonych wiadomości są rejestrowane odszyfrować na tym poziomie.  
  
### <a name="transport-level"></a>Poziom transportu  
 Komunikaty zarejestrowane w tej warstwie jest gotowe do być szyfrowanym lub dekodowanym na lub po transportu w sieci. Jeśli zostały zdefiniowane filtry, będą rejestrowane tylko komunikaty, które pasują do filtrów. W przeciwnym razie są rejestrowane wszystkie komunikaty w warstwie transportowej. Wszystkie komunikaty infrastruktury są rejestrowane w tej warstwie, w tym komunikaty niezawodnej obsługi komunikatów. W strumieniu wiadomości tylko nagłówki są rejestrowane. Ponadto zabezpieczonych wiadomości są rejestrowane jako zaszyfrowane na tym poziomie, chyba że bezpiecznym transportem, takie jak jest używany protokół HTTPS.  
  
### <a name="malformed-level"></a>Poziom źle sformułowany  
 Źle sformułowane komunikaty są komunikaty, które zostały odrzucone przez stos WCF na każdym etapie cyklu przetwarzania. Źle sformułowane komunikaty są rejestrowane jako-to: szyfrowane, gdy są one tak, za pomocą XML nie są poprawne i tak dalej. `maxSizeOfMessageToLog` zdefiniowany rozmiar komunikatu, które mają być rejestrowane jako typu CDATA. Domyślnie `maxSizeOfMessageToLog` jest równa 256 KB. Więcej informacji na temat tego atrybutu znajduje się w sekcji inne opcje.  
  
### <a name="other-options"></a>Inne opcje  
 Oprócz poziomów rejestrowania użytkownik może określić następujące opcje:  
  
-   Zaloguj się cały komunikat (`logEntireMessage` atrybutu): Ta wartość określa, czy cały komunikat (nagłówek i treść wiadomości) jest rejestrowane. Wartość domyślna to `false`, co oznacza, że zostanie zarejestrowany tylko nagłówek. To ustawienie ma wpływ na usług i mechanizm transportu poziomów rejestrowania komunikatów...  
  
-   Maksymalna liczba komunikatów do zarejestrowania (`maxMessagesToLog` atrybutu): Ta wartość określa maksymalną liczbę wiadomości rejestrowaną w dzienniku. Wszystkie komunikaty (usługa transportu i źle sformułowane komunikaty) liczy się do tego przydziału. Po osiągnięciu limitu przydziału śledzenia jest emitowane, a nie dodatkowe komunikat jest rejestrowany. Wartość domyślna to 10000.  
  
-   Maksymalny rozmiar komunikatu do dziennika (`maxSizeOfMessageToLog` atrybutu): Ta wartość określa maksymalny rozmiar wiadomości rejestrowaną w dzienniku w bajtach. Komunikaty, które przekraczają limit rozmiaru nie jest zalogowany, a żadnych innych czynności jest wykonywane dla tego komunikatu. To ustawienie ma wpływ na wszystkie poziomy śledzenia. Jeśli ServiceModel śledzenia jest włączona, poziom śledzenia ostrzeżenie jest emitowane na pierwszy punkt rejestrowania (ServiceModelSend * lub TransportReceive) do powiadamiania użytkownika. Wartością domyślną dla transportu i na poziomie komunikatów usługi to 256 KB, wartością domyślną dla źle sformułowane komunikaty jest 4K.  
  
    > [!CAUTION]
    >  Rozmiar komunikatu, który jest kolumną obliczaną, aby porównać `maxSizeOfMessageToLog` jest rozmiar wiadomości w pamięci, przed serializacji. Ten rozmiar może się różnić od rzeczywistej długości ciąg komunikatu który jest rejestrowany, a w wielu przypadkach jest większy niż rzeczywisty rozmiar. W rezultacie komunikaty nie mogą być rejestrowane. Użytkownik może uwzględnić, określając ten fakt `maxSizeOfMessageToLog` atrybut był większy niż rozmiar oczekiwanego komunikatu w 10%. Ponadto, jeśli wadliwe komunikaty są rejestrowane, rzeczywista ilość miejsca na dysku wykorzystywane przez dzienników komunikatów może być maksymalnie 5 razy większy niż wartość określoną przez `maxSizeOfMessageToLog`.  
  
 Jeśli odbiornik śledzenia, nie jest zdefiniowana w pliku konfiguracji, Brak rejestrowania danych wyjściowych jest generowany niezależnie od określonego poziomu rejestrowania.  
  
 Opcje rejestrowania komunikatów, takie jak atrybuty opisane w tej sekcji można zmienić w czasie wykonywania za pomocą Instrumentacji zarządzania Windows (WMI). Można to zrobić, uzyskując dostęp do [AppDomainInfo](../../../../docs/framework/wcf/diagnostics/wmi/appdomaininfo.md) wystąpienia, który uwidacznia następujące właściwości logiczne: `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`, i `LogMalformedMessages`. W związku z tym, jeśli Konfigurowanie odbiornika śledzenia dla rejestrowania komunikatów, ale ustawiony korzystać z tych opcji do `false` w konfiguracji można później zmienić ich `true` gdy aplikacja jest uruchomiona. Umożliwia to efektywne rejestrowanie komunikatów w czasie wykonywania. Podobnie jeśli włączysz rejestrowanie w pliku konfiguracyjnym komunikatów, można ją wyłączyć w czasie wykonywania przy użyciu usługi WMI. Aby uzyskać więcej informacji, zobacz [przy użyciu Instrumentacji zarządzania Windows Diagnostics](../../../../docs/framework/wcf/diagnostics/wmi/index.md).  
  
 `source` Pola w dzienniku komunikatów Określa, w którym kontekście jest rejestrowany: podczas wysyłania/odbierania komunikat żądania typu żądanie odpowiedź lub sposób 1 żądanie, w warstwie usług opartych na modelu lub transportu lub w przypadku uszkodzony komunikat.  
  
 Źle sformułowane komunikaty `source` jest równa `Malformed`. W przeciwnym razie źródło ma następujące wartości, na podstawie kontekstu.  
  
 Aby uzyskać żądanie/nietypizowana odpowiedź  
  
||Wyślij żądanie|Żądania odbioru|Wyślij odpowiedź|Odebrać odpowiedzi|  
|-|------------------|---------------------|----------------|-------------------|  
|Warstwy modelu usług|Usługa<br /><br /> Poziom<br /><br /> Wyślij<br /><br /> Żądanie|Usługa<br /><br /> Poziom<br /><br /> Odbieranie<br /><br /> Żądanie|Usługa<br /><br /> Poziom<br /><br /> Wyślij<br /><br /> Odpowiedz|Usługa<br /><br /> Poziom<br /><br /> Odbieranie<br /><br /> Odpowiedz|  
|Warstwa transportu|Transportu<br /><br /> Wyślij|Transportu<br /><br /> Odbieranie|Transportu<br /><br /> Wyślij|Transportu<br /><br /> Odbieranie|  
  
 Dla żądania jednokierunkowego  
  
||Wyślij żądanie|Żądania odbioru|  
|-|------------------|---------------------|  
|Warstwy modelu usług|Usługa<br /><br /> Poziom<br /><br /> Wyślij<br /><br /> Datagram|Usługa<br /><br /> Poziom<br /><br /> Odbieranie<br /><br /> Datagram|  
|Warstwa transportu|Transportu<br /><br /> Wyślij|Transportu<br /><br /> Odbieranie|  
  
## <a name="message-filters"></a>Filtry komunikatów  
 Filtry komunikatów są zdefiniowane w `messageLogging` elementu konfiguracji `diagnostics` sekcji konfiguracji. Są one stosowane na poziomie usług i mechanizm transportu. Po zdefiniowaniu co najmniej jeden filtr tylko komunikatów spełniających co najmniej jeden z filtrów są rejestrowane. Jeśli nie zdefiniowano żadnego filtru, wszystkie komunikaty przechodzi przez.  
  
 Filtry obsługuje pełnej składni XPath i są stosowane w kolejności, w jakiej znajdują się w pliku konfiguracji. Nieprawidłowy filtr powoduje wyjątek konfiguracji.  
  
 Filtry zapewniają również funkcję bezpieczeństwa przy użyciu `nodeQuota` atrybut, który ogranicza maksymalną liczbę węzłów w modelu DOM języka XPath, które mogą być sprawdzane w celu są zgodne z filtrem.  
  
 Poniższy przykład pokazuje, jak skonfigurować filtr tej wiadomości tylko rekordy, które mają sekcji nagłówka SOAP.  
  
```xml  
<messageLogging logEntireMessage="true"  
    logMalformedMessages="true"   
    logMessagesAtServiceLevel="true"  
    logMessagesAtTransportLevel="true"  
    maxMessagesToLog="420">  
    <filters>  
        <add nodeQuota="10" xmlns:soap="http://www.w3.org/2003/05/soap-envelope">  
                 /soap:Envelope/soap:Header  
        </add>  
     </filters>  
</messageLogging>  
```  
  
 Nie można zastosować filtry do treści wiadomości. Filtry, które próbują manipulowania treści wiadomości są usuwane z listy filtrów. Zdarzenia są emitowane również wskazującą to. Na przykład następujący filtr zostaną usunięte z tabeli filtru.  
  
```xml  
<add xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">/s:Envelope/s:Body[contains(text(), "Hello")]</add>  
```  
  
## <a name="configuring-a-custom-listener"></a>Konfigurowanie odbiornika niestandardowe  
 Odbiornik niestandardowe można również skonfigurować dodatkowe opcje. Odbiornik niestandardowego może być przydatne w filtrowania elementów dane osobowe specyficzne dla aplikacji z komunikatów przed zalogowaniem. W poniższym przykładzie pokazano konfigurację niestandardowej odbiornika.  
  
```xml  
<system.diagnostics>  
   <sources>  
     <source name="System.ServiceModel.MessageLogging">  
           <listeners>  
             <add name="MyListener"   
                    type="YourCustomListener"  
                    initializeData="c:\logs\messages.svclog"  
                    maxDiskSpace="1000"/>  
           </listeners>  
     </source>  
   </sources>  
</system.diagnostics>  
```  
  
 Należy pamiętać, że `type` atrybutu powinna być równa kwalifikowaną nazwę typu.  
  
## <a name="see-also"></a>Zobacz też  
 [\<messageLogging >](../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)  
 [Rejestrowanie komunikatów](../../../../docs/framework/wcf/diagnostics/message-logging.md)  
 [Zalecane ustawienia śledzenia i rejestrowania komunikatów](../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md)
