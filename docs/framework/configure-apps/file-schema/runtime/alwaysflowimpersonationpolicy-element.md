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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b42c141362d99090db922d3a6b429f05592130cd
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659014"
---
# <a name="alwaysflowimpersonationpolicy-element"></a><span data-ttu-id="a747c-102">\<alwaysFlowImpersonationPolicy> Element</span><span class="sxs-lookup"><span data-stu-id="a747c-102">\<alwaysFlowImpersonationPolicy> Element</span></span>
<span data-ttu-id="a747c-103">Określa, że tożsamość systemu Windows jest zawsze przepływów między punktami asynchronicznymi, niezależnie od tego, jak personifikacja została wykonana.</span><span class="sxs-lookup"><span data-stu-id="a747c-103">Specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>  
  
 <span data-ttu-id="a747c-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a747c-104">\<configuration></span></span>  
<span data-ttu-id="a747c-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="a747c-105">\<runtime></span></span>  
<span data-ttu-id="a747c-106">\<alwaysFlowImpersonationPolicy></span><span class="sxs-lookup"><span data-stu-id="a747c-106">\<alwaysFlowImpersonationPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a747c-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="a747c-107">Syntax</span></span>  
  
```xml  
<alwaysFlowImpersonationPolicy    
  enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a747c-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a747c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a747c-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a747c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a747c-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a747c-110">Attributes</span></span>  
  
|<span data-ttu-id="a747c-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a747c-111">Attribute</span></span>|<span data-ttu-id="a747c-112">Opis</span><span class="sxs-lookup"><span data-stu-id="a747c-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="a747c-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="a747c-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="a747c-114">Wskazuje, czy tożsamość systemu Windows jest przesyłana między punkty asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="a747c-114">Indicates whether the Windows identity flows across asynchronous points.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="a747c-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="a747c-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="a747c-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="a747c-116">Value</span></span>|<span data-ttu-id="a747c-117">Opis</span><span class="sxs-lookup"><span data-stu-id="a747c-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="a747c-118">Tożsamość systemu Windows nie jest przepływa między punktami asynchronicznymi, chyba że personifikacja jest wykonywana za <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>pomocą metod zarządzanych, takich jak.</span><span class="sxs-lookup"><span data-stu-id="a747c-118">The Windows identity does not flow across asynchronous points, unless the impersonation is performed through managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>.</span></span> <span data-ttu-id="a747c-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="a747c-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="a747c-120">Tożsamość systemu Windows jest zawsze przepływów między punktami asynchronicznymi, niezależnie od tego, jak personifikacja została wykonana.</span><span class="sxs-lookup"><span data-stu-id="a747c-120">The Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a747c-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a747c-121">Child Elements</span></span>  
 <span data-ttu-id="a747c-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="a747c-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a747c-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a747c-123">Parent Elements</span></span>  
  
|<span data-ttu-id="a747c-124">Element</span><span class="sxs-lookup"><span data-stu-id="a747c-124">Element</span></span>|<span data-ttu-id="a747c-125">Opis</span><span class="sxs-lookup"><span data-stu-id="a747c-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a747c-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a747c-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="a747c-127">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="a747c-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a747c-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a747c-128">Remarks</span></span>  
 <span data-ttu-id="a747c-129">W .NET Framework wersje 1,0 i 1,1 tożsamość systemu Windows nie jest przesyłana między punktami asynchronicznymi.</span><span class="sxs-lookup"><span data-stu-id="a747c-129">In the .NET Framework versions 1.0 and 1.1, the Windows identity does not flow across asynchronous points.</span></span> <span data-ttu-id="a747c-130">W .NET Framework w wersji 2,0 istnieje <xref:System.Threading.ExecutionContext> obiekt, który zawiera informacje o aktualnie wykonywanym wątku i przepływa przez punkty asynchroniczne w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a747c-130">In the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and flows it across asynchronous points within an application domain.</span></span> <span data-ttu-id="a747c-131">Również przepływy jako część informacji przesyłanych przez punkty asynchroniczne, pod warunkiem, że personifikacja została osiągnięta przy użyciu metod <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> zarządzanych, takich jak, a nie za pośrednictwem innych, takich jak wywołanie platformy do metod natywnych. <xref:System.Security.Principal.WindowsIdentity></span><span class="sxs-lookup"><span data-stu-id="a747c-131">The <xref:System.Security.Principal.WindowsIdentity> also flows as part of the information that flows across the asynchronous points, provided the impersonation was achieved using managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> and not through other means such as platform invoke to native methods.</span></span> <span data-ttu-id="a747c-132">Ten element służy do określenia, że tożsamość systemu Windows jest przesyłana w punktach asynchronicznych, niezależnie od sposobu uzyskania personifikacji.</span><span class="sxs-lookup"><span data-stu-id="a747c-132">This element is used to specify that the Windows identity does flow across asynchronous points, regardless of how the impersonation was achieved.</span></span>  
  
 <span data-ttu-id="a747c-133">To zachowanie domyślne można zmienić na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="a747c-133">You can alter this default behavior in two other ways:</span></span>  
  
1. <span data-ttu-id="a747c-134">W kodzie zarządzanym dla poszczególnych wątków.</span><span class="sxs-lookup"><span data-stu-id="a747c-134">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="a747c-135">Przepływ można pominąć dla <xref:System.Threading.ExecutionContext> każdego wątku, modyfikując ustawienia i <xref:System.Security.SecurityContext> przy użyciu <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>metody, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>, lub <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="a747c-135">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>, or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="a747c-136">W wywołaniu interfejsu hostingu niezarządzanego w celu załadowania środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="a747c-136">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="a747c-137">Jeśli do załadowania środowiska CLR jest używany niezarządzany interfejs hostingu (zamiast prostego zarządzanego pliku wykonywalnego), można określić specjalną flagę w wywołaniu funkcji [funkcji CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) .</span><span class="sxs-lookup"><span data-stu-id="a747c-137">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="a747c-138">Aby włączyć tryb zgodności dla całego procesu, należy ustawić `flags` parametr dla [funkcji CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) na. `STARTUP_ALWAYSFLOW_IMPERSONATION`</span><span class="sxs-lookup"><span data-stu-id="a747c-138">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) to `STARTUP_ALWAYSFLOW_IMPERSONATION`.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="a747c-139">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a747c-139">Configuration File</span></span>  
 <span data-ttu-id="a747c-140">W aplikacji .NET Framework ten element może być używany tylko w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a747c-140">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="a747c-141">W przypadku aplikacji ASP.NET przepływ personifikacji można skonfigurować w pliku aspnet. config znajdującym się w \<folderze systemu Windows > katalogu \Microsoft.NET\Framework\vx.x.xxxx.</span><span class="sxs-lookup"><span data-stu-id="a747c-141">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="a747c-142">Domyślnie ASP.NET powoduje wyłączenie przepływu personifikacji w pliku aspnet. config przy użyciu następujących ustawień konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="a747c-142">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
```xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="a747c-143">W ASP.NET, jeśli chcesz zezwolić na przepływ personifikacji, musisz jawnie użyć następujących ustawień konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="a747c-143">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="a747c-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="a747c-144">Example</span></span>  
 <span data-ttu-id="a747c-145">Poniższy przykład pokazuje, jak określić, że tożsamość systemu Windows jest realizowana w punktach asynchronicznych, nawet jeśli Personifikacja jest realizowana za pośrednictwem środków innych niż metody zarządzane.</span><span class="sxs-lookup"><span data-stu-id="a747c-145">The following example shows how to specify that the Windows identity flows across asynchronous points, even when the impersonation is achieved through means other than managed methods.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a747c-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a747c-146">See also</span></span>

- [<span data-ttu-id="a747c-147">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="a747c-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a747c-148">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a747c-148">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="a747c-149">\<legacyImpersonationPolicy, element ></span><span class="sxs-lookup"><span data-stu-id="a747c-149">\<legacyImpersonationPolicy> Element</span></span>](legacyimpersonationpolicy-element.md)
