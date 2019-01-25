---
title: Konfigurowanie zachowań klienta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: df5b32fa-e73b-4e8e-b66f-357c748e0173
ms.openlocfilehash: bf65844cda195847989d1eb8ef752fe87c9de22c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54532202"
---
# <a name="configuring-client-behaviors"></a>Konfigurowanie zachowań klienta
Windows Communication Foundation (WCF) umożliwia skonfigurowanie zachowania na dwa sposoby: przy odwoływaniu się do konfiguracji zachowanie — które są zdefiniowane w `<behavior>` sekcję pliku konfiguracji aplikacji klienta — lub programowo w wywołania aplikacja. W tym temacie opisano oba podejścia.  
  
 Korzystając z pliku konfiguracji, konfiguracji zachowanie jest nazwany zestaw ustawień konfiguracji. Nazwa każdej konfiguracji zachowanie musi być unikatowa. Ten ciąg jest używany podczas `behaviorConfiguration` atrybutu konfiguracji punktu końcowego do łączenia punktu końcowego do zachowania.  
  
## <a name="example"></a>Przykład  
 Poniższy kod konfiguracji definiuje zachowanie nazywane `myBehavior`. Punkt końcowy klienta odwołuje się do zachowania w `behaviorConfiguration` atrybutu.  
  
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
 Można również skonfigurować lub programowe Wstawianie zachowania, znajdując odpowiednie `Behaviors` właściwości w obiekcie klienta usługi Windows Communication Foundation (WCF) lub na obiekt fabryki kanału klienta przed otwarciem klienta.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, jak programowe Wstawianie zachowania, uzyskując dostęp do <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> właściwość <xref:System.ServiceModel.Description.ServiceEndpoint> zwróciło <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> właściwości przed utworzenia obiektu kanału.  
  
 [!code-csharp[ChannelFactoryBehaviors#10](../../../samples/snippets/csharp/VS_Snippets_CFX/channelfactorybehaviors/cs/client.cs#10)]
 [!code-vb[ChannelFactoryBehaviors#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelfactorybehaviors/vb/client.vb#10)]  
  
## <a name="see-also"></a>Zobacz także
- [\<zachowania >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)
