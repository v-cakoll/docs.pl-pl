---
title: '&lt;legacyimpersonationpolicy —&gt; — Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#legacyImpersonationPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/legacyImpersonationPolicy
helpviewer_keywords:
- <legacyImpersonationPolicy> element
- legacyImpersonationPolicy element
ms.assetid: 6e00af10-42f3-4235-8415-1bb2db78394e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f90853a93b40eeb72f07ad9b1849aa99c8e8bf3d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32745191"
---
# <a name="ltlegacyimpersonationpolicygt-element"></a>&lt;legacyimpersonationpolicy —&gt; — Element
Określa, że tożsamość systemu Windows nie przepływ między punktami asynchroniczne, niezależnie od ustawień przepływu kontekstu wykonywania w bieżącym wątku.  
  
 \<Konfiguracja >  
\<runtime>  
\<legacyImpersonationPolicy>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<legacyImpersonationPolicy    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`enabled`|Atrybut wymagany.<br /><br /> Określa, że <xref:System.Security.Principal.WindowsIdentity> nie przepływ między punktami asynchroniczne, niezależnie od tego <xref:System.Threading.ExecutionContext> przepływu ustawień w bieżącym wątku.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|<xref:System.Security.Principal.WindowsIdentity> przepływy między punktami asynchronicznych w zależności od <xref:System.Threading.ExecutionContext> przepływu ustawienia bieżącego wątku. Domyślnie włączone.|  
|`true`|<xref:System.Security.Principal.WindowsIdentity> nie przepływ między punktami asynchroniczne, niezależnie od tego <xref:System.Threading.ExecutionContext> przepływu ustawień w bieżącym wątku.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 W wersji systemu .NET Framework 1.0 i 1.1 <xref:System.Security.Principal.WindowsIdentity> nie przepływ między punktami asynchroniczne wszelkie zdefiniowane przez użytkownika. W programie .NET Framework w wersji 2.0, Brak <xref:System.Threading.ExecutionContext> obiektu, który zawiera informacje o obecnie wykonywanym wątku który przepływa między punktami asynchronicznych w domenie aplikacji. <xref:System.Security.Principal.WindowsIdentity> Znajduje się w tym kontekście wykonania i w związku z tym przepływa również między punktami asynchroniczne, co oznacza, że jeśli kontekst personifikacji istnieje, jej będą przepływać również.  
  
 Począwszy od programu .NET Framework 2.0, można użyć `<legacyImpersonationPolicy>` elementu, aby określić, że <xref:System.Security.Principal.WindowsIdentity> nie przepływ między punktami asynchronicznego.  
  
> [!NOTE]
>  Środowisko uruchomieniowe języka wspólnego (CLR) jest świadome personifikacji operacje wykonywane przy użyciu tylko kodu zarządzanego nie pochodzi z personifikacji realizuje poza kodu zarządzanego, takich jak platforma wywołania do kodu niezarządzanego lub poprzez bezpośrednie wywołania funkcji Win32. Tylko zarządzanego <xref:System.Security.Principal.WindowsIdentity> obiektów może przechodzić między punktami asynchroniczne, chyba że `alwaysFlowImpersonationPolicy` element została ustawiona na true (`<alwaysFlowImpersonationPolicy enabled="true"/>`). Ustawienie `alwaysFlowImpersonationPolicy` elementu na wartość true, określa, czy tożsamości systemu Windows zawsze przepływa między punktami asynchroniczne, niezależnie od tego, jak została wykonana personifikacji. Aby uzyskać więcej informacji na temat przechodzenia przez punkty asynchroniczne niezarządzany personifikacji, zobacz [ \<alwaysflowimpersonationpolicy — > elementu](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md).  
  
 Można zmienić to zachowanie domyślne są dwa inne sposoby:  
  
1.  W kodzie zarządzanym na podstawie dla każdego wątku.  
  
     Można pominąć przepływem na podstawie dla każdego wątku, modyfikując <xref:System.Threading.ExecutionContext> i <xref:System.Security.SecurityContext> ustawienia za pomocą <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> lub <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> metody.  
  
2.  W wywołaniu niezarządzane interfejsu hostingu załadować środowisko uruchomieniowe języka wspólnego (CLR).  
  
     Jeśli interfejs hostingu niezarządzane (zamiast prostego pliku wykonywalnego zarządzane) służy do ładowania środowiska CLR, można określić Flaga specjalna w wywołaniu [CorBindToRuntimeEx — funkcja](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) funkcji. Aby włączyć tryb zgodności dla całego procesu, ustaw `flags` parametr [CorBindToRuntimeEx — funkcja](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) do STARTUP_LEGACY_IMPERSONATION.  
  
 Aby uzyskać więcej informacji, zobacz [ \<alwaysflowimpersonationpolicy — > elementu](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md).  
  
## <a name="configuration-file"></a>Plik konfiguracji  
 W aplikacji .NET Framework ten element może być użyty tylko w pliku konfiguracyjnym aplikacji.  
  
 Dla aplikacji ASP.NET można skonfigurować przepływ personifikacji w znaleziono w pliku konfigurację aspnet.config \<Windows Folder > \Microsoft.NET\Framework\vx.x.xxxx katalogu.  
  
 ASP.NET domyślnie wyłącza przepływu personifikacji w pliku konfigurację aspnet.config przy użyciu następujących ustawień konfiguracji:  
  
``` xml
<configuration>  
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
 Poniższy przykład pokazuje, jak określić zachowanie starszych tożsamości systemu Windows nie przepływ między punktami asynchronicznego.  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<alwaysflowimpersonationpolicy — > — Element](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)
