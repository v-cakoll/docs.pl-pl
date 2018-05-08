---
title: Konfigurowanie zachowań klienta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: df5b32fa-e73b-4e8e-b66f-357c748e0173
ms.openlocfilehash: 062e726b6f1d6831303e1cc0ae82a434daab860c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="configuring-client-behaviors"></a>Konfigurowanie zachowań klienta
Windows Communication Foundation (WCF) konfiguruje zachowań na dwa sposoby: poprzez odwołujących się do konfiguracji zachowania — które są zdefiniowane w `<behavior>` sekcji pliku konfiguracji aplikacji klienta — lub programowo w wywołaniu aplikacja. W tym temacie opisano obu podejść.  
  
 Podczas korzystania z pliku konfiguracji, konfiguracji zachowanie jest nazwany zestaw ustawień konfiguracji. Nazwa konfiguracji każdego zachowanie musi być unikatowa. Ten ciąg jest używany w `behaviorConfiguration` atrybutu konfiguracji punktu końcowego do łączenia punktu końcowego do zachowania.  
  
## <a name="example"></a>Przykład  
 Poniższy kod konfiguracji definiuje zachowanie nazywane `myBehavior`. Punkt końcowy klienta odwołuje się do tego zachowania w `behaviorConfiguration` atrybutu.  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name="myBehavior">  
                    <clientVia />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
        <bindings>  
            <basicHttpBinding>  
                <binding name="myBinding" maxReceivedMessageSize="10000" />  
            </basicHttpBinding>  
        </bindings>  
        <client>  
            <endpoint address="myAddress" binding="basicHttpBinding" bindingConfiguration="myBinding" behaviorConfiguration="myBehavior" contract="myContract" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="using-behaviors-programmatically"></a>Programowo za pomocą zachowań  
 Można również skonfigurować lub wstawić zachowania programowo dzięki umieszczeniu odpowiednie `Behaviors` właściwości w obiekcie klienta usługi Windows Communication Foundation (WCF) lub na obiekt fabryki kanału klienta przed otwarciem klienta.  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod przedstawia sposób programowane Wstawianie zachowanie po zalogowaniu się do <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> właściwość <xref:System.ServiceModel.Description.ServiceEndpoint> zwrócony z <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> właściwości przed utworzenia obiektu kanału.  
  
 [!code-csharp[ChannelFactoryBehaviors#10](../../../samples/snippets/csharp/VS_Snippets_CFX/channelfactorybehaviors/cs/client.cs#10)]
 [!code-vb[ChannelFactoryBehaviors#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelfactorybehaviors/vb/client.vb#10)]  
  
## <a name="see-also"></a>Zobacz też  
 [\<zachowania >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)
