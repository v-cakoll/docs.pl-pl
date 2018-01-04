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
# <a name="ltalwaysflowimpersonationpolicygt-element"></a><span data-ttu-id="ca4ed-102">&lt;alwaysflowimpersonationpolicy —&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="ca4ed-102">&lt;alwaysFlowImpersonationPolicy&gt; Element</span></span>
<span data-ttu-id="ca4ed-103">Określa, czy tożsamość systemu Windows zawsze przepływa między punktami asynchroniczne, niezależnie od tego, jak została wykonana personifikacji.</span><span class="sxs-lookup"><span data-stu-id="ca4ed-103">Specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>  
  
 <span data-ttu-id="ca4ed-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="ca4ed-104">\<configuration></span></span>  
<span data-ttu-id="ca4ed-105">\<Runtime ></span><span class="sxs-lookup"><span data-stu-id="ca4ed-105">\<runtime></span></span>  
<span data-ttu-id="ca4ed-106">\<alwaysflowimpersonationpolicy — ></span><span class="sxs-lookup"><span data-stu-id="ca4ed-106">\<alwaysFlowImpersonationPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca4ed-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="ca4ed-107">Syntax</span></span>  
  
```xml  
<alwaysFlowImpersonationPolicy    
  enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ca4ed-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ca4ed-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ca4ed-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ca4ed-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ca4ed-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ca4ed-110">Attributes</span></span>  
  
|<span data-ttu-id="ca4ed-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ca4ed-111">Attribute</span></span>|<span data-ttu-id="ca4ed-112">Opis</span><span class="sxs-lookup"><span data-stu-id="ca4ed-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="ca4ed-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="ca4ed-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="ca4ed-114">Wskazuje, czy tożsamość systemu Windows przepływa między punktami asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="ca4ed-114">Indicates whether the Windows identity flows across asynchronous points.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="ca4ed-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="ca4ed-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="ca4ed-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="ca4ed-116">Value</span></span>|<span data-ttu-id="ca4ed-117">Opis</span><span class="sxs-lookup"><span data-stu-id="ca4ed-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="ca4ed-118">Takie jak zarządzane tożsamości nie przepływ między punktami asynchroniczne, chyba że personifikacja odbywa się za pośrednictwem systemu Windows metody <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>.</span><span class="sxs-lookup"><span data-stu-id="ca4ed-118">The Windows identity does not flow across asynchronous points, unless the impersonation is performed through managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>.</span></span> <span data-ttu-id="ca4ed-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="ca4ed-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="ca4ed-120">Tożsamość systemu Windows zawsze przepływa między punktami asynchroniczne, niezależnie od tego, jak została wykonana personifikacji.</span><span class="sxs-lookup"><span data-stu-id="ca4ed-120">The Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ca4ed-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ca4ed-121">Child Elements</span></span>  
 <span data-ttu-id="ca4ed-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="ca4ed-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ca4ed-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ca4ed-123">Parent Elements</span></span>  
  
|<span data-ttu-id="ca4ed-124">Element</span><span class="sxs-lookup"><span data-stu-id="ca4ed-124">Element</span></span>|<span data-ttu-id="ca4ed-125">Opis</span><span class="sxs-lookup"><span data-stu-id="ca4ed-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ca4ed-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ca4ed-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ca4ed-127">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="ca4ed-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca4ed-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ca4ed-128">Remarks</span></span>  
 <span data-ttu-id="ca4ed-129">W wersji systemu .NET Framework 1.0 i 1.1 tożsamość systemu Windows nie przepływ między punktami asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="ca4ed-129">In the .NET Framework versions 1.0 and 1.1, the Windows identity does not flow across asynchronous points.</span></span> <span data-ttu-id="ca4ed-130">W programie .NET Framework w wersji 2.0, Brak <xref:System.Threading.ExecutionContext> obiekt, który zawiera informacje o obecnie wykonywanym wątku i go przepływa między punktami asynchronicznych w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ca4ed-130">In the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and flows it across asynchronous points within an application domain.</span></span> <span data-ttu-id="ca4ed-131"><xref:System.Security.Principal.WindowsIdentity> Także przepływów jako część informacji przepływającego między punktami asynchroniczne, pod warunkiem personifikację został osiągnięty przy użyciu zarządzane metody takie jak <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> , a nie za pomocą innych środków, takich jak platforma wywołania do metody natywnej.</span><span class="sxs-lookup"><span data-stu-id="ca4ed-131">The <xref:System.Security.Principal.WindowsIdentity> also flows as part of the information that flows across the asynchronous points, provided the impersonation was achieved using managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> and not through other means such as platform invoke to native methods.</span></span> <span data-ttu-id="ca4ed-132">Ten element jest używany do określenia, czy między punktami asynchroniczne, niezależnie od tego, jak została osiągnięta personifikację przepływu tożsamości systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ca4ed-132">This element is used to specify that the Windows identity does flow across asynchronous points, regardless of how the impersonation was achieved.</span></span>  
  
 <span data-ttu-id="ca4ed-133">Można zmienić to zachowanie domyślne są dwa inne sposoby:</span><span class="sxs-lookup"><span data-stu-id="ca4ed-133">You can alter this default behavior in two other ways:</span></span>  
  
1.  <span data-ttu-id="ca4ed-134">W kodzie zarządzanym na podstawie dla każdego wątku.</span><span class="sxs-lookup"><span data-stu-id="ca4ed-134">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="ca4ed-135">Można pominąć przepływem na podstawie dla każdego wątku, modyfikując <xref:System.Threading.ExecutionContext> i <xref:System.Security.SecurityContext> ustawienia za pomocą <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>, lub <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="ca4ed-135">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>, or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2.  <span data-ttu-id="ca4ed-136">W wywołaniu niezarządzane interfejsu hostingu załadować środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="ca4ed-136">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="ca4ed-137">Jeśli interfejs hostingu niezarządzane (zamiast prostego pliku wykonywalnego zarządzane) służy do ładowania środowiska CLR, można określić Flaga specjalna w wywołaniu [CorBindToRuntimeEx — funkcja](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="ca4ed-137">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="ca4ed-138">Aby włączyć tryb zgodności dla całego procesu, ustaw `flags` parametr [CorBindToRuntimeEx — funkcja](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) do `STARTUP_ALWAYSFLOW_IMPERSONATION`.</span><span class="sxs-lookup"><span data-stu-id="ca4ed-138">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) to `STARTUP_ALWAYSFLOW_IMPERSONATION`.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="ca4ed-139">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ca4ed-139">Configuration File</span></span>  
 <span data-ttu-id="ca4ed-140">W aplikacji .NET Framework ten element może być użyty tylko w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ca4ed-140">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="ca4ed-141">Dla aplikacji ASP.NET można skonfigurować przepływ personifikacji w znaleziono w pliku konfigurację aspnet.config \<Windows Folder > \Microsoft.NET\Framework\vx.x.xxxx katalogu.</span><span class="sxs-lookup"><span data-stu-id="ca4ed-141">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="ca4ed-142">ASP.NET domyślnie wyłącza przepływu personifikacji w pliku konfigurację aspnet.config przy użyciu następujących ustawień konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="ca4ed-142">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
```  
configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="ca4ed-143">W programie ASP.NET Jeśli chcesz umożliwić przepływ personifikacji zamiast tego należy jawnie użyć następujących ustawień konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="ca4ed-143">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="ca4ed-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="ca4ed-144">Example</span></span>  
 <span data-ttu-id="ca4ed-145">Poniższy przykład przedstawia sposób określania, czy tożsamość systemu Windows przepływa między punktami asynchroniczne, nawet wtedy, gdy personifikacja odbywa się za pośrednictwem oznacza innych niż zarządzane metody.</span><span class="sxs-lookup"><span data-stu-id="ca4ed-145">The following example shows how to specify that the Windows identity flows across asynchronous points, even when the impersonation is achieved through means other than managed methods.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ca4ed-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ca4ed-146">See Also</span></span>  
 [<span data-ttu-id="ca4ed-147">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="ca4ed-147">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="ca4ed-148">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ca4ed-148">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="ca4ed-149">\<legacyimpersonationpolicy — > — Element</span><span class="sxs-lookup"><span data-stu-id="ca4ed-149">\<legacyImpersonationPolicy> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)
