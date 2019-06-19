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
ms.openlocfilehash: 022f0efbbb2e6e9a4ac9d3d7ddcc1fb1022cdbee
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2019
ms.locfileid: "67169775"
---
# <a name="startup-element"></a><span data-ttu-id="f341d-102">\<Uruchamianie > element</span><span class="sxs-lookup"><span data-stu-id="f341d-102">\<startup> element</span></span>

<span data-ttu-id="f341d-103">Określa informacje o uruchamianiu środowisko uruchomieniowe wspólnego języka.</span><span class="sxs-lookup"><span data-stu-id="f341d-103">Specifies common language runtime startup information.</span></span>

 <span data-ttu-id="f341d-104">\<Konfiguracja > \<uruchamiania ></span><span class="sxs-lookup"><span data-stu-id="f341d-104">\<configuration> \<startup></span></span>

## <a name="syntax"></a><span data-ttu-id="f341d-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f341d-105">Syntax</span></span>

```xml
<startup useLegacyV2RuntimeActivationPolicy="true|false" > 
</startup>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f341d-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f341d-106">Attributes and elements</span></span>

 <span data-ttu-id="f341d-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f341d-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="f341d-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f341d-108">Attributes</span></span>

|<span data-ttu-id="f341d-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f341d-109">Attribute</span></span>|<span data-ttu-id="f341d-110">Opis</span><span class="sxs-lookup"><span data-stu-id="f341d-110">Description</span></span>|
|---------------|-----------------|
|`useLegacyV2RuntimeActivationPolicy`|<span data-ttu-id="f341d-111">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="f341d-111">Optional attribute.</span></span><br /><br /> <span data-ttu-id="f341d-112">Określa, czy włączyć zasady aktywacji .NET Framework 2.0 środowisko uruchomieniowe zasady aktywacji .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="f341d-112">Specifies whether to enable the .NET Framework 2.0 runtime activation policy or to use the .NET Framework 4 activation policy.</span></span>|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="f341d-113">Atrybut useLegacyV2RuntimeActivationPolicy</span><span class="sxs-lookup"><span data-stu-id="f341d-113">useLegacyV2RuntimeActivationPolicy attribute</span></span>

|<span data-ttu-id="f341d-114">Wartość</span><span class="sxs-lookup"><span data-stu-id="f341d-114">Value</span></span>|<span data-ttu-id="f341d-115">Opis</span><span class="sxs-lookup"><span data-stu-id="f341d-115">Description</span></span>|
|-----------|-----------------|
|`true`|<span data-ttu-id="f341d-116">Włączanie zasad aktywacji środowiska uruchomieniowego .NET Framework 2.0 dla wybranego środowiska uruchomieniowego, czyli można powiązać technik aktywacji starszej wersji środowiska uruchomieniowego (takie jak [corbindtoruntimeex — funkcja](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) do środowiska uruchomieniowego zamiast tego wybrać z pliku konfiguracji z nakładanie je na wersji CLR 2.0.</span><span class="sxs-lookup"><span data-stu-id="f341d-116">Enable .NET Framework 2.0 runtime activation policy for the chosen runtime, which is to bind legacy runtime activation techniques (such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) to the runtime chosen from the configuration file instead of capping them at CLR version 2.0.</span></span> <span data-ttu-id="f341d-117">W związku z tym Jeśli wersja środowiska CLR 4 lub nowszego jest wybierany z pliku konfiguracji, zestawy mieszane utworzonych w starszych wersjach programu .NET Framework są ładowane z wybranej wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="f341d-117">Thus, if CLR version 4 or later is chosen from the configuration file, mixed-mode assemblies created with earlier versions of the .NET Framework are loaded with the chosen CLR version.</span></span> <span data-ttu-id="f341d-118">Ustawienie tej wartości zapobiega środowisko CLR w wersji 1.1 lub środowisko CLR w wersji 2.0 ładowanie do tego samego procesu i efektywne wyłączenie funkcji side-by-side w procesie.</span><span class="sxs-lookup"><span data-stu-id="f341d-118">Setting this value prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature.</span></span>|
|`false`|<span data-ttu-id="f341d-119">Używanie domyślnych zasad aktywacji dla programu .NET Framework 4 i nowszych wersji, aby zezwolić na starszej wersji środowiska uruchomieniowego technik aktywacji można załadować środowiska CLR w wersji 1.1 lub 2.0 do procesu.</span><span class="sxs-lookup"><span data-stu-id="f341d-119">Use the default activation policy for the .NET Framework 4 and later, which is to allow legacy runtime activation techniques to load CLR version 1.1 or 2.0 into the process.</span></span> <span data-ttu-id="f341d-120">Ta wartość zapobiega zestawy mieszane ładowanie do programu .NET Framework 4 lub nowszy, chyba że zostały skompilowane przy użyciu programu .NET Framework 4 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="f341d-120">Setting this value prevents mixed-mode assemblies from loading into the .NET Framework 4 or later unless they were built with the .NET Framework 4 or later.</span></span> <span data-ttu-id="f341d-121">Ta wartość jest domyślna.</span><span class="sxs-lookup"><span data-stu-id="f341d-121">This value is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="f341d-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f341d-122">Child elements</span></span>

|<span data-ttu-id="f341d-123">Element</span><span class="sxs-lookup"><span data-stu-id="f341d-123">Element</span></span>|<span data-ttu-id="f341d-124">Opis</span><span class="sxs-lookup"><span data-stu-id="f341d-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f341d-125">\<requiredRuntime></span><span class="sxs-lookup"><span data-stu-id="f341d-125">\<requiredRuntime></span></span>](requiredruntime-element.md)|<span data-ttu-id="f341d-126">Określa, że aplikacja obsługuje tylko wersję 1.0 środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="f341d-126">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="f341d-127">Skorzystaj z aplikacji utworzonych za pomocą środowiska uruchomieniowego wersji 1.1 lub nowszej  **\<supportedRuntime >** elementu.</span><span class="sxs-lookup"><span data-stu-id="f341d-127">Applications built with runtime version 1.1 or later should use the **\<supportedRuntime>** element.</span></span>|
|[<span data-ttu-id="f341d-128">\<supportedRuntime></span><span class="sxs-lookup"><span data-stu-id="f341d-128">\<supportedRuntime></span></span>](supportedruntime-element.md)|<span data-ttu-id="f341d-129">Określa wersje środowiska uruchomieniowego języka wspólnego, które obsługuje aplikacja.</span><span class="sxs-lookup"><span data-stu-id="f341d-129">Specifies which versions of the common language runtime the application supports.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f341d-130">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f341d-130">Parent elements</span></span>

|<span data-ttu-id="f341d-131">Element</span><span class="sxs-lookup"><span data-stu-id="f341d-131">Element</span></span>|<span data-ttu-id="f341d-132">Opis</span><span class="sxs-lookup"><span data-stu-id="f341d-132">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="f341d-133">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f341d-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f341d-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f341d-134">Remarks</span></span>

 <span data-ttu-id="f341d-135">**\<SupportedRuntime >** element powinien być używany przez wszystkie aplikacje kompilowane przy użyciu wersji 1.1 lub nowszej środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="f341d-135">The **\<supportedRuntime>** element should be used by all applications built using version 1.1 or later of the runtime.</span></span> <span data-ttu-id="f341d-136">Aplikacje stworzone z myślą o obsługiwały tylko wersję 1.0 środowiska uruchomieniowego muszą używać  **\<requiredRuntime >** elementu.</span><span class="sxs-lookup"><span data-stu-id="f341d-136">Applications built to support only version 1.0 of the runtime must use the **\<requiredRuntime>** element.</span></span>

 <span data-ttu-id="f341d-137">Ignoruje kodu startowego dla aplikacji hostowanej w programie Internet Explorer  **\<uruchamiania >** elementu i jego elementy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="f341d-137">The startup code for an application hosted in Microsoft Internet Explorer ignores the **\<startup>** element and its child elements.</span></span>

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="f341d-138">Atrybut useLegacyV2RuntimeActivationPolicy</span><span class="sxs-lookup"><span data-stu-id="f341d-138">The useLegacyV2RuntimeActivationPolicy attribute</span></span>

 <span data-ttu-id="f341d-139">Ten atrybut jest przydatna, jeśli aplikacja używa ścieżki aktywacji starszych [corbindtoruntimeex — funkcja](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), i potrzebujesz tych ścieżek do aktywacji w wersji 4 środowiska CLR zamiast wcześniejszej wersji, czy aplikacja jest utworzonych za pomocą programu .NET Framework 4, lecz jest zależność w zestawie mieszanym skompilowanych przy użyciu wcześniejszej wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f341d-139">This attribute is useful if your application uses legacy activation paths, such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), and you want those paths to activate version 4 of the CLR instead of an earlier version, or if your application is built with the .NET Framework 4 but has a dependency on a mixed-mode assembly built with an earlier version of the .NET Framework.</span></span> <span data-ttu-id="f341d-140">W tych scenariuszach atrybut na `true`.</span><span class="sxs-lookup"><span data-stu-id="f341d-140">In those scenarios, set the attribute to `true`.</span></span>

> [!NOTE]
> <span data-ttu-id="f341d-141">Ustawienie atrybutu `true` uniemożliwia ładowanie do tego samego procesu i efektywne wyłączenie funkcji side-by-side w trakcie środowisko CLR w wersji 1.1 lub środowisko CLR w wersji 2.0 (zobacz [Side-by-Side wykonywania COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).</span><span class="sxs-lookup"><span data-stu-id="f341d-141">Setting the attribute to `true` prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature (see [Side-by-Side Execution for COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).</span></span>

## <a name="example"></a><span data-ttu-id="f341d-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="f341d-142">Example</span></span>

 <span data-ttu-id="f341d-143">Poniższy przykład pokazuje, jak określić wersji środowiska uruchomieniowego w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f341d-143">The following example shows how to specify the runtime version in a configuration file.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f341d-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f341d-144">See also</span></span>

- [<span data-ttu-id="f341d-145">Schemat ustawień uruchamiania</span><span class="sxs-lookup"><span data-stu-id="f341d-145">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="f341d-146">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="f341d-146">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="f341d-147">Instrukcje: Konfigurowanie aplikacji do obsługi w programie .NET Framework 4 lub nowszy</span><span class="sxs-lookup"><span data-stu-id="f341d-147">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- <span data-ttu-id="f341d-148">[Wykonanie Side-by-Side dla współdziałania z modelem COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f341d-148">[Side-by-Side Execution for COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span></span>
- [<span data-ttu-id="f341d-149">Wykonywanie równoczesne i wewnątrzprocesowe</span><span class="sxs-lookup"><span data-stu-id="f341d-149">In-Process Side-by-Side Execution</span></span>](../../../deployment/in-process-side-by-side-execution.md)
