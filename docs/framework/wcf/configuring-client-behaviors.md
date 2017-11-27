---
title: "Konfigurowanie zachowań klienta"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: df5b32fa-e73b-4e8e-b66f-357c748e0173
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6f16f32128c7223fa600802ae593d36286847dc8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="configuring-client-behaviors"></a>Konfigurowanie zachowań klienta
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]Konfiguruje zachowań na dwa sposoby: poprzez odwołujących się do konfiguracji zachowania — które są zdefiniowane w `<behavior>` sekcji pliku konfiguracji aplikacji klienta — lub programowo w aplikacji wywołującej. W tym temacie opisano obu podejść.  
  
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
 Można również skonfigurować lub wstawić zachowania programowo dzięki umieszczeniu odpowiednie `Behaviors` właściwość [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] obiektu klienta lub w obiekcie fabryki kanału klienta przed otwarciem klienta.  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod przedstawia sposób programowane Wstawianie zachowanie po zalogowaniu się do <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> właściwość <xref:System.ServiceModel.Description.ServiceEndpoint> zwrócony z <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> właściwości przed utworzenia obiektu kanału.  
  
 [!code-csharp[ChannelFactoryBehaviors#10](../../../samples/snippets/csharp/VS_Snippets_CFX/channelfactorybehaviors/cs/client.cs#10)]
 [!code-vb[ChannelFactoryBehaviors#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelfactorybehaviors/vb/client.vb#10)]  
  
## <a name="see-also"></a>Zobacz też  
 [\<zachowania >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)
