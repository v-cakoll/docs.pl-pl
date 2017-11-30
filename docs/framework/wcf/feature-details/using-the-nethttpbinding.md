---
title: "Używanie elementu NetHttpBinding"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fe134acf-ceca-49de-84a9-05a37e3841f1
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 56528078895ea7c624afaf716e9a26eabe335d69
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="using-the-nethttpbinding"></a>Używanie elementu NetHttpBinding
<xref:System.ServiceModel.NetHttpBinding>jest przeznaczony do używania protokołu HTTP lub protokołu WebSocket usług powiązania i używa kodowanie binarne domyślnie. <xref:System.ServiceModel.NetHttpBinding>wykryje, czy jest używana z kontraktu "żądanie-odpowiedź" lub kontraktu dwukierunkowego i zmianę jego zachowania, aby dopasować — zostanie użyty HTTP dla kontraktów "żądanie-odpowiedź" i technologia WebSockets dla kontraktów dupleksowych. To zachowanie można przesłonić przy użyciu <!--zz <xref:System.ServiceModel.NetHttpBinding.WebSocketTransportUsage%2A> --> `WebSocketTransportUsage` ustawienia:  
  
1.  Zawsze — wymusza Websocket do użycia nawet w przypadku kontraktów "żądanie-odpowiedź".  
  
2.  Nigdy nie - zapobiega to Websocket używana. Podjęto próbę użycia kontraktu dwukierunkowego tego ustawienia spowoduje Wystąpił wyjątek.  
  
3.  WhenDuplex — jest to wartość domyślna i działa zgodnie z powyższym opisem.  
  
 <xref:System.ServiceModel.NetHttpBinding>niezawodnej sesji obsługuje zarówno w trybie HTTP, jak i w trybie protokołu WebSocket. W WebSocket tryb sesji są dostarczane przez transport.  
  
> [!WARNING]
>  Korzystając z <xref:System.ServiceModel.NetHttpBinding> i tryb transferu wiązania jest ustawiona na TransferMode.Streamed, dużych strumieni może spowodować zakleszczenie i zostanie limit czasu wywołania. Aby obejść ten problem wysyłać mniejszych wiadomości, lub użyj elementy TransferMode.Buffered.  
  
## <a name="configuring-a-service-to-use-nethttpbinding"></a>Konfigurowanie usługi do użycia NetHttpBinding  
 <xref:System.ServiceModel.NetHttpBinding> Może być skonfigurowane tak samo jak wszystkie inne powiązanie. Poniższy fragment konfiguracji przedstawiono sposób konfigurowania usługi WCF za pomocą <xref:System.ServiceModel.NetHttpBinding>.  
  
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
