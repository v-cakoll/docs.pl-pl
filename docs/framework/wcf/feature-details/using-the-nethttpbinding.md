---
title: Używanie elementu NetHttpBinding
ms.date: 03/30/2017
ms.assetid: fe134acf-ceca-49de-84a9-05a37e3841f1
ms.openlocfilehash: 82222dbfa3f35ed00d0173f2bc927c32e9e98470
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184232"
---
# <a name="using-the-nethttpbinding"></a>Używanie elementu NetHttpBinding
<xref:System.ServiceModel.NetHttpBinding>jest wiązaniem przeznaczonym do korzystania z usług HTTP lub WebSocket i domyślnie używa kodowania binarnego. <xref:System.ServiceModel.NetHttpBinding>wykryje, czy jest używany z umową żądanie odpowiedź lub dupleksu i zmienić jego zachowanie, aby dopasować - użyje HTTP dla umów żądanie odpowiedzi i WebSockets dla kontraktów dupleksu. To zachowanie można zastąpić za <xref:System.ServiceModel.Channels.WebSocketTransportUsage> pomocą ustawienia:  
  
1. <xref:System.ServiceModel.Channels.WebSocketTransportUsage.Always>- Zmusza to WebSockets do wykorzystania nawet dla umowy żądanie odpowiedzi.  
  
2. <xref:System.ServiceModel.Channels.WebSocketTransportUsage.Never>- Zapobiega to użyciu WebSockets. Próba użycia umowy dupleksu z tym ustawieniem spowoduje wyjątek.  
  
3. <xref:System.ServiceModel.Channels.WebSocketTransportUsage.WhenDuplex>- Jest to wartość domyślna i zachowuje się tak, jak opisano powyżej.  
  
 <xref:System.ServiceModel.NetHttpBinding>obsługuje niezawodne sesje zarówno w trybie HTTP, jak i WebSocket. W trybie WebSocket sesje są dostarczane przez transport.  
  
> [!WARNING]
> Podczas korzystania <xref:System.ServiceModel.NetHttpBinding> z i powiązania TransferMode jest ustawiona na TransferMode.Streamed, duże strumienie mogą powodować zakleszczenie i wywołanie będzie limit czasu. Aby obejść ten problem, wyślij mniejsze wiadomości lub użyj Pliku TransferMode.Buffered.  
  
## <a name="configuring-a-service-to-use-nethttpbinding"></a>Konfigurowanie usługi do używania funkcji NetHttpBinding  
 <xref:System.ServiceModel.NetHttpBinding> Można skonfigurować tak samo jak inne powiązanie. Poniższy fragment kodu konfiguracji ilustruje sposób konfigurowania usługi <xref:System.ServiceModel.NetHttpBinding>WCF za pomocą programu .  
  
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
  
 Poniższy fragment kodu pokazuje, jak <xref:System.ServiceModel.NetHttpBinding> dodać w kodzie.  
  
```csharp  
ServiceHost svchost = new ServiceHost(typeof(Service1), baseAddress);  
            NetHttpBinding binding = new NetHttpBinding();  
            svchost.AddServiceEndpoint(typeof(IService1), binding, address);
        }  
```  
  
## <a name="see-also"></a>Zobacz też

- [Konfigurowanie powiązań dla usług](../../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)
- [Powiązania](../../../../docs/framework/wcf/feature-details/bindings.md)
- [Powiązania dostarczane przez system](../../../../docs/framework/wcf/system-provided-bindings.md)
- [Usługi dwukierunkowe](../../../../docs/framework/wcf/feature-details/duplex-services.md)
