---
title: Konfigurowanie rejestrowania komunikatów
ms.date: 03/30/2017
helpviewer_keywords:
- message logging [WCF]
ms.assetid: 0ff4c857-8f09-4b85-9dc0-89084706e4c9
ms.openlocfilehash: 283f43239d6cf5aea5ea668397a52313ff526e2a
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345184"
---
# <a name="configuring-message-logging"></a>Konfigurowanie rejestrowania komunikatów

W tym temacie opisano, jak można skonfigurować rejestrowanie wiadomości dla różnych scenariuszy.

## <a name="enabling-message-logging"></a>Włączanie rejestrowania wiadomości

Windows Communication Foundation (WCF) domyślnie nie rejestruje komunikatów. Aby aktywować rejestrowanie wiadomości, należy dodać `System.ServiceModel.MessageLogging` odbiornik śledzenia do źródła `<messagelogging>` śledzenia i ustawić atrybuty elementu w pliku konfiguracyjnym.

W poniższym przykładzie pokazano, jak włączyć rejestrowanie i określić dodatkowe opcje.

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

Aby uzyskać więcej informacji na temat ustawień rejestrowania wiadomości, zobacz [Zalecane ustawienia śledzenia i rejestrowania wiadomości](./tracing/recommended-settings-for-tracing-and-message-logging.md).

Można użyć `add` do określenia nazwy i typu odbiornika, którego chcesz użyć. W przykładowej konfiguracji odbiornik nosi nazwę "wiadomości" i dodaje standardowy`System.Diagnostics.XmlWriterTraceListener`odbiornik śledzenia programu .NET Framework ( ) jako typ do użycia. W przypadku `System.Diagnostics.XmlWriterTraceListener`użycia należy określić lokalizację i nazwę pliku wyjściowego w pliku konfiguracyjnym. Odbywa się to `initializeData` przez ustawienie nazwy pliku dziennika. W przeciwnym razie system zgłasza wyjątek. Można również zaimplementować niestandardowy odbiornik, który emituje dzienniki do pliku domyślnego.

> [!NOTE]
> Ponieważ rejestrowanie wiadomości uzyskuje dostęp do miejsca na dysku, należy ograniczyć liczbę wiadomości, które są zapisywane na dysku dla określonej usługi. Po osiągnięciu limitu wiadomości jest produkowany śledzenia na poziomie informacji i wszystkie działania rejestrowania wiadomości zatrzymać.

Poziom rejestrowania, a także dodatkowe opcje, są omówione w logging level i opcje sekcji.

Atrybut `switchValue` a jest `source` prawidłowy tylko dla śledzenia. Jeśli określisz `switchValue` atrybut dla `System.ServiceModel.MessageLogging` źródła śledzenia w następujący sposób, nie ma wpływu.

```xml
<source name="System.ServiceModel.MessageLogging" switchValue="Verbose">
</source>
```

Jeśli chcesz wyłączyć źródło śledzenia, należy `logMessagesAtServiceLevel`użyć `logMalformedMessages`, `logMessagesAtTransportLevel` i `messageLogging` atrybuty elementu zamiast. Wszystkie te atrybuty `false`należy ustawić na . Można to zrobić za pomocą pliku konfiguracji w poprzednim przykładzie kodu, za pośrednictwem interfejsu użytkownika Edytora konfiguracji lub przy użyciu usługi WMI. Aby uzyskać więcej informacji na temat narzędzia Edytor konfiguracji, zobacz [Narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md). Aby uzyskać więcej informacji na temat usługi WMI, zobacz [Korzystanie z instrumentacji zarządzania windowsem dla diagnostyki](./wmi/index.md).

## <a name="logging-levels-and-options"></a>Poziomy i opcje rejestrowania

W przypadku wiadomości przychodzących rejestrowanie odbywa się natychmiast po utworzeniu wiadomości, bezpośrednio przed wiadomości dostaje się do kodu użytkownika na poziomie usługi i po wykryciu nieprawidłowo sformułowanych wiadomości.

W przypadku wiadomości wychodzących rejestrowanie odbywa się natychmiast po opuszczeniu kodu użytkownika i bezpośrednio przed przesłaniem wiadomości.

WCF rejestruje komunikaty na dwóch różnych poziomach, usługi i transportu. Nieprawidłowo sformułowane wiadomości są również rejestrowane. Trzy kategorie są niezależne od siebie i mogą być aktywowane oddzielnie w konfiguracji.

Poziom rejestrowania można kontrolować, `logMessagesAtServiceLevel`ustawiając `logMalformedMessages` `logMessagesAtTransportLevel` atrybuty `messageLogging` elementu i atrybuty elementu.

### <a name="service-level"></a>Poziom usług

Wiadomości rejestrowane w tej warstwie mają zamiar wprowadzić (po otrzymaniu) lub pozostawić (przy wysyłaniu) kod użytkownika. Jeśli filtry zostały zdefiniowane, rejestrowane są tylko komunikaty pasujące do filtrów. W przeciwnym razie wszystkie komunikaty na poziomie usługi są rejestrowane. Komunikaty infrastruktury (transakcje, kanał równorzędny i zabezpieczenia) są również rejestrowane na tym poziomie, z wyjątkiem komunikatów niezawodnej obsługi wiadomości. W wiadomościach przesyłanych strumieniowo rejestrowane są tylko nagłówki. Ponadto bezpieczne wiadomości są rejestrowane odszyfrowywane na tym poziomie.

### <a name="transport-level"></a>Poziom transportu

Wiadomości rejestrowane w tej warstwie są gotowe do zakodowania lub dekodowania dla lub po transporcie w sieci. Jeśli filtry zostały zdefiniowane, rejestrowane są tylko komunikaty pasujące do filtrów. W przeciwnym razie wszystkie komunikaty w warstwie transportu są rejestrowane. Wszystkie komunikaty infrastruktury są rejestrowane w tej warstwie, w tym wiadomości niezawodne wiadomości. W wiadomościach przesyłanych strumieniowo rejestrowane są tylko nagłówki. Ponadto bezpieczne wiadomości są rejestrowane jako zaszyfrowane na tym poziomie, z wyjątkiem, jeśli używany jest bezpieczny transport, taki jak HTTPS.

### <a name="malformed-level"></a>Nieprawidłowo uformowany poziom

Nieprawidłowo sformułowane wiadomości są wiadomości, które są odrzucane przez stos WCF na dowolnym etapie przetwarzania. Nieprawidłowo sformułowane wiadomości są rejestrowane jako — jest: szyfrowane, jeśli tak jest, z nienaskładanym kodem XML i tak dalej. `maxSizeOfMessageToLog`zdefiniował rozmiar wiadomości, która ma być zarejestrowana jako CDATA. Domyślnie `maxSizeOfMessageToLog` jest równa 256K. Aby uzyskać więcej informacji na temat tego atrybutu, zobacz sekcję Inne opcje.

### <a name="other-options"></a>Inne opcje

Oprócz poziomów rejestrowania użytkownik może określić następujące opcje:

- Log Entire`logEntireMessage` Message (atrybut): Ta wartość określa, czy cała wiadomość (nagłówek wiadomości i treść) jest rejestrowana. Wartością domyślną jest `false`, co oznacza, że tylko nagłówek jest rejestrowany. To ustawienie ma wpływ na poziomy rejestrowania komunikatów usługi i transportu..

- Maksymalna liczba`maxMessagesToLog` komunikatów do zarejestrowania (atrybut): Ta wartość określa maksymalną liczbę wiadomości do zarejestrowania. Wszystkie wiadomości (usługa, transport i nieprawidłowo sformułowane wiadomości) są wliczane do tego przydziału. Po osiągnięciu przydziału jest emitowany śledzenia i nie jest rejestrowany żaden dodatkowy komunikat. Wartość domyślna to 10000.

- Maksymalny rozmiar wiadomości`maxSizeOfMessageToLog` do dziennika (atrybut): Ta wartość określa maksymalny rozmiar wiadomości do logowania bajtów. Komunikaty, które przekraczają limit rozmiaru nie są rejestrowane i nie jest wykonywane żadne inne działanie dla tej wiadomości. To ustawienie ma wpływ na wszystkie poziomy śledzenia. Jeśli śledzenie ServiceModel jest włączone, śledzenie poziomu ostrzeżenia jest emitowane w pierwszym punkcie rejestrowania (ServiceModelSend* lub TransportReceive), aby powiadomić użytkownika. Domyślną wartością komunikatów poziomu usługi i poziomu transportu jest 256K, podczas gdy domyślną wartością dla nieprawidłowo sformułowanych komunikatów jest 4K.

  > [!CAUTION]
  > Rozmiar wiadomości, który jest obliczany do porównania z `maxSizeOfMessageToLog` jest rozmiar wiadomości w pamięci przed serializacji. Ten rozmiar może się różnić od rzeczywistej długości ciągu wiadomości, który jest rejestrowany, a w wielu przypadkach jest większy niż rzeczywisty rozmiar. W rezultacie wiadomości mogą nie być rejestrowane. Można uwzględnić ten fakt, `maxSizeOfMessageToLog` określając atrybut jest o 10% większy niż oczekiwany rozmiar wiadomości. Ponadto w przypadku rejestrowania nieprawidłowo sformułowanych komunikatów rzeczywiste miejsce na dysku wykorzystywane przez dzienniki komunikatów może `maxSizeOfMessageToLog`być nawet 5 razy większe od rozmiaru wartości określonej przez program .

Jeśli w pliku konfiguracyjnym nie zdefiniowano żadnego odbiornika śledzenia, nie jest generowane żadne dane wyjściowe rejestrowania niezależnie od określonego poziomu rejestrowania.

Opcje rejestrowania komunikatów, takie jak atrybuty opisane w tej sekcji, można zmienić w czasie wykonywania przy użyciu instrumentacji zarządzania windowsem (WMI). Można to zrobić, uzyskując dostęp do [wystąpienia AppDomainInfo,](./wmi/appdomaininfo.md) które `LogMessagesAtServiceLevel` `LogMessagesAtTransportLevel`udostępnia `LogMalformedMessages`te właściwości logiczne: , i . W związku z tym jeśli skonfigurujesz odbiornik śledzenia do `false` rejestrowania wiadomości, ale ustaw `true` te opcje w konfiguracji, można później zmienić je na gdy aplikacja jest uruchomiona. To skutecznie umożliwia rejestrowanie wiadomości w czasie wykonywania. Podobnie po włączeniu rejestrowania wiadomości w pliku konfiguracji, można go wyłączyć w czasie wykonywania przy użyciu usługi WMI. Aby uzyskać więcej informacji, zobacz [Korzystanie z instrumentacji zarządzania windowsem dla diagnostyki](./wmi/index.md).

Pole `source` w dzienniku wiadomości określa, w którym kontekście wiadomość jest rejestrowana: podczas wysyłania/odbierania wiadomości żądania, dla żądania odpowiedzi lub żądania 1-drogowego, w modelu usługi lub warstwy transportu lub w przypadku nieprawidłowo sformułowanej wiadomości.

W przypadku nieprawidłowo `source` sformułowanych `Malformed`wiadomości jest równa . W przeciwnym razie źródło ma następujące wartości na podstawie kontekstu.

Na wniosek/odpowiedź

||Wyślij żądanie|Otrzymaj żądanie|Wyślij odpowiedź|Odbierz odpowiedź|
|-|------------------|---------------------|----------------|-------------------|
|Warstwa modelu usługi|Usługa<br /><br /> Poziom<br /><br /> Wysyłanie<br /><br /> Żądanie|Usługa<br /><br /> Poziom<br /><br /> Odbieranie<br /><br /> Żądanie|Usługa<br /><br /> Poziom<br /><br /> Wysyłanie<br /><br /> Odpowiedz|Usługa<br /><br /> Poziom<br /><br /> Odbieranie<br /><br /> Odpowiedz|
|Warstwa transportowa|Transport<br /><br /> Wysyłanie|Transport<br /><br /> Odbieranie|Transport<br /><br /> Wysyłanie|Transport<br /><br /> Odbieranie|

Dla żądania jednokierunkowego

||Wyślij żądanie|Otrzymaj żądanie|
|-|------------------|---------------------|
|Warstwa modelu usługi|Usługa<br /><br /> Poziom<br /><br /> Wysyłanie<br /><br /> Datagram|Usługa<br /><br /> Poziom<br /><br /> Odbieranie<br /><br /> Datagram|
|Warstwa transportowa|Transport<br /><br /> Wysyłanie|Transport<br /><br /> Odbieranie|

## <a name="message-filters"></a>Filtry komunikatów

Filtry komunikatów są `messageLogging` definiowane `diagnostics` w elemencie konfiguracji sekcji konfiguracji. Są one stosowane na poziomie usług i transportu. Gdy zdefiniowano jeden lub więcej filtrów, rejestrowane są tylko komunikaty, które pasują do co najmniej jednego z filtrów. Jeśli żaden filtr nie jest zdefiniowany, wszystkie komunikaty przechodzą przez.

Filtry obsługują pełną składnię XPath i są stosowane w kolejności, w jakiej pojawiają się w pliku konfiguracyjnym. Niepoprawny syntaktycznie filtr powoduje wyjątek konfiguracji.

Filtry zapewniają również funkcję `nodeQuota` bezpieczeństwa przy użyciu atrybutu, który ogranicza maksymalną liczbę węzłów w XPath DOM, które mogą być badane w celu dopasowania filtru.

W poniższym przykładzie pokazano, jak skonfigurować filtr, który rejestruje tylko wiadomości, które mają sekcję nagłówka PROTOKOŁU SOAP.

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

Filtrów nie można zastosować do treści wiadomości. Filtry, które próbują manipulować treścią wiadomości, są usuwane z listy filtrów. Emitowane jest również zdarzenie, które wskazuje to. Na przykład następujący filtr zostanie usunięty z tabeli filtrów.

```xml
<add xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">/s:Envelope/s:Body[contains(text(), "Hello")]</add>
```

## <a name="configuring-a-custom-listener"></a>Konfigurowanie odbiornika niestandardowego

Można również skonfigurować odbiornik niestandardowy z dodatkowymi opcjami. Niestandardowy odbiornik może być przydatne w filtrowaniu elementów pii specyficzne dla aplikacji z wiadomości przed rejestrowaniem. W poniższym przykładzie przedstawiono niestandardową konfigurację odbiornika.

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

Należy pamiętać, że `type` atrybut powinien być ustawiony na nazwę zestawu kwalifikowanego typu.

## <a name="see-also"></a>Zobacz też

- [\<>rejestrowania wiadomości](../../configure-apps/file-schema/wcf/messagelogging.md)
- [Rejestrowanie komunikatów](message-logging.md)
- [Zalecane ustawienia śledzenia i rejestrowania komunikatów](./tracing/recommended-settings-for-tracing-and-message-logging.md)
