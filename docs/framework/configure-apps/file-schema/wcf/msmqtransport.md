---
title: '&lt;msmqTransport&gt;'
ms.date: 03/30/2017
ms.assetid: 19d89f35-76ac-49dc-832b-e8bec2d5e33b
ms.openlocfilehash: 523f2fd030f40a6d55080a48773159ab4b5887ec
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660583"
---
# <a name="ltmsmqtransportgt"></a>&lt;msmqTransport&gt;
Powoduje, że kanał przenosi wiadomości w usłudze transportowej MSMQ gdy jest włączony do niestandardowego powiązania.  
  
 \<system.serviceModel>  
\<powiązania >  
\<customBinding>  
\<Powiązanie >  
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
|customDeadLetterQueue|Identyfikator URI, który wskazuje lokalizację kolejki utraconych wiadomości dla aplikacji, gdzie są przesyłane komunikaty, które wygasły lub nie może być dostarczane do aplikacji.<br /><br /> Komunikaty, które wymagają gwarancji ExactlyOnce (to znaczy `exactlyOnce` jest ustawiona na `true`), tego atrybutu, wartość domyślna to systemowe kolejki utraconych wiadomości transakcyjnych w usłudze MSMQ.<br /><br /> Komunikaty, które wymagają żadnych zapewnień (to znaczy, `exactlyOnce` jest ustawiona na `false`), tego atrybutu, wartość domyślna to `null`.<br /><br /> Wartość musi używać schematu net.msmq. Wartość domyślna to `null`.<br /><br /> Jeśli `deadLetterQueue` ustawiono `None` lub `System`, a następnie ten atrybut musi być równa `null`. Jeśli ten atrybut nie jest `null`, następnie `deadLetterQueue` musi być równa `Custom`.|  
|deadLetterQueue|Określa typ używanej kolejki utraconych wiadomości.<br /><br /> Prawidłowe wartości to<br /><br /> -Niestandardowy: Custom deadletter queue.<br />-Brak: Kolejka utraconych wiadomości ma być używany.<br />— System: Użyj kolejki utraconych wiadomości systemu.<br /><br /> Ten atrybut jest typu DeadLetterQueue wartość.|  
|trwałe|Wartość logiczna określająca, czy komunikaty przetwarzane przez to powiązanie są trwałe lub zmienne. Wartość domyślna to `true`.<br /><br /> Trwały komunikat przeżyje awarii menedżera kolejki, a komunikat volatile nie. Volatile komunikaty są przydatne, jeśli aplikacje wymagają mniejsze opóźnienia, które mogą tolerować okazjonalne utracone wiadomości.<br /><br /> Jeśli `exactlyOnce` ustawiono `true`, komunikaty muszą być trwałe.|  
|exactlyOnce|Wartość logiczna określająca, czy komunikaty przetwarzane przez to powiązanie będą odbierane dokładnie raz. Wartość domyślna to `true`.<br /><br /> Mogą być wysyłane wiadomości, z lub bez gwarancji. Zapewnienie umożliwia aplikacji upewnij się, że wysłaną wiadomość dotarła odbieranie kolejki komunikatów lub jeśli nie, aplikacja można to ustalić, czytając kolejki utraconych wiadomości.<br /><br /> `exactlyOnce`, gdy wartość `true`, wskazuje, że usługi MSMQ będzie upewnij się, że wiadomość jest dostarczany do odbierania kolejki komunikatów, jeden raz i tylko jeden raz, a w przypadku niepowodzenia dostarczenia komunikat jest wysyłany do kolejki utraconych wiadomości.<br /><br /> Komunikaty wysyłane za pomocą `exactlyOnce` równa `true` muszą być wysyłane do tylko kolejkę transakcyjną.|  
|opcję manualAddressing|Wartość logiczna umożliwiająca użytkownikowi przejęcie kontroli nad adresowaniem komunikatów. Ta właściwość jest zwykle używana w scenariuszach routera, gdzie Określa, co kilka miejsc docelowych, można wysłać wiadomości do aplikacji.<br /><br /> Po ustawieniu `true`, kanał zakłada komunikat już został rozwiązany i nie dodaje żadnych dodatkowych informacji do niego. Użytkownik może następnie indywidualnie adresów każdej wiadomości.<br /><br /> Po ustawieniu `false`, domyślnego mechanizmu adresowania Windows Communication Foundation (WCF) automatycznie tworzy adresy wszystkich wiadomości.<br /><br /> Wartość domyślna to `false`.|  
|maxBufferPoolSize|Dodatnia liczba całkowita, która określa maksymalny rozmiar puli bufora. Wartość domyślna to 524288.<br /><br /> Wiele elementów usług WCF za pomocą buforów. Tworzenie i niszczenie buforów za każdym razem, gdy są one używane jest kosztowne, a także jest kosztowne wyrzucania elementów bezużytecznych dla buforów. Dzięki pulom buforu zająć buforu z puli, go używać i przywrócić go do puli, gdy wszystko będzie gotowe. Ten sposób unika się obciążenie tworzeniem i likwidowaniem buforów.|  
|maxImmediateRetries|Liczba całkowita określająca maksymalną liczbę natychmiastowego ponawiania próby w wiadomości, które są odczytywane z kolejki aplikacji. Wartość domyślna to 5.<br /><br /> Jeśli zostanie podjęta maksymalną liczbę natychmiastowe ponawianie próby w przypadku wiadomości i komunikat nie jest używane przez aplikację, wiadomości są wysyłane do kolejki ponawiania prób w przypadku ponawiania w pewnym momencie później w czasie. Jeśli nie określono nie ponownych prób cyklów, albo przesłany komunikaty w kolejce skażonych komunikatów lub negatywnego potwierdzenia są wysyłane do nadawcy.|  
|maxPoolSize|Dodatnia liczba całkowita, która określa maksymalny rozmiar puli. Wartość domyślna to 524288.|  
|maxReceivedMessageSize|Dodatnia liczba całkowita, która określa maksymalny rozmiar wiadomości w bajtach, włącznie z nagłówkami. Nadawca wiadomości otrzymuje protokołu SOAP wiadomości jest za duża dla odbiornika. Należy określić odbiorcę porzuca wiadomość i tworzy wpis zdarzenia w dzienniku śledzenia. Wartość domyślna to 65536.|  
|maxRetryCycles|Liczba całkowita określająca maksymalną liczbę ponownych prób cyklów próby dostarczenia komunikatów do aplikacji odbierającej. Wartość domyślna to <xref:System.Int32.MaxValue>.<br /><br /> Pojedynczy cykl prób dostarczenia komunikatu do aplikacji z określoną liczbę razy. Liczba podjętych jest ustawiana przez `maxImmediateRetries` atrybutu. Jeśli aplikacja nie może używać komunikat po wyczerpaniu próbami dostarczenia, komunikat jest wysyłany do kolejki ponownych prób. Cykle kolejnym ponowieniem próby składają się z wiadomości zwracanych z kolejki ponownych prób do kolejki aplikacji próby dostarczenia do aplikacji, ponownie z opóźnieniem, określony przez `retryCycleDelay` atrybutu. `maxRetryCycles` Atrybut określa liczbę ponownych prób cyklów przez aplikację prób dostarczenia komunikatu.|  
|queueTransferProtocol|Określa zakolejkowany kanał transportowy komunikacji, który używa tego powiązania. Prawidłowe wartości to:<br /><br /> — Natywna:  Użyj natywnego protokołu usługi MSMQ.<br />-Srmp:  Użyj niezawodnej obsługi komunikatów protokołu Soap (SRMP).<br />-SrmpSecure: Użyj transportu protokołu Soap niezawodnej obsługi komunikatów protokołu Secure (SRMPS).<br /><br /> Ten atrybut jest typu <xref:System.ServiceModel.QueueTransferProtocol>.<br /><br /> Ponieważ usługa MSMQ nie obsługuje usługi Active Directory adresowania, korzystając z protokołu SOAP Reliable Messaging Protocol, nie należy ustawiać ten atrybut Srmp lub Srmps podczas `useActiveDirectory` ustawiono `true`.|  
|rejectAfterLastRetry|Wartość logiczna, która określa, jaką akcję należy podjąć, aby uzyskać komunikat, który zakończył się niepowodzeniem dostarczania po zostanie podjęta określona maksymalna liczba ponownych prób.<br /><br /> `true` oznacza, że negatywnego potwierdzenia jest zwracana do nadawcy wiadomości jest porzucany; `false` oznacza, że komunikat jest wysyłany do kolejki Zarządzanie skażonymi komunikatami. Wartość domyślna to `false`.<br /><br /> Jeśli wartość jest `false`, aplikacja może odczytywać Zarządzanie skażonymi komunikatami kolejki do przetworzenia skażone wiadomości (czyli wiadomości, które nie powiodły dostarczania).<br /><br /> Usługa MSMQ 3.0 nie obsługuje zwracania negatywnego potwierdzenia do nadawcy, więc ten atrybut zostanie zignorowany w usłudze MSMQ 3.0.|  
|retryCycleDelay|Element <xref:System.TimeSpan> , który określa czas opóźnienia między ponownych prób cyklów przy próbie dostarczenia komunikatu, którego nie można dostarczyć natychmiast. Wartość domyślna to 00:10:00.<br /><br /> Pojedynczego cykl prób dostarczenia komunikatu do aplikacji odbierającej określoną liczbę razy. Liczba podjętych jest określona przez `maxImmediateRetries` atrybutu. Jeśli aplikacja nie może używać komunikat po określonej liczbie ponownych prób natychmiastowe, komunikat jest wysyłany do kolejki ponownych prób. Cykle kolejnym ponowieniem próby składają się z wiadomości zwracanych z kolejki ponownych prób do kolejki aplikacji próby dostarczenia do aplikacji, ponownie z opóźnieniem, określony przez `retryCycleDelay` atrybutu. Liczba ponownych prób cyklów jest określona przez `maxRetryCycles` atrybutu.|  
|timeToLive|A <xref:System.TimeSpan> określający, jak długo komunikaty zachowują poprawność, zanim wygasną i są umieszczane w kolejce wiadomości utraconych. Wartość domyślna to 1.00:00:00, czyli 1 dzień.<br /><br /> Ten atrybut jest ustawiony, aby upewnić się, że komunikaty zależne od czasu nie staną się przestarzałe zanim zostaną one przetworzone przez aplikacje odbierające. Komunikat w kolejce, który nie jest używane przez aplikację odbierającą w określonym przedziale czasu jest nazywany wygasnąć. Wygasłe komunikaty są wysyłane do kolejki specjalne o nazwie Kolejka utraconych wiadomości. Lokalizacja kolejkę z utraconymi została ustawiona za pomocą `customDeadLetterQueue` atrybut lub odpowiednie domyślne na podstawie gwarancji.|  
|UseActiveDirectory|Wartość logiczna określająca, czy adresy kolejki powinny być konwertowane przy użyciu usługi Active Directory.<br /><br /> Adresy kolejki usługi MSMQ mogą składać się z nazw ścieżki lub bezpośrednich nazw formatu. Z bezpośrednią nazwą formatu usługa MSMQ jest rozpoznawana jako nazwę komputera, przy użyciu DNS, NetBIOS lub adres IP. Z nazwą ścieżki MSMQ jest rozpoznawana jako nazwę komputera, przy użyciu usługi Active Directory. Domyślnie program Windows Communication Framework (WCF) w kolejce konwertuje transportu kolejki komunikatów, która z bezpośrednią nazwą formatu identyfikatora URI. Przez ustawienie tego atrybutu na `true`, aplikacja może określić, czy transport umieszczonych w kolejce powinien rozwiązać nazwę komputera, przy użyciu usługi Active Directory, a nie DNS, NetBIOS lub adresu IP.|  
|useMsmqTracing|Wartość logiczna określająca, czy komunikaty przetwarzane przez to powiązanie powinny być śledzone. Wartość domyślna to `false`.<br /><br /> Po włączeniu funkcji śledzenia komunikatów raportów tworzonych i wysyłanych do kolejki raportu za każdym razem wiadomości pozostawia lub dociera do komputera usługi kolejkowania komunikatów.|  
|useSourceJournal|Wartość logiczna określająca, czy kopie komunikatów przetwarzanych przez to powiązanie powinny być przechowywane w kolejce dziennika źródła. Wartość domyślna to `false`.<br /><br /> Umieszczonych w kolejce aplikacji, których chcesz prowadzić rejestr, wiadomości, które pozostało w kolejce wychodzącej komputera można skopiować komunikaty do kolejki dziennika. Gdy wiadomość pozostawia kolejek wychodzących i potwierdzenia otrzymania, czy wiadomość została odebrana na komputerze docelowym, kopia wiadomości są przechowywane w kolejce dziennika systemu komputera wysyłającego.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<msmqTransportSecurity>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqtransportsecurity.md)|Określa ustawienia zabezpieczenia transportu dla tego powiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Powiązanie >](../../../../../docs/framework/misc/binding.md)|Definiuje wszystkie funkcje powiązania niestandardowego powiązania.|  
  
## <a name="remarks"></a>Uwagi  
 `msmqTransport` Element umożliwia użytkownikowi na ustawianie właściwości kanału komunikacji z obsługą kolejek. Kanał komunikacyjny umieszczonych w kolejce używa usługi kolejkowania komunikatów dla transportu.  
  
 Stanem tego elementu powiązania jest domyślny element powiązania, używany przez powiązanie standardowe usługi kolejkowania komunikatów (`netMsmqBinding`).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Configuration.MsmqTransportElement>
- <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Kolejki programu WCF](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [Transporty](../../../../../docs/framework/wcf/feature-details/transports.md)
- [Wybieranie transportu](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [Powiązania](../../../../../docs/framework/wcf/bindings.md)
- [Rozszerzanie powiązań](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Powiązania niestandardowe](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
