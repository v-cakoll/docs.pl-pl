---
title: <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: a68b44d7-7799-43a3-9e63-f07c782810a6
ms.openlocfilehash: 7456c6373c64e07b73e15e7e2bb229dce4032121
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "74140750"
---
# \<netMsmqBinding>
Definiuje powiązanie kolejkowane odpowiednie dla komunikacji między komputerami.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netMsmqBinding>**  
  
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
|`closeTimeout`|<xref:System.TimeSpan>Wartość określająca interwał czasu podanego do ukończenia operacji zamknięcia. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> . Wartość domyślna to 00:01:00.|  
|`customDeadLetterQueue`|Identyfikator URI, który zawiera lokalizację kolejki utraconych wiadomości dla aplikacji, w której znajdują się komunikaty, które wygasły lub które nie zostały przesłane.<br /><br /> Kolejka utraconych wiadomości jest kolejką w Menedżerze kolejek aplikacji wysyłającej dla wygasłych komunikatów, których dostarczenie nie powiodło się.<br /><br /> Identyfikator URI określony przez <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> musi używać schematu net. MSMQ.|  
|`deadLetterQueue`|<xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A>Wartość określająca typ używanej kolejki utraconych wiadomości, jeśli istnieje.<br /><br /> Kolejka utraconych wiadomości jest miejscem, w którym nie można przesłać komunikatów, które nie zostały dostarczone do aplikacji.<br /><br /> W przypadku komunikatów, które wymagają `exactlyOnce` zapewnienia pewności (oznacza to, że `exactlyOnce` atrybut jest ustawiony na `true` ), ten atrybut domyślnie jest kolejką utraconych wiadomości transakcyjnych w całej systemie w usłudze MSMQ.<br /><br /> W przypadku wiadomości, które nie wymagają żadnych gwarancji, ten atrybut domyślnie przyjmuje wartość `null` .|  
|`durable`|Wartość logiczna wskazująca, czy komunikat jest trwały, czy nietrwały w kolejce. Trwały komunikat przeżyje awarię Menedżera kolejki, podczas gdy nietrwały komunikat nie jest. Komunikaty nietrwałe są przydatne, gdy aplikacje wymagają mniejszych opóźnień i mogą tolerować sporadycznie utracone komunikaty. Jeśli `exactlyOnce` atrybut jest ustawiony na `true` , komunikaty muszą być trwałe. Wartość domyślna to `true`.|  
|`exactlyOnce`|Wartość logiczna wskazująca, czy każdy komunikat przetwarzany przez to powiązanie jest dostarczany tylko raz. Nadawca zostanie powiadomiony o błędach dostawy. Gdy `durable` jest `false` , ten atrybut jest ignorowany i komunikaty są przesyłane bez gwarancji dostarczania. Wartość domyślna to `true`. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A>.|  
|`maxBufferPoolSize`|Liczba całkowita określająca maksymalny rozmiar puli buforów dla tego powiązania. Wartość domyślna to 8.|  
|`maxReceivedMessageSize`|Dodatnia liczba całkowita, która określa maksymalny rozmiar komunikatu (w bajtach, włącznie z nagłówkami) przetwarzanych przez to powiązanie. Nadawca komunikatu przekraczającego ten limit otrzyma błąd protokołu SOAP. Odbiorca odrzuca komunikat i tworzy wpis zdarzenia w dzienniku śledzenia. Wartość domyślna to 65536. Ta wartość związana z rozmiarem komunikatu jest przeznaczona do ograniczania narażenia na ataki typu "odmowa usługi" (DoS).|  
|`maxRetryCycles`|Liczba całkowita, która wskazuje liczbę ponownych prób używanych przez funkcję wykrywania skażonych komunikatów. Komunikat jest skażony komunikatem, gdy nie powiedzie się wszystkie próby dostarczenia wszystkich cykli. Wartość domyślna to 3. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A>.|  
|`name`|Atrybut wymagany. Ciąg zawierający nazwę konfiguracji powiązania. Ta wartość powinna być unikatowa, ponieważ jest używana jako identyfikacja dla powiązania. Począwszy od .NET Framework 4, powiązania i zachowania nie muszą mieć nazwy. Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).|  
|`openTimeout`|<xref:System.TimeSpan>Wartość, która określa przedział czasu podanego na zakończenie operacji otwarcia. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> . Wartość domyślna to 00:01:00.|  
|`QueueTransferProtocol`|Prawidłowa wartość określająca <xref:System.ServiceModel.QueueTransferProtocol> transport kanału komunikacyjnego znajdującego się w kolejce, który jest wykorzystywany przez to powiązanie. Usługa MSMQ nie obsługuje adresowania Active Directory w przypadku korzystania z protokołu niezawodnej obsługi komunikatów protokołu SOAP. W związku z tym nie należy ustawiać tego atrybutu na `Srmp` lub `Srmps` , gdy `useActiveDirectory` atrybut jest ustawiony na `true` .|  
|`receiveErrorHandling`|Wartość określająca <xref:System.ServiceModel.ReceiveErrorHandling> sposób obsługi komunikatów trujących i niewysyłających.|  
|`receiveRetryCount`|Liczba całkowita określająca maksymalną liczbę prób wysłania komunikatu przez Menedżera kolejki przed przekazaniem go do kolejki ponownych prób.|  
|`receiveTimeout`|Wartość określająca <xref:System.TimeSpan> interwał czasu podanego do ukończenia operacji odbioru. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> . Wartość domyślna to 00:10:00.|  
|`retryCycleDelay`|Wartość TimeSpan określająca czas opóźnienia między kolejnymi próbami dostarczenia komunikatu, którego nie można było dostarczyć natychmiast. Wartość definiuje tylko minimalny czas oczekiwania, ponieważ rzeczywisty czas oczekiwania może być dłuższy. Wartość domyślna to 00:10:00. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A>.|  
|`sendTimeout`|<xref:System.TimeSpan>Wartość określająca interwał czasu podanego do ukończenia operacji wysyłania. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> . Wartość domyślna to 00:01:00.|  
|`timeToLive`|Wartość TimeSpan określająca czas ważności komunikatów przed ich wygaśnięciem i umieszczona w kolejce utraconych wiadomości. Wartość domyślna to 1,00:00:00.<br /><br /> Ten atrybut jest ustawiony w celu zapewnienia, że komunikaty zależne od czasu nie stają się nieodświeżone przed przetworzeniem przez aplikacje do odebrania. Wiadomość w kolejce, która nie jest używana przez aplikację otrzymującą w określonym przedziale czasu, jest uznawana za wygasłą. Wygasłe komunikaty są wysyłane do kolejki specjalnej zwanej kolejką utraconych wiadomości. Lokalizacja kolejki utraconych wiadomości jest ustawiana z `DeadLetterQueue` atrybutem lub z odpowiednim ustawieniem domyślnym w oparciu o gwarancje.|  
|`usingActiveDirectory`|Wartość logiczna określająca, czy adresy kolejek mają być konwertowane przy użyciu Active Directory.<br /><br /> Adresy kolejki MSMQ mogą składać się z nazw ścieżek lub bezpośrednich nazw formatu. W przypadku bezpośredniej nazwy formatu usługa MSMQ rozpoznaje nazwę komputera przy użyciu systemu DNS, NetBIOS lub IP. Przy użyciu nazwy ścieżki usługa MSMQ rozpoznaje nazwę komputera przy użyciu Active Directory.<br /><br /> Domyślnie usługa Windows Communication Foundation (WCF) w kolejce transport konwertuje identyfikator URI kolejki komunikatów na nazwę formatu bezpośredniego. Ustawiając `UseActiveDirectory` Właściwość na wartość true, aplikacja może określić, że transport w kolejce powinien rozpoznać nazwę komputera przy użyciu Active Directory, a nie DNS, NetBIOS lub IP.|  
|`useMsmqTracing`|Wartość logiczna określająca, czy komunikaty przetwarzane przez to powiązanie powinny być śledzone. Wartość domyślna to `false`. Gdy śledzenie jest włączone, wiadomości raportów są tworzone i wysyłane do kolejki raportu za każdym razem, gdy komunikat opuszcza lub dociera do komputera usługi kolejkowania komunikatów.|  
|`useSourceJournal`|Wartość logiczna określająca kopie komunikatów przetwarzanych przez to powiązanie powinny być przechowywane w dzienniku źródłowym. Wartość domyślna to `false`.<br /><br /> W kolejce aplikacje, które chcą zachować rekord komunikatów, które zostały pozostawione przez kolejkę wychodzącą komputera, mogą kopiować komunikaty do kolejki dziennika. Gdy wiadomość opuszcza kolejkę wychodzącą i otrzyma potwierdzenie odebrania komunikatu na komputerze docelowym, kopia komunikatu jest przechowywana w kolejce dziennika systemowego komputera wysyłającego.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|Definiuje ograniczenia złożoności komunikatów protokołu SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane za pomocą tego powiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .|  
|[\<security>](security-of-netmsmqbinding.md)|Definiuje ustawienia zabezpieczeń dla powiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement> .|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|Ten element zawiera kolekcję powiązań standardowych i niestandardowych.|  
  
## <a name="remarks"></a>Uwagi  
 `netMsmqBinding`Powiązanie zapewnia obsługę kolejkowania, wykorzystując usługę kolejkowania komunikatów (MSMQ) jako Transport i umożliwia obsługę luźno sprzężonych aplikacji, izolacja niepowodzeń, przeciążania obciążeń i rozłączonych operacji. Dyskusje na temat tych funkcji znajdują się [w temacie Queues in WCF](../../../wcf/feature-details/queues-in-wcf.md).  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.NetMsmqBinding>
- <xref:System.ServiceModel.Configuration.NetMsmqBindingElement>
- [\<binding>](bindings.md)
- [Powiązania](../../../wcf/bindings.md)
- [Konfigurowanie powiązań dostarczanych przez system](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [Kolejki programu WCF](../../../wcf/feature-details/queues-in-wcf.md)
