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
ms.openlocfilehash: 7c8ac37932a528ff0f000cbaab49124dec51b88c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154486"
---
# <a name="alwaysflowimpersonationpolicy-element"></a>\<zawsze Element> PolitykiFlowImpersonation
Określa, że tożsamość systemu Windows zawsze przepływa przez punkty asynchroniczne, niezależnie od sposobu personifikacji została wykonana.  
  
[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>czasu wykonywania**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<alwaysFlowImpersonationPolicy>**\  
  
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
|`enabled`|Atrybut wymagany.<br /><br /> Wskazuje, czy tożsamość systemu Windows przepływa przez punkty asynchroniczne.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|Tożsamość systemu Windows nie przepływa przez punkty asynchroniczne, chyba <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>że personifikacja jest wykonywana za pomocą metod zarządzanych, takich jak . Domyślnie włączone.|  
|`true`|Tożsamość systemu Windows zawsze przepływa przez punkty asynchroniczne, niezależnie od sposobu personifikacji została wykonana.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 W programie .NET Framework w wersjach 1.0 i 1.1 tożsamość systemu Windows nie przepływa przez punkty asynchroniczne. W programie .NET Framework w wersji 2.0 znajduje się obiekt zawierający <xref:System.Threading.ExecutionContext> informacje o aktualnie wykonywanym wątku i przepływający przez punkty asynchroniczne w domenie aplikacji. Przepływy <xref:System.Security.Principal.WindowsIdentity> również jako część informacji, które przepływa przez punkty asynchroniczne, pod warunkiem, że personifikacji został osiągnięty przy użyciu metod zarządzanych, takich jak <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> i nie za pomocą innych środków, takich jak platforma wywołać do metod natywnych. Ten element jest używany do określenia, że tożsamość systemu Windows przepływa przez punkty asynchroniczne, niezależnie od tego, jak personifikacja została osiągnięta.  
  
 To domyślne zachowanie można zmienić na dwa inne sposoby:  
  
1. W kodzie zarządzanym na podstawie wątku.  
  
     Przepływ można pominąć na podstawie wątku, <xref:System.Threading.ExecutionContext> modyfikując ustawienia <xref:System.Security.SecurityContext> i ustawienia za pomocą metody <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>lub . <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType>  
  
2. W wywołaniu interfejsu hostingu niezarządzanego, aby załadować środowisko uruchomieniowe języka wspólnego (CLR).  
  
     Jeśli do załadowania środowiska CLR używany jest niezarządzany interfejs hostingu (zamiast prostego zarządzanego pliku wykonywalnego), można określić specjalną flagę w wywołaniu funkcji [CorBindToRuntimeEx.](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) Aby włączyć tryb zgodności dla całego procesu, `flags` ustaw parametr [funkcji CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) na `STARTUP_ALWAYSFLOW_IMPERSONATION`.  
  
## <a name="configuration-file"></a>Plik konfiguracji  
 W aplikacji .NET Framework ten element może być używany tylko w pliku konfiguracji aplikacji.  
  
 W przypadku aplikacji ASP.NET przepływ personifikacji można skonfigurować w pliku aspnet.config znajdującym \<się w katalogu Folder systemu Windows>\Microsoft.NET\Framework\vx.x.xxxx.  
  
 ASP.NET domyślnie wyłącza przepływ personifikacji w pliku aspnet.config przy użyciu następujących ustawień konfiguracyjnych:  
  
```xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 W ASP.NET, jeśli chcesz zezwolić na przepływ personifikacji zamiast tego, należy jawnie użyć następujących ustawień konfiguracji:  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak określić, że tożsamość systemu Windows przepływa przez punkty asynchroniczne, nawet wtedy, gdy personifikacja zostanie osiągnięta za pomocą środków innych niż metody zarządzane.  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też

- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
- [\<legacyImpersonationPolicy> Element](legacyimpersonationpolicy-element.md)
