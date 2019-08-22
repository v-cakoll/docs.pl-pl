---
title: <add> dla <backupList>
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: 53af01a519c244376b262db1f6515a438dcc554f
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663372"
---
# <a name="add-of-backuplist"></a>\<Dodawanie > \<backupList >
Reprezentuje element konfiguracji, który definiuje kopię zapasową elementu punktu końcowego.  
  
 \<system.serviceModel>  
\<> routingu  
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
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|nazwa|Ciąg określający nazwę punktu końcowego kopii zapasowej.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> routingu](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|Zawiera listę punktów końcowych, które mają być używane przez usługę routingu w przypadku, gdy podstawowy punkt końcowy nie zostanie osiągnięty.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType>
