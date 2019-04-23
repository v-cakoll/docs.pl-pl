---
title: <legacyImpersonationPolicy>, element
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
ms.openlocfilehash: c39ee551dde19d87a75403f3db7433d1ef829f3b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59333993"
---
# <a name="legacyimpersonationpolicy-element"></a>\<legacyImpersonationPolicy> Element
Określa, że tożsamość Windows nie przepływać przez punkty asynchroniczne, na niezależnie od ustawień przepływu kontekstu wykonania dla bieżącego wątku.  
  
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
|`enabled`|Atrybut wymagany.<br /><br /> Określa, że <xref:System.Security.Principal.WindowsIdentity> przepływać przez punkty asynchroniczne, niezależnie od wartości <xref:System.Threading.ExecutionContext> przepływu ustawień w bieżącym wątku.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|<xref:System.Security.Principal.WindowsIdentity> przepływy przez punkty asynchroniczne, w zależności od <xref:System.Threading.ExecutionContext> przepływu ustawienia dla bieżącego wątku. Domyślnie włączone.|  
|`true`|<xref:System.Security.Principal.WindowsIdentity> przepływać przez punkty asynchroniczne, niezależnie od wartości <xref:System.Threading.ExecutionContext> przepływu ustawień w bieżącym wątku.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 W .NET Framework w wersji 1.0 i 1.1 <xref:System.Security.Principal.WindowsIdentity> nie przepływać przez punkty asynchroniczne wszelkie zdefiniowane przez użytkownika. Począwszy od programu .NET Framework w wersji 2.0, Brak <xref:System.Threading.ExecutionContext> obiektu, który zawiera informacje o aktualnie wykonywany wątek który przepływa przez punkty asynchroniczne w domenie aplikacji. <xref:System.Security.Principal.WindowsIdentity> Znajduje się w tym kontekście wykonania i w związku z tym również odbywa się przez punkty asynchroniczne, co oznacza, że istnienia kontekstu personifikacji go będą przepływać także.  
  
 Począwszy od programu .NET Framework 2.0, można użyć `<legacyImpersonationPolicy>` elementu, aby określić, że <xref:System.Security.Principal.WindowsIdentity> nie przepływać przez punkty asynchroniczne.  
  
> [!NOTE]
>  Środowisko uruchomieniowe języka wspólnego (CLR) ma informacje o personifikacji operacje wykonywane przy użyciu tylko kod zarządzany nie jest personifikacji realizuje poza kodu zarządzanego, takich jak platforma wywołania do kodu niezarządzanego lub za pomocą bezpośredniego wywołania funkcji Win32. Tylko zarządzane <xref:System.Security.Principal.WindowsIdentity> obiektów może przepływać przez punkty asynchroniczne, chyba że `alwaysFlowImpersonationPolicy` element został ustawiony na wartość true (`<alwaysFlowImpersonationPolicy enabled="true"/>`). Ustawienie `alwaysFlowImpersonationPolicy` element na wartość true Określa, że tożsamość Windows zawsze odbywa się za pośrednictwem punkty asynchroniczne, niezależnie od tego, jak zostało wykonane personifikacji. Aby uzyskać więcej informacji na temat przepływać przez punkty asynchroniczne niezarządzany personifikacji, zobacz [ \<alwaysflowimpersonationpolicy — > Element](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md).  
  
 Możesz zmienić to zachowanie domyślne na dwa inne sposoby:  
  
1. W kodzie zarządzanym na zasadzie na wątek.  
  
     Można pominąć przepływu na podstawie na wątek, modyfikując <xref:System.Threading.ExecutionContext> i <xref:System.Security.SecurityContext> ustawienia za pomocą <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> lub <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> metody.  
  
2. W wywołaniu do niezarządzanego interfejsu hostingu załadować środowisko uruchomieniowe języka wspólnego (CLR).  
  
     Jeśli niezarządzane hostingu interfejsu (zamiast prostego pliku wykonywalnego zarządzane) jest używana do ładowania CLR, można określić Flaga specjalna, w wywołaniu [corbindtoruntimeex — funkcja](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) funkcji. Aby włączyć tryb zgodności dla całego procesu, należy ustawić `flags` parametr [corbindtoruntimeex — funkcja](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) do STARTUP_LEGACY_IMPERSONATION.  
  
 Aby uzyskać więcej informacji, zobacz [ \<alwaysflowimpersonationpolicy — > Element](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md).  
  
## <a name="configuration-file"></a>Plik konfiguracji  
 W aplikacji .NET Framework ten element może być użyty tylko w pliku konfiguracyjnym aplikacji.  
  
 Dla aplikacji ASP.NET można skonfigurować przepływ personifikacji w znaleziono w pliku konfigurację aspnet.config \<Windows Folder > \Microsoft.NET\Framework\vx.x.xxxx katalogu.  
  
 ASP.NET domyślnie wyłącza przepływ personifikacji w pliku konfigurację aspnet.config przy użyciu następujących ustawień konfiguracji:  
  
``` xml
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
 Poniższy przykład pokazuje, jak określić starsze zachowanie, które nie przepływać tożsamości Windows przez punkty asynchroniczne.  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [\<alwaysFlowImpersonationPolicy> Element](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)
