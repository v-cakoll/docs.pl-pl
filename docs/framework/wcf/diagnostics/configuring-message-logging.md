---
title: Konfigurowanie rejestrowania komunikatów
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- message logging [WCF]
ms.assetid: 0ff4c857-8f09-4b85-9dc0-89084706e4c9
caps.latest.revision: 40
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6e2d45e7b8769ee525835ad3dc50262a03a5a7b6
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="configuring-message-logging"></a>Konfigurowanie rejestrowania komunikatów
W tym temacie opisano, jak można skonfigurować rejestrowania komunikatów dla różnych scenariuszy.  
  
## <a name="enabling-message-logging"></a>Włączanie rejestrowania komunikatów  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] rejestruje komunikaty domyślnie. Aby włączyć rejestrowanie komunikatów, należy dodać odbiornik śledzenia do `System.ServiceModel.MessageLogging` źródło śledzenia i ustawić atrybuty `<messagelogging>` w pliku konfiguracji.  
  
 Poniższy przykład pokazuje, jak włączyć rejestrowanie i określ opcje dodatkowe.  
  
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
  
 Aby uzyskać więcej informacji o ustawieniach rejestrowania komunikatów, zobacz [zalecane ustawienia śledzenia i rejestrowania komunikatów](../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md).  
  
 Można użyć `add` Aby określić nazwę i typ odbiornika, którego chcesz użyć. W konfiguracji przykład odbiornik o nazwie "wiadomości" i dodaje standardowe nasłuchującego śledzenia .NET Framework (`System.Diagnostics.XmlWriterTraceListener`) jako typ do użycia. Jeśli używasz `System.Diagnostics.XmlWriterTraceListener`, należy określić dane wyjściowe lokalizację i nazwę pliku w pliku konfiguracji. Odbywa się przez ustawienie `initializeData` do nazwy pliku dziennika. W przeciwnym razie system zgłasza wyjątek. Można też wdrożyć niestandardowe odbiornik, który emituje dzienniki, aby plik domyślny.  
  
> [!NOTE]
>  Ponieważ rejestrowanie komunikatów uzyskuje dostęp do miejsca na dysku, należy ograniczyć liczbę wiadomości, które są zapisywane na dysku dla określonej usługi. Po osiągnięciu limitu wiadomości śledzenia na poziomie informacji jest tworzony, i Zatrzymaj wszystkie działania rejestrowania komunikatów.  
  
 Poziom rejestrowania, a także dodatkowe opcje, omówiono w sekcji Opcje i poziom rejestrowania.  
  
 `switchValue` Atrybutu `source` jest prawidłowy tylko dla śledzenia. Jeśli określisz `switchValue` atrybutu dla `System.ServiceModel.MessageLogging` źródło śladu jako zgodna, nie działa.  
  
```xml  
<source name="System.ServiceModel.MessageLogging" switchValue="Verbose">  
```  
  
 Jeśli chcesz wyłączyć źródła śledzenia, należy użyć `logMessagesAtServiceLevel`, `logMalformedMessages`, i `logMessagesAtTransportLevel` atrybuty `messageLogging` elementu zamiast tego. Należy ustawić te atrybuty `false`. Można to zrobić przy użyciu pliku konfiguracji, w poprzednim przykładzie kodu za pomocą interfejsu użytkownika edytora konfiguracji interfejsu, lub za pomocą usługi WMI. Aby uzyskać więcej informacji o narzędziu edytora konfiguracji, zobacz [narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md). Aby uzyskać więcej informacji dotyczących usługi WMI, zobacz [przy użyciu Instrumentacji zarządzania Windows dla diagnostyki](../../../../docs/framework/wcf/diagnostics/wmi/index.md).  
  
## <a name="logging-levels-and-options"></a>Opcje i poziomy rejestrowania  
 Dla komunikatów przychodzących rejestrowanie odbywa się natychmiast po sformułowany komunikat bezpośrednio przed pobiera komunikat, aby kod użytkownika na poziomie usługi i po wykryciu wadliwe komunikaty.  
  
 Dla komunikatów wychodzących rejestrowanie odbywa się natychmiast po wiadomość opuszcza kod użytkownika i bezpośrednio przed przejdzie do przesyłania wiadomości.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] rejestruje komunikaty w dwóch różnych poziomach, usług i mechanizm transportu. Wadliwe komunikaty są także rejestrowane. Trzy kategorie są niezależne od siebie i można aktywować niezależnie w konfiguracji.  
  
 Poziom rejestrowania można kontrolować przez ustawienie `logMessagesAtServiceLevel`, `logMalformedMessages`, i `logMessagesAtTransportLevel` atrybuty `messageLogging` elementu.  
  
### <a name="service-level"></a>Poziom usług  
 Komunikaty zarejestrowane w tej warstwie zamiar wprowadź (na odbieranie) lub pozostaw (przy wysyłaniu) kodu użytkownika. Jeśli zostały określone filtry, są rejestrowane tylko komunikatów spełniających filtrów. W przeciwnym razie są rejestrowane wszystkie wiadomości na poziomie usługi. Komunikaty infrastruktury (transakcje, kanałów równorzędnych i zabezpieczeń) również są rejestrowane na tym poziomie, z wyjątkiem komunikaty niezawodnej obsługi komunikatów. Na strumienia wiadomości tylko nagłówki są rejestrowane. Ponadto zabezpieczonych wiadomości są rejestrowane odszyfrować na tym poziomie.  
  
### <a name="transport-level"></a>Poziom transportu  
 Komunikaty zarejestrowane w tej warstwie jest gotowe do można lub dekodowanym na lub po transportu w sieci. Jeśli zostały określone filtry, są rejestrowane tylko komunikatów spełniających filtrów. W przeciwnym razie są rejestrowane wszystkie komunikaty w warstwie transportowej. Wszystkie komunikaty infrastruktury są rejestrowane w tej warstwie, w tym komunikaty niezawodnej obsługi komunikatów. Na strumienia wiadomości tylko nagłówki są rejestrowane. Ponadto zabezpieczonych wiadomości są rejestrowane szyfrowane na tym poziomie, chyba że bezpiecznego transportu, takie jak jest używany protokół HTTPS.  
  
### <a name="malformed-level"></a>Poziom źle sformułowany  
 Wadliwe komunikaty są komunikaty, które zostały odrzucone prze [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] stosu na każdym etapie przetwarzania. Wadliwe komunikaty są rejestrowane jako — jest: szyfrowane, gdy są one tak, z XML bez odpowiedniego i tak dalej. `maxSizeOfMessageToLog` rozmiar komunikatu, który ma zostać zarejestrowany jako typu CDATA zdefiniowany. Domyślnie `maxSizeOfMessageToLog` jest równa 256 KB. Aby uzyskać więcej informacji na temat tego atrybutu zobacz sekcję inne opcje.  
  
### <a name="other-options"></a>Inne opcje  
 Oprócz poziomów rejestrowania użytkownika można określić następujące opcje:  
  
-   Zaloguj się cały komunikat (`logEntireMessage` atrybut): Ta wartość określa, czy cały komunikat (nagłówek i treść wiadomości) jest zarejestrowany. Wartość domyślna to `false`, co oznacza, że jest rejestrowane tylko nagłówek. To ustawienie ma wpływ usług i mechanizm transportu poziomy rejestrowania komunikatów.  
  
-   Maksymalna liczba komunikatów do zarejestrowania (`maxMessagesToLog` atrybut): Ta wartość określa maksymalną liczbę komunikatów do zarejestrowania. Wszystkie komunikaty (usługa transportu i wadliwe komunikaty) są liczone kierunku ten limit przydziału. Po osiągnięciu limitu przydziału jest emitowany śledzenia i nie dodatkowe jest rejestrowany. Wartość domyślna to 10 000.  
  
-   Maksymalny rozmiar komunikatu do dziennika (`maxSizeOfMessageToLog` atrybut): Ta wartość określa maksymalny rozmiar wiadomości dziennika w bajtach. Komunikaty, które przekraczają limit rozmiaru nie jest zalogowany, a żadnych innych czynności jest wykonywane dla tej wiadomości. To ustawienie ma wpływ na wszystkie poziomy śledzenia. Jeśli śledzenie ServiceModel znajduje się na ostrzeżenie poziomu śledzenia jest emitowany przy pierwszym rejestrowania (ServiceModelSend * lub TransportReceive) do powiadamiania użytkownika. Wartością domyślną dla transportu i na poziomie komunikatów usługi jest 256 KB, gdy wartością domyślną dla źle sformułowane wiadomości jest 4K.  
  
    > [!CAUTION]
    >  Rozmiar wiadomości, która jest kolumną obliczaną, aby porównać `maxSizeOfMessageToLog` rozmiar wiadomości w pamięci przed serializacji. Ten rozmiar może się różnić od rzeczywista długość ciągu komunikat, który jest rejestrowany i w wielu przypadkach jest większy niż rzeczywisty rozmiar. W związku z tym komunikaty nie mogą być rejestrowane. Można uwzględnić ten fakt, określając `maxSizeOfMessageToLog` atrybutu, aby była większa niż rozmiar wiadomości oczekiwano 10%. Ponadto, czy wadliwe komunikaty są rejestrowane, rzeczywista ilość miejsca na dysku wykorzystywane przez dzienniki komunikat może mieć maksymalnie 5 razy rozmiar wartość określoną przez `maxSizeOfMessageToLog`.  
  
 Jeśli nie nasłuchującego śledzenia jest zdefiniowany w pliku konfiguracji, niezależnie od określonego poziomu rejestrowania są generowane nie dane wyjściowe rejestrowania.  
  
 Opcje rejestrowania komunikatów, takie jak atrybuty opisane w tej sekcji można zmienić w czasie wykonywania za pomocą Instrumentacji zarządzania Windows (WMI). Można to zrobić po zalogowaniu się do [AppDomainInfo](../../../../docs/framework/wcf/diagnostics/wmi/appdomaininfo.md) wystąpienia, która udostępnia te właściwości, wartość logiczna: `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`, i `LogMalformedMessages`. W związku z tym jeśli skonfiguruj odbiornik śledzenia dla rejestrowanie komunikatów, ale ustawiona korzystać z tych opcji do `false` w konfiguracji można później zmienić ich `true` gdy aplikacja jest uruchomiona. Umożliwia to efektywne rejestrowanie komunikatów w czasie wykonywania. Podobnie po włączeniu rejestrowania w pliku konfiguracyjnym komunikatów, można ją wyłączyć w czasie wykonywania za pomocą usługi WMI. Aby uzyskać więcej informacji, zobacz [przy użyciu Instrumentacji zarządzania Windows dla diagnostyki](../../../../docs/framework/wcf/diagnostics/wmi/index.md).  
  
 `source` Pola w dzienniku komunikatów Określa, w którego kontekście jest rejestrowany: podczas wysyłania/odbierania komunikatu żądania, żądanie odpowiedź lub sposób 1 żądania, w przypadku warstwy transportu i modelu usługi lub w przypadku uszkodzony komunikat.  
  
 Źle sformułowane wiadomości `source` jest równa `Malformed`. W przeciwnym razie źródło zawiera następujące wartości na podstawie kontekstu.  
  
 Dla żądania i odpowiedzi  
  
||Wyślij żądanie|Limit czasu żądania odbioru|Wysłanie odpowiedzi|Odebrać odpowiedzi|  
|-|------------------|---------------------|----------------|-------------------|  
|Warstwy modelu usług|Usługa<br /><br /> Poziom<br /><br /> Wyślij<br /><br /> Żądanie|Usługa<br /><br /> Poziom<br /><br /> Odbieranie<br /><br /> Żądanie|Usługa<br /><br /> Poziom<br /><br /> Wyślij<br /><br /> odpowiedź|Usługa<br /><br /> Poziom<br /><br /> Odbieranie<br /><br /> odpowiedź|  
|Warstwa transportu|Transportu<br /><br /> Wyślij|Transportu<br /><br /> Odbieranie|Transportu<br /><br /> Wyślij|Transportu<br /><br /> Odbieranie|  
  
 Dla żądania jednokierunkowe  
  
||Wyślij żądanie|Limit czasu żądania odbioru|  
|-|------------------|---------------------|  
|Warstwy modelu usług|Usługa<br /><br /> Poziom<br /><br /> Wyślij<br /><br /> Datagram|Usługa<br /><br /> Poziom<br /><br /> Odbieranie<br /><br /> Datagram|  
|Warstwa transportu|Transportu<br /><br /> Wyślij|Transportu<br /><br /> Odbieranie|  
  
## <a name="message-filters"></a>Filtry komunikatów  
 Filtry komunikatów są zdefiniowane w `messageLogging` elementu konfiguracji `diagnostics` sekcji konfiguracji. Są one stosowane na poziomie usług i mechanizm transportu. Po zdefiniowaniu co najmniej jeden filtr są rejestrowane tylko komunikatów spełniających co najmniej jeden z filtrów. Jeśli nie jest definiować filtru, wszystkie komunikaty przekazywane.  
  
 Filtry obsługuje pełnej składni języka XPath i są stosowane w kolejności, w jakiej znajdują się w pliku konfiguracji. Nieprawidłowy filtr powoduje wyjątek konfiguracji.  
  
 Filtry również udostępniać funkcję bezpieczeństwa przy użyciu `nodeQuota` atrybut, który ogranicza maksymalną liczbę węzłów w modelu DOM XPath, które można zbadać zgodny z filtrem.  
  
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
  
 Nie można zastosować filtry do treści wiadomości. Filtry, które mają na celu manipulowania treści wiadomości są usuwane z listy filtrów. Zdarzenie jest również emitowane wskazującą to. Na przykład następujący filtr zostaną usunięte z tabeli filtrów.  
  
```xml  
<add xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">/s:Envelope/s:Body[contains(text(), "Hello")]</add>  
```  
  
## <a name="configuring-a-custom-listener"></a>Konfigurowanie niestandardowych odbiornika  
 Odbiornik niestandardowej można także skonfigurować dodatkowe opcje. Niestandardowe odbiornika mogą być przydatne w filtrowania elementów dane osobowe specyficzne dla aplikacji z wiadomości przed zalogowaniem. W poniższym przykładzie pokazano konfiguracji odbiornika niestandardowych.  
  
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
  
 Należy pamiętać, że `type` atrybut powinien mieć ustawioną nazwę kwalifikowaną zestawu typu.  
  
## <a name="see-also"></a>Zobacz też  
 [\<messageLogging >](../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)  
 [Rejestrowanie komunikatów](../../../../docs/framework/wcf/diagnostics/message-logging.md)  
 [Zalecane ustawienia śledzenia i rejestrowania komunikatów](../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md)
