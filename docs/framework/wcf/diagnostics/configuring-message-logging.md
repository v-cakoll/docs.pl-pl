---
title: Konfigurowanie rejestrowania komunikatów
ms.date: 03/30/2017
helpviewer_keywords:
- message logging [WCF]
ms.assetid: 0ff4c857-8f09-4b85-9dc0-89084706e4c9
ms.openlocfilehash: db538634dccf22fb954ccf0827909e5cf3563f77
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798160"
---
# <a name="configuring-message-logging"></a>Konfigurowanie rejestrowania komunikatów

W tym temacie opisano, jak można skonfigurować rejestrowanie komunikatów dla różnych scenariuszy.

## <a name="enabling-message-logging"></a>Włączanie rejestrowania komunikatów

Windows Communication Foundation (WCF) nie rejestruje komunikatów domyślnie. Aby uaktywnić rejestrowanie komunikatów, należy dodać odbiornik śledzenia do `System.ServiceModel.MessageLogging` źródła śledzenia i ustawić atrybuty `<messagelogging>` dla elementu w pliku konfiguracji.

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

Aby uzyskać więcej informacji na temat ustawień rejestrowania komunikatów, zobacz [zalecane ustawienia śledzenia i rejestrowania komunikatów](./tracing/recommended-settings-for-tracing-and-message-logging.md).

Możesz użyć `add` , aby określić nazwę i typ odbiornika, którego chcesz użyć. W przykładowej konfiguracji odbiornik ma nazwę "Messages" i dodaje odbiornik standardowego .NET Framework śledzenia (`System.Diagnostics.XmlWriterTraceListener`) jako typ do użycia. Jeśli używasz `System.Diagnostics.XmlWriterTraceListener`, musisz określić lokalizację i nazwę pliku wyjściowego w pliku konfiguracji. Można to zrobić, ustawiając `initializeData` nazwę pliku dziennika. W przeciwnym razie system zgłasza wyjątek. Możesz również zaimplementować niestandardowy odbiornik, który emituje dzienniki do pliku domyślnego.

> [!NOTE]
> Ponieważ rejestrowanie komunikatów uzyskuje dostęp do miejsca na dysku, należy ograniczyć liczbę wiadomości, które są zapisywane na dysku dla określonej usługi. Po osiągnięciu limitu komunikatów zostaje wygenerowany ślad na poziomie informacji i wszystkie działania związane z rejestrowaniem komunikatów zostaną zatrzymane.

Poziom rejestrowania, a także opcje dodatkowe są omówione w sekcji poziom rejestrowania i opcje.

`switchValue` Atrybut elementu`source` jest prawidłowy tylko dla śledzenia. Jeśli określisz `switchValue` atrybut `System.ServiceModel.MessageLogging` dla źródła śledzenia w następujący sposób, nie ma to żadnego efektu.

```xml
<source name="System.ServiceModel.MessageLogging" switchValue="Verbose">
```

Jeśli chcesz wyłączyć źródło śledzenia, zamiast tego `logMessagesAtServiceLevel`należy użyć atrybutów `messageLogging` , `logMalformedMessages`i `logMessagesAtTransportLevel` . Należy ustawić wszystkie te atrybuty na `false`. Można to zrobić za pomocą pliku konfiguracji w poprzednim przykładzie kodu, za pomocą interfejsu użytkownika edytora konfiguracji lub przy użyciu usługi WMI. Aby uzyskać więcej informacji o narzędziu Edytor konfiguracji, zobacz [Narzędzie edytora konfiguracji (SvcConfigEditor. exe)](../configuration-editor-tool-svcconfigeditor-exe.md). Aby uzyskać więcej informacji na temat usługi WMI, zobacz [używanie Instrumentacja zarządzania Windows do diagnostyki](./wmi/index.md).

## <a name="logging-levels-and-options"></a>Poziomy rejestrowania i opcje

W przypadku wiadomości przychodzących rejestrowanie odbywa się natychmiast po utworzeniu komunikatu, bezpośrednio przed wprowadzeniem komunikatu do kodu użytkownika na poziomie usługi i po wykryciu źle sformułowanych komunikatów.

W przypadku wiadomości wychodzących rejestrowanie odbywa się natychmiast po opuszczeniu przez komunikat kodu użytkownika i natychmiast przed wysłaniem komunikatu do sieci.

Usługa WCF rejestruje komunikaty na dwóch różnych poziomach, usługach i transportach. Rejestrowane są również źle sformułowane komunikaty. Trzy kategorie są niezależne od siebie i można je aktywować osobno w konfiguracji.

Poziom rejestrowania można kontrolować `logMessagesAtServiceLevel`przez ustawienie atrybutów `messageLogging` elementu, `logMalformedMessages`, i `logMessagesAtTransportLevel` .

### <a name="service-level"></a>Poziom usług

Komunikaty zarejestrowane w tej warstwie mają na celu wprowadzenie (przy odbiorze) lub pozostawienie (przy wysyłaniu) kodu użytkownika. Jeśli filtry zostały zdefiniowane, rejestrowane są tylko komunikaty zgodne z filtrami. W przeciwnym razie zostaną zarejestrowane wszystkie komunikaty na poziomie usługi. Komunikaty infrastruktury (transakcje, kanał równorzędny i zabezpieczenia) są również rejestrowane na tym poziomie, z wyjątkiem komunikatów o niezawodnej komunikacji. W przypadku komunikatów przesyłanych strumieniowo rejestrowane są tylko nagłówki. Ponadto na tym poziomie są zaszyfrowane bezpieczne komunikaty.

### <a name="transport-level"></a>Poziom transportu

Komunikaty zarejestrowane w tej warstwie są gotowe do zakodowania lub dekodowania dla lub po transporcie w sieci. Jeśli filtry zostały zdefiniowane, rejestrowane są tylko komunikaty zgodne z filtrami. W przeciwnym razie wszystkie komunikaty w warstwie transportowej są rejestrowane. Wszystkie komunikaty infrastruktury są rejestrowane w tej warstwie, w tym komunikaty niezawodnej obsługi komunikatów. W przypadku komunikatów przesyłanych strumieniowo rejestrowane są tylko nagłówki. Ponadto bezpieczne wiadomości są rejestrowane jako zaszyfrowane na tym poziomie, z wyjątkiem tego, czy jest używany bezpieczny transport, taki jak HTTPS.

### <a name="malformed-level"></a>Źle skonstruowany poziom

Źle sformułowane komunikaty to komunikaty odrzucone przez stos WCF na dowolnym etapie przetwarzania. Źle sformułowane komunikaty są rejestrowane jako: zaszyfrowane, jeśli tak, z nieprawidłowym kodem XML i tak dalej. `maxSizeOfMessageToLog`zdefiniowano rozmiar wiadomości, która ma zostać zarejestrowana jako CDATA. Domyślnie `maxSizeOfMessageToLog` jest równa 256 k. Więcej informacji o tym atrybucie zawiera sekcja inne opcje.

### <a name="other-options"></a>Inne opcje

Oprócz poziomów rejestrowania użytkownik może określić następujące opcje:

- Rejestruj cały komunikat (`logEntireMessage` atrybut): Ta wartość określa, czy cały komunikat (nagłówek i treść wiadomości) jest rejestrowany. Wartość domyślna to `false`, co oznacza, że tylko nagłówek jest rejestrowany. To ustawienie ma wpływ na poziomy rejestrowania komunikatów usługi i transportu..

- Maksymalna liczba komunikatów do rejestrowania`maxMessagesToLog` (atrybut): Ta wartość określa maksymalną liczbę komunikatów do zarejestrowania. Wszystkie komunikaty (usługa, transport i źle sformułowane komunikaty) są zliczane do tego przydziału. Po osiągnięciu limitu przydziału ślad jest emitowany i nie jest rejestrowany żaden dodatkowy komunikat. Wartość domyślna to 10000.

- Maksymalny rozmiar komunikatu do zarejestrowania (`maxSizeOfMessageToLog` atrybut): Ta wartość określa maksymalny rozmiar komunikatów, które mają być rejestrowane w bajtach. Komunikaty przekraczające limit rozmiaru nie są rejestrowane i żadne inne działanie nie jest wykonywane dla tego komunikatu. To ustawienie ma wpływ na wszystkie poziomy śledzenia. Jeśli śledzenie ServiceModel jest włączone, ślad poziomu ostrzeżeń jest emitowany w pierwszym punkcie rejestrowania (ServiceModelSend * lub TransportReceive) w celu powiadomienia użytkownika. Wartość domyślna dla komunikatów poziomu usługi i na poziomie transportu to 256 K, podczas gdy wartość domyślna dla źle sformułowanych komunikatów to 4K.

  > [!CAUTION]
  > Rozmiar komunikatu, który jest obliczany do porównania `maxSizeOfMessageToLog` , jest rozmiarem komunikatu w pamięci przed serializacji. Ten rozmiar może różnić się od rzeczywistej długości rejestrowanego ciągu komunikatu, a w wielu przypadkach jest większy niż rzeczywisty rozmiar. W związku z tym komunikaty mogą nie być rejestrowane. Możesz obsłużyć ten fakt, określając atrybut `maxSizeOfMessageToLog` , który ma być 10% większy niż oczekiwany rozmiar wiadomości. Ponadto w przypadku zarejestrowania źle sformułowanych komunikatów rzeczywista ilość miejsca na dysku wykorzystana przez dzienniki komunikatów może być maksymalnie 5 razy większa niż wartość określona przez `maxSizeOfMessageToLog`.

Jeśli żaden odbiornik śledzenia nie jest zdefiniowany w pliku konfiguracji, żadne dane wyjściowe rejestrowania nie są generowane niezależnie od określonego poziomu rejestrowania.

Opcje rejestrowania komunikatów, takie jak atrybuty opisane w tej sekcji, można zmienić w czasie wykonywania przy użyciu Instrumentacja zarządzania Windows (WMI). Można to zrobić, uzyskując dostęp do wystąpienia [AppDomainInfo](./wmi/appdomaininfo.md) , które uwidacznia następujące właściwości logiczne `LogMessagesAtServiceLevel`: `LogMessagesAtTransportLevel`,, `LogMalformedMessages`i. `false` W związku z tym, jeśli skonfigurujesz odbiornik śledzenia do rejestrowania komunikatów, ale ustawisz te opcje w konfiguracji, możesz później zmienić je `true` na, gdy aplikacja jest uruchomiona. Pozwala to efektywnie rejestrować komunikaty w czasie wykonywania. Podobnie, jeśli włączysz rejestrowanie komunikatów w pliku konfiguracji, możesz go wyłączyć w czasie wykonywania za pomocą usługi WMI. Aby uzyskać więcej informacji, zobacz [używanie Instrumentacja zarządzania Windows do diagnostyki](./wmi/index.md).

`source` Pole w dzienniku komunikatów określa, w którym kontekście komunikat jest rejestrowany: podczas wysyłania/otrzymywania komunikatu żądania, dla żądania żądanie-odpowiedź lub 1-kierunkowego, w modelu usług lub warstwie transportowej lub w przypadku nieprawidłowo sformułowanego komunikatu.

W przypadku źle sformułowanych `source` komunikatów jest `Malformed`równa. W przeciwnym razie źródło ma następujące wartości na podstawie kontekstu.

Dla żądania/odpowiedzi

||Wyślij żądanie|Żądanie odebrania|Wyślij odpowiedź|Odbierz odpowiedź|
|-|------------------|---------------------|----------------|-------------------|
|Warstwa modelu usług|Usługa<br /><br /> Poziom<br /><br /> Send<br /><br /> Request|Usługa<br /><br /> Poziom<br /><br /> Receive<br /><br /> Request|Usługa<br /><br /> Poziom<br /><br /> Send<br /><br /> Przesyła|Usługa<br /><br /> Poziom<br /><br /> Receive<br /><br /> Przesyła|
|Warstwa transportu|Transportu<br /><br /> Send|Transportu<br /><br /> Receive|Transportu<br /><br /> Send|Transportu<br /><br /> Receive|

Dla żądania jednokierunkowego

||Wyślij żądanie|Żądanie odebrania|
|-|------------------|---------------------|
|Warstwa modelu usług|Usługa<br /><br /> Poziom<br /><br /> Send<br /><br /> Odebran|Usługa<br /><br /> Poziom<br /><br /> Receive<br /><br /> Odebran|
|Warstwa transportu|Transportu<br /><br /> Send|Transportu<br /><br /> Receive|

## <a name="message-filters"></a>Filtry komunikatów

Filtry komunikatów są zdefiniowane w `messageLogging` elemencie `diagnostics` Configuration sekcji konfiguracji. Są one stosowane na poziomie usługi i transportu. Jeśli zdefiniowano co najmniej jeden filtr, rejestrowane są tylko komunikaty zgodne z co najmniej jednym filtrem. Jeśli żaden filtr nie jest zdefiniowany, wszystkie komunikaty są przekazywane.

Filtry obsługują pełną składnię XPath i są stosowane w kolejności, w której pojawiają się w pliku konfiguracji. Składnia nieprawidłowego filtru powoduje wyjątek w konfiguracji.

Filtry zapewniają również funkcję bezpieczeństwa przy użyciu `nodeQuota` atrybutu, który ogranicza maksymalną liczbę węzłów w Dom XPath, które można sprawdzić w celu dopasowania do filtru.

Poniższy przykład pokazuje, jak skonfigurować filtr, który rejestruje tylko wiadomości, które mają sekcję nagłówka SOAP.

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

Nie można zastosować filtrów do treści komunikatu. Filtry, które próbują manipulować treścią wiadomości, są usuwane z listy filtrów. Jest również emitowane zdarzenie wskazujące na to. Na przykład następujący filtr zostałby usunięty z tabeli filtrów.

```xml
<add xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">/s:Envelope/s:Body[contains(text(), "Hello")]</add>
```

## <a name="configuring-a-custom-listener"></a>Konfigurowanie odbiornika niestandardowego

Możesz również skonfigurować odbiornik niestandardowy z dodatkowymi opcjami. Odbiornik niestandardowy może być przydatny do filtrowania elementów samodzielnych specyficznych dla aplikacji z komunikatów przed zarejestrowaniem. Poniższy przykład demonstruje konfigurację odbiorników niestandardowych.

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

Należy pamiętać, że `type` atrybut powinien być ustawiony na kwalifikowaną nazwę zestawu typu.

## <a name="see-also"></a>Zobacz także

- [\<messageLogging >](../../configure-apps/file-schema/wcf/messagelogging.md)
- [Rejestrowanie komunikatów](message-logging.md)
- [Zalecane ustawienia śledzenia i rejestrowania komunikatów](./tracing/recommended-settings-for-tracing-and-message-logging.md)
