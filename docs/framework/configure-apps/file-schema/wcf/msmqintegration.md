---
title: <msmqIntegration>
ms.date: 03/30/2017
ms.assetid: ab677405-1ffe-457a-803f-00c1770e51e2
ms.openlocfilehash: 143557833457f379d410c3b71d87199a5b9e783b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738897"
---
# \<msmqIntegration>
Określa transport usługi MSMQ dla niestandardowego powiązania.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<msmqIntegration>**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<msmqIntegration customDeadLetterQueue="Uri"
                 deadLetterQueue="Custom/None/System"
                 durable="Boolean"
                 exactlyOnce="Boolean"
                 manualAddressing="Boolean"
                 maxBufferPoolSize="Integer"
                 maxImmediateRetries="Integer"
                 maxReceivedMessageSize="Integer"
                 maxRetryCycles="Integer"
                 rejectAfterLastRetry="Boolean"
                 retryCycleDelay="TimeSpan"
                 serializationFormat="XML/Binary/ActiveX/ByteArray/Stream"
                 timeToLive="TimeSpan"
                 useSourceJournal="Boolean"
                 useMsmqTracing="Boolean">
  <msmqTransportSecurity>
  </msmqTransportSecurity>
</msmqIntegration>
```  
  
## <a name="type"></a>Typ  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|customDeadLetterQueue|Identyfikator URI wskazujący lokalizację kolejki utraconych wiadomości dla aplikacji, w której przesyłane są komunikaty, które wygasły lub których nie można dostarczyć do aplikacji.<br /><br /> W przypadku komunikatów, które wymagają gwarancji ExactlyOnce (ma `exactlyOnce` ustawioną wartość `true` ), ten atrybut domyślnie jest kolejką utraconych wiadomości transakcyjnych w całej systemie w usłudze MSMQ.<br /><br /> W przypadku wiadomości, które nie wymagają żadnych gwarancji (ma `exactlyOnce` ustawioną wartość `false` ), ten atrybut jest domyślnie ustawiony na `null` .<br /><br /> Wartość musi używać schematu net. MSMQ. Wartość domyślna to `null`.<br /><br /> Jeśli `deadLetterQueue` jest ustawiona na `None` lub `System` , ten atrybut musi być ustawiony na `null` . Jeśli ten atrybut nie jest `null` , `deadLetterQueue` należy ustawić na `Custom` .|  
|deadLetterQueue|Określa typ używanej kolejki utraconych wiadomości.<br /><br /> Prawidłowe wartości to<br /><br /> -Custom: niestandardowa Kolejka utraconych wiadomości.<br />-Brak: nie ma potrzeby używania kolejki utraconych wiadomości.<br />-System: Użyj kolejki utraconych wiadomości systemowych.<br /><br /> Ten atrybut jest typu DeadLetterQueue.|  
|służąc|Wartość logiczna określająca, czy komunikaty przetwarzane przez to powiązanie są trwałe czy nietrwałe. Wartość domyślna to `true`.<br /><br /> Trwały komunikat przeżyje awarię Menedżera kolejki, podczas gdy nietrwały komunikat nie jest. Komunikaty nietrwałe są przydatne, gdy aplikacje wymagają mniejszych opóźnień i mogą tolerować sporadycznie utracone komunikaty.<br /><br /> Jeśli `exactlyOnce` jest ustawiona na `true` , komunikaty muszą być trwałe.|  
|exactlyOnce|Wartość logiczna określająca, czy komunikaty przetwarzane przez to powiązanie będą odbierane dokładnie raz. Wartość domyślna to `true`.<br /><br /> Komunikat może być wysyłany z gwarancjami lub bez nich. Gwarancja umożliwia aplikacji upewnienie się, że wysłany komunikat osiągnął kolejkę komunikatów odebranych lub jeśli nie, może ona ustalić przez odczytanie kolejki utraconych wiadomości.<br /><br /> `exactlyOnce`Po ustawieniu na `true` , oznacza, że usługa MSMQ zagwarantuje, że wysłany komunikat zostanie dostarczony do kolejki komunikatów odebranych jeden raz i tylko raz, a jeśli dostarczenie nie powiedzie się, komunikat zostanie wysłany do kolejki utraconych wiadomości.<br /><br /> Komunikaty wysyłane z `exactlyOnce` zestawem do `true` muszą być wysyłane tylko do kolejki transakcyjnej.|  
|Opcję ManualAddressing|Wartość logiczna umożliwiająca użytkownikowi przejęcie kontroli nad adresowaniem komunikatów. Ta właściwość jest zwykle używana w scenariuszach routera, gdzie aplikacja określa, z której jednego z kilku miejsc docelowych ma być wysyłany komunikat.<br /><br /> Gdy jest ustawiona na `true` , kanał zakłada, że komunikat został już rozkierowany i nie dodaje do niego żadnych dodatkowych informacji. Użytkownik może następnie osobno rozwiązać każdy komunikat.<br /><br /> W przypadku ustawienia opcji `false` domyślny mechanizm adresowania Windows Communication Foundation (WCF) automatycznie tworzy adresy dla wszystkich komunikatów.<br /><br /> Wartość domyślna to `false`.|  
|maxBufferPoolSize|Dodatnia liczba całkowita, która określa maksymalny rozmiar puli buforów. Wartość domyślna to 524288.<br /><br /> Wiele części usługi WCF korzysta z buforów. Tworzenie i niszczenie buforów za każdym razem, gdy są używane, jest kosztowne i wyrzucanie elementów bezużytecznych dla buforów jest również kosztowne. W przypadku pul buforów można pobrać bufor z puli, użyć go i zwrócić do puli po zakończeniu. W ten sposób nie ma konieczności narzutu na tworzenie i niszczenie buforów.|  
|maxImmediateRetries|Liczba całkowita określająca maksymalną liczbę natychmiastowych ponownych prób w komunikacie odczytywanym z kolejki aplikacji. Wartość domyślna to 5.<br /><br /> Jeśli zostanie podjęta Maksymalna liczba natychmiastowych ponownych prób dla wiadomości, a wiadomość nie zostanie użyta przez aplikację, komunikat jest wysyłany do kolejki ponownych prób w przypadku ponawiania próby w późniejszym czasie. Jeśli nie zostaną określone żadne cykle ponawiania, komunikaty są wysyłane do kolejki trujących komunikatów lub do nadawcy jest wysyłane negatywne potwierdzenie.|  
|maxReceivedMessageSize|Dodatnia liczba całkowita, która określa maksymalny rozmiar wiadomości w bajtach, włącznie z nagłówkami. Nadawca komunikatu otrzymuje błąd protokołu SOAP, gdy komunikat jest zbyt duży dla odbiornika. Odbiorca odrzuca komunikat i tworzy wpis zdarzenia w dzienniku śledzenia. Wartość domyślna to 65536.|  
|maxRetryCycles|Liczba całkowita określająca maksymalną liczbę ponownych prób dostarczenia komunikatów do aplikacji odbiorczej. Wartość domyślna to <xref:System.Int32.MaxValue>.<br /><br /> Pojedynczy cykl ponowień próbuje dostarczyć komunikat do aplikacji przez określoną liczbę razy. Liczba podjętych prób jest ustawiana przez `maxImmediateRetries` atrybut. Jeśli aplikacja nie będzie mogła użyć komunikatu po wyczerpaniu prób dostarczenia, komunikat jest wysyłany do kolejki ponownych prób. Kolejne cykle ponowień obejmują komunikat zwracany z kolejki ponownych prób do kolejki aplikacji, aby ponowić próbę dostarczenia do aplikacji po opóźnieniu określonym przez `retryCycleDelay` atrybut. Ten `maxRetryCycles` atrybut określa liczbę ponownych prób dostarczenia wiadomości przez aplikację.|  
|rejectAfterLastRetry|Wartość logiczna określająca, która akcja ma zostać podjęta dla komunikatu, którego dostarczenie nie powiodło się po osiągnięciu maksymalnej liczby ponownych prób.<br /><br /> `true`oznacza, że zwroty negatywne są zwracane do nadawcy, a komunikat zostanie porzucony. `false`oznacza, że wiadomość jest wysyłana do kolejki skażonych komunikatów. Wartość domyślna to `false`.<br /><br /> Jeśli wartość to `false` , aplikacja otrzymująca może odczytać trującą kolejkę komunikatów w celu przetworzenia skażonych komunikatów (czyli komunikatów, których dostarczenie nie powiodło się).<br /><br /> Usługa MSMQ 3,0 nie obsługuje zwracania negatywnego potwierdzenia do nadawcy, więc ten atrybut zostanie zignorowany w usłudze MSMQ 3,0.|  
|retryCycleDelay|A <xref:System.TimeSpan> Określa opóźnienie czasu między kolejnymi próbami dostarczenia komunikatu, którego nie można było dostarczyć natychmiast. Wartość domyślna to 00:10:00.<br /><br /> Pojedynczy cykl ponowień próbuje dostarczyć komunikat do aplikacji odbiorczej określoną liczbę razy. Liczba podjętych prób jest określona przez `maxImmediateRetries` atrybut. Jeśli aplikacja nie wykorzysta komunikatu po określonej liczbie natychmiastowych ponownych prób, komunikat zostanie wysłany do kolejki ponownych prób. Kolejne cykle ponowień obejmują komunikat zwracany z kolejki ponownych prób do kolejki aplikacji, aby ponowić próbę dostarczenia do aplikacji po opóźnieniu określonym przez `retryCycleDelay` atrybut. Liczba cykli ponowień jest określona przez `maxRetryCycles` atrybut.|  
|serializationFormat|Określa program formatujący, który jest używany do serializacji obiektów, które są wysyłane w ramach wiadomości MSMQ. Prawidłowe wartości to<br /><br /> -ActiveX: program formatujący ActiveX jest używany podczas serializowania obiektów COM.<br />-Binary: serializacja obiektu do pakietu binarnego.<br />-ByteArray: serializować obiektu do tablicy bajtów.<br />-Stream: serializować obiekt do strumienia.<br />-XML: serializacja obiektu do pakietu XML. Wartość domyślna to XML.<br /><br /> Ten atrybut jest typu <xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat> .|  
|timeToLive|A <xref:System.TimeSpan> , która określa, jak długo komunikaty są prawidłowe i są umieszczane w kolejce wiadomości utraconych. Wartość domyślna to 1,00:00:00, co oznacza 1 dzień.<br /><br /> Ten atrybut jest ustawiony w celu zapewnienia, że komunikaty zależne od czasu nie stają się nieodświeżone przed przetworzeniem przez aplikacje do odebrania. Wiadomość w kolejce, która nie jest używana przez aplikację otrzymującą w określonym przedziale czasu, jest uznawana za wygasłą. Wygasłe komunikaty są wysyłane do kolejki specjalnej zwanej kolejką utraconych wiadomości. Lokalizacja kolejki utraconych wiadomości jest ustawiana z `customDeadLetterQueue` atrybutem lub z odpowiednim ustawieniem domyślnym w oparciu o gwarancje.|  
|useMsmqTracing|Wartość logiczna określająca, czy komunikaty przetwarzane przez to powiązanie powinny być śledzone. Wartość domyślna to `false`.<br /><br /> Gdy śledzenie jest włączone, wiadomości raportów są tworzone i wysyłane do kolejki raportu za każdym razem, gdy komunikat opuszcza lub dociera do komputera usługi kolejkowania komunikatów.|  
|useSourceJournal|Wartość logiczna określająca, czy kopie komunikatów przetwarzanych przez to powiązanie powinny być przechowywane w kolejce dziennika źródła. Wartość domyślna to `false`.<br /><br /> W kolejce aplikacje, które chcą zachować rekord komunikatów, które zostały pozostawione przez kolejkę wychodzącą komputera, mogą kopiować komunikaty do kolejki dziennika. Gdy wiadomość opuszcza kolejkę wychodzącą i otrzyma potwierdzenie odebrania komunikatu na komputerze docelowym, kopia komunikatu jest przechowywana w kolejce dziennika systemowego komputera wysyłającego.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|msmqTransportSecurity|Określa ustawienia zabezpieczeń transportu dla tego powiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement> .|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|Definiuje wszystkie możliwości powiązań niestandardowego powiązania.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.MsmqIntegrationElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Transporty](../../../wcf/feature-details/transports.md)
- [Kolejki programu WCF](../../../wcf/feature-details/queues-in-wcf.md)
- [Wybieranie transportu](../../../wcf/feature-details/choosing-a-transport.md)
- [Powiązania](../../../wcf/bindings.md)
- [Rozszerzanie powiązań](../../../wcf/extending/extending-bindings.md)
- [Powiązania niestandardowe](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
