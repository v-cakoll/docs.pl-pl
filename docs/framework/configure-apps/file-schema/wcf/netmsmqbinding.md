---
title: '&lt;netMsmqBinding&gt;'
ms.date: 03/30/2017
ms.assetid: a68b44d7-7799-43a3-9e63-f07c782810a6
ms.openlocfilehash: d4d28a799acecd335d8155a7ae67b6365b3f0023
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltnetmsmqbindinggt"></a>&lt;netMsmqBinding&gt;
Definiuje Zakolejkowane powiązanie odpowiednie dla komunikacji między komputerami.  
  
 \<system.ServiceModel>  
\<powiązania >  
\<netMsmqBinding>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<netMsmqBinding>  
    <binding   
       closeTimeout="TimeSpan"   
       customDeadLetterQueue="Uri"  
       deadLetterQueue="Uri"  
       durable="Boolean"  
       exactlyOnce="Boolean"   
       maxBufferPoolSize="Integer"  
       maxReceivedMessageSize"Integer"  
       maxRetryCycles="Integer"   
       name="string"   
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
       useMsmqTracing="Boolean  
       useSourceJournal="Boolean"  
          <security>  
                  <message    
                        algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            clientCredentialType="None/Windows/UserName/Certificate/InfoCard "/>  
                  <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"  
            msmqEncryptionAlgorithm="RC4Stream/AES"  
            msmqProtectionLevel="None/Sign/EncryptAndSign"  
            msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
          </security>  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />   </binding></netMsmqBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`closeTimeout`|A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji zamknięcia. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|`customDeadLetterQueue`|Identyfikator URI zawiera lokalizację kolejki utraconych wiadomości dla każdej aplikacji, gdzie umieścić są komunikaty wygasłe, lub które nie przeszły przesłanie bądź dostarczenie.<br /><br /> Kolejki utraconych wiadomości jest kolejką na aplikację wysyłającą wygasłych komunikatów, które nie można dostarczyć do menedżera kolejki.<br /><br /> Identyfikator URI, który jest określony przez <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> musi być stosowany schemat net.msmq.|  
|`deadLetterQueue`|A <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A> wartość określającą typu kolejki utraconych wiadomości, aby użyć, jeśli istnieje.<br /><br /> Kolejki utraconych wiadomości jest miejscem, w którym będą przekazywane wiadomości, które nie powiodły się do dostarczenia do aplikacji.<br /><br /> Komunikaty, które wymagają `exactlyOnce` gwarancji (to znaczy `exactlyOnce` atrybut ma ustawioną `true`), tego atrybutu wartością domyślną systemowe kolejki utraconych wiadomości transakcyjnych w usłudze MSMQ.<br /><br /> Komunikaty, które wymagają nie zapewnień, domyślna tego atrybutu `null`.|  
|`durable`|Wartość logiczna wskazująca, czy komunikat jest trwałe lub zmienne w kolejce. Trwałe komunikat przeżyje awarii menedżera kolejki, a komunikat nietrwałe nie. Volatile wiadomości są przydatne, gdy aplikacje wymagają mniejsze opóźnienia i może tolerować okazjonalne utratą komunikatów. Jeśli `exactlyOnce` atrybut ma ustawioną `true`, komunikaty muszą być trwałe. Wartość domyślna to `true`.|  
|`exactlyOnce`|Wartość logiczna wskazująca, czy każdy komunikat przetwarzane przez to powiązanie jest dostarczany tylko raz. Nadawca będą powiadamiani niepowodzeń dostarczania. Gdy `durable` jest `false`, ten atrybut jest ignorowany i wiadomości są przekazywane bez gwarancji dostarczenia. Wartość domyślna to `true`. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A>.|  
|`maxBufferPoolSize`|Liczba całkowita określająca maksymalny rozmiar puli buforów dla tego powiązania. Wartość domyślna to 8.|  
|`maxReceivedMessageSize`|Dodatnia liczba całkowita określająca maksymalny rozmiar wiadomości, w bajtach, włącznie z nagłówkami, które są przetwarzane przez to powiązanie. Nadawcy wiadomości przekracza ten limit, zostanie wyświetlony błąd protokołu SOAP. Odbiornik porzuca wiadomości i tworzy wpis zdarzenia w dzienniku śledzenia. Wartość domyślna to 65536. To powiązana rozmiar wiadomości ma na celu ograniczenia narażenia na ataki przeprowadzenie ataku typu "odmowa usługi" (DoS).|  
|`maxRetryCycles`|Liczba całkowita, która wskazuje liczbę cykli ponownych prób używane przez funkcję wykrywania poison wiadomości. Komunikat staje się Trująca wiadomość po błędzie wszystkich kolejnymi próbami dostarczenia wszystkich cykli. Wartość domyślna to 3. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A>.|  
|`name`|Atrybut wymagany. Ciąg zawierający nazwę konfiguracji powiązania. Wartość ta powinna być unikatowa, ponieważ jest używany jako identyfikator dla tego powiązania. Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę. Aby uzyskać więcej informacji o konfiguracji domyślnej i bez powiązania i zachowania, zobacz [uproszczony konfiguracji](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|`openTimeout`|A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji otwarcia. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|`QueueTransferProtocol`|Prawidłowy <xref:System.ServiceModel.QueueTransferProtocol> wartość, która określa zakolejkowany kanał transportowy komunikacji, który używa tego powiązania. Usługa MSMQ nie obsługuje adresów usługi Active Directory przy użyciu protokołu SOAP Reliable Messaging Protocol. W związku z tym nie należy ustawiać ten atrybut `Srmp` lub `Srmps` podczas `u``seActiveDirectory` atrybut ma ustawioną `true`.|  
|`receiveErrorHandling`|A <xref:System.ServiceModel.ReceiveErrorHandling> wartość, która określa sposób obsługi poison i nondispatchable wiadomości.|  
|`receiveRetryCount`|Liczba całkowita określająca maksymalną liczbę razy menedżera kolejek powinien próbować wysłać wiadomość przed przeniesieniem ich do kolejki ponawiania.|  
|`receiveTimeout`|A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji odbioru. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:10:00.|  
|`retryCycleDelay`|Wartość TimeSpan określający czas opóźnienia między kolejnymi próbami dostarczenia komunikatu, którego nie można było dostarczyć natychmiast. Wartość określa tylko minimalny czas oczekiwania, czas oczekiwania rzeczywiste mogą być dłuższe. Wartość domyślna to 00:10:00. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A>.|  
|`sendTimeout`|A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji wysyłania. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|`timeToLive`|Wartość TimeSpan Określa, jak długo komunikaty są prawidłowe, zanim wygasną i umieścić w kolejce wiadomości utraconych. Wartość domyślna to 1.00:00:00.<br /><br /> Ten atrybut ma ustawioną upewnij się, że komunikaty o określonym terminie ważności nie nieodświeżone przetworzenia przez aplikacje odbierające. Wiadomości w kolejce, który nie jest używane przez aplikację odbierającą w określonym przedziale czasu jest określany wygasło. Wygasłe komunikaty są wysyłane do specjalnego kolejki o nazwie Kolejka utraconych wiadomości. Ustawiono lokalizację kolejki utraconych wiadomości `DeadLetterQueue` atrybut lub odpowiednie domyślne oparte na gwarancji.|  
|`usingActiveDirectory`|Wartość logiczna określająca, czy adresy kolejek powinny być konwertowane przy użyciu usługi Active Directory.<br /><br /> Adresy kolejki usługi MSMQ mogą składać się z nazw ścieżki lub bezpośrednich nazw formatu. Z bezpośredniej nazwy formatu usługi MSMQ jest rozpoznawany jako nazwę komputera, przy użyciu DNS, NetBIOS lub adres IP. Z nazwą ścieżki MSMQ jest rozpoznawany jako nazwy komputera przy użyciu usługi Active Directory.<br /><br /> Domyślnie program Windows Communication Foundation (WCF) w kolejce konwertuje transportu identyfikatora URI do bezpośredniej nazwy formatu kolejki wiadomości. Przez ustawienie `UseActiveDirectory` właściwości na wartość true, aplikacji można określić, czy transport z kolejką powinien rozwiązać nazwę komputera, przy użyciu usługi Active Directory, a nie DNS, NetBIOS lub adres IP.|  
|`useMsmqTracing`|Wartość logiczna określająca, czy komunikaty przetwarzane przez to powiązanie powinny być śledzone. Wartość domyślna to `false`. Gdy śledzenie jest włączone, wiadomości raportów tworzonych i wysyłanych do kolejki raportu za każdym razem wiadomość opuszcza lub dociera do komputera usługi kolejkowania komunikatów.|  
|`useSourceJournal`|Wartość logiczna, która określa kopie komunikatów przetwarzanych przez to powiązanie powinny być przechowywane w dzienniku źródłowego. Wartość domyślna to `false`.<br /><br /> W kolejce aplikacji, które chcesz rejestrować komunikatów, które zostały zwolnione kolejki wychodzącej komputera można skopiować wiadomości do kolejki dziennika. Po komunikat pozostawia kolejek wychodzących i potwierdzenia otrzymania, czy wiadomość została odebrana na komputerze docelowym, kopia wiadomości jest przechowywana w kolejce dziennika systemu komputera wysyłającego.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<readerQuotas>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[\<Zabezpieczenia >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|Definiuje ustawienia zabezpieczeń dla powiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<powiązania >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.|  
  
## <a name="remarks"></a>Uwagi  
 `netMsmqBinding` Powiązanie zapewnia obsługę dla usługi kolejkowania wiadomości dzięki wykorzystaniu Microsoft usługi kolejkowania komunikatów (MSMQ) jako transportu i włącza obsługę dla luźno powiązanych aplikacji, izolacji niepowodzenia operacji bilansowania i odłączone. Aby uzyskać informacje dotyczące tych funkcji, zobacz [kolejki programu WCF](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md).  
  
## <a name="example"></a>Przykład  
  
```xml  
<configuration>  
<system.ServiceModel>  
    <bindings>  
           <netMsmqBinding>  
                <binding   
                         closeTimeout="00:00:10"   
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
 [Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [Kolejki programu WCF](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
