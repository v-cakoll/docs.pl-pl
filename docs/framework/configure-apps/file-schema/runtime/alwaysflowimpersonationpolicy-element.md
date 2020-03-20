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
# <a name="alwaysflowimpersonationpolicy-element"></a><span data-ttu-id="1481b-102">\<zawsze Element> PolitykiFlowImpersonation</span><span class="sxs-lookup"><span data-stu-id="1481b-102">\<alwaysFlowImpersonationPolicy> Element</span></span>
<span data-ttu-id="1481b-103">Określa, że tożsamość systemu Windows zawsze przepływa przez punkty asynchroniczne, niezależnie od sposobu personifikacji została wykonana.</span><span class="sxs-lookup"><span data-stu-id="1481b-103">Specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>  
  
<span data-ttu-id="1481b-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1481b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1481b-105">&nbsp;&nbsp;[**\<>czasu wykonywania**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="1481b-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="1481b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<alwaysFlowImpersonationPolicy>**</span><span class="sxs-lookup"><span data-stu-id="1481b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<alwaysFlowImpersonationPolicy>**</span></span>\  
  
## <a name="syntax"></a><span data-ttu-id="1481b-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="1481b-107">Syntax</span></span>  
  
```xml  
<alwaysFlowImpersonationPolicy
  enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1481b-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1481b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1481b-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1481b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1481b-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1481b-110">Attributes</span></span>  
  
|<span data-ttu-id="1481b-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1481b-111">Attribute</span></span>|<span data-ttu-id="1481b-112">Opis</span><span class="sxs-lookup"><span data-stu-id="1481b-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="1481b-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="1481b-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="1481b-114">Wskazuje, czy tożsamość systemu Windows przepływa przez punkty asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="1481b-114">Indicates whether the Windows identity flows across asynchronous points.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="1481b-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="1481b-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="1481b-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="1481b-116">Value</span></span>|<span data-ttu-id="1481b-117">Opis</span><span class="sxs-lookup"><span data-stu-id="1481b-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="1481b-118">Tożsamość systemu Windows nie przepływa przez punkty asynchroniczne, chyba <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>że personifikacja jest wykonywana za pomocą metod zarządzanych, takich jak .</span><span class="sxs-lookup"><span data-stu-id="1481b-118">The Windows identity does not flow across asynchronous points, unless the impersonation is performed through managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>.</span></span> <span data-ttu-id="1481b-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="1481b-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="1481b-120">Tożsamość systemu Windows zawsze przepływa przez punkty asynchroniczne, niezależnie od sposobu personifikacji została wykonana.</span><span class="sxs-lookup"><span data-stu-id="1481b-120">The Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1481b-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1481b-121">Child Elements</span></span>  
 <span data-ttu-id="1481b-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="1481b-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1481b-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1481b-123">Parent Elements</span></span>  
  
|<span data-ttu-id="1481b-124">Element</span><span class="sxs-lookup"><span data-stu-id="1481b-124">Element</span></span>|<span data-ttu-id="1481b-125">Opis</span><span class="sxs-lookup"><span data-stu-id="1481b-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1481b-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1481b-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="1481b-127">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="1481b-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1481b-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1481b-128">Remarks</span></span>  
 <span data-ttu-id="1481b-129">W programie .NET Framework w wersjach 1.0 i 1.1 tożsamość systemu Windows nie przepływa przez punkty asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="1481b-129">In the .NET Framework versions 1.0 and 1.1, the Windows identity does not flow across asynchronous points.</span></span> <span data-ttu-id="1481b-130">W programie .NET Framework w wersji 2.0 znajduje się obiekt zawierający <xref:System.Threading.ExecutionContext> informacje o aktualnie wykonywanym wątku i przepływający przez punkty asynchroniczne w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1481b-130">In the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and flows it across asynchronous points within an application domain.</span></span> <span data-ttu-id="1481b-131">Przepływy <xref:System.Security.Principal.WindowsIdentity> również jako część informacji, które przepływa przez punkty asynchroniczne, pod warunkiem, że personifikacji został osiągnięty przy użyciu metod zarządzanych, takich jak <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> i nie za pomocą innych środków, takich jak platforma wywołać do metod natywnych.</span><span class="sxs-lookup"><span data-stu-id="1481b-131">The <xref:System.Security.Principal.WindowsIdentity> also flows as part of the information that flows across the asynchronous points, provided the impersonation was achieved using managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> and not through other means such as platform invoke to native methods.</span></span> <span data-ttu-id="1481b-132">Ten element jest używany do określenia, że tożsamość systemu Windows przepływa przez punkty asynchroniczne, niezależnie od tego, jak personifikacja została osiągnięta.</span><span class="sxs-lookup"><span data-stu-id="1481b-132">This element is used to specify that the Windows identity does flow across asynchronous points, regardless of how the impersonation was achieved.</span></span>  
  
 <span data-ttu-id="1481b-133">To domyślne zachowanie można zmienić na dwa inne sposoby:</span><span class="sxs-lookup"><span data-stu-id="1481b-133">You can alter this default behavior in two other ways:</span></span>  
  
1. <span data-ttu-id="1481b-134">W kodzie zarządzanym na podstawie wątku.</span><span class="sxs-lookup"><span data-stu-id="1481b-134">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="1481b-135">Przepływ można pominąć na podstawie wątku, <xref:System.Threading.ExecutionContext> modyfikując ustawienia <xref:System.Security.SecurityContext> i ustawienia za pomocą metody <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>lub . <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="1481b-135">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>, or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="1481b-136">W wywołaniu interfejsu hostingu niezarządzanego, aby załadować środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="1481b-136">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="1481b-137">Jeśli do załadowania środowiska CLR używany jest niezarządzany interfejs hostingu (zamiast prostego zarządzanego pliku wykonywalnego), można określić specjalną flagę w wywołaniu funkcji [CorBindToRuntimeEx.](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)</span><span class="sxs-lookup"><span data-stu-id="1481b-137">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="1481b-138">Aby włączyć tryb zgodności dla całego procesu, `flags` ustaw parametr [funkcji CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) na `STARTUP_ALWAYSFLOW_IMPERSONATION`.</span><span class="sxs-lookup"><span data-stu-id="1481b-138">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) to `STARTUP_ALWAYSFLOW_IMPERSONATION`.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="1481b-139">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="1481b-139">Configuration File</span></span>  
 <span data-ttu-id="1481b-140">W aplikacji .NET Framework ten element może być używany tylko w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1481b-140">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="1481b-141">W przypadku aplikacji ASP.NET przepływ personifikacji można skonfigurować w pliku aspnet.config znajdującym \<się w katalogu Folder systemu Windows>\Microsoft.NET\Framework\vx.x.xxxx.</span><span class="sxs-lookup"><span data-stu-id="1481b-141">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="1481b-142">ASP.NET domyślnie wyłącza przepływ personifikacji w pliku aspnet.config przy użyciu następujących ustawień konfiguracyjnych:</span><span class="sxs-lookup"><span data-stu-id="1481b-142">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
```xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="1481b-143">W ASP.NET, jeśli chcesz zezwolić na przepływ personifikacji zamiast tego, należy jawnie użyć następujących ustawień konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="1481b-143">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="1481b-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="1481b-144">Example</span></span>  
 <span data-ttu-id="1481b-145">W poniższym przykładzie pokazano, jak określić, że tożsamość systemu Windows przepływa przez punkty asynchroniczne, nawet wtedy, gdy personifikacja zostanie osiągnięta za pomocą środków innych niż metody zarządzane.</span><span class="sxs-lookup"><span data-stu-id="1481b-145">The following example shows how to specify that the Windows identity flows across asynchronous points, even when the impersonation is achieved through means other than managed methods.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1481b-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1481b-146">See also</span></span>

- [<span data-ttu-id="1481b-147">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="1481b-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="1481b-148">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="1481b-148">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="1481b-149">\<legacyImpersonationPolicy> Element</span><span class="sxs-lookup"><span data-stu-id="1481b-149">\<legacyImpersonationPolicy> Element</span></span>](legacyimpersonationpolicy-element.md)
