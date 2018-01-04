---
title: "&lt;alwaysflowimpersonationpolicy —&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/alwaysFlowImpersonationPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#alwaysFlowImpersonationPolicy
helpviewer_keywords:
- alwaysFlowImpersonationPolicy element
- <alwaysFlowImpersonationPolicy> element
ms.assetid: ee622801-9e46-470b-85ab-88c4b1dd2ee1
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: be1df955f7586848968cb32cd66a4c6889cfffa8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltalwaysflowimpersonationpolicygt-element"></a>&lt;alwaysflowimpersonationpolicy —&gt; — Element
Określa, czy tożsamość systemu Windows zawsze przepływa między punktami asynchroniczne, niezależnie od tego, jak została wykonana personifikacji.  
  
 \<Konfiguracja >  
\<Runtime >  
\<alwaysflowimpersonationpolicy — >  
  
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
|`enabled`|Atrybut wymagany.<br /><br /> Wskazuje, czy tożsamość systemu Windows przepływa między punktami asynchronicznego.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|Takie jak zarządzane tożsamości nie przepływ między punktami asynchroniczne, chyba że personifikacja odbywa się za pośrednictwem systemu Windows metody <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>. Domyślnie włączone.|  
|`true`|Tożsamość systemu Windows zawsze przepływa między punktami asynchroniczne, niezależnie od tego, jak została wykonana personifikacji.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 W wersji systemu .NET Framework 1.0 i 1.1 tożsamość systemu Windows nie przepływ między punktami asynchronicznego. W programie .NET Framework w wersji 2.0, Brak <xref:System.Threading.ExecutionContext> obiekt, który zawiera informacje o obecnie wykonywanym wątku i go przepływa między punktami asynchronicznych w domenie aplikacji. <xref:System.Security.Principal.WindowsIdentity> Także przepływów jako część informacji przepływającego między punktami asynchroniczne, pod warunkiem personifikację został osiągnięty przy użyciu zarządzane metody takie jak <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> , a nie za pomocą innych środków, takich jak platforma wywołania do metody natywnej. Ten element jest używany do określenia, czy między punktami asynchroniczne, niezależnie od tego, jak została osiągnięta personifikację przepływu tożsamości systemu Windows.  
  
 Można zmienić to zachowanie domyślne są dwa inne sposoby:  
  
1.  W kodzie zarządzanym na podstawie dla każdego wątku.  
  
     Można pominąć przepływem na podstawie dla każdego wątku, modyfikując <xref:System.Threading.ExecutionContext> i <xref:System.Security.SecurityContext> ustawienia za pomocą <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>, lub <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> metody.  
  
2.  W wywołaniu niezarządzane interfejsu hostingu załadować środowisko uruchomieniowe języka wspólnego (CLR).  
  
     Jeśli interfejs hostingu niezarządzane (zamiast prostego pliku wykonywalnego zarządzane) służy do ładowania środowiska CLR, można określić Flaga specjalna w wywołaniu [CorBindToRuntimeEx — funkcja](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) funkcji. Aby włączyć tryb zgodności dla całego procesu, ustaw `flags` parametr [CorBindToRuntimeEx — funkcja](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) do `STARTUP_ALWAYSFLOW_IMPERSONATION`.  
  
## <a name="configuration-file"></a>Plik konfiguracji  
 W aplikacji .NET Framework ten element może być użyty tylko w pliku konfiguracyjnym aplikacji.  
  
 Dla aplikacji ASP.NET można skonfigurować przepływ personifikacji w znaleziono w pliku konfigurację aspnet.config \<Windows Folder > \Microsoft.NET\Framework\vx.x.xxxx katalogu.  
  
 ASP.NET domyślnie wyłącza przepływu personifikacji w pliku konfigurację aspnet.config przy użyciu następujących ustawień konfiguracji:  
  
```  
configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 W programie ASP.NET Jeśli chcesz umożliwić przepływ personifikacji zamiast tego należy jawnie użyć następujących ustawień konfiguracji:  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób określania, czy tożsamość systemu Windows przepływa między punktami asynchroniczne, nawet wtedy, gdy personifikacja odbywa się za pośrednictwem oznacza innych niż zarządzane metody.  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<legacyimpersonationpolicy — > — Element](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)
