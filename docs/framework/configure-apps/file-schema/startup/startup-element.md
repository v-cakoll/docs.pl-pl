---
title: '&lt;uruchamianie&gt; — Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup
- http://schemas.microsoft.com/.NetConfiguration/v2.0#startup
helpviewer_keywords:
- container tags, <startup> element
- <startup> element
- startup element
ms.assetid: 536acfd8-f827-452f-838a-e14fa3b87621
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 60699f0335bb35589341558800cfd64503d0aa0a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltstartupgt-element"></a><span data-ttu-id="2abad-102">&lt;uruchamianie&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="2abad-102">&lt;startup&gt; Element</span></span>
<span data-ttu-id="2abad-103">Określa uruchamiania informacje CLR.</span><span class="sxs-lookup"><span data-stu-id="2abad-103">Specifies common language runtime startup information.</span></span>  
  
 <span data-ttu-id="2abad-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="2abad-104">\<configuration></span></span>  
<span data-ttu-id="2abad-105">\<startup></span><span class="sxs-lookup"><span data-stu-id="2abad-105">\<startup></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2abad-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="2abad-106">Syntax</span></span>  
  
```xml  
<startup useLegacyV2RuntimeActivationPolicy="true|false" >   
</startup>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2abad-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2abad-107">Attributes and Elements</span></span>  
 <span data-ttu-id="2abad-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2abad-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2abad-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2abad-109">Attributes</span></span>  
  
|<span data-ttu-id="2abad-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2abad-110">Attribute</span></span>|<span data-ttu-id="2abad-111">Opis</span><span class="sxs-lookup"><span data-stu-id="2abad-111">Description</span></span>|  
|---------------|-----------------|  
|`useLegacyV2RuntimeActivationPolicy`|<span data-ttu-id="2abad-112">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="2abad-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="2abad-113">Określa, czy włączyć [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] zasad aktywacji środowiska uruchomieniowego lub użyć [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] zasad aktywacji.</span><span class="sxs-lookup"><span data-stu-id="2abad-113">Specifies whether to enable the [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] runtime activation policy or to use the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] activation policy.</span></span>|  
  
## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="2abad-114">Atrybut useLegacyV2RuntimeActivationPolicy</span><span class="sxs-lookup"><span data-stu-id="2abad-114">useLegacyV2RuntimeActivationPolicy Attribute</span></span>  
  
|<span data-ttu-id="2abad-115">Wartość</span><span class="sxs-lookup"><span data-stu-id="2abad-115">Value</span></span>|<span data-ttu-id="2abad-116">Opis</span><span class="sxs-lookup"><span data-stu-id="2abad-116">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="2abad-117">Włącz [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] zasad wykonywania aktywacji dla wybranego środowiska uruchomieniowego, czyli powiązać techniki aktywacji starszej wersji środowiska uruchomieniowego (takich jak [CorBindToRuntimeEx — funkcja](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)) do środowiska wykonawczego wybrane z pliku konfiguracji zamiast ograniczanie ich w CLR w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="2abad-117">Enable [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] runtime activation policy for the chosen runtime, which is to bind legacy runtime activation techniques (such as the [CorBindToRuntimeEx function](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)) to the runtime chosen from the configuration file instead of capping them at CLR version 2.0.</span></span> <span data-ttu-id="2abad-118">W związku z tym jeśli CLR w wersji 4 lub nowszej jest wybierany z pliku konfiguracji, trybu mieszanego zestawów utworzonych w starszych wersjach programu .NET Framework są ładowane z wybranej wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="2abad-118">Thus, if CLR version 4 or later is chosen from the configuration file, mixed-mode assemblies created with earlier versions of the .NET Framework are loaded with the chosen CLR version.</span></span> <span data-ttu-id="2abad-119">Ta wartość uniemożliwia CLR w wersji 1.1 lub CLR w wersji 2.0 ładowania do tego samego procesu, efektywne wyłączenie funkcji side-by-side w procesie.</span><span class="sxs-lookup"><span data-stu-id="2abad-119">Setting this value prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature.</span></span>|  
|`false`|<span data-ttu-id="2abad-120">Użyj domyślnych zasad aktywacji dla [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] i później, która umożliwia starszej wersji środowiska uruchomieniowego techniki aktywacji można załadować w procesie CLR w wersji 1.1 lub 2.0.</span><span class="sxs-lookup"><span data-stu-id="2abad-120">Use the default activation policy for the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] and later, which is to allow legacy runtime activation techniques to load CLR version 1.1 or 2.0 into the process.</span></span> <span data-ttu-id="2abad-121">Ustawienie tej wartości zapobiega zestawy trybu mieszanego ładowania do programu .NET Framework 4 lub nowszy, chyba że zostały one skompilowane z programu .NET Framework 4 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="2abad-121">Setting this value prevents mixed-mode assemblies from loading into the .NET Framework 4 or later unless they were built with the .NET Framework 4 or later.</span></span> <span data-ttu-id="2abad-122">Ta wartość jest ustawieniem domyślnym.</span><span class="sxs-lookup"><span data-stu-id="2abad-122">This value is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2abad-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2abad-123">Child Elements</span></span>  
  
|<span data-ttu-id="2abad-124">Element</span><span class="sxs-lookup"><span data-stu-id="2abad-124">Element</span></span>|<span data-ttu-id="2abad-125">Opis</span><span class="sxs-lookup"><span data-stu-id="2abad-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2abad-126">\<requiredRuntime ></span><span class="sxs-lookup"><span data-stu-id="2abad-126">\<requiredRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|<span data-ttu-id="2abad-127">Określa, czy aplikacja obsługuje tylko wersję 1.0 środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="2abad-127">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="2abad-128">Należy użyć aplikacji skompilowanej za pomocą środowiska wykonawczego w wersji 1.1 lub nowszej  **\<supportedRuntime >** elementu.</span><span class="sxs-lookup"><span data-stu-id="2abad-128">Applications built with runtime version 1.1 or later should use the **\<supportedRuntime>** element.</span></span>|  
|[<span data-ttu-id="2abad-129">\<supportedRuntime ></span><span class="sxs-lookup"><span data-stu-id="2abad-129">\<supportedRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|<span data-ttu-id="2abad-130">Określa wersje środowiska uruchomieniowego języka wspólnego, które obsługuje aplikacja.</span><span class="sxs-lookup"><span data-stu-id="2abad-130">Specifies which versions of the common language runtime the application supports.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2abad-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2abad-131">Parent Elements</span></span>  
  
|<span data-ttu-id="2abad-132">Element</span><span class="sxs-lookup"><span data-stu-id="2abad-132">Element</span></span>|<span data-ttu-id="2abad-133">Opis</span><span class="sxs-lookup"><span data-stu-id="2abad-133">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="2abad-134">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2abad-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2abad-135">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2abad-135">Remarks</span></span>  
 <span data-ttu-id="2abad-136">**\<SupportedRuntime >** element powinna być używana przez wszystkie aplikacje utworzone przy użyciu wersji 1.1 lub nowszej środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="2abad-136">The **\<supportedRuntime>** element should be used by all applications built using version 1.1 or later of the runtime.</span></span> <span data-ttu-id="2abad-137">Aplikacje przeznaczone do obsługi tylko wersję 1.0 środowiska uruchomieniowego musi używać  **\<requiredRuntime >** elementu.</span><span class="sxs-lookup"><span data-stu-id="2abad-137">Applications built to support only version 1.0 of the runtime must use the **\<requiredRuntime>** element.</span></span>  
  
 <span data-ttu-id="2abad-138">Kod uruchomienia dla aplikacji hostowanej w programie Internet Explorer ignoruje  **\<uruchamiania >** elementu i jego elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="2abad-138">The startup code for an application hosted in Microsoft Internet Explorer ignores the **\<startup>** element and its child elements.</span></span>  
  
## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="2abad-139">Atrybut useLegacyV2RuntimeActivationPolicy</span><span class="sxs-lookup"><span data-stu-id="2abad-139">The useLegacyV2RuntimeActivationPolicy Attribute</span></span>  
 <span data-ttu-id="2abad-140">Ten atrybut jest przydatne, jeśli aplikacja używa ścieżek aktywacji starszych wersji [CorBindToRuntimeEx — funkcja](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), i chcesz tych ścieżek do aktywowania zamiast starszej wersji środowiska CLR w wersji 4 lub w przypadku aplikacji zbudowany z [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] ale ma zależność w zestawie trybu mieszanego skompilowanej za pomocą starszej wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2abad-140">This attribute is useful if your application uses legacy activation paths, such as the [CorBindToRuntimeEx function](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), and you want those paths to activate version 4 of the CLR instead of an earlier version, or if your application is built with the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] but has a dependency on a mixed-mode assembly built with an earlier version of the .NET Framework.</span></span> <span data-ttu-id="2abad-141">W tych scenariuszach, ustaw dla atrybutu `true`.</span><span class="sxs-lookup"><span data-stu-id="2abad-141">In those scenarios, set the attribute to `true`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2abad-142">Ustawienie atrybutu `true` uniemożliwia ładowanie do tego samego procesu, efektywne wyłączenie funkcji side-by-side w trakcie CLR w wersji 1.1 lub CLR w wersji 2.0 (zobacz [Side-by-Side wykonywanie COM Interop](http://msdn.microsoft.com/library/4302318c-3586-49bf-8620-b9a39cdf4a32)).</span><span class="sxs-lookup"><span data-stu-id="2abad-142">Setting the attribute to `true` prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature (see [Side-by-Side Execution for COM Interop](http://msdn.microsoft.com/library/4302318c-3586-49bf-8620-b9a39cdf4a32)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2abad-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="2abad-143">Example</span></span>  
 <span data-ttu-id="2abad-144">Poniższy przykład pokazuje, jak do określania wersji środowiska uruchomieniowego w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2abad-144">The following example shows how to specify the runtime version in a configuration file.</span></span>  
  
```xml  
<!-- When used with version 1.0 of the .NET Framework runtime -->  
<configuration>  
   <startup>  
      <requiredRuntime version="v1.0.3705" safemode="true"/>  
   </startup>  
</configuration>  
<!-- When used with version 1.1 (or later) of the runtime -->  
<configuration>  
   <startup>  
      <supportedRuntime version="v1.1.4322"/>  
      <supportedRuntime version="v1.0.3705"/>  
   </startup>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2abad-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2abad-145">See Also</span></span>  
 [<span data-ttu-id="2abad-146">Schemat ustawień uruchamiania</span><span class="sxs-lookup"><span data-stu-id="2abad-146">Startup Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/index.md)  
 [<span data-ttu-id="2abad-147">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="2abad-147">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="2abad-148">\<PaveOver > Określanie wersji środowiska uruchomieniowego do użycia</span><span class="sxs-lookup"><span data-stu-id="2abad-148">\<PaveOver> Specifying Which Runtime Version to Use</span></span>](http://msdn.microsoft.com/library/c376208d-980d-42b4-865b-fbe0d9cc97c2)  
 [<span data-ttu-id="2abad-149">Wykonanie Side-by-Side dla międzyoperacyjności z modelem COM</span><span class="sxs-lookup"><span data-stu-id="2abad-149">Side-by-Side Execution for COM Interop</span></span>](http://msdn.microsoft.com/library/4302318c-3586-49bf-8620-b9a39cdf4a32)  
 [<span data-ttu-id="2abad-150">Wykonywanie równoczesne i wewnątrzprocesowe</span><span class="sxs-lookup"><span data-stu-id="2abad-150">In-Process Side-by-Side Execution</span></span>](../../../../../docs/framework/deployment/in-process-side-by-side-execution.md)
