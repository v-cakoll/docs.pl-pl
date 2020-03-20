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
# <a name="legacyimpersonationpolicy-element"></a><span data-ttu-id="94dab-102">\<legacyImpersonationPolicy> Element</span><span class="sxs-lookup"><span data-stu-id="94dab-102">\<legacyImpersonationPolicy> Element</span></span>
<span data-ttu-id="94dab-103">Określa, że tożsamość systemu Windows nie przepływa przez punkty asynchroniczne, niezależnie od ustawień przepływu dla kontekstu wykonywania w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="94dab-103">Specifies that the Windows identity does not flow across asynchronous points, regardless of the flow settings for the execution context on the current thread.</span></span>  
  
<span data-ttu-id="94dab-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="94dab-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="94dab-105">&nbsp;&nbsp;[**\<>czasu wykonywania**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="94dab-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="94dab-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<legacyImpersonationPolicy>**</span><span class="sxs-lookup"><span data-stu-id="94dab-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<legacyImpersonationPolicy>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94dab-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="94dab-107">Syntax</span></span>  
  
```xml  
<legacyImpersonationPolicy
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="94dab-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="94dab-108">Attributes and Elements</span></span>  
 <span data-ttu-id="94dab-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="94dab-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="94dab-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="94dab-110">Attributes</span></span>  
  
|<span data-ttu-id="94dab-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="94dab-111">Attribute</span></span>|<span data-ttu-id="94dab-112">Opis</span><span class="sxs-lookup"><span data-stu-id="94dab-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="94dab-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="94dab-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="94dab-114">Określa, że <xref:System.Security.Principal.WindowsIdentity> nie przepływa przez punkty asynchroniczne, niezależnie od ustawień <xref:System.Threading.ExecutionContext> przepływu w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="94dab-114">Specifies that the <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="94dab-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="94dab-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="94dab-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="94dab-116">Value</span></span>|<span data-ttu-id="94dab-117">Opis</span><span class="sxs-lookup"><span data-stu-id="94dab-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="94dab-118"><xref:System.Security.Principal.WindowsIdentity>przepływów przez punkty asynchroniczne w zależności od ustawień <xref:System.Threading.ExecutionContext> przepływu dla bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="94dab-118"><xref:System.Security.Principal.WindowsIdentity> flows across asynchronous points depending upon the <xref:System.Threading.ExecutionContext> flow settings for the current thread.</span></span> <span data-ttu-id="94dab-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="94dab-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="94dab-120"><xref:System.Security.Principal.WindowsIdentity>nie przepływa przez punkty asynchroniczne, <xref:System.Threading.ExecutionContext> niezależnie od ustawień przepływu w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="94dab-120"><xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="94dab-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="94dab-121">Child Elements</span></span>  
 <span data-ttu-id="94dab-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="94dab-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="94dab-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="94dab-123">Parent Elements</span></span>  
  
|<span data-ttu-id="94dab-124">Element</span><span class="sxs-lookup"><span data-stu-id="94dab-124">Element</span></span>|<span data-ttu-id="94dab-125">Opis</span><span class="sxs-lookup"><span data-stu-id="94dab-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="94dab-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="94dab-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="94dab-127">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="94dab-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94dab-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="94dab-128">Remarks</span></span>  
 <span data-ttu-id="94dab-129">W .NET Framework w wersjach 1.0 i <xref:System.Security.Principal.WindowsIdentity> 1.1 nie przepływa przez żadnych punktów asynchronicznych zdefiniowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="94dab-129">In the .NET Framework versions 1.0 and 1.1, the <xref:System.Security.Principal.WindowsIdentity> does not flow across any user-defined asynchronous points.</span></span> <span data-ttu-id="94dab-130">Począwszy od programu .NET Framework w wersji <xref:System.Threading.ExecutionContext> 2.0, istnieje obiekt, który zawiera informacje o aktualnie wykonywanym wątku i przepływa przez punkty asynchroniczne w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="94dab-130">Starting with the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and it flows across asynchronous points within an application domain.</span></span> <span data-ttu-id="94dab-131">Jest <xref:System.Security.Principal.WindowsIdentity> uwzględniony w tym kontekście wykonywania i w związku z tym również przepływa przez punkty asynchroniczne, co oznacza, że jeśli istnieje kontekst personifikacji, będzie również przepływać.</span><span class="sxs-lookup"><span data-stu-id="94dab-131">The <xref:System.Security.Principal.WindowsIdentity> is included in this execution context and therefore also flows across the asynchronous points, which means that if an impersonation context exists, it will flow as well.</span></span>  
  
 <span data-ttu-id="94dab-132">Począwszy od programu .NET Framework 2.0, można użyć `<legacyImpersonationPolicy>` elementu, aby określić, że <xref:System.Security.Principal.WindowsIdentity> nie przepływa przez punkty asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="94dab-132">Starting with the .NET Framework 2.0, you can use the `<legacyImpersonationPolicy>` element to specify that  <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="94dab-133">Środowisko wykonawcze języka wspólnego (CLR) jest świadomy operacji personifikacji wykonywanych przy użyciu tylko kodu zarządzanego, a nie personifikacji wykonywane poza kodem zarządzanym, takich jak za pośrednictwem platformy wywołać do kodu niezarządzanego lub za pośrednictwem bezpośrednich wywołań funkcji Win32.</span><span class="sxs-lookup"><span data-stu-id="94dab-133">The common language runtime (CLR) is aware of impersonation operations performed using only managed code, not of impersonation performed outside of managed code, such as through platform invoke to unmanaged code or through direct calls to Win32 functions.</span></span> <span data-ttu-id="94dab-134">Tylko <xref:System.Security.Principal.WindowsIdentity> obiekty zarządzane mogą przepływać przez punkty `alwaysFlowImpersonationPolicy` asynchroniczne,`<alwaysFlowImpersonationPolicy enabled="true"/>`chyba że element został ustawiony na true ( ).</span><span class="sxs-lookup"><span data-stu-id="94dab-134">Only managed <xref:System.Security.Principal.WindowsIdentity> objects can flow across asynchronous points, unless the `alwaysFlowImpersonationPolicy` element has been set to true (`<alwaysFlowImpersonationPolicy enabled="true"/>`).</span></span> <span data-ttu-id="94dab-135">Ustawienie `alwaysFlowImpersonationPolicy` elementu na true określa, że tożsamość systemu Windows zawsze przepływa przez punkty asynchroniczne, niezależnie od sposobu personifikacji została wykonana.</span><span class="sxs-lookup"><span data-stu-id="94dab-135">Setting the `alwaysFlowImpersonationPolicy` element to true specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span> <span data-ttu-id="94dab-136">Aby uzyskać więcej informacji na temat przepływu personifikacji niezarządzanej w punktach asynchronicznych, zobacz [ \<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).</span><span class="sxs-lookup"><span data-stu-id="94dab-136">For more information on flowing unmanaged impersonation across asynchronous points, see [\<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).</span></span>  
  
 <span data-ttu-id="94dab-137">To domyślne zachowanie można zmienić na dwa inne sposoby:</span><span class="sxs-lookup"><span data-stu-id="94dab-137">You can alter this default behavior in two other ways:</span></span>  
  
1. <span data-ttu-id="94dab-138">W kodzie zarządzanym na podstawie wątku.</span><span class="sxs-lookup"><span data-stu-id="94dab-138">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="94dab-139">Przepływ można pominąć na podstawie wątku, <xref:System.Threading.ExecutionContext> modyfikując ustawienia <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType> <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> i <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> <xref:System.Security.SecurityContext> ustawienia za pomocą metody , lub.</span><span class="sxs-lookup"><span data-stu-id="94dab-139">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="94dab-140">W wywołaniu interfejsu hostingu niezarządzanego, aby załadować środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="94dab-140">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="94dab-141">Jeśli do załadowania środowiska CLR używany jest niezarządzany interfejs hostingu (zamiast prostego zarządzanego pliku wykonywalnego), można określić specjalną flagę w wywołaniu funkcji [CorBindToRuntimeEx.](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)</span><span class="sxs-lookup"><span data-stu-id="94dab-141">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="94dab-142">Aby włączyć tryb zgodności dla całego procesu, `flags` ustaw parametr [funkcji CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) na STARTUP_LEGACY_IMPERSONATION.</span><span class="sxs-lookup"><span data-stu-id="94dab-142">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) to STARTUP_LEGACY_IMPERSONATION.</span></span>  
  
 <span data-ttu-id="94dab-143">Aby uzyskać więcej informacji, zobacz [ \<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).</span><span class="sxs-lookup"><span data-stu-id="94dab-143">For more information, see the [\<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="94dab-144">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="94dab-144">Configuration File</span></span>  
 <span data-ttu-id="94dab-145">W aplikacji .NET Framework ten element może być używany tylko w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="94dab-145">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="94dab-146">W przypadku aplikacji ASP.NET przepływ personifikacji można skonfigurować w pliku aspnet.config znajdującym \<się w katalogu Folder systemu Windows>\Microsoft.NET\Framework\vx.x.xxxx.</span><span class="sxs-lookup"><span data-stu-id="94dab-146">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="94dab-147">ASP.NET domyślnie wyłącza przepływ personifikacji w pliku aspnet.config przy użyciu następujących ustawień konfiguracyjnych:</span><span class="sxs-lookup"><span data-stu-id="94dab-147">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
``` xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="94dab-148">W ASP.NET, jeśli chcesz zezwolić na przepływ personifikacji zamiast tego, należy jawnie użyć następujących ustawień konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="94dab-148">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="94dab-149">Przykład</span><span class="sxs-lookup"><span data-stu-id="94dab-149">Example</span></span>  
 <span data-ttu-id="94dab-150">W poniższym przykładzie pokazano, jak określić starsze zachowanie, które nie przepływa tożsamości systemu Windows przez punkty asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="94dab-150">The following example shows how to specify the legacy behavior that does not flow the Windows identity across asynchronous points.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="94dab-151">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="94dab-151">See also</span></span>

- [<span data-ttu-id="94dab-152">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="94dab-152">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="94dab-153">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="94dab-153">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="94dab-154">\<zawsze Element> PolitykiFlowImpersonation</span><span class="sxs-lookup"><span data-stu-id="94dab-154">\<alwaysFlowImpersonationPolicy> Element</span></span>](alwaysflowimpersonationpolicy-element.md)
