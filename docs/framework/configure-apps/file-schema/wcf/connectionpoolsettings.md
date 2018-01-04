---
title: '&lt;connectionPoolSettings&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6fa7fa65-2c6e-4eab-b8cf-7690112c0be5
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 11500830c7c5fd75a9e2880a5875bd21fb070634
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltconnectionpoolsettingsgt"></a>&lt;connectionPoolSettings&gt;
Określa ustawienia puli dodatkowego połączenia powiązania nazwanego potoku.  
  
 \<system.serviceModel >  
\<powiązania >  
\<customBinding >  
\<Powiązanie >  
\<namePipeTransport >  
\<connectionPoolSettings >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<connectionPoolSettings  
        groupName="String"  
    idleTimeout"TimeSpan"  
    maxOutboundConnectionsPerEndpopint="Integer" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`groupName`|Ciąg, który definiuje nazwę puli połączeń dla wychodzących kanałów. W trybie przesyłanej strumieniowo połączenia nie są udostępniane, co oznacza, że buforowanie połączeń jest wyłączona. Wartość domyślna to ciąg "domyślny". Można zmodyfikować tę wartość, aby odizolować połączeń dla określonego klienta do oddzielnych grup.|  
|`idleTimeout`|Dodatnią <xref:System.TimeSpan> , który określa maksymalny czas, połączenie może być bezczynne, zanim zostanie rozłączone. Wartość domyślna to 00:02:00.|  
|`maxOutboundConnectionsPerEndpoint`|Dodatnia liczba całkowita, która określa maksymalną liczbę połączeń do zdalnego punktu końcowego, inicjowanego przez usługę. Połączenia poza limitem są umieszczane w kolejce, dopóki nie będzie dostępne miejsce poniżej limitu. `idleTimeout` Ogranicza okres, w którym połączenia pozostają w kolejce przed jest zgłaszany wyjątek. Wartość domyślna to 10.<br /><br /> Ten atrybut ogranicza liczbę równoczesnych aktywnych połączeń z klienta do określonego punktu końcowego. Tę wartość po przekroczeniu dzięki użyciu aktywnych połączeń klienckich, usługi mogą być wyświetlane odpowiadać do klienta. W takim przypadku ta wartość powinna dostosowana do przekracza maksymalną liczbę oczekiwanych równoczesnych połączeń klientów do określonego punktu końcowego.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<namedPipeTransport >](../../../../../docs/framework/configure-apps/file-schema/wcf/namedpipetransport.md)|Definiuje transport, powodujący przesył kanałem wiadomości używając potoków nazwanych.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>  
 <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Transporty](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [Wybieranie transportu](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Rozszerzanie powiązań](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Powiązania niestandardowe](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
