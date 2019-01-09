---
title: '&lt;add&gt; w &lt;backupList&gt;'
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: 4a8eb3df9be6b6b5bfe43aee330f3174ddca66ab
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151478"
---
# <a name="ltaddgt-of-ltbackuplistgt"></a>&lt;add&gt; w &lt;backupList&gt;
Reprezentuje element konfiguracji, który definiuje element kopii zapasowej punktu końcowego.  
  
 \<system.serviceModel>  
\<Routing >  
\<backupLists >  
\<backupList >  
\<add>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|nazwa|Ciąg, który określa nazwę punktu końcowego, tworzenia kopii zapasowej.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Routing >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|Zawiera listę punktów końcowych, które chcesz, aby usługa routingu do użycia w przypadku, gdy nie można nawiązać połączenia z podstawowego punktu końcowego.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType> 
