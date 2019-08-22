---
title: <alwaysFlowImpersonationPolicy>, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/alwaysFlowImpersonationPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#alwaysFlowImpersonationPolicy
helpviewer_keywords:
- alwaysFlowImpersonationPolicy element
- <alwaysFlowImpersonationPolicy> element
ms.assetid: ee622801-9e46-470b-85ab-88c4b1dd2ee1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b42c141362d99090db922d3a6b429f05592130cd
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659014"
---
# <a name="alwaysflowimpersonationpolicy-element"></a>\<alwaysFlowImpersonationPolicy> Element
Określa, że tożsamość systemu Windows jest zawsze przepływów między punktami asynchronicznymi, niezależnie od tego, jak personifikacja została wykonana.  
  
 \<> konfiguracji  
\<runtime>  
\<alwaysFlowImpersonationPolicy>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<alwaysFlowImpersonationPolicy    
  enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`enabled`|Atrybut wymagany.<br /><br /> Wskazuje, czy tożsamość systemu Windows jest przesyłana między punkty asynchroniczne.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|Tożsamość systemu Windows nie jest przepływa między punktami asynchronicznymi, chyba że personifikacja jest wykonywana za <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>pomocą metod zarządzanych, takich jak. Domyślnie włączone.|  
|`true`|Tożsamość systemu Windows jest zawsze przepływów między punktami asynchronicznymi, niezależnie od tego, jak personifikacja została wykonana.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 W .NET Framework wersje 1,0 i 1,1 tożsamość systemu Windows nie jest przesyłana między punktami asynchronicznymi. W .NET Framework w wersji 2,0 istnieje <xref:System.Threading.ExecutionContext> obiekt, który zawiera informacje o aktualnie wykonywanym wątku i przepływa przez punkty asynchroniczne w domenie aplikacji. Również przepływy jako część informacji przesyłanych przez punkty asynchroniczne, pod warunkiem, że personifikacja została osiągnięta przy użyciu metod <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> zarządzanych, takich jak, a nie za pośrednictwem innych, takich jak wywołanie platformy do metod natywnych. <xref:System.Security.Principal.WindowsIdentity> Ten element służy do określenia, że tożsamość systemu Windows jest przesyłana w punktach asynchronicznych, niezależnie od sposobu uzyskania personifikacji.  
  
 To zachowanie domyślne można zmienić na dwa sposoby:  
  
1. W kodzie zarządzanym dla poszczególnych wątków.  
  
     Przepływ można pominąć dla <xref:System.Threading.ExecutionContext> każdego wątku, modyfikując ustawienia i <xref:System.Security.SecurityContext> przy użyciu <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>metody, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>, lub <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> .  
  
2. W wywołaniu interfejsu hostingu niezarządzanego w celu załadowania środowiska uruchomieniowego języka wspólnego (CLR).  
  
     Jeśli do załadowania środowiska CLR jest używany niezarządzany interfejs hostingu (zamiast prostego zarządzanego pliku wykonywalnego), można określić specjalną flagę w wywołaniu funkcji [funkcji CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) . Aby włączyć tryb zgodności dla całego procesu, należy ustawić `flags` parametr dla [funkcji CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) na. `STARTUP_ALWAYSFLOW_IMPERSONATION`  
  
## <a name="configuration-file"></a>Plik konfiguracji  
 W aplikacji .NET Framework ten element może być używany tylko w pliku konfiguracji aplikacji.  
  
 W przypadku aplikacji ASP.NET przepływ personifikacji można skonfigurować w pliku aspnet. config znajdującym się w \<folderze systemu Windows > katalogu \Microsoft.NET\Framework\vx.x.xxxx.  
  
 Domyślnie ASP.NET powoduje wyłączenie przepływu personifikacji w pliku aspnet. config przy użyciu następujących ustawień konfiguracji:  
  
```xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 W ASP.NET, jeśli chcesz zezwolić na przepływ personifikacji, musisz jawnie użyć następujących ustawień konfiguracji:  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak określić, że tożsamość systemu Windows jest realizowana w punktach asynchronicznych, nawet jeśli Personifikacja jest realizowana za pośrednictwem środków innych niż metody zarządzane.  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
- [\<legacyImpersonationPolicy, element >](legacyimpersonationpolicy-element.md)
