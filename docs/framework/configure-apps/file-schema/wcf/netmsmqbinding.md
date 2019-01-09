---
title: '&lt;netMsmqBinding&gt;'
ms.date: 03/30/2017
ms.assetid: a68b44d7-7799-43a3-9e63-f07c782810a6
ms.openlocfilehash: e0b8c75d8c3407e48d177a8085f601174b18a211
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147749"
---
# <a name="ltnetmsmqbindinggt"></a>&lt;netMsmqBinding&gt;
Definiuje Zakolejkowane powiązanie odpowiednie dla komunikacji między komputerami.  
  
 \<system.ServiceModel>  
\<powiązania >  
\<netMsmqBinding>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<netMsmqBinding>
  <binding closeTimeout="TimeSpan"
           customDeadLetterQueue="Uri"
           deadLetterQueue="Uri"
           durable="Boolean"
           exactlyOnce="Boolean"
           maxBufferPoolSize="Integer"
           maxReceivedMessageSize="Integer"
           maxRetryCycles="Integer"
           name="String"
           openTimeout="TimeSpan"
           poisonMessageHandling="Disabled/EnabledIfSupported"
           queueTransferProtocol="Native/Srmp/SrmpSecure"
           receiveErrorHandling="Drop/Fault/Move/Reject"
           receiveTimeout="TimeSpan"
           receiveRetryCount="Integer"
           rejectAfterLastRetry="Boolean"
           retryCycleDelay="TimeSpan"
           sendTimeout="TimeSpan"
           timeToLive="TimeSpan"
           useActiveDirectory="Boolean"
           useMsmqTracing="Boolean"
           useSourceJournal="Boolean">
    <security>
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="None/Windows/UserName/Certificate/InfoCard" />
      <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
                 msmqEncryptionAlgorithm="RC4Stream/AES"
                 msmqProtectionLevel="None/Sign/EncryptAndSign"
                 msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netMsmqBinding>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`closeTimeout`|A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji zamknięcia. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|`customDeadLetterQueue`|Identyfikator URI, który zawiera lokalizację kolejki utraconych wiadomości dla aplikacji, gdzie umieszcza komunikaty wygasły lub mają niepowodzeniem transferu lub dostarczania.<br /><br /> Kolejka utraconych wiadomości jest kolejką na Menedżer kolejki wysyłania aplikacji dla wygasłe wiadomości, które nie powiodły się do dostarczenia.<br /><br /> Identyfikator URI, który jest określony przez <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> musi używać schematu net.msmq.|  
|`deadLetterQueue`|A <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A> wartość określającą jakiego typu kolejki utraconych wiadomości, aby użyć, jeśli istnieje.<br /><br /> Kolejki utraconych wiadomości jest miejscem, w którym będą przekazywane wiadomości, które nie powiodły się dostarczane do aplikacji.<br /><br /> Komunikaty, które wymagają `exactlyOnce` assurance (czyli `exactlyOnce` ma ustawioną wartość atrybutu `true`), tego atrybutu, wartość domyślna to systemowe kolejki utraconych wiadomości transakcyjnych w usłudze MSMQ.<br /><br /> Komunikaty, które wymagają żadnych zapewnień, ten atrybut są domyślnie `null`.|  
|`durable`|Wartość logiczna wskazująca, czy komunikat jest trwałe lub nietrwała w kolejce. Trwały komunikat przeżyje awarii menedżera kolejki, a komunikat volatile nie. Volatile komunikaty są przydatne, jeśli aplikacje wymagają mniejsze opóźnienia, które mogą tolerować okazjonalne utracone wiadomości. Jeśli `exactlyOnce` ma ustawioną wartość atrybutu `true`, komunikaty muszą być trwałe. Wartość domyślna to `true`.|  
|`exactlyOnce`|Wartość logiczna wskazująca, czy każdy komunikat przetwarzane przez to powiązanie jest dostarczany tylko raz. Nadawca będą powiadamiani dostarczania błędów. Gdy `durable` jest `false`, ten atrybut jest ignorowany i wiadomości są przekazywane bez zapewnienia dostarczania. Wartość domyślna to `true`. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A>.|  
|`maxBufferPoolSize`|Liczba całkowita określająca maksymalny rozmiar puli buforów dla tego powiązania. Wartość domyślna to 8.|  
|`maxReceivedMessageSize`|Dodatnia liczba całkowita określająca maksymalny rozmiar komunikatu, w bajtach, włącznie z nagłówkami, który jest przetwarzany przez to wiązanie. Nadawca wiadomości przekroczenie tego limitu zostanie wyświetlony błąd protokołu SOAP. Należy określić odbiorcę porzuca wiadomość i tworzy wpis zdarzenia w dzienniku śledzenia. Wartość domyślna to 65536. Powiązana rozmiar komunikatu ma to ograniczyć narażenie na ataki przeprowadzenie ataku typu "odmowa usługi" (DoS).|  
|`maxRetryCycles`|Liczba całkowita, która wskazuje liczbę ponownych prób cyklów używane przez funkcję wykrywania poison komunikatu. Komunikat staje się zarządzanie skażonymi komunikatami, gdy zakończy się niepowodzeniem ze wszystkich prób dostarczenia wszystkich cykli. Wartość domyślna to 3. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A>.|  
|`name`|Atrybut wymagany. Ciąg, który zawiera nazwę konfiguracji powiązania. Wartość ta powinna być unikatowy, ponieważ jest używany jako identyfikator dla wiązania. Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę. Aby uzyskać więcej informacji o domyślnej konfiguracji i powiązania pustego oraz zachowań, zobacz [uproszczona konfiguracja](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|`openTimeout`|A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji Otwórz. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|`QueueTransferProtocol`|Nieprawidłowy <xref:System.ServiceModel.QueueTransferProtocol> wartość, która określa zakolejkowany kanał transportowy komunikacji, który używa tego powiązania. Usługa MSMQ nie obsługuje usługi Active Directory adresowania, korzystając z protokołu SOAP Reliable Messaging Protocol. W związku z tym, nie należy ustawiać dla tego atrybutu `Srmp` lub `Srmps` podczas `useActiveDirectory` ma ustawioną wartość atrybutu `true`.|  
|`receiveErrorHandling`|A <xref:System.ServiceModel.ReceiveErrorHandling> wartość, która określa sposób obsługi poison i nondispatchable wiadomości.|  
|`receiveRetryCount`|Liczba całkowita określająca maksymalną liczbę razy menedżera kolejek powinien próbować wysłać wiadomość przed przeniesieniem jej do kolejki ponownych prób.|  
|`receiveTimeout`|A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji odbierania. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:10:00.|  
|`retryCycleDelay`|Wartość przedziału czasu, który określa czas opóźnienia między cykle przy próbie dostarczenia komunikatu, którego nie można dostarczyć natychmiast. Wartość określa tylko minimalny czas oczekiwania, ponieważ rzeczywisty czas może być dłużej. Wartość domyślna to 00:10:00. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A>.|  
|`sendTimeout`|A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji wysyłania. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|`timeToLive`|Wartość przedziału czasu, który określa, jak długo komunikaty są prawidłowe, zanim wygasną i umieścić w kolejce wiadomości utraconych. Wartość domyślna to 1.00:00:00.<br /><br /> Ten atrybut jest ustawiony, aby upewnić się, że komunikaty zależne od czasu nie staną się przestarzałe zanim zostaną one przetworzone przez aplikacje odbierające. Komunikat w kolejce, który nie jest używane przez aplikację odbierającą w określonym przedziale czasu jest nazywany wygasnąć. Wygasłe komunikaty są wysyłane do kolejki specjalne o nazwie Kolejka utraconych wiadomości. Lokalizacja kolejkę z utraconymi została ustawiona za pomocą `DeadLetterQueue` atrybut lub odpowiednie domyślne na podstawie gwarancji.|  
|`usingActiveDirectory`|Wartość logiczna określająca, jeśli adresy kolejki powinny być konwertowane przy użyciu usługi Active Directory.<br /><br /> Adresy kolejki usługi MSMQ mogą składać się z nazw ścieżki lub bezpośrednich nazw formatu. Z bezpośrednią nazwą formatu usługa MSMQ jest rozpoznawana jako nazwę komputera, przy użyciu DNS, NetBIOS lub adres IP. Z nazwą ścieżki MSMQ jest rozpoznawana jako nazwę komputera, przy użyciu usługi Active Directory.<br /><br /> Domyślnie program Windows Communication Foundation (WCF) w kolejce konwertuje transportu kolejki komunikatów, która z bezpośrednią nazwą formatu identyfikatora URI. Ustawiając `UseActiveDirectory` właściwości na wartość true, aplikacja może określić czy umieszczonych w kolejce transportu powinien rozwiązać nazwę komputera, przy użyciu usługi Active Directory, a nie DNS, NetBIOS lub adresu IP.|  
|`useMsmqTracing`|Wartość logiczna określająca, czy komunikaty przetwarzane przez to powiązanie powinny być śledzone. Wartość domyślna to `false`. Po włączeniu funkcji śledzenia komunikatów raportów tworzonych i wysyłanych do kolejki raportu za każdym razem wiadomości pozostawia lub dociera do komputera usługi kolejkowania komunikatów.|  
|`useSourceJournal`|Wartość logiczna, która określa kopie komunikatów przetwarzanych przez to powiązanie powinny być przechowywane w dzienniku źródłowego. Wartość domyślna to `false`.<br /><br /> Umieszczonych w kolejce aplikacji, których chcesz prowadzić rejestr, wiadomości, które pozostało w kolejce wychodzącej komputera można skopiować komunikaty do kolejki dziennika. Gdy wiadomość pozostawia kolejek wychodzących i potwierdzenia otrzymania, czy wiadomość została odebrana na komputerze docelowym, kopia wiadomości są przechowywane w kolejce dziennika systemu komputera wysyłającego.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<readerQuotas>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[\<Zabezpieczenia >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|Definiuje ustawienia zabezpieczeń dla wiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<powiązania >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.|  
  
## <a name="remarks"></a>Uwagi  
 `netMsmqBinding` Powiązania zapewnia obsługę usługi kolejkowania wiadomości przy użyciu Microsoft usługi kolejkowania komunikatów (MSMQ) jako transportu i umożliwia obsługę dla aplikacji luźno powiązanych, izolacja błędów operacji bilansowania i odłączonych. Omówienie tych funkcji, zobacz [kolejki programu WCF](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md).  
  
## <a name="example"></a>Przykład  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <netMsmqBinding>
        <binding closeTimeout="00:00:10"
                 openTimeout="00:00:20"
                 receiveTimeout="00:00:30"
                 sendTimeout="00:00:40"
                 deadLetterQueue="net.msmq://localhost/blah"
                 durable="true"
                 exactlyOnce="true"
                 maxReceivedMessageSize="1000"
                 maxRetries="11"
                 maxRetryCycles="12"
                 poisonMessageHandling="Disabled"
                 rejectAfterLastRetry="false"
                 retryCycleDelay="00:05:55"
                 timeToLive="00:11:11"
                 sourceJournal="true"
                 useMsmqTracing="true"
                 useActiveDirectory="true">
          <security>
            <message clientCredentialType="Windows" />
          </security>
        </binding>
      </netMsmqBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.NetMsmqBinding>  
 <xref:System.ServiceModel.Configuration.NetMsmqBindingElement>  
 [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurowanie powiązań dostarczanych przez system](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Konfigurowanie usług i klientów za pomocą powiązań](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [Kolejki programu WCF](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
