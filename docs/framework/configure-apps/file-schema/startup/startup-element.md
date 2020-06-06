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
ms.openlocfilehash: e936c069275bfa9f7ac81ef1c6fc6228828182a8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153737"
---
# <a name="startup-element"></a><span data-ttu-id="4958c-102">\<startup>, element</span><span class="sxs-lookup"><span data-stu-id="4958c-102">\<startup> element</span></span>

<span data-ttu-id="4958c-103">Określa informacje uruchamiania środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="4958c-103">Specifies common language runtime startup information.</span></span>

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<startup>**  

## <a name="syntax"></a><span data-ttu-id="4958c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4958c-104">Syntax</span></span>

```xml
<startup useLegacyV2RuntimeActivationPolicy="true|false" >
</startup>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4958c-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4958c-105">Attributes and elements</span></span>

 <span data-ttu-id="4958c-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4958c-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="4958c-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4958c-107">Attributes</span></span>

|<span data-ttu-id="4958c-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4958c-108">Attribute</span></span>|<span data-ttu-id="4958c-109">Opis</span><span class="sxs-lookup"><span data-stu-id="4958c-109">Description</span></span>|
|---------------|-----------------|
|`useLegacyV2RuntimeActivationPolicy`|<span data-ttu-id="4958c-110">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="4958c-110">Optional attribute.</span></span><br /><br /> <span data-ttu-id="4958c-111">Określa, czy włączyć zasady aktywacji środowiska uruchomieniowego .NET Framework 2,0 lub użyć zasad aktywacji .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="4958c-111">Specifies whether to enable the .NET Framework 2.0 runtime activation policy or to use the .NET Framework 4 activation policy.</span></span>|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="4958c-112">useLegacyV2RuntimeActivationPolicy — atrybut</span><span class="sxs-lookup"><span data-stu-id="4958c-112">useLegacyV2RuntimeActivationPolicy attribute</span></span>

|<span data-ttu-id="4958c-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="4958c-113">Value</span></span>|<span data-ttu-id="4958c-114">Opis</span><span class="sxs-lookup"><span data-stu-id="4958c-114">Description</span></span>|
|-----------|-----------------|
|`true`|<span data-ttu-id="4958c-115">Włącz zasady aktywacji środowiska uruchomieniowego .NET Framework 2,0 dla wybranego środowiska uruchomieniowego, czyli powiązać starsze techniki aktywacji w środowisku uruchomieniowym (takie jak [Funkcja CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) w środowisku uruchomieniowym wybranym z pliku konfiguracji zamiast przeznaczyć je na środowisko CLR w wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="4958c-115">Enable .NET Framework 2.0 runtime activation policy for the chosen runtime, which is to bind legacy runtime activation techniques (such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) to the runtime chosen from the configuration file instead of capping them at CLR version 2.0.</span></span> <span data-ttu-id="4958c-116">W takim przypadku, jeśli środowisko CLR w wersji 4 lub nowszej zostanie wybrane z pliku konfiguracji, zestawy w trybie mieszanym utworzone przy użyciu wcześniejszych wersji .NET Framework są ładowane z wybraną wersją środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="4958c-116">Thus, if CLR version 4 or later is chosen from the configuration file, mixed-mode assemblies created with earlier versions of the .NET Framework are loaded with the chosen CLR version.</span></span> <span data-ttu-id="4958c-117">Ustawienie tej wartości uniemożliwia załadowanie środowiska CLR w wersji 1,1 lub 2,0 CLR w ramach tego samego procesu, co skutecznie wyłącza funkcję równoczesną w procesie.</span><span class="sxs-lookup"><span data-stu-id="4958c-117">Setting this value prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature.</span></span>|
|`false`|<span data-ttu-id="4958c-118">Użyj domyślnych zasad aktywacji dla .NET Framework 4 i nowszych, co umożliwia stosowanie starszych technik aktywacji środowiska uruchomieniowego w celu załadowania środowiska CLR w wersji 1,1 lub 2,0 do procesu.</span><span class="sxs-lookup"><span data-stu-id="4958c-118">Use the default activation policy for the .NET Framework 4 and later, which is to allow legacy runtime activation techniques to load CLR version 1.1 or 2.0 into the process.</span></span> <span data-ttu-id="4958c-119">Ustawienie tej wartości uniemożliwia ładowanie zestawów w trybie mieszanym do .NET Framework 4 lub nowszego, chyba że zostały skompilowane przy użyciu .NET Framework 4 lub nowszego.</span><span class="sxs-lookup"><span data-stu-id="4958c-119">Setting this value prevents mixed-mode assemblies from loading into the .NET Framework 4 or later unless they were built with the .NET Framework 4 or later.</span></span> <span data-ttu-id="4958c-120">Ta wartość jest domyślna.</span><span class="sxs-lookup"><span data-stu-id="4958c-120">This value is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="4958c-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4958c-121">Child elements</span></span>

|<span data-ttu-id="4958c-122">Element</span><span class="sxs-lookup"><span data-stu-id="4958c-122">Element</span></span>|<span data-ttu-id="4958c-123">Opis</span><span class="sxs-lookup"><span data-stu-id="4958c-123">Description</span></span>|
|-------------|-----------------|
|[\<requiredRuntime>](requiredruntime-element.md)|<span data-ttu-id="4958c-124">Określa, że aplikacja obsługuje tylko wersję 1,0 środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="4958c-124">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="4958c-125">Aplikacje skompilowane przy użyciu środowiska uruchomieniowego w wersji 1,1 lub nowszej powinny używać **\<supportedRuntime>** elementu.</span><span class="sxs-lookup"><span data-stu-id="4958c-125">Applications built with runtime version 1.1 or later should use the **\<supportedRuntime>** element.</span></span>|
|[\<supportedRuntime>](supportedruntime-element.md)|<span data-ttu-id="4958c-126">Określa wersje środowiska uruchomieniowego języka wspólnego, które obsługuje aplikacja.</span><span class="sxs-lookup"><span data-stu-id="4958c-126">Specifies which versions of the common language runtime the application supports.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4958c-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4958c-127">Parent elements</span></span>

|<span data-ttu-id="4958c-128">Element</span><span class="sxs-lookup"><span data-stu-id="4958c-128">Element</span></span>|<span data-ttu-id="4958c-129">Opis</span><span class="sxs-lookup"><span data-stu-id="4958c-129">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="4958c-130">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4958c-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4958c-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4958c-131">Remarks</span></span>

 <span data-ttu-id="4958c-132">**\<supportedRuntime>** Element powinien być używany przez wszystkie aplikacje skompilowane przy użyciu wersji 1,1 lub nowszej środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="4958c-132">The **\<supportedRuntime>** element should be used by all applications built using version 1.1 or later of the runtime.</span></span> <span data-ttu-id="4958c-133">Aplikacje skompilowane do obsługi tylko wersji 1,0 środowiska uruchomieniowego muszą używać **\<requiredRuntime>** elementu.</span><span class="sxs-lookup"><span data-stu-id="4958c-133">Applications built to support only version 1.0 of the runtime must use the **\<requiredRuntime>** element.</span></span>

 <span data-ttu-id="4958c-134">Kod uruchamiania aplikacji hostowanej w programie Microsoft Internet Explorer ignoruje **\<startup>** element i jego elementy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="4958c-134">The startup code for an application hosted in Microsoft Internet Explorer ignores the **\<startup>** element and its child elements.</span></span>

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="4958c-135">Atrybut useLegacyV2RuntimeActivationPolicy</span><span class="sxs-lookup"><span data-stu-id="4958c-135">The useLegacyV2RuntimeActivationPolicy attribute</span></span>

 <span data-ttu-id="4958c-136">Ten atrybut jest przydatny, jeśli aplikacja używa starszych ścieżek aktywacji, takich jak [Funkcja CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), i chcesz, aby te ścieżki uaktywniali wersję 4 środowiska CLR zamiast wcześniejszej wersji, lub jeśli aplikacja została skompilowana przy użyciu .NET Framework 4, ale ma zależność od zestawu w trybie mieszanym skompilowanego z wcześniejszą wersją .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4958c-136">This attribute is useful if your application uses legacy activation paths, such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), and you want those paths to activate version 4 of the CLR instead of an earlier version, or if your application is built with the .NET Framework 4 but has a dependency on a mixed-mode assembly built with an earlier version of the .NET Framework.</span></span> <span data-ttu-id="4958c-137">W tych scenariuszach należy ustawić atrybut na `true` .</span><span class="sxs-lookup"><span data-stu-id="4958c-137">In those scenarios, set the attribute to `true`.</span></span>

> [!NOTE]
> <span data-ttu-id="4958c-138">Ustawienie atrybutu w celu `true` uniemożliwienia załadowania środowiska CLR w wersji 1,1 lub CLR w wersji 2,0 do tego samego procesu, co skutecznie wyłącza wbudowane funkcje równoległe (zobacz [Wykonywanie równoczesne dla międzyoperacyjności modelu COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).</span><span class="sxs-lookup"><span data-stu-id="4958c-138">Setting the attribute to `true` prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature (see [Side-by-Side Execution for COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).</span></span>

## <a name="example"></a><span data-ttu-id="4958c-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="4958c-139">Example</span></span>

 <span data-ttu-id="4958c-140">Poniższy przykład pokazuje, jak określić wersję środowiska uruchomieniowego w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4958c-140">The following example shows how to specify the runtime version in a configuration file.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4958c-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4958c-141">See also</span></span>

- [<span data-ttu-id="4958c-142">Schemat ustawień uruchamiania</span><span class="sxs-lookup"><span data-stu-id="4958c-142">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="4958c-143">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="4958c-143">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="4958c-144">Instrukcje: Konfigurowanie aplikacji do obsługi .NET Framework 4 lub nowszej wersji</span><span class="sxs-lookup"><span data-stu-id="4958c-144">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- <span data-ttu-id="4958c-145">[Wykonywanie równoczesne dla współdziałania z modelem COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="4958c-145">[Side-by-Side Execution for COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span></span>
- [<span data-ttu-id="4958c-146">Wykonywanie równoczesne i wewnątrzprocesowe</span><span class="sxs-lookup"><span data-stu-id="4958c-146">In-Process Side-by-Side Execution</span></span>](../../../deployment/in-process-side-by-side-execution.md)
