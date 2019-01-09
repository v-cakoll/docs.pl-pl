---
title: '&lt;netTcpContextBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 1d4715e1-5fff-4c3d-a226-18f21d0b30c4
ms.openlocfilehash: da769e57a44880d5050b06a8e2a3d317daff35d6
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146072"
---
# <a name="ltnettcpcontextbindinggt"></a>&lt;netTcpContextBinding&gt;
Określa kontekst dla <xref:System.ServiceModel.NetTcpBinding> wymaga, aby poziom ochrony były podpisane. Wartość właściwości contextExchangeMechanism dla NetTcpContextBinding jest SOAPHeader.  
  
 \<system.ServiceModel>  
\<powiązania >  
\<netTcpContextBinding>  
  
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
|closeTimeout|A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji zamknięcia. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|contextProtectionLevel|Nieprawidłowy <xref:System.Net.Security.ProtectionLevel> wartość, która określa poziom ochrony żądany nagłówek SOAP, wykorzystywany do propagowania informacje o kontekście.  Wartość domyślna to `Sign`.|  
|hostnameComparisonMode|Określa tryb porównywania nazwy hosta HTTP używany do analizowania identyfikatorów URI. Ten atrybut jest typu `System.ServiceModel.HostnameComparisonMode`, która wskazuje, czy nazwa hosta jest używana w celu dotarcia do usługi podczas dopasowywania identyfikatora URI. Wartość domyślna to `StrongWildcard`, który ignoruje hostname dopasowania.|  
|listenBacklog|Dodatnia liczba całkowita, określająca maksymalną liczbę kanałów, które oczekuje na zatwierdzenie na odbiorniku. Połączenia przekraczające ten limit są umieszczane w kolejce, dopóki miejsce poniżej limitu staje się dostępna. `connectionTimeout` Atrybut ogranicza czas, klient będzie czekać połączenia zanim zostanie zgłoszony wyjątek połączenia. Wartość domyślna wynosi 10.|  
|maxBufferPoolSize|Liczba całkowita określająca maksymalny rozmiar puli buforów dla tego powiązania. Wartość domyślna to 512 * 1024 bajty. Wiele części programu Windows Communication Foundation (WCF) za pomocą buforów. Tworzenie i niszczenie buforów za każdym razem, gdy są one używane jest kosztowne, a także jest kosztowne wyrzucania elementów bezużytecznych dla buforów. Dzięki pulom buforu zająć buforu z puli, go używać i przywrócić go do puli, gdy wszystko będzie gotowe. Ten sposób unika się obciążenie tworzeniem i likwidowaniem buforów.|  
|wartość maxBufferSize|Dodatnia liczba całkowita, która określa maksymalny rozmiar w bajtach buforu używany do przechowywania komunikatów w pamięci. Jeśli bufor jest pełna, nadmiar danych pozostaje w podstawowej gniazda, aż buforu, będzie miał miejsce ponownie. Ta wartość nie może być mniejsza niż `maxReceivedMessageSize` atrybutu. Wartość domyślna to 65536. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.|  
|MaxConnections|Liczba całkowita określająca maksymalną liczbę połączeń wychodzące i przychodzące usługa tworzenia/akceptuje. Połączenia przychodzące i wychodzące są przeliczane względem oddzielne limit określony przez atrybut.<br /><br /> Połączenia przychodzące poza limitem zostaną umieszczone w kolejce, dopóki miejsce poniżej limitu staje się dostępna.<br /><br /> Połączenia wychodzące poza limitem zostaną umieszczone w kolejce, dopóki miejsce poniżej limitu staje się dostępna.<br /><br /> Wartość domyślna wynosi 10.|  
|maxReceivedMessageSize|Dodatnia liczba całkowita, która określa maksymalny rozmiar komunikatu, w bajtach, włącznie z nagłówkami, które może zostać odebrany w kanale skonfigurowany tym wiązaniem. Nadawca wiadomości przekroczenie tego limitu zostanie wyświetlony błąd protokołu SOAP. Należy określić odbiorcę porzuca wiadomość i tworzy wpis zdarzenia w dzienniku śledzenia. Wartość domyślna to 65536.|  
|nazwa|Ciąg, który zawiera nazwę konfiguracji powiązania. Wartość ta powinna być unikatowy, ponieważ jest używany jako identyfikator dla wiązania. Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę. Aby uzyskać więcej informacji o domyślnej konfiguracji i powiązania pustego oraz zachowań, zobacz [uproszczona konfiguracja](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|openTimeout|A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji Otwórz. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|portSharingEnabled|Wartość logiczna określająca, czy włączone jest udostępnianie portów TCP dla tego połączenia. Jeśli jest to `false`, wyłączny portu korzysta z każdego powiązania. To ustawienie jest odpowiednie tylko dla usług, ponieważ nie dotyczy to klientów.|  
|receiveTimeout|A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji odbierania. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:10:00.|  
|sendTimeout|A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji wysyłania. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|transactionFlow|Wartość logiczna określająca, czy powiązanie obsługuje płynące WS-transakcji. Wartość domyślna to `false`.|  
|Element transactionProtocol|Określa protokół transakcji do użycia z tym powiązaniem. Prawidłowe wartości to:<br /><br /> -OleTransactions<br />-WSAtomicTransactionOctober2004<br /><br /> Wartość domyślna to OleTransactions. Ten atrybut jest typu <xref:System.ServiceModel.TransactionProtocol>.|  
|Tryb transferu|A <xref:System.ServiceModel.TransferMode> wartość określającą, czy komunikaty są buforowane lub przesyłane strumieniowo lub żądania lub odpowiedzi.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Zabezpieczenia >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|Definiuje ustawienia zabezpieczeń dla wiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>.|  
|[\<readerQuotas>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[reliableSession](https://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|Określa, jeśli niezawodnej sesji są ustanawiane między punktami końcowymi kanału.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<powiązania >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.NetTcpBinding>  
 <xref:System.ServiceModel.NetTcpContextBinding>  
 <xref:System.ServiceModel.Configuration.NetTcpContextBindingElement>  
 <xref:System.ServiceModel.Channels.ContextBindingElement>  
 [\<netTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurowanie powiązań dostarczanych przez system](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Konfigurowanie usług i klientów za pomocą powiązań](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)
