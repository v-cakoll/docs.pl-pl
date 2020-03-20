---
title: 'Instrukcje: Inspekcja lub modyfikowanie komunikatów na kliencie'
ms.date: 03/30/2017
ms.assetid: b8256335-f1c2-419f-b862-9f220ccad84c
ms.openlocfilehash: db1a99d2ed1f765e39815e6b6c70d6ada1db1d15
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185538"
---
# <a name="how-to-inspect-or-modify-messages-on-the-client"></a>Instrukcje: Inspekcja lub modyfikowanie komunikatów na kliencie
Można sprawdzić lub zmodyfikować przychodzące lub wychodzące wiadomości w <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> kliencie WCF, implementując i wstawiając go do środowiska wykonawczego klienta. Aby uzyskać więcej informacji, zobacz [Rozszerzanie klientów](extending-clients.md). Równoważną funkcją w <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>usłudze jest . W przykładzie pełnego kodu zobacz przykład [Inspektorów wiadomości.](../samples/message-inspectors.md)  
  
### <a name="to-inspect-or-modify-messages"></a>Aby sprawdzić lub zmodyfikować wiadomości  
  
1. Zaimplementuj interfejs <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.  
  
2. Zaimplementuj <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> lub <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> w zależności od zakresu, w którym chcesz wstawić inspektora wiadomości klienta. <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>umożliwia zmianę zachowania na poziomie punktu końcowego. <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>pozwala na zmianę zachowania na poziomie kontraktu.  
  
3. Wstaw zachowanie przed <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> wywołaniem <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> lub <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>metody na . Aby uzyskać szczegółowe informacje, zobacz [Konfigurowanie i rozszerzanie środowiska wykonawczego za pomocą zachowań](configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="example"></a>Przykład  
 Poniższe przykłady kodu pokazują, w kolejności:  
  
- Implementacja inspektora klienta.  
  
- Zachowanie punktu końcowego, który wstawia inspektora.  
  
- A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>- klasa pochodna, która umożliwia dodawanie zachowania w pliku konfiguracyjnym.  
  
- Plik konfiguracji, który dodaje zachowanie punktu końcowego, który wstawia inspektora komunikatów klienta do środowiska wykonawczego klienta.  
  
```csharp  
// Client message inspector  
public class SimpleMessageInspector : IClientMessageInspector  
{  
    public void AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
    {  
        // Implement this method to inspect/modify messages after a message  
        // is received but prior to passing it back to the client
        Console.WriteLine("AfterReceiveReply called");  
    }  
  
    public object BeforeSendRequest(ref System.ServiceModel.Channels.Message request, IClientChannel channel)  
    {  
        // Implement this method to inspect/modify messages before they
        // are sent to the service  
        Console.WriteLine("BeforeSendRequest called");  
        return null;  
    }  
}  
```  
  
```csharp  
// Endpoint behavior  
public class SimpleEndpointBehavior : IEndpointBehavior  
{  
    public void AddBindingParameters(ServiceEndpoint endpoint, System.ServiceModel.Channels.BindingParameterCollection bindingParameters)  
    {  
         // No implementation necessary  
    }  
  
    public void ApplyClientBehavior(ServiceEndpoint endpoint, ClientRuntime clientRuntime)  
    {  
        clientRuntime.MessageInspectors.Add(new SimpleMessageInspector());  
    }  
  
    public void ApplyDispatchBehavior(ServiceEndpoint endpoint, EndpointDispatcher endpointDispatcher)  
    {  
         // No implementation necessary  
    }  
  
    public void Validate(ServiceEndpoint endpoint)  
    {  
         // No implementation necessary  
    }  
}  
```  
  
```csharp  
// Configuration element
public class SimpleBehaviorExtensionElement : BehaviorExtensionElement  
{  
    public override Type BehaviorType  
    {  
        get { return typeof(SimpleEndpointBehavior); }  
    }  
  
    protected override object CreateBehavior()  
    {  
         // Create the  endpoint behavior that will insert the message  
         // inspector into the client runtime  
        return new SimpleEndpointBehavior();  
    }  
}  
```  
  
```xml
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
    <system.serviceModel>  
        <client>  
            <endpoint address="http://localhost:8080/SimpleService/"
                      binding="wsHttpBinding"
                      behaviorConfiguration="clientInspectorsAdded"
                      contract="ServiceReference1.IService1"  
                      name="WSHttpBinding_IService1"/>  
        </client>  
  
      <behaviors>  
        <endpointBehaviors>  
          <behavior name="clientInspectorsAdded">  
            <simpleBehaviorExtension />  
          </behavior>  
        </endpointBehaviors>  
      </behaviors>  
      <extensions>  
        <behaviorExtensions>  
          <add  
            name="simpleBehaviorExtension"  
            type="SimpleServiceLib.SimpleBehaviorExtensionElement, Host, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
        </behaviorExtensions>  
      </extensions>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>
- [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](configuring-and-extending-the-runtime-with-behaviors.md)
