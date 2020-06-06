---
title: <netTcpContextBinding>
ms.date: 03/30/2017
ms.assetid: 1d4715e1-5fff-4c3d-a226-18f21d0b30c4
ms.openlocfilehash: 360cdf76e013d085022f45eba5f8549e11cd68d3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "74140699"
---
# \<netTcpContextBinding>
Określa kontekst dla programu <xref:System.ServiceModel.NetTcpBinding> , który wymaga podpisania poziomu ochrony. ContextExchangeMechanism dla NetTcpContextBinding to SOAPHeader.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netTcpContextBinding>**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<netTcpContextBinding>
  <binding closeTimeout="TimeSpan"
           contextProtectionLevel="EncryptAndSign/None/Sign"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           listenBacklog="Integer"
           maxBufferPoolSize="integer"
           maxBufferSize="Integer"
           maxConnections="Integer"
           maxReceivedMessageSize="Integer"
           name="string"
           openTimeout="TimeSpan"
           portSharingEnabled="Boolean"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           transactionFlow="Boolean"
           transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004"
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan"
                     enabled="Boolean" />
    <security mode="Message/None/Transport/TransportWithCredential">
      <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
                 proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
                 realm="String"
                 defaultClientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
                 defaultProxyCredentialType="Basic/Digest/None/Ntlm/Windows"
                 defaultRealm="String" />
      <message clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               establishSecurityContext="Boolean"
               negotiateServiceCredential="Boolean" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netTcpContextBinding>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|closeTimeout|<xref:System.TimeSpan>Wartość określająca interwał czasu podanego do ukończenia operacji zamknięcia. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> . Wartość domyślna to 00:01:00.|  
|contextProtectionLevel|Prawidłowa wartość określająca <xref:System.Net.Security.ProtectionLevel> żądany poziom ochrony nagłówka SOAP używanego do propagowania informacji kontekstowych.  Wartość domyślna to <xref:System.Net.Security.ProtectionLevel.Sign>.|  
|hostnameComparisonMode|Określa tryb porównania nazw hostów HTTP używany do analizowania identyfikatorów URI. Ten atrybut jest typu <xref:System.ServiceModel.HostNameComparisonMode> , który wskazuje, czy nazwa hosta jest używana do uzyskiwania dostępu do usługi podczas dopasowywania identyfikatora URI. Wartość domyślna to <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> , co powoduje ignorowanie nazwy hosta w dopasowaniu.|  
|listenBacklog|Dodatnia liczba całkowita, która określa maksymalną liczbę kanałów oczekujących na akceptację odbiornika. Połączenia o przekroczeniu tego limitu są umieszczane w kolejce do momentu udostępnienia przestrzeni poniżej limitu. `connectionTimeout`Atrybut ogranicza czas, przez który klient będzie oczekiwał na połączenie przed wygenerowaniem wyjątku połączenia. Wartość domyślna to 10.|  
|maxBufferPoolSize|Liczba całkowita określająca maksymalny rozmiar puli buforów dla tego powiązania. Wartość domyślna to 512 * 1024 bajtów. Wiele części Windows Communication Foundation (WCF) używa buforów. Tworzenie i niszczenie buforów za każdym razem, gdy są używane, jest kosztowne i wyrzucanie elementów bezużytecznych dla buforów jest również kosztowne. W przypadku pul buforów można pobrać bufor z puli, użyć go i zwrócić do puli po zakończeniu. W ten sposób nie ma konieczności narzutu na tworzenie i niszczenie buforów.|  
|maxBufferSize|Dodatnia liczba całkowita, która określa maksymalny rozmiar buforu używany do przechowywania komunikatów w pamięci. Jeśli bufor jest pełny, nadmiarowe dane pozostają w podstawowym gnieździe do momentu ponownego uruchomienia buforu. Ta wartość nie może być mniejsza niż `maxReceivedMessageSize` atrybut. Wartość domyślna to 65536. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.|  
|maxConnections|Liczba całkowita określająca maksymalną liczbę połączeń wychodzących i przychodzących, które usługa zostanie utworzona/zaakceptowana. Połączenia przychodzące i wychodzące są liczone względem oddzielnego limitu określonego przez ten atrybut.<br /><br /> Połączenia przychodzące przekraczające limit są umieszczane w kolejce do momentu udostępnienia odstępu poniżej limitu.<br /><br /> Połączenia wychodzące przekraczające limit są umieszczane w kolejce do momentu udostępnienia odstępu poniżej limitu.<br /><br /> Wartość domyślna to 10.|  
|maxReceivedMessageSize|Dodatnia liczba całkowita, która określa maksymalny rozmiar wiadomości (w bajtach), w tym nagłówki, które można odbierać w kanale skonfigurowanym dla tego powiązania. Nadawca komunikatu przekraczającego ten limit otrzyma błąd protokołu SOAP. Odbiorca odrzuca komunikat i tworzy wpis zdarzenia w dzienniku śledzenia. Wartość domyślna to 65536.|  
|name|Ciąg zawierający nazwę konfiguracji powiązania. Ta wartość powinna być unikatowa, ponieważ jest używana jako identyfikacja dla powiązania. Począwszy od .NET Framework 4, powiązania i zachowania nie muszą mieć nazwy. Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).|  
|openTimeout|<xref:System.TimeSpan>Wartość, która określa przedział czasu podanego na zakończenie operacji otwarcia. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> . Wartość domyślna to 00:01:00.|  
|portSharingEnabled|Wartość logiczna określająca, czy włączone jest Udostępnianie portów TCP dla tego połączenia. W takim przypadku `false` każde powiązanie używa własnego portu wyłącznego. To ustawienie ma zastosowanie tylko do usług, ponieważ nie ma to znaczenia dla klientów.|  
|receiveTimeout|Wartość określająca <xref:System.TimeSpan> interwał czasu podanego do ukończenia operacji odbioru. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> . Wartość domyślna to 00:10:00.|  
|Właściwości SendTimeout|<xref:System.TimeSpan>Wartość określająca interwał czasu podanego do ukończenia operacji wysyłania. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> . Wartość domyślna to 00:01:00.|  
|transactionFlow|Wartość logiczna określająca, czy powiązanie obsługuje przepływy WS-Transactions. Wartość domyślna to `false`.|  
|Element TransactionProtocol|Określa protokół transakcji, który ma być używany z tym powiązaniem. Prawidłowe wartości to<br /><br /> -OleTransactions<br />- WSAtomicTransactionOctober2004<br /><br /> Wartość domyślna to OleTransactions. Ten atrybut jest typu <xref:System.ServiceModel.TransactionProtocol> .|  
|Elementy TransferMode|Wartość określająca <xref:System.ServiceModel.TransferMode> , czy komunikaty są buforowane, czy przesyłane strumieniowo, czy też żądanie lub odpowiedź.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<security>](security-of-nettcpbinding.md)|Definiuje ustawienia zabezpieczeń dla powiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.NetTcpSecurityElement> .|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|Definiuje ograniczenia złożoności komunikatów protokołu SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane za pomocą tego powiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .|  
|[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))|Określa, czy niezawodne sesje są nawiązywane między punktami końcowymi kanałów.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|Ten element zawiera kolekcję powiązań standardowych i niestandardowych.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.NetTcpBinding>
- <xref:System.ServiceModel.NetTcpContextBinding>
- <xref:System.ServiceModel.Configuration.NetTcpContextBindingElement>
- <xref:System.ServiceModel.Channels.ContextBindingElement>
- [\<netTcpBinding>](nettcpbinding.md)
- [Powiązania](../../../wcf/bindings.md)
- [Konfigurowanie powiązań dostarczanych przez system](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
