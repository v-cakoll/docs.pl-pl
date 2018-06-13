---
title: '&lt;gcserver —&gt; — Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcServer
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcServer
helpviewer_keywords:
- gcServer element
- <gcServer> element
ms.assetid: 8d25b80e-2581-4803-bd87-a59528e3cb03
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 027176bdff644a6ff3314df7484ed88ace93001b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32745022"
---
# <a name="ltgcservergt-element"></a>&lt;gcserver —&gt; — Element
Określa, czy środowisko uruchomieniowe języka wspólnego Uruchamia odzyskiwanie pamięci na serwerze.  
  
 \<Konfiguracja >  
\<runtime>  
\<gcServer>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<gcServer    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy środowisko uruchomieniowe Uruchamia odzyskiwanie pamięci na serwerze.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|Odzyskiwanie pamięci na serwerze nie jest możliwe. Domyślnie włączone.|  
|`true`|Uruchamia odzyskiwanie pamięci na serwerze.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko uruchomieniowe języka wspólnego (CLR) obsługuje dwa typy operacji wyrzucania elementów bezużytecznych: wyrzucanie elementów bezużytecznych stacji roboczej, która jest dostępna we wszystkich systemach, i odzyskiwanie pamięci na serwerze, który jest dostępny w systemach wieloprocesorowych. Możesz użyć `<gcServer>` wykonuje element, aby kontrolować typ operacji wyrzucania elementów bezużytecznych środowiska CLR. Użyj <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> właściwości w celu określenia, czy jest włączone odzyskiwanie pamięci na serwerze.  
  
 W przypadku komputerów z jednym procesorem domyślnej kolekcji elementy bezużyteczne stacji roboczej powinna być najszybszą opcję. Dla dwóch komputerów można stacji roboczej lub serwera. Odzyskiwanie pamięci na serwerze powinny być najszybszą opcję dla więcej niż dwa procesory.  
  
 Ten element może być używana tylko w pliku konfiguracji aplikacji; jest ona ignorowana, jeśli znajduje się w pliku konfiguracji komputera.  
  
> [!NOTE]
>  W .NET Framework 4 i starszych wersjach współbieżne odzyskiwanie pamięci nie jest dostępna, gdy jest włączone odzyskiwanie pamięci na serwerze. Począwszy od [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], jest współbieżne odzyskiwanie pamięci na serwerze. Aby użyć serwera z systemem innym niż współbieżne odzyskiwanie pamięci, należy ustawić `<gcServer>` elementu `true` i [ \<gcconcurrent — > element](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) do `false`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład umożliwia odzyskiwanie pamięci na serwerze.  
  
```xml  
<configuration>  
   <runtime>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>  
 [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Porady: wyłączanie współbieżne odzyskiwanie pamięci](http://msdn.microsoft.com/library/ba2c6c67-5778-497c-9fac-5f793b5500c7)
