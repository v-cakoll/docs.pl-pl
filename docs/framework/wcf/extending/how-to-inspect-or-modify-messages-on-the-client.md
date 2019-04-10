---
title: 'Instrukcje: sprawdzanie lub modyfikowanie komunikatów na kliencie'
ms.date: 03/30/2017
ms.assetid: b8256335-f1c2-419f-b862-9f220ccad84c
ms.openlocfilehash: 67fa0e092e6494ff55d71e666b5137cfc9a3069e
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59343301"
---
# <a name="how-to-inspect-or-modify-messages-on-the-client"></a>Instrukcje: sprawdzanie lub modyfikowanie komunikatów na kliencie
Można sprawdzić lub modyfikowanie komunikatów przychodzących lub wychodzących przez klienta programu WCF poprzez implementację <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> oraz wstawieniu ich do środowiska uruchomieniowego klienta. Aby uzyskać więcej informacji, zobacz [rozszerzanie klientów](../../../../docs/framework/wcf/extending/extending-clients.md). Jest równoważna funkcji w usłudze <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>. Aby uzyskać pełny przykład kodu zobacz [inspektorzy komunikatów](../../../../docs/framework/wcf/samples/message-inspectors.md) próbki.  
  
### <a name="to-inspect-or-modify-messages"></a>Aby inspekcja lub modyfikowanie komunikatów  
  
1. Implementowanie <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> interfejsu.  
  
2. Implementowanie <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> lub <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> w zależności od zakresu, w którym ma zostać wstawiony Inspektor komunikat klienta. <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> Umożliwia zmianę zachowania na poziomie punktu końcowego. <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> Umożliwia zmianę zachowania na poziomie kontraktu.  
  
3. Wstaw działanie przed wywołaniem <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> lub <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> metody <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>. Aby uzyskać więcej informacji, zobacz [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="example"></a>Przykład  
 Pokaż w poniższych przykładach kodu w kolejności:  
  
-   Implementacji Inspektor klienta.  
  
-   Zachowanie punktu końcowego, który wstawia Inspektor.  
  
-   A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>-klasy, która pozwala na dodanie zachowania w pliku konfiguracji.  
  
-   Plik konfiguracji, który dodaje zachowanie punktu końcowego, który wstawia Inspektor komunikat klienta do środowiska uruchomieniowego klienta.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>
- [Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
