---
title: '&lt;msmqTransport&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19d89f35-76ac-49dc-832b-e8bec2d5e33b
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bc96bcaae74be5e59f0da69b02e350e2c77d61e1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltmsmqtransportgt"></a>&lt;msmqTransport&gt;
Powoduje, że kanał przenosi wiadomości w usłudze transportowej MSMQ gdy jest włączony do niestandardowego powiązania.  
  
 \<system.serviceModel >  
\<powiązania >  
\<customBinding >  
\<Powiązanie >  
\<msmqIntegration >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<msmqTransport>  
    customDeadLetterQueue="Uri"  
    deadLetterQueue="Custom/None/System"  
    durable="Boolean"  
    exactlyOnce="Boolean"  
    manualAddressing="Boolean"  
    maxBufferPoolSize="Integer"  
    maxImmediateRetries="Integer"  
    maxPoolSize="Integer"  
    maxReceivedMessageSize="Integer"  
    maxRetryCycles="Integer"  
....queueTransferProtocol="Native/Srmp/SrmpSecure"  
    rejectAfterLastRetry="Boolean"  
    retryCycleDelay="TimeSpan"  
    timeToLive="TimeSpan"  
    useActiveDirectory="Boolean"  
    useSourceJournal="Boolean"  
    useMsmqTracing="Boolean"  
    <msmqTransportSecurity>  
    </msmqTransportSecurity>  
</msmqIntegration>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|CustomDeadLetterQueue|Identyfikator URI, który wskazuje lokalizację kolejki utraconych wiadomości dla każdej aplikacji, gdzie są przesyłane komunikaty, które wygasły lub nie można dostarczyć do aplikacji.<br /><br /> Komunikaty, które wymagają gwarancji ExactlyOnce (to znaczy `exactlyOnce` ma ustawioną wartość `true`), tego atrybutu wartością domyślną systemowe kolejki utraconych wiadomości transakcyjnych w usłudze MSMQ.<br /><br /> Komunikaty, które wymagają nie zapewnień (to znaczy `exactlyOnce` ma ustawioną wartość `false`), domyślna tego atrybutu `null`.<br /><br /> Wartość musi być stosowany schemat net.msmq. Wartość domyślna to `null`.<br /><br /> Jeśli `deadLetterQueue` ustawiono `None` lub `System`, a następnie ten atrybut musi mieć ustawioną `null`. Jeśli ten atrybut nie jest `null`, następnie `deadLetterQueue` musi mieć ustawioną `Custom`.|  
|DeadLetterQueue wartość|Określa typ używanej kolejki utraconych wiadomości.<br /><br /> Prawidłowe wartości to<br /><br /> -Niestandardowy: Niestandardowa kolejka utraconych wiadomości.<br />-Brak: Nie kolejki utraconych wiadomości ma być używany.<br />-System: Użyj systemu kolejki utraconych wiadomości.<br /><br /> Ten atrybut jest typu DeadLetterQueue wartość.|  
|trwałe|Wartość logiczna określająca, czy komunikaty przetwarzane przez to powiązanie są trwałe lub zmienne. Wartość domyślna to `true`.<br /><br /> Trwałe komunikat przeżyje awarii menedżera kolejki, a komunikat nietrwałe nie. Volatile wiadomości są przydatne, gdy aplikacje wymagają mniejsze opóźnienia i może tolerować okazjonalne utratą komunikatów.<br /><br /> Jeśli `exactlyOnce` ma ustawioną wartość `true`, komunikaty muszą być trwałe.|  
|ExactlyOnce|Wartość logiczna określająca, czy komunikaty przetwarzane przez to powiązanie będą odbierane dokładnie raz. Wartość domyślna to `true`.<br /><br /> Można wysłać komunikatu z lub bez gwarancji. Zapewnienie umożliwia aplikacji upewnij się, że wiadomość dotarła do odbierania kolejki wiadomości, lub jeśli nie, aplikacja może to ustalić, odczytując kolejki utraconych wiadomości.<br /><br /> `exactlyOnce`, jeśli wartość `true`, wskazuje, że usługi MSMQ zapewni, że wiadomość jest dostarczany do odbierania kolejki komunikatów, jeden raz i tylko jeden raz, a w przypadku niepowodzenia dostarczenia komunikat jest wysyłany do kolejki utraconych wiadomości.<br /><br /> Wiadomości wysyłane z `exactlyOnce` ustawioną `true` muszą zostać przesłane do tylko kolejką transakcyjną.|  
|Opcję ManualAddressing|Wartość logiczna, która umożliwia użytkownikowi przejęcie kontroli nad adresowaniem komunikatów. Ta właściwość jest zwykle używana w scenariuszach router gdzie aplikacji Określa jedną z kilku miejsca docelowe, aby wysłać wiadomość.<br /><br /> Jeśli wartość `true`, zakłada kanału wiadomości już został rozwiązany i nie dodaje żadnych dodatkowych informacji do niego. Użytkownik może następnie indywidualnie adresów każdej wiadomości.<br /><br /> Jeśli wartość `false`, domyślny mechanizm adresowania Windows Communication Foundation (WCF) automatycznie tworzy adresy dla wszystkich wiadomości.<br /><br /> Wartość domyślna to `false`.|  
|MaxBufferPoolSize|Dodatnia liczba całkowita, która określa maksymalny rozmiar puli buforów. Wartość domyślna to 524288.<br /><br /> Wiele elementów WCF za pomocą buforów. Tworzenie i niszczenie buforów za każdym razem, gdy są one używane jest kosztowne i odzyskiwanie pamięci dla buforów również jest kosztowna. Używając puli buforów można podjąć buforu z puli, ten jest używany i zwracać do puli, gdy wszystko będzie gotowe. W związku z tym jest unikać obciążenie związane z tworzeniem i niszczenie buforów.|  
|maxImmediateRetries|Liczba całkowita określająca maksymalną liczbę natychmiastowego ponawiania próby w przypadku komunikatu odczytywanego z kolejki aplikacji. Wartość domyślna to 5.<br /><br /> Jeśli nastąpiła maksymalna liczba natychmiastowego ponownych prób dla komunikatu, komunikat nie jest używane przez aplikację komunikat jest wysyłany do kolejki ponownych prób ponawiania w pewnym momencie nowsze w czasie. Jeśli nie określono żadnych liczbę cykli ponownych prób, albo odesłana wiadomości do kolejki Trująca wiadomość została lub negatywnego potwierdzenia są wysyłane do nadawcy.|  
|maxPoolSize|Dodatnia liczba całkowita, która określa maksymalny rozmiar puli. Wartość domyślna to 524288.|  
|MaxReceivedMessageSize|Dodatnia liczba całkowita, która określa maksymalny rozmiar wiadomości w bajtach, włącznie z nagłówkami. Nadawca komunikatu otrzymuje błędu protokołu SOAP wiadomości jest za duża dla odbiornika. Odbiornik porzuca wiadomości i tworzy wpis zdarzenia w dzienniku śledzenia. Wartość domyślna to 65536.|  
|MaxRetryCycles|Liczba całkowita określająca maksymalną liczbę cykli ponawiania próby dostarczenia komunikatów do aplikacji odbierającej. Wartość domyślna to <xref:System.Int32.MaxValue>.<br /><br /> Jeden cykl prób dostarczenia komunikatu, do aplikacji przez określoną liczbę razy. Liczba prób jest ustawiana przez `maxImmediateRetries` atrybutu. Jeśli aplikacja nie może korzystać z po wyczerpaniu próbami dostarczenia komunikatu, komunikat jest wysyłany do kolejki ponawiania. Liczbę cykli ponownych prób kolejnych składają się z komunikat z kolejki ponawiania do kolejki aplikacji prób dostarczenia do aplikacji, z opóźnieniem określony przez `retryCycleDelay` atrybutu. `maxRetryCycles` Atrybut określa liczbę cykli ponownych prób aplikacja używa prób dostarczenia komunikatu.|  
|Właściwość queueTransferProtocol|Określa zakolejkowany kanał transportowy komunikacji, który używa tego powiązania. Prawidłowe wartości to<br /><br /> -Native: Używać natywnego protokołu usługi MSMQ.<br />-Srmp: Protokół Soap niezawodnej obsługi komunikatów (SRMP);<br />-SrmpSecure: Użyj transportu Soap niezawodnej obsługi komunikatów protokołu Secure (SRMPS).<br /><br /> Ten atrybut jest typu <xref:System.ServiceModel.QueueTransferProtocol>.<br /><br /> Ponieważ usługa MSMQ nie obsługuje adresów usługi Active Directory przy użyciu protokołu SOAP Reliable Messaging Protocol, nie należy ustawiać ten atrybut Srmp lub Srmps podczas `u``seActiveDirectory` ma ustawioną wartość `true`.|  
|rejectAfterLastRetry|Wartość logiczna, która określa, jaka akcja ma być komunikatu, który nie powiodła się dostarczania po prób wykonania maksymalnej liczby ponownych prób.<br /><br /> `true`oznacza, że potwierdzenie negatywne jest zwracana do nadawcy wiadomości jest porzucany; `false` oznacza, że komunikat jest wysyłany do kolejki Trująca wiadomość. Wartość domyślna to `false`.<br /><br /> Jeśli wartość jest `false`, aplikacja odbierająca może odczytywać kolejki Trująca wiadomość do przetworzenia skażone wiadomości (oznacza to, że wiadomości, które nie powiodły dostarczania).<br /><br /> Usługa MSMQ 3.0 nie obsługuje zwracania potwierdzenie negatywne nadawcy, więc ten atrybut zostanie zignorowany w 3.0 usługi MSMQ.|  
|RetryCycleDelay|A <xref:System.TimeSpan> , który określa czas opóźnienia między liczbę cykli ponownych prób przy próbie dostarczenia komunikatu, którego nie można było dostarczyć natychmiast. Wartość domyślna to 00:10:00.<br /><br /> Jeden cykl prób dostarczenia komunikatu, do aplikacji odbierającej określoną liczbę razy. Liczba prób jest określona przez `maxImmediateRetries` atrybutu. Jeśli aplikacja nie może używać komunikat po określonej liczbie prób natychmiastowe, komunikat jest wysyłany do kolejki ponawiania. Liczbę cykli ponownych prób kolejnych składają się z komunikat z kolejki ponawiania do kolejki aplikacji prób dostarczenia do aplikacji, z opóźnieniem określony przez `retryCycleDelay` atrybutu. Liczba cykli ponownych prób jest określona przez `maxRetryCycles` atrybutu.|  
|Wartość TimeToLive|A <xref:System.TimeSpan> Określa, jak długo komunikaty zachowują poprawność zanim wygasną i są umieszczane w kolejce wiadomości utraconych. Wartość domyślna to 1.00:00:00, czyli 1 dzień.<br /><br /> Ten atrybut ma ustawioną upewnij się, że komunikaty o określonym terminie ważności nie nieodświeżone przetworzenia przez aplikacje odbierające. Wiadomości w kolejce, który nie jest używane przez aplikację odbierającą w określonym przedziale czasu jest określany wygasło. Wygasłe komunikaty są wysyłane do specjalnego kolejki o nazwie Kolejka utraconych wiadomości. Ustawiono lokalizację kolejki utraconych wiadomości `customDeadLetterQueue` atrybut lub odpowiednie domyślne oparte na gwarancji.|  
|Właściwość UseActiveDirectory|Wartość logiczna określająca, czy adresy kolejek powinny być konwertowane przy użyciu usługi Active Directory.<br /><br /> Adresy kolejki usługi MSMQ mogą składać się z nazw ścieżki lub bezpośrednich nazw formatu. Z bezpośredniej nazwy formatu usługi MSMQ jest rozpoznawany jako nazwę komputera, przy użyciu DNS, NetBIOS lub adres IP. Z nazwą ścieżki MSMQ jest rozpoznawany jako nazwy komputera przy użyciu usługi Active Directory. Domyślnie program Windows Communication Framework (WCF) w kolejce konwertuje transportu identyfikatora URI do bezpośredniej nazwy formatu kolejki wiadomości. Ustawienie tego atrybutu `true`, aplikację można określić, czy transport z kolejką powinien rozwiązać nazwę komputera, przy użyciu usługi Active Directory, a nie DNS, NetBIOS lub adres IP.|  
|UseMsmqTracing|Wartość logiczna określająca, czy komunikaty przetwarzane przez to powiązanie powinny być śledzone. Wartość domyślna to `false`.<br /><br /> Gdy śledzenie jest włączone, wiadomości raportów tworzonych i wysyłanych do kolejki raportu za każdym razem wiadomość opuszcza lub dociera do komputera usługi kolejkowania komunikatów.|  
|UseSourceJournal|Wartość logiczna określająca, czy kopie komunikatów przetwarzanych przez to powiązanie powinny być przechowywane w kolejce dziennika źródła. Wartość domyślna to `false`.<br /><br /> W kolejce aplikacji, które chcesz rejestrować komunikatów, które zostały zwolnione kolejki wychodzącej komputera można skopiować wiadomości do kolejki dziennika. Po komunikat pozostawia kolejek wychodzących i potwierdzenia otrzymania, czy wiadomość została odebrana na komputerze docelowym, kopia wiadomości jest przechowywana w kolejce dziennika systemu komputera wysyłającego.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<msmqTransportSecurity >](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqtransportsecurity.md)|Określa ustawienia zabezpieczenia transportu dla tego powiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Powiązanie >](../../../../../docs/framework/misc/binding.md)|Definiuje wszystkie możliwości powiązania niestandardowego powiązania.|  
  
## <a name="remarks"></a>Uwagi  
 `msmqTransport` Element włącza użytkownika można ustawić właściwości kolejkowany kanał komunikacyjny. Kolejkowany kanał komunikacyjny używa usługi kolejkowania komunikatów dla transportu.  
  
 Ten element powiązania jest domyślny element powiązania, używany przez powiązanie standardowe usługi kolejkowania komunikatów (`netMsmqBinding`).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.MsmqTransportElement>  
 <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Kolejki programu WCF](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [Transporty](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [Wybieranie transportu](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Rozszerzanie powiązań](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Powiązania niestandardowe](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
