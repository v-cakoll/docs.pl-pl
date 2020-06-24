---
title: 'Instrukcje: Inspekcja lub modyfikowanie komunikatów na kliencie'
description: Dowiedz się, jak sprawdzać lub modyfikować komunikaty przychodzące lub wychodzące przez klienta lub usługę WCF przez implementację odpowiedniego interfejsu.
ms.date: 03/30/2017
ms.assetid: b8256335-f1c2-419f-b862-9f220ccad84c
ms.openlocfilehash: 6f6a3d20d7f3a9fb79de5cd3e29096e270d0f188
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247510"
---
# <a name="how-to-inspect-or-modify-messages-on-the-client"></a>Instrukcje: Inspekcja lub modyfikowanie komunikatów na kliencie
Możesz sprawdzić lub zmodyfikować przychodzące lub wychodzące komunikaty przez klienta WCF, implementując <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> i wstawiając go do środowiska uruchomieniowego klienta. Aby uzyskać więcej informacji, zobacz [Rozszerzanie klientów](extending-clients.md). Równoważna funkcja w usłudze to <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> . Aby uzyskać pełny przykład kodu, zobacz przykład [inspektorów komunikatów](../samples/message-inspectors.md) .  
  
### <a name="to-inspect-or-modify-messages"></a>Aby sprawdzić lub zmodyfikować komunikaty  
  
1. Zaimplementuj interfejs <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.  
  
2. Zaimplementuj <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> lub w <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> zależności od zakresu, w którym ma zostać wstawiony Inspektor komunikatów klienta. <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>umożliwia zmianę zachowania na poziomie punktu końcowego. <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>umożliwia zmianę zachowania na poziomie kontraktu.  
  
3. Wstaw zachowanie przed wywołaniem <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> lub <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> metodą w <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> . Aby uzyskać szczegółowe informacje, zobacz [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, w kolejności:  
  
- Implementacja inspektora klienta.  
  
- Zachowanie punktu końcowego, które wstawia inspektora.  
  
- <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>Klasa pochodna, która umożliwia dodanie zachowania w pliku konfiguracji.  
  
- Plik konfiguracji, który dodaje zachowanie punktu końcowego, który wstawia inspektora komunikatów klienta do środowiska uruchomieniowego klienta.  
  
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
