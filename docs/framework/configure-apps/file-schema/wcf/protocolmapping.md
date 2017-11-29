---
title: '&lt;protocolMapping&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5076644b-1f33-4f26-9488-87de9fcda04c
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 769ca7b96c3671fdd1b154c99516778f7cbd542e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltprotocolmappinggt"></a>&lt;protocolMapping&gt;
Reprezentuje sekcję konfiguracji określającą zestaw domyślnego mapowania protokołu pomiędzy schematami protokołu transportu (np. http, net.tcp, net.pipe, itp.) i powiązaniami WCF. Podczas tworzenia domyślne punkty końcowe w czasie wykonywania, [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] analizuje skonfigurowanego mapowania i decyduje o tym, na których powiązanie dla określonego na podstawie adresów.  
  
 \<system.serviceModel >  
\<protocolMapping >  
  
## <a name="syntax"></a>Składnia  
  
```xml
   <protocolMapping>    <add binding="String"         bindingConfiguration="String"         scheme="http/net.msmq/net.pipe/net.tcp"/></protocolMapping>  
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Filtry >](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|Zawiera domyślne mapowanie protokołu pomiędzy schematem protokołu transportu (np. http, net.tcp, net.pipe, itp.) i powiązanie WCF.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|System.ServiceModel|Element główny wszystkich elementów konfiguracji usługi WCF.|  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie konfiguracji zawiera domyślne mapowanie protokołu w pliku machine.config. Można zastąpić to domyślne mapowanie na poziomie komputera przez zmodyfikowanie pliku machine.config. Lub jeśli chcesz tylko jej zastąpienie w zakresie aplikacji, można zastąpić w tej sekcji w pliku konfiguracji aplikacji i zmień mapowanie dla poszczególnych protokołu systemów.  
  
```xml  
<protocolMapping>  
        <add scheme="http" binding="basicHttpBinding"/>  
        <add scheme="net.tcp" binding="netTcpBinding"/>  
        <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
        <add scheme="net.msmq" binding="netMsmqBinding"/>  
</protocolMapping>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>    
