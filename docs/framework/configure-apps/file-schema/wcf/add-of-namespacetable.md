---
title: '&lt;add&gt; w &lt;namespaceTable&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 394657abcebb42192fb7a8b57b0402bcacf37693
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltnamespacetablegt"></a>&lt;add&gt; w &lt;namespaceTable&gt;
Reprezentuje element konfiguracji, który zawiera przestrzeń nazw jako przedrostkowe mapowanie, które mogą być następnie używane w filtrach XPath dla routingu.  
  
 \<system.serviceModel >  
\<Routing >  
\<namespaceTable >  
\<Dodaj >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
   <routing>   <namespaceTable>  
     <add namespace="String" prefix="String" />    </namespaceTable></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|— przestrzeń nazw|Ciąg zawierający przestrzeń nazw.|  
|Prefiks|Ciąg zawierający prefiks dla tej przestrzeni nazw.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<namespaceTable >](../../../../../docs/framework/configure-apps/file-schema/wcf/namespacetable.md)|Reprezentuje sekcję konfiguracji definiującą zestaw elementów zawierających przestrzeń nazw do mapowania prefiksów, które mogą być następnie używane w filtrach XPath dla routingu.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>    
