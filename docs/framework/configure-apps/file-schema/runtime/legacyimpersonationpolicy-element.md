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
ms.openlocfilehash: 5e43ead278ecd4049014f4000a2f056b2190f7e5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154107"
---
# <a name="legacyimpersonationpolicy-element"></a>\<legacyImpersonationPolicy> Element
Określa, że tożsamość systemu Windows nie przepływa przez punkty asynchroniczne, niezależnie od ustawień przepływu dla kontekstu wykonywania w bieżącym wątku.  
  
[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>czasu wykonywania**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<legacyImpersonationPolicy>**  
  
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
|`enabled`|Atrybut wymagany.<br /><br /> Określa, że <xref:System.Security.Principal.WindowsIdentity> nie przepływa przez punkty asynchroniczne, niezależnie od ustawień <xref:System.Threading.ExecutionContext> przepływu w bieżącym wątku.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|<xref:System.Security.Principal.WindowsIdentity>przepływów przez punkty asynchroniczne w zależności od ustawień <xref:System.Threading.ExecutionContext> przepływu dla bieżącego wątku. Domyślnie włączone.|  
|`true`|<xref:System.Security.Principal.WindowsIdentity>nie przepływa przez punkty asynchroniczne, <xref:System.Threading.ExecutionContext> niezależnie od ustawień przepływu w bieżącym wątku.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 W .NET Framework w wersjach 1.0 i <xref:System.Security.Principal.WindowsIdentity> 1.1 nie przepływa przez żadnych punktów asynchronicznych zdefiniowanych przez użytkownika. Począwszy od programu .NET Framework w wersji <xref:System.Threading.ExecutionContext> 2.0, istnieje obiekt, który zawiera informacje o aktualnie wykonywanym wątku i przepływa przez punkty asynchroniczne w domenie aplikacji. Jest <xref:System.Security.Principal.WindowsIdentity> uwzględniony w tym kontekście wykonywania i w związku z tym również przepływa przez punkty asynchroniczne, co oznacza, że jeśli istnieje kontekst personifikacji, będzie również przepływać.  
  
 Począwszy od programu .NET Framework 2.0, można użyć `<legacyImpersonationPolicy>` elementu, aby określić, że <xref:System.Security.Principal.WindowsIdentity> nie przepływa przez punkty asynchroniczne.  
  
> [!NOTE]
> Środowisko wykonawcze języka wspólnego (CLR) jest świadomy operacji personifikacji wykonywanych przy użyciu tylko kodu zarządzanego, a nie personifikacji wykonywane poza kodem zarządzanym, takich jak za pośrednictwem platformy wywołać do kodu niezarządzanego lub za pośrednictwem bezpośrednich wywołań funkcji Win32. Tylko <xref:System.Security.Principal.WindowsIdentity> obiekty zarządzane mogą przepływać przez punkty `alwaysFlowImpersonationPolicy` asynchroniczne,`<alwaysFlowImpersonationPolicy enabled="true"/>`chyba że element został ustawiony na true ( ). Ustawienie `alwaysFlowImpersonationPolicy` elementu na true określa, że tożsamość systemu Windows zawsze przepływa przez punkty asynchroniczne, niezależnie od sposobu personifikacji została wykonana. Aby uzyskać więcej informacji na temat przepływu personifikacji niezarządzanej w punktach asynchronicznych, zobacz [ \<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).  
  
 To domyślne zachowanie można zmienić na dwa inne sposoby:  
  
1. W kodzie zarządzanym na podstawie wątku.  
  
     Przepływ można pominąć na podstawie wątku, <xref:System.Threading.ExecutionContext> modyfikując ustawienia <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType> <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> i <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> <xref:System.Security.SecurityContext> ustawienia za pomocą metody , lub.  
  
2. W wywołaniu interfejsu hostingu niezarządzanego, aby załadować środowisko uruchomieniowe języka wspólnego (CLR).  
  
     Jeśli do załadowania środowiska CLR używany jest niezarządzany interfejs hostingu (zamiast prostego zarządzanego pliku wykonywalnego), można określić specjalną flagę w wywołaniu funkcji [CorBindToRuntimeEx.](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) Aby włączyć tryb zgodności dla całego procesu, `flags` ustaw parametr [funkcji CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) na STARTUP_LEGACY_IMPERSONATION.  
  
 Aby uzyskać więcej informacji, zobacz [ \<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).  
  
## <a name="configuration-file"></a>Plik konfiguracji  
 W aplikacji .NET Framework ten element może być używany tylko w pliku konfiguracji aplikacji.  
  
 W przypadku aplikacji ASP.NET przepływ personifikacji można skonfigurować w pliku aspnet.config znajdującym \<się w katalogu Folder systemu Windows>\Microsoft.NET\Framework\vx.x.xxxx.  
  
 ASP.NET domyślnie wyłącza przepływ personifikacji w pliku aspnet.config przy użyciu następujących ustawień konfiguracyjnych:  
  
``` xml
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
 W poniższym przykładzie pokazano, jak określić starsze zachowanie, które nie przepływa tożsamości systemu Windows przez punkty asynchroniczne.  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też

- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
- [\<zawsze Element> PolitykiFlowImpersonation](alwaysflowimpersonationpolicy-element.md)
