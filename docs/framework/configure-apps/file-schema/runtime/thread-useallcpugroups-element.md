---
title: '&lt;Thread_UseAllCpuGroups&gt; — Element'
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 47d8bcdb9bbb7ec6f5a5386a5ac5951ad8891c28
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltthreaduseallcpugroupsgt-element"></a>&lt;Thread_UseAllCpuGroups&gt; — Element
Określa, czy środowisko uruchomieniowe dystrybuuje zarządzanych wątków we wszystkich grupach procesora CPU.  
  
 \<Konfiguracja >  
\<runtime>  
< Thread_UseAllCpuGroups >  
  
## <a name="syntax"></a>Składnia  
  
```xml
<Thread_UseAllCpuGroups    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy środowisko uruchomieniowe dystrybuuje zarządzanych wątków we wszystkich grupach procesora CPU.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|Środowisko uruchomieniowe nie rozpowszechniają zarządzanych wątków wielu grup procesorów. Domyślnie włączone.|  
|`true`|Środowisko uruchomieniowe dystrybuuje zarządzanych wątków wieloma grupami procesorów, jeśli komputer ma wiele grup procesora CPU i [ \<gccpugroup — >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element jest włączony.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 Gdy komputer ma wiele grup procesora CPU, włączenie tego elementu powoduje środowiska uruchomieniowego do dystrybucji zarządzanych wątków we wszystkich grupach procesora CPU. Aby użyć tej funkcji, należy również włączyć [ \<gccpugroup — >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element, który rozszerza wyrzucanie elementów bezużytecznych do wszystkich grup procesorów i uwzględnia wszystkie rdzenie podczas tworzenia i równoważenie stosów. Włączanie [ \<gccpugroup — >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element wymaga włączenia [ \<gcserver — >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) elementu. Jeśli te elementy nie są włączone, włączanie `<Thread_UseAllCpuGroups>` element nie ma wpływu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak włączyć obsługę wielu grup procesorów.  
  
```xml  
<configuration>  
   <runtime>  
      <Thread_UseAllCpuGroups enabled="true"/>  
      <GCCpuGroup enabled="true"/>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<Gccpugroup — > — Element](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)
