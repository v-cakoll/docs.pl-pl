---
title: Konfigurowanie zachowań klienta
description: 'Dowiedz się więcej na temat dwóch sposobów konfigurowania zachowań przez funkcję WCF: w pliku konfiguracyjnym aplikacji lub programowo przy użyciu aplikacji wywołującej.'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: df5b32fa-e73b-4e8e-b66f-357c748e0173
ms.openlocfilehash: 4b83862221cf249455478c3ade159a3101062f3e
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245443"
---
# <a name="configuring-client-behaviors"></a>Konfigurowanie zachowań klienta
Windows Communication Foundation (WCF) konfiguruje zachowania na dwa sposoby: w odniesieniu do konfiguracji zachowania — które są zdefiniowane w `<behavior>` sekcji pliku konfiguracyjnego aplikacji klienckiej — lub programowo w aplikacji wywołującej. W tym temacie opisano oba podejścia.  
  
 W przypadku korzystania z pliku konfiguracji, konfiguracja zachowania jest nazwaną kolekcją ustawień konfiguracji. Nazwa każdej konfiguracji zachowania musi być unikatowa. Ten ciąg jest używany w `behaviorConfiguration` atrybucie konfiguracji punktu końcowego w celu połączenia punktu końcowego z zachowaniem.  
  
## <a name="example"></a>Przykład  
 Poniższy kod konfiguracji definiuje zachowanie o nazwie `myBehavior` . Punkt końcowy klienta odwołuje się do tego zachowania w `behaviorConfiguration` atrybucie.  
  
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
  
## <a name="using-behaviors-programmatically"></a>Programistyczne używanie zachowań  
 Można również programowo skonfigurować lub wstawić zachowania, lokalizując odpowiednią `Behaviors` Właściwość w obiekcie klienta Windows Communication Foundation (WCF) lub w obiekcie fabryki kanału klienta przed otwarciem klienta.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, jak programowo wstawić zachowanie, uzyskując dostęp do <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> właściwości <xref:System.ServiceModel.Description.ServiceEndpoint> zwracanej z <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> Właściwości przed utworzeniem obiektu kanału.  
  
 [!code-csharp[ChannelFactoryBehaviors#10](../../../samples/snippets/csharp/VS_Snippets_CFX/channelfactorybehaviors/cs/client.cs#10)]
 [!code-vb[ChannelFactoryBehaviors#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelfactorybehaviors/vb/client.vb#10)]  
  
## <a name="see-also"></a>Zobacz też

- [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md)
