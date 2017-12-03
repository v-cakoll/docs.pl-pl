---
title: '&lt;netTcpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: netTcpBinding Element
ms.assetid: 5c5104a7-8754-4335-8233-46a45322503e
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5e5cfaec2d77bd4455877f92da2e65f7080fa6dd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltnettcpbindinggt"></a>&lt;netTcpBinding&gt;
Określa bezpieczne, niezawodne i zoptymalizowane powiązanie odpowiednie dla komunikacji między komputerami. Domyślnie generuje środowiska uruchomieniowego stosu komunikacji z zabezpieczeniami systemu Windows dla komunikatów zabezpieczeń i uwierzytelniania, TCP dostarczanie komunikatów i kodowanie komunikatu binarnego.  
  
 \<System. ServiceModel >  
\<powiązania >  
\<netTcpBinding >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<netTcpBinding>  
   <binding   
      closeTimeout="TimeSpan"  
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
            transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"  
  
      <reliableSession ordered="Boolean"  
            inactivityTimeout="TimeSpan"  
            enabled="Boolean" />  
      <security mode="None/Transport/Message/Both">  
            <message clientCredentialType="None/Windows/UserName/Certificate/CardSpace"  
                defaultProtectionLevel="None/Sign/EncryptAndSign"   
algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" />  
            <transport clientCredentialType="None/Windows/Certificate"  
                protectionLevel="None/Sign/EncryptAndSign" />  
      </security>  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />   </binding>  
</netTcpBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|closeTimeout|A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji zamknięcia. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|parametru hostnameComparisonMode|Określa tryb porównania nazw hostów HTTP używany do przeprowadzenia analizy identyfikatorów URI. Ten atrybut jest typu `System.ServiceModel.HostnameComparisonMode`, która wskazuje, czy nazwa hosta jest używana w celu dotarcia do usługi podczas dopasowywania identyfikatora URI. Wartość domyślna to `StrongWildcard`, który ignoruje nazwy hosta w dopasowania.|  
|ListenBacklog|Dodatnia liczba całkowita, która określa maksymalną liczbę kanałów oczekujących na akceptację na odbiornika. Połączenia przekracza ten limit są umieszczane w kolejce, dopóki nie będzie dostępne miejsce poniżej limitu. `connectionTimeout` Atrybut ogranicza czas, klient będzie czekać do podłączenia przed zgłaszanie wyjątek połączenia. Wartość domyślna to 10.|  
|MaxBufferPoolSize|Liczba całkowita określająca maksymalny rozmiar puli buforów dla tego powiązania. Wartość domyślna to 512 * 1024 bajty. Bufory za pomocą wielu części programu Windows Communication Foundation (WCF). Tworzenie i niszczenie buforów za każdym razem, gdy są one używane jest kosztowne i odzyskiwanie pamięci dla buforów również jest kosztowna. Używając puli buforów można podjąć buforu z puli, ten jest używany i zwracać do puli, gdy wszystko będzie gotowe. W związku z tym jest unikać obciążenie związane z tworzeniem i niszczenie buforów.|  
|wartość maxBufferSize|Dodatnia liczba całkowita, która określa maksymalny rozmiar w bajtach buforu używany do przechowywania wiadomości w pamięci.<br /><br /> Jeśli `transferMode` atrybutu jest równa `Buffered`, ten atrybut powinien być równy `maxReceivedMessageSize` wartość atrybutu.<br /><br /> Jeśli `transferMode` atrybutu jest równa `Streamed`, ten atrybut nie może być więcej niż `maxReceivedMessageSize` wartość atrybutu, a powinien być co najmniej rozmiar nagłówków.<br /><br /> Wartość domyślna to 65536. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.|  
|maxConnections|Liczba całkowita określająca maksymalną liczbę połączeń wychodzące i przychodzące usługi Utwórz/akceptuje. Połączenia przychodzące i wychodzące są uwzględniane w oddzielnych określonym przez atrybut.<br /><br /> Połączenia przychodzące poza limitem są umieszczane w kolejce, dopóki nie będzie dostępne miejsce poniżej limitu.<br /><br /> Połączenia wychodzące poza limitem są umieszczane w kolejce, dopóki nie będzie dostępne miejsce poniżej limitu.<br /><br /> Wartość domyślna to 10.|  
|MaxReceivedMessageSize|Dodatnia liczba całkowita, która określa maksymalny rozmiar wiadomości, w bajtach, włącznie z nagłówkami, odebranych z kanału skonfigurowane dla tego wiązania. Nadawcy wiadomości przekracza ten limit, zostanie wyświetlony błąd protokołu SOAP. Odbiornik porzuca wiadomości i tworzy wpis zdarzenia w dzienniku śledzenia. Wartość domyślna to 65536.|  
|nazwa|Ciąg zawierający nazwę konfiguracji powiązania. Wartość ta powinna być unikatowa, ponieważ jest używany jako identyfikator dla tego powiązania. Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę. Aby uzyskać więcej informacji o konfiguracji domyślnej i bez powiązania i zachowania, zobacz [uproszczony konfiguracji](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|openTimeout|A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji otwarcia. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|PortSharingEnabled|Wartość logiczna określająca, czy włączone jest udostępnianie portów TCP dla tego połączenia. Jeśli jest to `false`, każdego powiązania używa własnego portu wyłącznego. To ustawienie dotyczy tylko do usług, ponieważ nie dotyczy to klientów.|  
|receiveTimeout|A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji odbioru. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:10:00.|  
|właściwości sendTimeout|A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji wysyłania. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|transactionFlow|Wartość logiczna określająca, czy wiązanie obsługuje przechodzenia WS-transakcji. Wartość domyślna to `false`.|  
|Element TransactionProtocol|Określa protokół transakcji do użycia z tym powiązaniem. Prawidłowe wartości to<br /><br /> -OleTransactions<br />-WSAtomicTransactionOctober2004<br /><br /> Wartość domyślna to OleTransactions. Ten atrybut jest typu <xref:System.ServiceModel.TransactionProtocol>.|  
|Tryb transferu|A <xref:System.ServiceModel.TransferMode> wartość określająca, czy komunikaty są buforowane lub przesyłane strumieniowo lub żądania lub odpowiedzi.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Zabezpieczenia >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|Definiuje ustawienia zabezpieczeń dla powiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>.|  
|[\<readerQuotas >](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[reliableSession](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|Określa, czy niezawodnej sesji są połączenia między punktami końcowymi kanału.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<powiązania >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.|  
  
## <a name="remarks"></a>Uwagi  
 To powiązanie generuje stosu komunikacji środowiska wykonawczego domyślnie, który używa zabezpieczeń transportu TCP w celu dostarczania komunikatów i kodowanie komunikatu binarnego. To powiązanie jest [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] wybór dostarczane przez system do komunikowania się za pośrednictwem intranetu.  
  
 Konfigurację domyślną dla `netTcpBinding` jest szybsza niż podana przez Konfiguracja `wsHttpBinding`, ale jest przeznaczona tylko dla [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]- do -[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] komunikacji. Zachowania zabezpieczeń jest można skonfigurować za pomocą opcjonalnego `securityMode` atrybutu. Korzystanie z protokołu WS-ReliableMessaging jest można skonfigurować za pomocą opcjonalnego `reliableSessionEnabled` atrybutu. Ale niezawodna obsługa komunikatów jest domyślnie wyłączone. Ogólnie rzecz biorąc, HTTP dostarczane przez system powiązań takich jak `wsHttpBinding` i `basicHttpBinding` są skonfigurowane do włączyć rzeczy domyślnie, podczas gdy `netTcpBinding` powiązanie wyłącza rzeczy domyślnie, aby należy wyrazić zgodę na uzyskać pomoc techniczną, na przykład dla jednego z WS-* specyfikacji. Oznacza to, że domyślna konfiguracja protokołu TCP dla ma szybszy w wymiana wiadomości między punktami końcowymi niż te, które domyślnie skonfigurowany dla powiązania protokołu HTTP.  
  
## <a name="example"></a>Przykład  
 Powiązanie jest określona w plikach konfiguracji dla klienta i usługi. Typ powiązania jest określona w `binding` atrybutu `<endpoint>` elementu. Jeśli chcesz skonfigurować powiązanie netTcpBinding i zmieniania jego ustawień należy zdefiniować konfiguracji powiązania. Punkt końcowy musi odwoływać się Konfiguracja powiązania z `bindingConfiguration` atrybutu. W poniższym przykładzie zdefiniowano konfiguracji powiązania.  
  
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
    <binding   
             closeTimeout="00:01:00"  
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
 <xref:System.ServiceModel.NetTcpBinding>  
 <xref:System.ServiceModel.Configuration.NetTcpBindingElement>  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurowanie powiązań dostarczanych przez System](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)
