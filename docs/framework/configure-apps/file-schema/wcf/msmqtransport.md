---
title: <msmqTransport>
ms.date: 03/30/2017
ms.assetid: 19d89f35-76ac-49dc-832b-e8bec2d5e33b
ms.openlocfilehash: b1e1ca1e22c0044f5a9454ab397b6c3052dc42fe
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928785"
---
# <a name="msmqtransport"></a>\<msmqTransport>
Powoduje, że kanał przesyła komunikaty w ramach transportu usługi MSMQ, gdy jest on uwzględniony w niestandardowym powiązaniu.  
  
 \<system.serviceModel>  
\<> powiązań  
\<customBinding>  
\<> powiązania  
\<msmqIntegration>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<msmqTransport customDeadLetterQueue="Uri"
               deadLetterQueue="Custom/None/System"
               durable="Boolean"
               exactlyOnce="Boolean"
               manualAddressing="Boolean"
               maxBufferPoolSize="Integer"
               maxImmediateRetries="Integer"
               maxPoolSize="Integer"
               maxReceivedMessageSize="Integer"
               maxRetryCycles="Integer"
               queueTransferProtocol="Native/Srmp/SrmpSecure"
               rejectAfterLastRetry="Boolean"
               retryCycleDelay="TimeSpan"
               timeToLive="TimeSpan"
               useActiveDirectory="Boolean"
               useSourceJournal="Boolean"
               useMsmqTracing="Boolean"
               ...>
  <msmqTransportSecurity>
  </msmqTransportSecurity>
</msmqTransport>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|customDeadLetterQueue|Identyfikator URI wskazujący lokalizację kolejki utraconych wiadomości dla aplikacji, w której przesyłane są komunikaty, które wygasły lub których nie można dostarczyć do aplikacji.<br /><br /> W przypadku komunikatów, które wymagają gwarancji exactlyOnce ( `exactlyOnce` ma `true`ustawioną wartość), ten atrybut domyślnie jest kolejką utraconych wiadomości transakcyjnych w całej systemie w usłudze MSMQ.<br /><br /> W przypadku wiadomości, które nie wymagają żadnych gwarancji ( `exactlyOnce` ma `false`ustawioną wartość), ten atrybut jest domyślnie `null`ustawiony na.<br /><br /> Wartość musi używać schematu net. MSMQ. Wartość domyślna to `null`.<br /><br /> Jeśli `deadLetterQueue` jest ustawiona na `None` lub `System`, ten atrybut musi być ustawiony na `null`. Jeśli ten atrybut nie `null`jest `deadLetterQueue` , należy ustawić na `Custom`.|  
|deadLetterQueue|Określa typ używanej kolejki utraconych wiadomości.<br /><br /> Prawidłowe wartości to<br /><br /> Celnej Niestandardowa Kolejka utraconych wiadomości.<br />Dawaj Nie ma potrzeby używania kolejki utraconych wiadomości.<br />Systemami Użyj kolejki wiadomości utraconych systemu.<br /><br /> Ten atrybut jest typu DeadLetterQueue.|  
|durable|Wartość logiczna określająca, czy komunikaty przetwarzane przez to powiązanie są trwałe czy nietrwałe. Wartość domyślna to `true`.<br /><br /> Trwały komunikat przeżyje awarię Menedżera kolejki, podczas gdy nietrwały komunikat nie jest. Komunikaty nietrwałe są przydatne, gdy aplikacje wymagają mniejszych opóźnień i mogą tolerować sporadycznie utracone komunikaty.<br /><br /> Jeśli `exactlyOnce` jest ustawiona na `true`, komunikaty muszą być trwałe.|  
|exactlyOnce|Wartość logiczna określająca, czy komunikaty przetwarzane przez to powiązanie będą odbierane dokładnie raz. Wartość domyślna to `true`.<br /><br /> Komunikat może być wysyłany z gwarancjami lub bez nich. Gwarancja umożliwia aplikacji upewnienie się, że wysłany komunikat osiągnął kolejkę komunikatów odebranych lub jeśli nie, może ona ustalić przez odczytanie kolejki utraconych wiadomości.<br /><br /> `exactlyOnce`Po ustawieniu na `true`, oznacza, że usługa MSMQ zagwarantuje, że wysłany komunikat zostanie dostarczony do kolejki komunikatów odebranych jeden raz i tylko raz, a jeśli dostarczenie nie powiedzie się, komunikat zostanie wysłany do kolejki utraconych wiadomości.<br /><br /> Komunikaty wysyłane z `exactlyOnce` zestawem `true` do muszą być wysyłane tylko do kolejki transakcyjnej.|  
|Opcję ManualAddressing|Wartość logiczna umożliwiająca użytkownikowi przejęcie kontroli nad adresowaniem komunikatów. Ta właściwość jest zwykle używana w scenariuszach routera, gdzie aplikacja określa, z której jednego z kilku miejsc docelowych ma być wysyłany komunikat.<br /><br /> Gdy jest ustawiona `true`na, kanał zakłada, że komunikat został już rozkierowany i nie dodaje do niego żadnych dodatkowych informacji. Użytkownik może następnie osobno rozwiązać każdy komunikat.<br /><br /> W przypadku ustawienia `false`opcji domyślny mechanizm adresowania Windows Communication Foundation (WCF) automatycznie tworzy adresy dla wszystkich komunikatów.<br /><br /> Wartość domyślna to `false`.|  
|maxBufferPoolSize|Dodatnia liczba całkowita, która określa maksymalny rozmiar puli buforów. Wartość domyślna to 524288.<br /><br /> Wiele części usługi WCF korzysta z buforów. Tworzenie i niszczenie buforów za każdym razem, gdy są używane, jest kosztowne i wyrzucanie elementów bezużytecznych dla buforów jest również kosztowne. W przypadku pul buforów można pobrać bufor z puli, użyć go i zwrócić do puli po zakończeniu. W ten sposób nie ma konieczności narzutu na tworzenie i niszczenie buforów.|  
|maxImmediateRetries|Liczba całkowita określająca maksymalną liczbę natychmiastowych ponownych prób w komunikacie odczytywanym z kolejki aplikacji. Wartość domyślna to 5.<br /><br /> Jeśli zostanie podjęta Maksymalna liczba natychmiastowych ponownych prób dla wiadomości, a wiadomość nie zostanie użyta przez aplikację, komunikat jest wysyłany do kolejki ponownych prób w przypadku ponawiania próby w późniejszym czasie. Jeśli nie zostaną określone żadne cykle ponawiania, komunikaty są wysyłane do kolejki trujących komunikatów lub do nadawcy jest wysyłane negatywne potwierdzenie.|  
|maxPoolSize|Dodatnia liczba całkowita, która określa maksymalny rozmiar puli. Wartość domyślna to 524288.|  
|maxReceivedMessageSize|Dodatnia liczba całkowita, która określa maksymalny rozmiar wiadomości w bajtach, włącznie z nagłówkami. Nadawca komunikatu otrzymuje błąd protokołu SOAP, gdy komunikat jest zbyt duży dla odbiornika. Odbiorca odrzuca komunikat i tworzy wpis zdarzenia w dzienniku śledzenia. Wartość domyślna to 65536.|  
|maxRetryCycles|Liczba całkowita określająca maksymalną liczbę ponownych prób dostarczenia komunikatów do aplikacji odbiorczej. Wartość domyślna to <xref:System.Int32.MaxValue>.<br /><br /> Pojedynczy cykl ponowień próbuje dostarczyć komunikat do aplikacji przez określoną liczbę razy. Liczba podjętych prób jest ustawiana przez `maxImmediateRetries` atrybut. Jeśli aplikacja nie będzie mogła użyć komunikatu po wyczerpaniu prób dostarczenia, komunikat jest wysyłany do kolejki ponownych prób. Kolejne cykle ponowień obejmują komunikat zwracany z kolejki ponownych prób do kolejki aplikacji, aby ponowić próbę dostarczenia do aplikacji po opóźnieniu określonym przez `retryCycleDelay` atrybut. Ten `maxRetryCycles` atrybut określa liczbę ponownych prób dostarczenia wiadomości przez aplikację.|  
|queueTransferProtocol|Określa transport kanałów komunikacji umieszczonych w kolejce, który jest wykorzystywany przez to powiązanie. Prawidłowe wartości to<br /><br /> Trybu  Użyj natywnego protokołu MSMQ.<br />SRMP  Użyj protokołu SOAP Messaging Protocol (SRMP).<br />- SrmpSecure: Użyj transportu protokołu niezawodnej obsługi komunikatów SOAP Secure (SRMP).<br /><br /> Ten atrybut jest typu <xref:System.ServiceModel.QueueTransferProtocol>.<br /><br /> Ponieważ usługa MSMQ nie obsługuje adresów Active Directory podczas korzystania z protokołu niezawodnych komunikatów protokołu SOAP, nie należy ustawiać tego atrybutu na wartość SRMP `useActiveDirectory` ani SRMP, `true`gdy jest ustawiony na.|  
|rejectAfterLastRetry|Wartość logiczna określająca, która akcja ma zostać podjęta dla komunikatu, którego dostarczenie nie powiodło się po osiągnięciu maksymalnej liczby ponownych prób.<br /><br /> `true`oznacza, że zwroty negatywne są zwracane do nadawcy, a komunikat zostanie porzucony. `false` oznacza, że wiadomość jest wysyłana do kolejki skażonych komunikatów. Wartość domyślna to `false`.<br /><br /> Jeśli wartość to `false`, aplikacja otrzymująca może odczytać trującą kolejkę komunikatów w celu przetworzenia skażonych komunikatów (czyli komunikatów, których dostarczenie nie powiodło się).<br /><br /> Usługa MSMQ 3,0 nie obsługuje zwracania negatywnego potwierdzenia do nadawcy, więc ten atrybut zostanie zignorowany w usłudze MSMQ 3,0.|  
|retryCycleDelay|A <xref:System.TimeSpan> Określa opóźnienie czasu między kolejnymi próbami dostarczenia komunikatu, którego nie można było dostarczyć natychmiast. Wartość domyślna to 00:10:00.<br /><br /> Pojedynczy cykl ponowień próbuje dostarczyć komunikat do aplikacji odbiorczej określoną liczbę razy. Liczba podjętych prób jest określona przez `maxImmediateRetries` atrybut. Jeśli aplikacja nie wykorzysta komunikatu po określonej liczbie natychmiastowych ponownych prób, komunikat zostanie wysłany do kolejki ponownych prób. Kolejne cykle ponowień obejmują komunikat zwracany z kolejki ponownych prób do kolejki aplikacji, aby ponowić próbę dostarczenia do aplikacji po opóźnieniu określonym przez `retryCycleDelay` atrybut. Liczba cykli ponowień jest określona `maxRetryCycles` przez atrybut.|  
|timeToLive|A <xref:System.TimeSpan> , która określa, jak długo komunikaty są prawidłowe i są umieszczane w kolejce wiadomości utraconych. Wartość domyślna to 1,00:00:00, co oznacza 1 dzień.<br /><br /> Ten atrybut jest ustawiony w celu zapewnienia, że komunikaty zależne od czasu nie stają się nieodświeżone przed przetworzeniem przez aplikacje do odebrania. Wiadomość w kolejce, która nie jest używana przez aplikację otrzymującą w określonym przedziale czasu, jest uznawana za wygasłą. Wygasłe komunikaty są wysyłane do kolejki specjalnej zwanej kolejką utraconych wiadomości. Lokalizacja kolejki utraconych wiadomości jest ustawiana z `customDeadLetterQueue` atrybutem lub z odpowiednim ustawieniem domyślnym w oparciu o gwarancje.|  
|UseActiveDirectory|Wartość logiczna określająca, czy adresy kolejek mają być konwertowane przy użyciu Active Directory.<br /><br /> Adresy kolejki MSMQ mogą składać się z nazw ścieżek lub bezpośrednich nazw formatu. W przypadku bezpośredniej nazwy formatu usługa MSMQ rozpoznaje nazwę komputera przy użyciu systemu DNS, NetBIOS lub IP. Przy użyciu nazwy ścieżki usługa MSMQ rozpoznaje nazwę komputera przy użyciu Active Directory. Domyślnie usługa Windows Communication Framework (WCF) w kolejce jest konwertowana identyfikator URI kolejki komunikatów na nazwę formatu bezpośredniego. Ustawienie tego atrybutu na `true`, aplikacja może określić, że transport w kolejce powinien rozpoznać nazwę komputera przy użyciu Active Directory, a nie DNS, NetBIOS lub IP.|  
|useMsmqTracing|Wartość logiczna określająca, czy komunikaty przetwarzane przez to powiązanie powinny być śledzone. Wartość domyślna to `false`.<br /><br /> Gdy śledzenie jest włączone, wiadomości raportów są tworzone i wysyłane do kolejki raportu za każdym razem, gdy komunikat opuszcza lub dociera do komputera usługi kolejkowania komunikatów.|  
|useSourceJournal|Wartość logiczna określająca, czy kopie komunikatów przetwarzanych przez to powiązanie powinny być przechowywane w kolejce dziennika źródła. Wartość domyślna to `false`.<br /><br /> W kolejce aplikacje, które chcą zachować rekord komunikatów, które zostały pozostawione przez kolejkę wychodzącą komputera, mogą kopiować komunikaty do kolejki dziennika. Gdy wiadomość opuszcza kolejkę wychodzącą i otrzyma potwierdzenie odebrania komunikatu na komputerze docelowym, kopia komunikatu jest przechowywana w kolejce dziennika systemowego komputera wysyłającego.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<msmqTransportSecurity>](msmqtransportsecurity.md)|Określa ustawienia zabezpieczeń transportu dla tego powiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> powiązania](../../../misc/binding.md)|Definiuje wszystkie możliwości powiązań niestandardowego powiązania.|  
  
## <a name="remarks"></a>Uwagi  
 `msmqTransport` Element umożliwia użytkownikowi ustawianie właściwości kanału komunikacyjnego znajdującego się w kolejce. Kanał komunikacji umieszczonych w kolejce używa usługi kolejkowania komunikatów do transportu.  
  
 Ten element powiązania jest domyślnym elementem powiązania używanym przez standardowe powiązanie usługi kolejkowania komunikatów (`netMsmqBinding`).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.MsmqTransportElement>
- <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Kolejki programu WCF](../../../wcf/feature-details/queues-in-wcf.md)
- [Transporty](../../../wcf/feature-details/transports.md)
- [Wybieranie transportu](../../../wcf/feature-details/choosing-a-transport.md)
- [Powiązania](../../../wcf/bindings.md)
- [Rozszerzanie powiązań](../../../wcf/extending/extending-bindings.md)
- [Powiązania niestandardowe](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
