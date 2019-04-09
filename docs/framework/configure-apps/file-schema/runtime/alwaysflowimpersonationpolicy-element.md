---
title: <alwaysFlowImpersonationPolicy> Element
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
ms.openlocfilehash: ce1928254699f4de41e92087c76be9bc3c249523
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108046"
---
# <a name="alwaysflowimpersonationpolicy-element"></a>\<alwaysFlowImpersonationPolicy> Element
Określa, że tożsamość Windows zawsze odbywa się za pośrednictwem punkty asynchroniczne, niezależnie od tego, jak zostało wykonane personifikacji.  
  
 \<Konfiguracja >  
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
|`enabled`|Atrybut wymagany.<br /><br /> Wskazuje, czy tożsamość Windows odbywa się za pośrednictwem punkty asynchroniczne.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|Windows tożsamości nie przepływać przez punkty asynchroniczne, chyba że personifikacji odbywa się za pośrednictwem zarządzanych metod, takich jak <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>. Domyślnie włączone.|  
|`true`|Tożsamość Windows zawsze odbywa się za pośrednictwem punkty asynchroniczne, niezależnie od tego, jak zostało wykonane personifikacji.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 W wersjach programu .NET Framework 1.0 i 1.1 tożsamości Windows nie przepływać przez punkty asynchroniczne. W programie .NET Framework 2.0, Brak <xref:System.Threading.ExecutionContext> obiekt, który zawiera informacje o aktualnie wykonywany wątek i przepływy go przez punkty asynchroniczne w domenie aplikacji. <xref:System.Security.Principal.WindowsIdentity> Także przepływy jako część informacji, który przepływa przez punkty asynchroniczne, pod warunkiem personifikacji został osiągnięty przy użyciu zarządzane metody takie jak <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> a nie za pomocą innych środków, takich jak platforma wywołania do metod macierzystych. Ten element jest używany do określenia, czy tożsamość Windows przepływać przez punkty asynchroniczne, niezależnie od tego, jak została osiągnięta personifikacji.  
  
 Możesz zmienić to zachowanie domyślne na dwa inne sposoby:  
  
1.  W kodzie zarządzanym na zasadzie na wątek.  
  
     Można pominąć przepływu na podstawie na wątek, modyfikując <xref:System.Threading.ExecutionContext> i <xref:System.Security.SecurityContext> ustawienia za pomocą <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>, lub <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> metody.  
  
2.  W wywołaniu do niezarządzanego interfejsu hostingu załadować środowisko uruchomieniowe języka wspólnego (CLR).  
  
     Jeśli niezarządzane hostingu interfejsu (zamiast prostego pliku wykonywalnego zarządzane) jest używana do ładowania CLR, można określić Flaga specjalna, w wywołaniu [corbindtoruntimeex — funkcja](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) funkcji. Aby włączyć tryb zgodności dla całego procesu, należy ustawić `flags` parametr [corbindtoruntimeex — funkcja](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) do `STARTUP_ALWAYSFLOW_IMPERSONATION`.  
  
## <a name="configuration-file"></a>Plik konfiguracji  
 W aplikacji .NET Framework ten element może być użyty tylko w pliku konfiguracyjnym aplikacji.  
  
 Dla aplikacji ASP.NET można skonfigurować przepływ personifikacji w znaleziono w pliku konfigurację aspnet.config \<Windows Folder > \Microsoft.NET\Framework\vx.x.xxxx katalogu.  
  
 ASP.NET domyślnie wyłącza przepływ personifikacji w pliku konfigurację aspnet.config przy użyciu następujących ustawień konfiguracji:  
  
```xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 W programie ASP.NET: Jeśli chcesz umożliwić przepływ personifikacji zamiast tego trzeba jawnie użyć następujących ustawień konfiguracji:  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak określić, że tożsamość Windows odbywa się za pośrednictwem punkty asynchroniczne, nawet wtedy, gdy personifikacji odbywa się za pośrednictwem oznacza, że inne niż zarządzanych metod.  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [\<legacyImpersonationPolicy> Element](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)
