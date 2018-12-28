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
ms.openlocfilehash: 80421a66a3ace4970324fb295e167b7d4875063f
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53610687"
---
# <a name="ltgcservergt-element"></a>&lt;gcserver —&gt; — Element
Określa, czy środowisko uruchomieniowe języka wspólnego uruchamia wyrzucanie elementów bezużytecznych serwera.  
  
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
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy środowisko uruchomieniowe jest uruchamiany serwer wyrzucania elementów bezużytecznych.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|Nie jest uruchamiany serwer wyrzucania elementów bezużytecznych. Domyślnie włączone.|  
|`true`|Uruchamia serwer wyrzucania elementów bezużytecznych.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko uruchomieniowe języka wspólnego (CLR) obsługuje dwa typy operacji wyrzucania elementów bezużytecznych: wyrzucanie elementów bezużytecznych, który jest dostępny we wszystkich systemach, i wyrzucanie elementów bezużytecznych serwera, który jest dostępny w systemach wieloprocesorowych. Możesz użyć `<gcServer>` wykonuje element, aby kontrolować typ wyrzucania elementów bezużytecznych środowiska CLR. Użyj <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> właściwości w celu określenia, czy włączono serwer wyrzucania elementów bezużytecznych.  
  
 W przypadku komputerów z jednym procesorem wyrzucanie elementów bezużytecznych stacji roboczej domyślne powinny być najszybszą opcję. Dwa procesory komputerów można stacji roboczej lub serwera. Wyrzucanie elementów bezużytecznych serwera powinien być najszybszą opcję dla więcej niż dwóch procesorów.  
  
 Ten element może być używany tylko w pliku konfiguracyjnym aplikacji; jest on ignorowany, jeśli znajduje się w pliku konfiguracji komputera.  
  
> [!NOTE]
>  W .NET Framework 4 i starszych wersjach współbieżne wyrzucanie elementów bezużytecznych nie jest dostępna, gdy serwer wyrzucania elementów bezużytecznych jest włączona. Począwszy od [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], serwer wyrzucania elementów bezużytecznych jest współbieżnych. Aby użyć serwera niewspółbieżnym wyrzucaniem elementów bezużytecznych, ustaw `<gcServer>` elementu `true` i [ \<gcconcurrent — > element](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) do `false`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład umożliwia wyrzucanie elementów bezużytecznych serwera.  
  
```xml  
<configuration>  
   <runtime>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>  
- [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)  
- [Instrukcje: Wyłączyć współbieżne wyrzucanie elementów bezużytecznych](https://msdn.microsoft.com/library/ba2c6c67-5778-497c-9fac-5f793b5500c7)
