---
title: <netTcpBinding>
description: Reprezentuje bezpieczne, niezawodne i zoptymalizowane powiązanie przeznaczone tylko dla komunikacji między komputerami WCF przy użyciu protokołu TCP. Niezawodna obsługa komunikatów jest domyślnie wyłączona.
ms.date: 03/30/2017
helpviewer_keywords:
- netTcpBinding Element
ms.assetid: 5c5104a7-8754-4335-8233-46a45322503e
ms.openlocfilehash: 95c2c691bf328050f3d189c790d111d2fdeb1bb0
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244000"
---
# \<netTcpBinding>

Określa bezpieczne, niezawodne i zoptymalizowane powiązanie odpowiednie dla komunikacji między komputerami. Domyślnie generuje stos komunikacji środowiska uruchomieniowego z zabezpieczeniami systemu Windows w celu zabezpieczenia i uwierzytelniania komunikatów, protokołu TCP na potrzeby dostarczania komunikatów i kodowania komunikatów binarnych.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netTcpBinding>**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<netTcpBinding>
  <binding closeTimeout="TimeSpan"
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
    <security mode="None/Transport/Message/Both">
      <message clientCredentialType="None/Windows/UserName/Certificate/CardSpace"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" />
      <transport clientCredentialType="None/Windows/Certificate"
                 protectionLevel="None/Sign/EncryptAndSign" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netTcpBinding>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`closeTimeout`|<xref:System.TimeSpan>Wartość określająca interwał czasu podanego do ukończenia operacji zamknięcia. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> . Wartość domyślna to 00:01:00.|  
|`hostNameComparisonMode`|Określa tryb porównania nazw hostów HTTP używany do analizowania identyfikatorów URI. Ten atrybut jest typu <xref:System.ServiceModel.HostNameComparisonMode> , który wskazuje, czy nazwa hosta jest używana do uzyskiwania dostępu do usługi podczas dopasowywania identyfikatora URI. Wartość domyślna to <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> , co powoduje ignorowanie nazwy hosta w dopasowaniu.|  
|`listenBacklog`|Dodatnia liczba całkowita, która określa maksymalną liczbę kanałów oczekujących na akceptację odbiornika. Połączenia o przekroczeniu tego limitu są umieszczane w kolejce do momentu udostępnienia przestrzeni poniżej limitu. `connectionTimeout`Atrybut ogranicza czas, przez który klient będzie oczekiwał na połączenie przed wygenerowaniem wyjątku połączenia. Wartość domyślna to 10.|  
|`maxBufferPoolSize`|Liczba całkowita określająca maksymalny rozmiar puli buforów dla tego powiązania. Wartość domyślna to 512 * 1024 bajtów. Wiele części Windows Communication Foundation (WCF) używa buforów. Tworzenie i niszczenie buforów za każdym razem, gdy są używane, jest kosztowne i wyrzucanie elementów bezużytecznych dla buforów jest również kosztowne. W przypadku pul buforów można pobrać bufor z puli, użyć go i zwrócić do puli po zakończeniu. W ten sposób nie ma konieczności narzutu na tworzenie i niszczenie buforów.|  
|`maxBufferSize`|Dodatnia liczba całkowita, która określa maksymalny rozmiar buforu używany do przechowywania komunikatów w pamięci.<br /><br /> Jeśli `transferMode` atrybut jest równy `Buffered` , ten atrybut powinien być równy `maxReceivedMessageSize` wartości atrybutu.<br /><br /> Jeśli `transferMode` atrybut jest równy `Streamed` , ten atrybut nie może być większy niż `maxReceivedMessageSize` wartość atrybutu i powinien mieć co najmniej rozmiar nagłówków.<br /><br /> Wartość domyślna to 65536. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.|  
|`maxConnections`|Liczba całkowita określająca maksymalną liczbę połączeń wychodzących i przychodzących, które usługa zostanie utworzona/zaakceptowana. Połączenia przychodzące i wychodzące są liczone względem oddzielnego limitu określonego przez ten atrybut.<br /><br /> Połączenia przychodzące przekraczające limit są umieszczane w kolejce do momentu udostępnienia odstępu poniżej limitu.<br /><br /> Połączenia wychodzące przekraczające limit są umieszczane w kolejce do momentu udostępnienia odstępu poniżej limitu.<br /><br /> Wartość domyślna to 10.|  
|`maxReceivedMessageSize`|Dodatnia liczba całkowita, która określa maksymalny rozmiar wiadomości (w bajtach), w tym nagłówki, które można odbierać w kanale skonfigurowanym dla tego powiązania. Nadawca komunikatu przekraczającego ten limit otrzyma błąd protokołu SOAP. Odbiorca odrzuca komunikat i tworzy wpis zdarzenia w dzienniku śledzenia. Wartość domyślna to 65536.|  
|`name`|Ciąg zawierający nazwę konfiguracji powiązania. Ta wartość powinna być unikatowa, ponieważ jest używana jako identyfikacja dla powiązania. Począwszy od .NET Framework 4, powiązania i zachowania nie muszą mieć nazwy. Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).|  
|`openTimeout`|<xref:System.TimeSpan>Wartość, która określa przedział czasu podanego na zakończenie operacji otwarcia. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> . Wartość domyślna to 00:01:00.|  
|`portSharingEnabled`|Wartość logiczna określająca, czy włączone jest Udostępnianie portów TCP dla tego połączenia. W takim przypadku `false` każde powiązanie używa własnego portu wyłącznego. To ustawienie ma zastosowanie tylko do usług, ponieważ nie ma to znaczenia dla klientów.|  
|`receiveTimeout`|Wartość określająca <xref:System.TimeSpan> interwał czasu podanego do ukończenia operacji odbioru. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> . Wartość domyślna to 00:10:00.|  
|`sendTimeout`|<xref:System.TimeSpan>Wartość określająca interwał czasu podanego do ukończenia operacji wysyłania. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> . Wartość domyślna to 00:01:00.|  
|`transactionFlow`|Wartość logiczna określająca, czy powiązanie obsługuje przepływy WS-Transactions. Wartość domyślna to `false`.|  
|`transactionProtocol`|Określa protokół transakcji, który ma być używany z tym powiązaniem. Prawidłowe wartości to<br /><br /> -OleTransactions<br />- WSAtomicTransactionOctober2004<br /><br /> Wartość domyślna to OleTransactions. Ten atrybut jest typu <xref:System.ServiceModel.TransactionProtocol> .|  
|`transferMode`|Wartość określająca <xref:System.ServiceModel.TransferMode> , czy komunikaty są buforowane, czy przesyłane strumieniowo, czy też żądanie lub odpowiedź.|  
  
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
  
## <a name="remarks"></a>Uwagi

To powiązanie generuje stos komunikacji w czasie wykonywania domyślnie, który korzysta z zabezpieczeń transportu, protokołu TCP do dostarczania komunikatów i kodowania komunikatów binarnych. To powiązanie jest odpowiednim wyborem systemu Windows Communication Foundation (WCF) w przypadku komunikacji za pośrednictwem intranetu.  
  
 Konfiguracja domyślna dla programu `netTcpBinding` jest szybsza niż konfiguracja podana przez `wsHttpBinding` , ale jest przeznaczona tylko do komunikacji z WCF. Zachowanie zabezpieczeń można skonfigurować przy użyciu opcjonalnego `securityMode` atrybutu. Korzystanie z protokołu WS-ReliableMessaging można skonfigurować przy użyciu opcjonalnego `reliableSessionEnabled` atrybutu. Jednak niezawodna obsługa komunikatów jest domyślnie wyłączona. Ogólnie rzecz biorąc, powiązania dostarczone przez system HTTP, takie jak `wsHttpBinding` i, `basicHttpBinding` są domyślnie skonfigurowane do włączania funkcji, natomiast `netTcpBinding` powiązanie to jest domyślnie wyłączone, dzięki czemu trzeba się dowiedzieć, aby uzyskać pomoc techniczną, na przykład dla jednej ze specyfikacji WS-*. Oznacza to, że domyślna konfiguracja protokołu TCP jest szybsza podczas wymiany komunikatów między punktami końcowymi niż te skonfigurowane dla powiązań HTTP domyślnie.  
  
## <a name="example"></a>Przykład

Powiązanie jest określone w plikach konfiguracji klienta i usługi. Typ powiązania jest określony w `binding` atrybucie `<endpoint>` elementu. Jeśli chcesz skonfigurować powiązanie netTcpBinding i zmienić niektóre z jego ustawień, musisz zdefiniować konfigurację powiązania. Punkt końcowy musi odwoływać się do konfiguracji powiązania z `bindingConfiguration` atrybutem. W poniższym przykładzie zdefiniowano konfigurację powiązania.  
  
```xml  
<services>
  <service name="Microsoft.ServiceModel.Samples.CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    ...
    <endpoint address=""
              binding="netTcpBinding"
              contract="Microsoft.ServiceModel.Samples.ICalculator" />
    ...
  </service>
</services>
<bindings>
  <netTcpBinding>
    <binding closeTimeout="00:01:00"
             openTimeout="00:01:00"
             receiveTimeout="00:10:00"
             sendTimeout="00:01:00"
             transactionFlow="false"
             transferMode="Buffered"
             transactionProtocol="OleTransactions"
             hostNameComparisonMode="StrongWildcard"
             listenBacklog="10"
             maxBufferPoolSize="524288"
             maxBufferSize="65536"
             maxConnections="10"
             maxReceivedMessageSize="65536">
      <readerQuotas maxDepth="32"
                    maxStringContentLength="8192"
                    maxArrayLength="16384"
                    maxBytesPerRead="4096"
                    maxNameTableCharCount="16384" />
      <reliableSession ordered="true"
                       inactivityTimeout="00:10:00"
                       enabled="false" />
      <security mode="Transport">
        <transport clientCredentialType="Windows" protectionLevel="EncryptAndSign" />
      </security>
    </binding>
  </netTcpBinding>
</bindings>
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.NetTcpBinding>
- <xref:System.ServiceModel.Configuration.NetTcpBindingElement>
- [Powiązania](../../../wcf/bindings.md)
- [Konfigurowanie powiązań dostarczanych przez system](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
