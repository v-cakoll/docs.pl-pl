---
title: <startup>, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup
- http://schemas.microsoft.com/.NetConfiguration/v2.0#startup
helpviewer_keywords:
- container tags, <startup> element
- <startup> element
- startup element
ms.assetid: 536acfd8-f827-452f-838a-e14fa3b87621
ms.openlocfilehash: 634d9c5248c33619abec50d441d95c111febdcbf
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699418"
---
# <a name="startup-element"></a><span data-ttu-id="bf531-102">\<startup > elementu</span><span class="sxs-lookup"><span data-stu-id="bf531-102">\<startup> element</span></span>

<span data-ttu-id="bf531-103">Określa informacje uruchamiania środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="bf531-103">Specifies common language runtime startup information.</span></span>

[<span data-ttu-id="bf531-104"> **@no__t — 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="bf531-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="bf531-105">&nbsp; @ no__t-1 **\<startup >**</span><span class="sxs-lookup"><span data-stu-id="bf531-105">&nbsp;&nbsp;**\<startup>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="bf531-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="bf531-106">Syntax</span></span>

```xml
<startup useLegacyV2RuntimeActivationPolicy="true|false" > 
</startup>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bf531-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="bf531-107">Attributes and elements</span></span>

 <span data-ttu-id="bf531-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="bf531-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="bf531-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bf531-109">Attributes</span></span>

|<span data-ttu-id="bf531-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="bf531-110">Attribute</span></span>|<span data-ttu-id="bf531-111">Opis</span><span class="sxs-lookup"><span data-stu-id="bf531-111">Description</span></span>|
|---------------|-----------------|
|`useLegacyV2RuntimeActivationPolicy`|<span data-ttu-id="bf531-112">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="bf531-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="bf531-113">Określa, czy włączyć zasady aktywacji środowiska uruchomieniowego .NET Framework 2,0 lub użyć zasad aktywacji .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="bf531-113">Specifies whether to enable the .NET Framework 2.0 runtime activation policy or to use the .NET Framework 4 activation policy.</span></span>|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="bf531-114">useLegacyV2RuntimeActivationPolicy — atrybut</span><span class="sxs-lookup"><span data-stu-id="bf531-114">useLegacyV2RuntimeActivationPolicy attribute</span></span>

|<span data-ttu-id="bf531-115">Wartość</span><span class="sxs-lookup"><span data-stu-id="bf531-115">Value</span></span>|<span data-ttu-id="bf531-116">Opis</span><span class="sxs-lookup"><span data-stu-id="bf531-116">Description</span></span>|
|-----------|-----------------|
|`true`|<span data-ttu-id="bf531-117">Włącz zasady aktywacji środowiska uruchomieniowego .NET Framework 2,0 dla wybranego środowiska uruchomieniowego, czyli powiązać starsze techniki aktywacji w środowisku uruchomieniowym (takie jak [Funkcja CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) w środowisku uruchomieniowym wybranym z pliku konfiguracji zamiast przeznaczyć je na środowisko CLR Wersja 2,0.</span><span class="sxs-lookup"><span data-stu-id="bf531-117">Enable .NET Framework 2.0 runtime activation policy for the chosen runtime, which is to bind legacy runtime activation techniques (such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) to the runtime chosen from the configuration file instead of capping them at CLR version 2.0.</span></span> <span data-ttu-id="bf531-118">W takim przypadku, jeśli środowisko CLR w wersji 4 lub nowszej zostanie wybrane z pliku konfiguracji, zestawy w trybie mieszanym utworzone przy użyciu wcześniejszych wersji .NET Framework są ładowane z wybraną wersją środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="bf531-118">Thus, if CLR version 4 or later is chosen from the configuration file, mixed-mode assemblies created with earlier versions of the .NET Framework are loaded with the chosen CLR version.</span></span> <span data-ttu-id="bf531-119">Ustawienie tej wartości uniemożliwia załadowanie środowiska CLR w wersji 1,1 lub 2,0 CLR w ramach tego samego procesu, co skutecznie wyłącza funkcję równoczesną w procesie.</span><span class="sxs-lookup"><span data-stu-id="bf531-119">Setting this value prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature.</span></span>|
|`false`|<span data-ttu-id="bf531-120">Użyj domyślnych zasad aktywacji dla .NET Framework 4 i nowszych, co umożliwia stosowanie starszych technik aktywacji środowiska uruchomieniowego w celu załadowania środowiska CLR w wersji 1,1 lub 2,0 do procesu.</span><span class="sxs-lookup"><span data-stu-id="bf531-120">Use the default activation policy for the .NET Framework 4 and later, which is to allow legacy runtime activation techniques to load CLR version 1.1 or 2.0 into the process.</span></span> <span data-ttu-id="bf531-121">Ustawienie tej wartości uniemożliwia ładowanie zestawów w trybie mieszanym do .NET Framework 4 lub nowszego, chyba że zostały skompilowane przy użyciu .NET Framework 4 lub nowszego.</span><span class="sxs-lookup"><span data-stu-id="bf531-121">Setting this value prevents mixed-mode assemblies from loading into the .NET Framework 4 or later unless they were built with the .NET Framework 4 or later.</span></span> <span data-ttu-id="bf531-122">Jest to wartość domyślna.</span><span class="sxs-lookup"><span data-stu-id="bf531-122">This value is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="bf531-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="bf531-123">Child elements</span></span>

|<span data-ttu-id="bf531-124">Element</span><span class="sxs-lookup"><span data-stu-id="bf531-124">Element</span></span>|<span data-ttu-id="bf531-125">Opis</span><span class="sxs-lookup"><span data-stu-id="bf531-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bf531-126">@no__t — 1requiredRuntime ></span><span class="sxs-lookup"><span data-stu-id="bf531-126">\<requiredRuntime></span></span>](requiredruntime-element.md)|<span data-ttu-id="bf531-127">Określa, że aplikacja obsługuje tylko wersję 1,0 środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="bf531-127">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="bf531-128">Aplikacje skompilowane przy użyciu środowiska uruchomieniowego w wersji 1,1 lub nowszej powinny używać elementu **\<supportedRuntime >** .</span><span class="sxs-lookup"><span data-stu-id="bf531-128">Applications built with runtime version 1.1 or later should use the **\<supportedRuntime>** element.</span></span>|
|[<span data-ttu-id="bf531-129">@no__t — 1supportedRuntime ></span><span class="sxs-lookup"><span data-stu-id="bf531-129">\<supportedRuntime></span></span>](supportedruntime-element.md)|<span data-ttu-id="bf531-130">Określa wersje środowiska uruchomieniowego języka wspólnego, które obsługuje aplikacja.</span><span class="sxs-lookup"><span data-stu-id="bf531-130">Specifies which versions of the common language runtime the application supports.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="bf531-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bf531-131">Parent elements</span></span>

|<span data-ttu-id="bf531-132">Element</span><span class="sxs-lookup"><span data-stu-id="bf531-132">Element</span></span>|<span data-ttu-id="bf531-133">Opis</span><span class="sxs-lookup"><span data-stu-id="bf531-133">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="bf531-134">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bf531-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="bf531-135">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bf531-135">Remarks</span></span>

 <span data-ttu-id="bf531-136">Element **\<supportedRuntime >** powinien być używany przez wszystkie aplikacje skompilowane przy użyciu wersji 1,1 lub nowszej środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="bf531-136">The **\<supportedRuntime>** element should be used by all applications built using version 1.1 or later of the runtime.</span></span> <span data-ttu-id="bf531-137">Aplikacje skompilowane do obsługi tylko wersji 1,0 środowiska uruchomieniowego muszą używać elementu **\<requiredRuntime >** .</span><span class="sxs-lookup"><span data-stu-id="bf531-137">Applications built to support only version 1.0 of the runtime must use the **\<requiredRuntime>** element.</span></span>

 <span data-ttu-id="bf531-138">Kod uruchamiania aplikacji hostowanej w programie Microsoft Internet Explorer ignoruje **\<startup >** elementu i jego elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="bf531-138">The startup code for an application hosted in Microsoft Internet Explorer ignores the **\<startup>** element and its child elements.</span></span>

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="bf531-139">Atrybut useLegacyV2RuntimeActivationPolicy</span><span class="sxs-lookup"><span data-stu-id="bf531-139">The useLegacyV2RuntimeActivationPolicy attribute</span></span>

 <span data-ttu-id="bf531-140">Ten atrybut jest przydatny, jeśli aplikacja używa starszych ścieżek aktywacji, takich jak [Funkcja CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), i chcesz, aby te ścieżki uaktywniali wersję 4 środowiska CLR zamiast wcześniejszej wersji, lub jeśli aplikacja została skompilowana przy użyciu platformy .NET Framework 4, ale ma zależność od zestawu w trybie mieszanym skompilowanego za pomocą wcześniejszej wersji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bf531-140">This attribute is useful if your application uses legacy activation paths, such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), and you want those paths to activate version 4 of the CLR instead of an earlier version, or if your application is built with the .NET Framework 4 but has a dependency on a mixed-mode assembly built with an earlier version of the .NET Framework.</span></span> <span data-ttu-id="bf531-141">W tych scenariuszach ustaw wartość atrybutu na `true`.</span><span class="sxs-lookup"><span data-stu-id="bf531-141">In those scenarios, set the attribute to `true`.</span></span>

> [!NOTE]
> <span data-ttu-id="bf531-142">Ustawienie atrybutu na `true` uniemożliwia ładowanie środowiska CLR w wersji 1,1 lub CLR Version 2,0 do tego samego procesu, co skutecznie wyłącza wbudowane funkcje równoległe (zobacz [Wykonywanie równoczesne dla](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))współdziałania z modelem com).</span><span class="sxs-lookup"><span data-stu-id="bf531-142">Setting the attribute to `true` prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature (see [Side-by-Side Execution for COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).</span></span>

## <a name="example"></a><span data-ttu-id="bf531-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="bf531-143">Example</span></span>

 <span data-ttu-id="bf531-144">Poniższy przykład pokazuje, jak określić wersję środowiska uruchomieniowego w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="bf531-144">The following example shows how to specify the runtime version in a configuration file.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="bf531-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bf531-145">See also</span></span>

- [<span data-ttu-id="bf531-146">Schemat ustawień uruchamiania</span><span class="sxs-lookup"><span data-stu-id="bf531-146">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="bf531-147">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="bf531-147">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="bf531-148">Instrukcje: Konfigurowanie aplikacji do obsługi .NET Framework 4 lub nowszej wersji</span><span class="sxs-lookup"><span data-stu-id="bf531-148">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- <span data-ttu-id="bf531-149">[Wykonywanie równoczesne dla współdziałania z modelem COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="bf531-149">[Side-by-Side Execution for COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span></span>
- [<span data-ttu-id="bf531-150">Wykonywanie równoczesne i wewnątrzprocesowe</span><span class="sxs-lookup"><span data-stu-id="bf531-150">In-Process Side-by-Side Execution</span></span>](../../../deployment/in-process-side-by-side-execution.md)
