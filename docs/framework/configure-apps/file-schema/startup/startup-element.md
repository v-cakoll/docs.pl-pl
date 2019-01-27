---
title: '&lt;uruchamianie&gt; — element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup
- http://schemas.microsoft.com/.NetConfiguration/v2.0#startup
helpviewer_keywords:
- container tags, <startup> element
- <startup> element
- startup element
ms.assetid: 536acfd8-f827-452f-838a-e14fa3b87621
ms.openlocfilehash: 9fc5a555085369cdec249eb9b5b247f403bd12ed
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083720"
---
# <a name="ltstartupgt-element"></a><span data-ttu-id="9703a-102">&lt;uruchamianie&gt; — element</span><span class="sxs-lookup"><span data-stu-id="9703a-102">&lt;startup&gt; element</span></span>

<span data-ttu-id="9703a-103">Określa informacje o uruchamianiu środowisko uruchomieniowe wspólnego języka.</span><span class="sxs-lookup"><span data-stu-id="9703a-103">Specifies common language runtime startup information.</span></span>

 <span data-ttu-id="9703a-104">\<Konfiguracja > \<uruchamiania ></span><span class="sxs-lookup"><span data-stu-id="9703a-104">\<configuration> \<startup></span></span>

## <a name="syntax"></a><span data-ttu-id="9703a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="9703a-105">Syntax</span></span>

```xml
<startup useLegacyV2RuntimeActivationPolicy="true|false" > 
</startup>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9703a-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9703a-106">Attributes and elements</span></span>

 <span data-ttu-id="9703a-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9703a-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="9703a-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9703a-108">Attributes</span></span>

|<span data-ttu-id="9703a-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9703a-109">Attribute</span></span>|<span data-ttu-id="9703a-110">Opis</span><span class="sxs-lookup"><span data-stu-id="9703a-110">Description</span></span>|
|---------------|-----------------|
|`useLegacyV2RuntimeActivationPolicy`|<span data-ttu-id="9703a-111">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="9703a-111">Optional attribute.</span></span><br /><br /> <span data-ttu-id="9703a-112">Określa, czy włączyć [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] zasad aktywacji środowiska uruchomieniowego lub użyć [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] zasad aktywacji.</span><span class="sxs-lookup"><span data-stu-id="9703a-112">Specifies whether to enable the [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] runtime activation policy or to use the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] activation policy.</span></span>|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="9703a-113">Atrybut useLegacyV2RuntimeActivationPolicy</span><span class="sxs-lookup"><span data-stu-id="9703a-113">useLegacyV2RuntimeActivationPolicy attribute</span></span>

|<span data-ttu-id="9703a-114">Wartość</span><span class="sxs-lookup"><span data-stu-id="9703a-114">Value</span></span>|<span data-ttu-id="9703a-115">Opis</span><span class="sxs-lookup"><span data-stu-id="9703a-115">Description</span></span>|
|-----------|-----------------|
|`true`|<span data-ttu-id="9703a-116">Włącz [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] środowiska uruchomieniowego zasad aktywacji dla wybranego środowiska uruchomieniowego, czyli można powiązać technik aktywacji starszej wersji środowiska uruchomieniowego (takie jak [corbindtoruntimeex — funkcja](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) do środowiska uruchomieniowego, wybrana z pliku konfiguracji zamiast Ograniczanie je na wersji CLR 2.0.</span><span class="sxs-lookup"><span data-stu-id="9703a-116">Enable [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] runtime activation policy for the chosen runtime, which is to bind legacy runtime activation techniques (such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) to the runtime chosen from the configuration file instead of capping them at CLR version 2.0.</span></span> <span data-ttu-id="9703a-117">W związku z tym Jeśli wersja środowiska CLR 4 lub nowszego jest wybierany z pliku konfiguracji, zestawy mieszane utworzonych w starszych wersjach programu .NET Framework są ładowane z wybranej wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="9703a-117">Thus, if CLR version 4 or later is chosen from the configuration file, mixed-mode assemblies created with earlier versions of the .NET Framework are loaded with the chosen CLR version.</span></span> <span data-ttu-id="9703a-118">Ustawienie tej wartości zapobiega środowisko CLR w wersji 1.1 lub środowisko CLR w wersji 2.0 ładowanie do tego samego procesu i efektywne wyłączenie funkcji side-by-side w procesie.</span><span class="sxs-lookup"><span data-stu-id="9703a-118">Setting this value prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature.</span></span>|
|`false`|<span data-ttu-id="9703a-119">Użyj domyślnych zasad aktywacji dla [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] i nowszy, która umożliwia starszej wersji środowiska uruchomieniowego technik aktywacji można załadować środowiska CLR w wersji 1.1 lub 2.0 do procesu.</span><span class="sxs-lookup"><span data-stu-id="9703a-119">Use the default activation policy for the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] and later, which is to allow legacy runtime activation techniques to load CLR version 1.1 or 2.0 into the process.</span></span> <span data-ttu-id="9703a-120">Ta wartość zapobiega zestawy mieszane ładowanie do programu .NET Framework 4 lub nowszy, chyba że zostały skompilowane przy użyciu programu .NET Framework 4 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="9703a-120">Setting this value prevents mixed-mode assemblies from loading into the .NET Framework 4 or later unless they were built with the .NET Framework 4 or later.</span></span> <span data-ttu-id="9703a-121">Ta wartość jest domyślna.</span><span class="sxs-lookup"><span data-stu-id="9703a-121">This value is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="9703a-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9703a-122">Child elements</span></span>

|<span data-ttu-id="9703a-123">Element</span><span class="sxs-lookup"><span data-stu-id="9703a-123">Element</span></span>|<span data-ttu-id="9703a-124">Opis</span><span class="sxs-lookup"><span data-stu-id="9703a-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="9703a-125">\<requiredRuntime></span><span class="sxs-lookup"><span data-stu-id="9703a-125">\<requiredRuntime></span></span>](requiredruntime-element.md)|<span data-ttu-id="9703a-126">Określa, że aplikacja obsługuje tylko wersję 1.0 środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="9703a-126">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="9703a-127">Skorzystaj z aplikacji utworzonych za pomocą środowiska uruchomieniowego wersji 1.1 lub nowszej  **\<supportedRuntime >** elementu.</span><span class="sxs-lookup"><span data-stu-id="9703a-127">Applications built with runtime version 1.1 or later should use the **\<supportedRuntime>** element.</span></span>|
|[<span data-ttu-id="9703a-128">\<supportedRuntime></span><span class="sxs-lookup"><span data-stu-id="9703a-128">\<supportedRuntime></span></span>](supportedruntime-element.md)|<span data-ttu-id="9703a-129">Określa wersje środowiska uruchomieniowego języka wspólnego, które obsługuje aplikacja.</span><span class="sxs-lookup"><span data-stu-id="9703a-129">Specifies which versions of the common language runtime the application supports.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="9703a-130">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9703a-130">Parent elements</span></span>

|<span data-ttu-id="9703a-131">Element</span><span class="sxs-lookup"><span data-stu-id="9703a-131">Element</span></span>|<span data-ttu-id="9703a-132">Opis</span><span class="sxs-lookup"><span data-stu-id="9703a-132">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="9703a-133">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9703a-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9703a-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9703a-134">Remarks</span></span>

 <span data-ttu-id="9703a-135"> *\*\<SupportedRuntime >** element powinien być używany przez wszystkie aplikacje kompilowane przy użyciu wersji 1.1 lub nowszej środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="9703a-135">The **\<supportedRuntime>** element should be used by all applications built using version 1.1 or later of the runtime.</span></span> <span data-ttu-id="9703a-136">Aplikacje stworzone z myślą o obsługiwały tylko wersję 1.0 środowiska uruchomieniowego muszą używać  **\<requiredRuntime >** elementu.</span><span class="sxs-lookup"><span data-stu-id="9703a-136">Applications built to support only version 1.0 of the runtime must use the **\<requiredRuntime>** element.</span></span>

 <span data-ttu-id="9703a-137">Ignoruje kodu startowego dla aplikacji hostowanej w programie Internet Explorer  **\<uruchamiania >** elementu i jego elementy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="9703a-137">The startup code for an application hosted in Microsoft Internet Explorer ignores the **\<startup>** element and its child elements.</span></span>

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="9703a-138">Atrybut useLegacyV2RuntimeActivationPolicy</span><span class="sxs-lookup"><span data-stu-id="9703a-138">The useLegacyV2RuntimeActivationPolicy attribute</span></span>

 <span data-ttu-id="9703a-139">Ten atrybut jest przydatna, jeśli aplikacja używa ścieżki aktywacji starszych [corbindtoruntimeex — funkcja](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), i potrzebujesz tych ścieżek do aktywacji w wersji 4 środowiska CLR zamiast wcześniejszej wersji, czy aplikacja jest utworzonych za pomocą [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] ale ma zależność od zestawu trybu mieszanego, skompilowanych przy użyciu wcześniejszej wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9703a-139">This attribute is useful if your application uses legacy activation paths, such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), and you want those paths to activate version 4 of the CLR instead of an earlier version, or if your application is built with the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] but has a dependency on a mixed-mode assembly built with an earlier version of the .NET Framework.</span></span> <span data-ttu-id="9703a-140">W tych scenariuszach atrybut na `true`.</span><span class="sxs-lookup"><span data-stu-id="9703a-140">In those scenarios, set the attribute to `true`.</span></span>

> [!NOTE]
> <span data-ttu-id="9703a-141">Ustawienie atrybutu `true` uniemożliwia ładowanie do tego samego procesu i efektywne wyłączenie funkcji side-by-side w trakcie środowisko CLR w wersji 1.1 lub środowisko CLR w wersji 2.0 (zobacz [Side-by-Side wykonywania COM Interop](https://msdn.microsoft.com/library/4302318c-3586-49bf-8620-b9a39cdf4a32)).</span><span class="sxs-lookup"><span data-stu-id="9703a-141">Setting the attribute to `true` prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature (see [Side-by-Side Execution for COM Interop](https://msdn.microsoft.com/library/4302318c-3586-49bf-8620-b9a39cdf4a32)).</span></span>

## <a name="example"></a><span data-ttu-id="9703a-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="9703a-142">Example</span></span>

 <span data-ttu-id="9703a-143">Poniższy przykład pokazuje, jak określić wersji środowiska uruchomieniowego w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="9703a-143">The following example shows how to specify the runtime version in a configuration file.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9703a-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9703a-144">See also</span></span>

- [<span data-ttu-id="9703a-145">Schemat ustawień uruchamiania</span><span class="sxs-lookup"><span data-stu-id="9703a-145">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="9703a-146">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="9703a-146">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="9703a-147">Instrukcje: Konfigurowanie aplikacji do obsługi w programie .NET Framework 4 lub nowszy</span><span class="sxs-lookup"><span data-stu-id="9703a-147">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [<span data-ttu-id="9703a-148">Wykonanie Side-by-Side dla współdziałania z modelem COM</span><span class="sxs-lookup"><span data-stu-id="9703a-148">Side-by-Side Execution for COM Interop</span></span>](https://msdn.microsoft.com/library/4302318c-3586-49bf-8620-b9a39cdf4a32)
- [<span data-ttu-id="9703a-149">Wykonywanie równoczesne i wewnątrzprocesowe</span><span class="sxs-lookup"><span data-stu-id="9703a-149">In-Process Side-by-Side Execution</span></span>](../../../deployment/in-process-side-by-side-execution.md)