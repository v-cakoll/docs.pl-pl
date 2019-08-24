---
title: Używanie elementu NetHttpBinding
ms.date: 03/30/2017
ms.assetid: fe134acf-ceca-49de-84a9-05a37e3841f1
ms.openlocfilehash: 0f908361c5f9152d333daaf5e3ee90de3b1b89e9
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988632"
---
# <a name="using-the-nethttpbinding"></a>Używanie elementu NetHttpBinding
<xref:System.ServiceModel.NetHttpBinding>to powiązanie przeznaczone do konsumowania usług HTTP lub WebSocket i domyślnie używa kodowania binarnego. <xref:System.ServiceModel.NetHttpBinding>Program wykrywa, czy jest używany z kontraktem typu żądanie-odpowiedź, czy z umową dupleksową, i zmienia jego zachowanie na zgodne — będzie używać protokołu HTTP dla kontraktów żądania i odpowiedzi oraz dla kontraktów dwukierunkowych. To zachowanie można zastąpić przy użyciu <xref:System.ServiceModel.Channels.WebSocketTransportUsage> ustawienia:  
  
1. <xref:System.ServiceModel.Channels.WebSocketTransportUsage.Always>— Spowoduje to wymuszenie użycia obiektów WebSockets nawet w przypadku kontraktów żądanie-odpowiedź.  
  
2. <xref:System.ServiceModel.Channels.WebSocketTransportUsage.Never>— Uniemożliwia korzystanie z obiektów WebSockets. Próba użycia kontraktu dupleksowego z tym ustawieniem spowoduje wyjątek.  
  
3. <xref:System.ServiceModel.Channels.WebSocketTransportUsage.WhenDuplex>— Jest to wartość domyślna i zachowuje się zgodnie z powyższym opisem.  
  
 <xref:System.ServiceModel.NetHttpBinding>obsługuje niezawodne sesje w trybie HTTP i w trybie WebSocket. W przypadku sesji trybu WebSocket są udostępniane przez transport.  
  
> [!WARNING]
> W przypadku korzystania <xref:System.ServiceModel.NetHttpBinding> z i elementu BindingMode ma ustawioną wartość TransferMode. streamd, duże strumienie mogą spowodować zakleszczenie i wywołanie zostanie przekroczenie limitu czasu. Aby obejść ten problem, Wyślij mniejsze wiadomości lub użyj przetransfermode. Buffered.  
  
## <a name="configuring-a-service-to-use-nethttpbinding"></a>Konfigurowanie usługi do korzystania z protokołu HttpBinding  
 <xref:System.ServiceModel.NetHttpBinding> Można skonfigurować takie same jak inne powiązania. Poniższy fragment konfiguracji ilustruje sposób konfigurowania usługi WCF w <xref:System.ServiceModel.NetHttpBinding>usłudze.  
  
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
    ...
  </system.serviceModel>  
```  
  
 Poniższy fragment kodu pokazuje, <xref:System.ServiceModel.NetHttpBinding> jak dodać kod w kodzie.  
  
```csharp  
ServiceHost svchost = new ServiceHost(typeof(Service1), baseAddress);  
            NetHttpBinding binding = new NetHttpBinding();  
            svchost.AddServiceEndpoint(typeof(IService1), binding, address);   
        }  
```  
  
## <a name="see-also"></a>Zobacz także

- [Konfigurowanie powiązań dla usług](../../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)
- [Powiązania](../../../../docs/framework/wcf/feature-details/bindings.md)
- [Powiązania dostarczane przez system](../../../../docs/framework/wcf/system-provided-bindings.md)
- [Usługi dwukierunkowe](../../../../docs/framework/wcf/feature-details/duplex-services.md)
