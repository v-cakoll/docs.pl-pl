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
---
# <a name="ltlegacyimpersonationpolicygt-element"></a><span data-ttu-id="4d099-102">&lt;legacyimpersonationpolicy —&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="4d099-102">&lt;legacyImpersonationPolicy&gt; Element</span></span>
<span data-ttu-id="4d099-103">Określa, że tożsamość systemu Windows nie przepływ między punktami asynchroniczne, niezależnie od ustawień przepływu kontekstu wykonywania w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="4d099-103">Specifies that the Windows identity does not flow across asynchronous points, regardless of the flow settings for the execution context on the current thread.</span></span>  
  
 <span data-ttu-id="4d099-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="4d099-104">\<configuration></span></span>  
<span data-ttu-id="4d099-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="4d099-105">\<runtime></span></span>  
<span data-ttu-id="4d099-106">\<legacyImpersonationPolicy></span><span class="sxs-lookup"><span data-stu-id="4d099-106">\<legacyImpersonationPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d099-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="4d099-107">Syntax</span></span>  
  
```xml  
<legacyImpersonationPolicy    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4d099-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4d099-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4d099-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4d099-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4d099-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4d099-110">Attributes</span></span>  
  
|<span data-ttu-id="4d099-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4d099-111">Attribute</span></span>|<span data-ttu-id="4d099-112">Opis</span><span class="sxs-lookup"><span data-stu-id="4d099-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="4d099-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="4d099-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="4d099-114">Określa, że <xref:System.Security.Principal.WindowsIdentity> nie przepływ między punktami asynchroniczne, niezależnie od tego <xref:System.Threading.ExecutionContext> przepływu ustawień w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="4d099-114">Specifies that the <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="4d099-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="4d099-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="4d099-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="4d099-116">Value</span></span>|<span data-ttu-id="4d099-117">Opis</span><span class="sxs-lookup"><span data-stu-id="4d099-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="4d099-118"><xref:System.Security.Principal.WindowsIdentity> przepływy między punktami asynchronicznych w zależności od <xref:System.Threading.ExecutionContext> przepływu ustawienia bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="4d099-118"><xref:System.Security.Principal.WindowsIdentity> flows across asynchronous points depending upon the <xref:System.Threading.ExecutionContext> flow settings for the current thread.</span></span> <span data-ttu-id="4d099-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="4d099-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="4d099-120"><xref:System.Security.Principal.WindowsIdentity> nie przepływ między punktami asynchroniczne, niezależnie od tego <xref:System.Threading.ExecutionContext> przepływu ustawień w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="4d099-120"><xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4d099-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4d099-121">Child Elements</span></span>  
 <span data-ttu-id="4d099-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="4d099-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4d099-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4d099-123">Parent Elements</span></span>  
  
|<span data-ttu-id="4d099-124">Element</span><span class="sxs-lookup"><span data-stu-id="4d099-124">Element</span></span>|<span data-ttu-id="4d099-125">Opis</span><span class="sxs-lookup"><span data-stu-id="4d099-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4d099-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4d099-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="4d099-127">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="4d099-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4d099-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4d099-128">Remarks</span></span>  
 <span data-ttu-id="4d099-129">W wersji systemu .NET Framework 1.0 i 1.1 <xref:System.Security.Principal.WindowsIdentity> nie przepływ między punktami asynchroniczne wszelkie zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4d099-129">In the .NET Framework versions 1.0 and 1.1, the <xref:System.Security.Principal.WindowsIdentity> does not flow across any user-defined asynchronous points.</span></span> <span data-ttu-id="4d099-130">W programie .NET Framework w wersji 2.0, Brak <xref:System.Threading.ExecutionContext> obiektu, który zawiera informacje o obecnie wykonywanym wątku który przepływa między punktami asynchronicznych w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4d099-130">Starting with the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and it flows across asynchronous points within an application domain.</span></span> <span data-ttu-id="4d099-131"><xref:System.Security.Principal.WindowsIdentity> Znajduje się w tym kontekście wykonania i w związku z tym przepływa również między punktami asynchroniczne, co oznacza, że jeśli kontekst personifikacji istnieje, jej będą przepływać również.</span><span class="sxs-lookup"><span data-stu-id="4d099-131">The <xref:System.Security.Principal.WindowsIdentity> is included in this execution context and therefore also flows across the asynchronous points, which means that if an impersonation context exists, it will flow as well.</span></span>  
  
 <span data-ttu-id="4d099-132">Począwszy od programu .NET Framework 2.0, można użyć `<legacyImpersonationPolicy>` elementu, aby określić, że <xref:System.Security.Principal.WindowsIdentity> nie przepływ między punktami asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="4d099-132">Starting with the .NET Framework 2.0, you can use the `<legacyImpersonationPolicy>` element to specify that  <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4d099-133">Środowisko uruchomieniowe języka wspólnego (CLR) jest świadome personifikacji operacje wykonywane przy użyciu tylko kodu zarządzanego nie pochodzi z personifikacji realizuje poza kodu zarządzanego, takich jak platforma wywołania do kodu niezarządzanego lub poprzez bezpośrednie wywołania funkcji Win32.</span><span class="sxs-lookup"><span data-stu-id="4d099-133">The common language runtime (CLR) is aware of impersonation operations performed using only managed code, not of impersonation performed outside of managed code, such as through platform invoke to unmanaged code or through direct calls to Win32 functions.</span></span> <span data-ttu-id="4d099-134">Tylko zarządzanego <xref:System.Security.Principal.WindowsIdentity> obiektów może przechodzić między punktami asynchroniczne, chyba że `alwaysFlowImpersonationPolicy` element została ustawiona na true (`<alwaysFlowImpersonationPolicy enabled="true"/>`).</span><span class="sxs-lookup"><span data-stu-id="4d099-134">Only managed <xref:System.Security.Principal.WindowsIdentity> objects can flow across asynchronous points, unless the `alwaysFlowImpersonationPolicy` element has been set to true (`<alwaysFlowImpersonationPolicy enabled="true"/>`).</span></span> <span data-ttu-id="4d099-135">Ustawienie `alwaysFlowImpersonationPolicy` elementu na wartość true, określa, czy tożsamości systemu Windows zawsze przepływa między punktami asynchroniczne, niezależnie od tego, jak została wykonana personifikacji.</span><span class="sxs-lookup"><span data-stu-id="4d099-135">Setting the `alwaysFlowImpersonationPolicy` element to true specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span> <span data-ttu-id="4d099-136">Aby uzyskać więcej informacji na temat przechodzenia przez punkty asynchroniczne niezarządzany personifikacji, zobacz [ \<alwaysflowimpersonationpolicy — > elementu](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md).</span><span class="sxs-lookup"><span data-stu-id="4d099-136">For more information on flowing unmanaged impersonation across asynchronous points, see [\<alwaysFlowImpersonationPolicy> Element](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md).</span></span>  
  
 <span data-ttu-id="4d099-137">Można zmienić to zachowanie domyślne są dwa inne sposoby:</span><span class="sxs-lookup"><span data-stu-id="4d099-137">You can alter this default behavior in two other ways:</span></span>  
  
1.  <span data-ttu-id="4d099-138">W kodzie zarządzanym na podstawie dla każdego wątku.</span><span class="sxs-lookup"><span data-stu-id="4d099-138">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="4d099-139">Można pominąć przepływem na podstawie dla każdego wątku, modyfikując <xref:System.Threading.ExecutionContext> i <xref:System.Security.SecurityContext> ustawienia za pomocą <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> lub <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="4d099-139">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2.  <span data-ttu-id="4d099-140">W wywołaniu niezarządzane interfejsu hostingu załadować środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="4d099-140">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="4d099-141">Jeśli interfejs hostingu niezarządzane (zamiast prostego pliku wykonywalnego zarządzane) służy do ładowania środowiska CLR, można określić Flaga specjalna w wywołaniu [CorBindToRuntimeEx — funkcja](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="4d099-141">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="4d099-142">Aby włączyć tryb zgodności dla całego procesu, ustaw `flags` parametr [CorBindToRuntimeEx — funkcja](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) do STARTUP_LEGACY_IMPERSONATION.</span><span class="sxs-lookup"><span data-stu-id="4d099-142">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) to STARTUP_LEGACY_IMPERSONATION.</span></span>  
  
 <span data-ttu-id="4d099-143">Aby uzyskać więcej informacji, zobacz [ \<alwaysflowimpersonationpolicy — > elementu](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md).</span><span class="sxs-lookup"><span data-stu-id="4d099-143">For more information, see the [\<alwaysFlowImpersonationPolicy> Element](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md).</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="4d099-144">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="4d099-144">Configuration File</span></span>  
 <span data-ttu-id="4d099-145">W aplikacji .NET Framework ten element może być użyty tylko w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4d099-145">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="4d099-146">Dla aplikacji ASP.NET można skonfigurować przepływ personifikacji w znaleziono w pliku konfigurację aspnet.config \<Windows Folder > \Microsoft.NET\Framework\vx.x.xxxx katalogu.</span><span class="sxs-lookup"><span data-stu-id="4d099-146">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="4d099-147">ASP.NET domyślnie wyłącza przepływu personifikacji w pliku konfigurację aspnet.config przy użyciu następujących ustawień konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="4d099-147">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
``` xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="4d099-148">W programie ASP.NET Jeśli chcesz umożliwić przepływ personifikacji zamiast tego należy jawnie użyć następujących ustawień konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="4d099-148">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="4d099-149">Przykład</span><span class="sxs-lookup"><span data-stu-id="4d099-149">Example</span></span>  
 <span data-ttu-id="4d099-150">Poniższy przykład pokazuje, jak określić zachowanie starszych tożsamości systemu Windows nie przepływ między punktami asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="4d099-150">The following example shows how to specify the legacy behavior that does not flow the Windows identity across asynchronous points.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4d099-151">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4d099-151">See Also</span></span>  
 [<span data-ttu-id="4d099-152">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="4d099-152">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="4d099-153">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="4d099-153">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="4d099-154">\<alwaysflowimpersonationpolicy — > — Element</span><span class="sxs-lookup"><span data-stu-id="4d099-154">\<alwaysFlowImpersonationPolicy> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)
