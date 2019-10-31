---
title: <legacyImpersonationPolicy> Element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#legacyImpersonationPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/legacyImpersonationPolicy
helpviewer_keywords:
- <legacyImpersonationPolicy> element
- legacyImpersonationPolicy element
ms.assetid: 6e00af10-42f3-4235-8415-1bb2db78394e
ms.openlocfilehash: 18a027bc09f2400a10a06efdc4c5355686bcb56d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116541"
---
# <a name="legacyimpersonationpolicy-element"></a>\<element > legacyImpersonationPolicy
Określa, że tożsamość systemu Windows nie przepływa między punktami asynchronicznymi, niezależnie od ustawień przepływu dla kontekstu wykonywania w bieżącym wątku.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<środowiska uruchomieniowego >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<legacyImpersonationPolicy >**  
  
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
|`enabled`|Atrybut wymagany.<br /><br /> Określa, że <xref:System.Security.Principal.WindowsIdentity> nie przepływa między punktami asynchronicznymi, niezależnie od ustawień przepływu <xref:System.Threading.ExecutionContext> w bieżącym wątku.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|<xref:System.Security.Principal.WindowsIdentity> przepływy w punktach asynchronicznych w zależności od ustawień przepływu <xref:System.Threading.ExecutionContext> dla bieżącego wątku. Domyślnie włączone.|  
|`true`|<xref:System.Security.Principal.WindowsIdentity> nie przepływa między punktami asynchronicznymi, niezależnie od ustawień przepływu <xref:System.Threading.ExecutionContext> w bieżącym wątku.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 W .NET Framework wersje 1,0 i 1,1 <xref:System.Security.Principal.WindowsIdentity> nie przepływa przez żadne punkty asynchroniczne zdefiniowane przez użytkownika. Począwszy od .NET Framework w wersji 2,0, istnieje <xref:System.Threading.ExecutionContext> obiekt, który zawiera informacje o aktualnie wykonywanym wątku, i przepływie między punktami asynchronicznymi w domenie aplikacji. <xref:System.Security.Principal.WindowsIdentity> jest uwzględniony w tym kontekście wykonywania i w związku z tym przepływy są wykonywane w punktach asynchronicznych, co oznacza, że jeśli istnieje kontekst personifikacji, również będzie przepływać.  
  
 Począwszy od .NET Framework 2,0, można użyć elementu `<legacyImpersonationPolicy>`, aby określić, że <xref:System.Security.Principal.WindowsIdentity> nie przepływów między punktami asynchronicznymi.  
  
> [!NOTE]
> Środowisko uruchomieniowe języka wspólnego (CLR) ma świadomość operacji personifikacji wykonywanych przy użyciu tylko kodu zarządzanego, a nie personifikacji wykonanej poza kodem zarządzanym, na przykład za pośrednictwem wywołania platformy do kodu niezarządzanego lub bezpośrednie wywołania do funkcji Win32. Tylko zarządzane obiekty <xref:System.Security.Principal.WindowsIdentity> mogą przepływać przez punkty asynchroniczne, chyba że element `alwaysFlowImpersonationPolicy` został ustawiony na wartość true (`<alwaysFlowImpersonationPolicy enabled="true"/>`). Ustawienie elementu `alwaysFlowImpersonationPolicy` na wartość true określa, że tożsamość systemu Windows zawsze przepływa w punktach asynchronicznych, bez względu na to, jak personifikacja została wykonana. Aby uzyskać więcej informacji na temat przepływu niezarządzanej personifikacji w punktach asynchronicznych, zobacz [\<alwaysFlowImpersonationPolicy > elementu](alwaysflowimpersonationpolicy-element.md).  
  
 To zachowanie domyślne można zmienić na dwa sposoby:  
  
1. W kodzie zarządzanym dla poszczególnych wątków.  
  
     Przepływ można pominąć dla poszczególnych wątków, modyfikując <xref:System.Threading.ExecutionContext> i <xref:System.Security.SecurityContext> ustawienia przy użyciu metody <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> lub <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType>.  
  
2. W wywołaniu interfejsu hostingu niezarządzanego w celu załadowania środowiska uruchomieniowego języka wspólnego (CLR).  
  
     Jeśli do załadowania środowiska CLR jest używany niezarządzany interfejs hostingu (zamiast prostego zarządzanego pliku wykonywalnego), można określić specjalną flagę w wywołaniu funkcji [funkcji CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) . Aby włączyć tryb zgodności dla całego procesu, należy ustawić parametr `flags` dla [funkcji CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) na STARTUP_LEGACY_IMPERSONATION.  
  
 Aby uzyskać więcej informacji, zobacz [\<alwaysFlowImpersonationPolicy >](alwaysflowimpersonationpolicy-element.md).  
  
## <a name="configuration-file"></a>Plik konfiguracji  
 W aplikacji .NET Framework ten element może być używany tylko w pliku konfiguracji aplikacji.  
  
 W przypadku aplikacji ASP.NET przepływ personifikacji można skonfigurować w pliku aspnet. config znajdującym się w folderze \<systemu Windows > katalogu \Microsoft.NET\Framework\vx.x.xxxx.  
  
 Domyślnie ASP.NET powoduje wyłączenie przepływu personifikacji w pliku aspnet. config przy użyciu następujących ustawień konfiguracji:  
  
``` xml
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
 Poniższy przykład pokazuje, jak określić starsze zachowanie, które nie przepływa tożsamości systemu Windows w punktach asynchronicznych.  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
- [\<element > alwaysFlowImpersonationPolicy](alwaysflowimpersonationpolicy-element.md)
