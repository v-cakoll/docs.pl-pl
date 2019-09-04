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
ms.openlocfilehash: cd09598800b74c4807163bc921806f5b470e0d24
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252494"
---
# <a name="legacyimpersonationpolicy-element"></a><span data-ttu-id="bb966-102">\<legacyImpersonationPolicy, element ></span><span class="sxs-lookup"><span data-stu-id="bb966-102">\<legacyImpersonationPolicy> Element</span></span>
<span data-ttu-id="bb966-103">Określa, że tożsamość systemu Windows nie przepływa między punktami asynchronicznymi, niezależnie od ustawień przepływu dla kontekstu wykonywania w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="bb966-103">Specifies that the Windows identity does not flow across asynchronous points, regardless of the flow settings for the execution context on the current thread.</span></span>  
  
<span data-ttu-id="bb966-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bb966-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bb966-105">&nbsp;&nbsp;[ **\<> środowiska uruchomieniowego**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="bb966-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="bb966-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<legacyImpersonationPolicy>**</span><span class="sxs-lookup"><span data-stu-id="bb966-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<legacyImpersonationPolicy>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb966-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="bb966-107">Syntax</span></span>  
  
```xml  
<legacyImpersonationPolicy    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bb966-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="bb966-108">Attributes and Elements</span></span>  
 <span data-ttu-id="bb966-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="bb966-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bb966-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bb966-110">Attributes</span></span>  
  
|<span data-ttu-id="bb966-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="bb966-111">Attribute</span></span>|<span data-ttu-id="bb966-112">Opis</span><span class="sxs-lookup"><span data-stu-id="bb966-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="bb966-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="bb966-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="bb966-114">Określa, że <xref:System.Security.Principal.WindowsIdentity> nie przepływy między punktami asynchronicznymi, niezależnie <xref:System.Threading.ExecutionContext> od ustawień przepływu w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="bb966-114">Specifies that the <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="bb966-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="bb966-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="bb966-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="bb966-116">Value</span></span>|<span data-ttu-id="bb966-117">Opis</span><span class="sxs-lookup"><span data-stu-id="bb966-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="bb966-118"><xref:System.Security.Principal.WindowsIdentity>przepływy w punktach asynchronicznych w <xref:System.Threading.ExecutionContext> zależności od ustawień przepływu dla bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="bb966-118"><xref:System.Security.Principal.WindowsIdentity> flows across asynchronous points depending upon the <xref:System.Threading.ExecutionContext> flow settings for the current thread.</span></span> <span data-ttu-id="bb966-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="bb966-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="bb966-120"><xref:System.Security.Principal.WindowsIdentity>nie przepływa między punktami asynchronicznymi, niezależnie od <xref:System.Threading.ExecutionContext> ustawień przepływu w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="bb966-120"><xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bb966-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="bb966-121">Child Elements</span></span>  
 <span data-ttu-id="bb966-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="bb966-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bb966-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bb966-123">Parent Elements</span></span>  
  
|<span data-ttu-id="bb966-124">Element</span><span class="sxs-lookup"><span data-stu-id="bb966-124">Element</span></span>|<span data-ttu-id="bb966-125">Opis</span><span class="sxs-lookup"><span data-stu-id="bb966-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="bb966-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bb966-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="bb966-127">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="bb966-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb966-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bb966-128">Remarks</span></span>  
 <span data-ttu-id="bb966-129">W .NET Framework wersje 1,0 i 1,1 <xref:System.Security.Principal.WindowsIdentity> nie przepływa między wszystkimi punktami asynchronicznymi zdefiniowanymi przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bb966-129">In the .NET Framework versions 1.0 and 1.1, the <xref:System.Security.Principal.WindowsIdentity> does not flow across any user-defined asynchronous points.</span></span> <span data-ttu-id="bb966-130">Począwszy od .NET Framework w wersji 2,0, istnieje <xref:System.Threading.ExecutionContext> obiekt, który zawiera informacje o aktualnie wykonywanym wątku i przepływie między punktami asynchronicznymi w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bb966-130">Starting with the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and it flows across asynchronous points within an application domain.</span></span> <span data-ttu-id="bb966-131"><xref:System.Security.Principal.WindowsIdentity> Jest uwzględniony w tym kontekście wykonywania i w związku z tym również przepływów między punktami asynchronicznymi, co oznacza, że jeśli istnieje kontekst personifikacji, będzie również przepływać.</span><span class="sxs-lookup"><span data-stu-id="bb966-131">The <xref:System.Security.Principal.WindowsIdentity> is included in this execution context and therefore also flows across the asynchronous points, which means that if an impersonation context exists, it will flow as well.</span></span>  
  
 <span data-ttu-id="bb966-132">Począwszy od .NET Framework 2,0, można użyć `<legacyImpersonationPolicy>` elementu, aby określić, że <xref:System.Security.Principal.WindowsIdentity> nie przepływa w punktach asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="bb966-132">Starting with the .NET Framework 2.0, you can use the `<legacyImpersonationPolicy>` element to specify that  <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bb966-133">Środowisko uruchomieniowe języka wspólnego (CLR) ma świadomość operacji personifikacji wykonywanych przy użyciu tylko kodu zarządzanego, a nie personifikacji wykonanej poza kodem zarządzanym, na przykład za pośrednictwem wywołania platformy do kodu niezarządzanego lub bezpośrednie wywołania do funkcji Win32.</span><span class="sxs-lookup"><span data-stu-id="bb966-133">The common language runtime (CLR) is aware of impersonation operations performed using only managed code, not of impersonation performed outside of managed code, such as through platform invoke to unmanaged code or through direct calls to Win32 functions.</span></span> <span data-ttu-id="bb966-134">Tylko obiekty <xref:System.Security.Principal.WindowsIdentity> zarządzane mogą przepływać przez punkty asynchroniczne, `alwaysFlowImpersonationPolicy` chyba że element został ustawiony na wartość true`<alwaysFlowImpersonationPolicy enabled="true"/>`().</span><span class="sxs-lookup"><span data-stu-id="bb966-134">Only managed <xref:System.Security.Principal.WindowsIdentity> objects can flow across asynchronous points, unless the `alwaysFlowImpersonationPolicy` element has been set to true (`<alwaysFlowImpersonationPolicy enabled="true"/>`).</span></span> <span data-ttu-id="bb966-135">`alwaysFlowImpersonationPolicy` Ustawienie elementu na wartość true określa, że tożsamość systemu Windows jest zawsze przepływana w punktach asynchronicznych, niezależnie od tego, jak personifikacja została wykonana.</span><span class="sxs-lookup"><span data-stu-id="bb966-135">Setting the `alwaysFlowImpersonationPolicy` element to true specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span> <span data-ttu-id="bb966-136">Aby uzyskać więcej informacji na temat przepływu niezarządzanej personifikacji w punktach asynchronicznych, zobacz [ \<alwaysFlowImpersonationPolicy > elementu](alwaysflowimpersonationpolicy-element.md).</span><span class="sxs-lookup"><span data-stu-id="bb966-136">For more information on flowing unmanaged impersonation across asynchronous points, see [\<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).</span></span>  
  
 <span data-ttu-id="bb966-137">To zachowanie domyślne można zmienić na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="bb966-137">You can alter this default behavior in two other ways:</span></span>  
  
1. <span data-ttu-id="bb966-138">W kodzie zarządzanym dla poszczególnych wątków.</span><span class="sxs-lookup"><span data-stu-id="bb966-138">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="bb966-139">Przepływ można pominąć dla każdego wątku, <xref:System.Threading.ExecutionContext> modyfikując <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> ustawienia i <xref:System.Security.SecurityContext> za pomocą <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>metody lub <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="bb966-139">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="bb966-140">W wywołaniu interfejsu hostingu niezarządzanego w celu załadowania środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="bb966-140">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="bb966-141">Jeśli do załadowania środowiska CLR jest używany niezarządzany interfejs hostingu (zamiast prostego zarządzanego pliku wykonywalnego), można określić specjalną flagę w wywołaniu funkcji [funkcji CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) .</span><span class="sxs-lookup"><span data-stu-id="bb966-141">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="bb966-142">Aby włączyć tryb zgodności dla całego procesu, należy ustawić `flags` parametr dla [funkcji CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) na STARTUP_LEGACY_IMPERSONATION.</span><span class="sxs-lookup"><span data-stu-id="bb966-142">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) to STARTUP_LEGACY_IMPERSONATION.</span></span>  
  
 <span data-ttu-id="bb966-143">Aby uzyskać więcej informacji, zobacz [ \<alwaysFlowImpersonationPolicy > elementu](alwaysflowimpersonationpolicy-element.md).</span><span class="sxs-lookup"><span data-stu-id="bb966-143">For more information, see the [\<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="bb966-144">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="bb966-144">Configuration File</span></span>  
 <span data-ttu-id="bb966-145">W aplikacji .NET Framework ten element może być używany tylko w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bb966-145">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="bb966-146">W przypadku aplikacji ASP.NET przepływ personifikacji można skonfigurować w pliku aspnet. config znajdującym się w \<folderze systemu Windows > katalogu \Microsoft.NET\Framework\vx.x.xxxx.</span><span class="sxs-lookup"><span data-stu-id="bb966-146">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="bb966-147">Domyślnie ASP.NET powoduje wyłączenie przepływu personifikacji w pliku aspnet. config przy użyciu następujących ustawień konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="bb966-147">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
``` xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="bb966-148">W ASP.NET, jeśli chcesz zezwolić na przepływ personifikacji, musisz jawnie użyć następujących ustawień konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="bb966-148">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="bb966-149">Przykład</span><span class="sxs-lookup"><span data-stu-id="bb966-149">Example</span></span>  
 <span data-ttu-id="bb966-150">Poniższy przykład pokazuje, jak określić starsze zachowanie, które nie przepływa tożsamości systemu Windows w punktach asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="bb966-150">The following example shows how to specify the legacy behavior that does not flow the Windows identity across asynchronous points.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bb966-151">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bb966-151">See also</span></span>

- [<span data-ttu-id="bb966-152">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="bb966-152">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="bb966-153">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="bb966-153">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="bb966-154">\<alwaysFlowImpersonationPolicy> Element</span><span class="sxs-lookup"><span data-stu-id="bb966-154">\<alwaysFlowImpersonationPolicy> Element</span></span>](alwaysflowimpersonationpolicy-element.md)
