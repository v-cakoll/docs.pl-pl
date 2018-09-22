---
title: Używanie elementu NetHttpBinding
ms.date: 03/30/2017
ms.assetid: fe134acf-ceca-49de-84a9-05a37e3841f1
ms.openlocfilehash: cd4a50798ff709c32db056c6aa7289993431f40e
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46696745"
---
# <a name="using-the-nethttpbinding"></a>Używanie elementu NetHttpBinding
<xref:System.ServiceModel.NetHttpBinding> jest przeznaczony dla korzystanie z usług HTTP i WebSocket powiązanie i używa kodowania binarnego domyślnie. <xref:System.ServiceModel.NetHttpBinding> wykryje, czy jest używana za pomocą kontraktu dwukierunkowego lub kontraktu "żądanie odpowiedź" i zmianę jej zachowania, aby dopasować — go będzie używany protokół HTTP dla kontraktów "żądanie odpowiedź" i technologia WebSockets kontrakty dwukierunkowe. To zachowanie można przesłonić przy użyciu <xref:System.ServiceModel.Channels.WebSocketTransportUsage> ustawienia:  
  
1. `Always` -Wymusza WebSockets ma być używany, nawet w przypadku kontraktów "żądanie odpowiedź".  
  
2. `Never` Zapobiega — używana przez protokół WebSockets. Podjęto próbę użycia kontrakt dupleksowy, to ustawienie powoduje wyjątek.  
  
3. `WhenDuplex` -Jest wartością domyślną i zachowuje się zgodnie z powyższym opisem.  
  
 <xref:System.ServiceModel.NetHttpBinding> niezawodne sesje obsługuje zarówno w trybie HTTP, jak i w trybie protokołu WebSocket. W WebSocket trybu sesji są dostarczane przez transportu.  
  
> [!WARNING]
>  Korzystając z <xref:System.ServiceModel.NetHttpBinding> i powiązania tryb transferu jest równa TransferMode.Streamed, dużych strumieni może spowodować, że zakleszczenie i limit czasu spowoduje wywołanie. Aby obejść ten problem wysyłać mniejszych wiadomości, lub użyj elementy TransferMode.Buffered.  
  
## <a name="configuring-a-service-to-use-nethttpbinding"></a>Konfigurowanie usługi do użycia NetHttpBinding  
 <xref:System.ServiceModel.NetHttpBinding> Może być skonfigurowane tak samo jak wszystkie inne powiązanie. Poniższy fragment kodu konfiguracji przedstawia sposób konfigurowania usługi WCF, za pomocą <xref:System.ServiceModel.NetHttpBinding>.  
  
```xml  
<system.serviceModel>  
    <services>  
      <service name="WcfService1.Service1">  
        <endpoint address=""  
                  binding="netHttpBinding"  
                  contract="WcfService1.IService1"/>  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange"/>  
      </service>  
    </services>  
    <bindings>  
      <netHttpBinding>  
        <binding name="My_NetHttpBindingConfig">  
          <webSocketSettings transportUsage="WhenDuplex"/>  
        </binding>  
      </netHttpBinding>  
    </bindings>  
    <!- ... -->   
  </system.serviceModel>  
```  
  
 Poniższy fragment kodu przedstawia sposób dodawania <xref:System.ServiceModel.NetHttpBinding> w kodzie.  
  
```csharp  
ServiceHost svchost = new ServiceHost(typeof(Service1), baseAddress);  
            NetHttpBinding binding = new NetHttpBinding();  
            svchost.AddServiceEndpoint(typeof(IService1), binding, address);   
        }  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie powiązań dla usług](../../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)  
 [Powiązania](../../../../docs/framework/wcf/feature-details/bindings.md)  
 [Powiązania dostarczane przez system](../../../../docs/framework/wcf/system-provided-bindings.md)  
 [Usługi dwukierunkowe](../../../../docs/framework/wcf/feature-details/duplex-services.md)
