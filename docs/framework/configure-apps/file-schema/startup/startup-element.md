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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153737"
---
# <a name="startup-element"></a><span data-ttu-id="c5a30-102">\<element> uruchamiania</span><span class="sxs-lookup"><span data-stu-id="c5a30-102">\<startup> element</span></span>

<span data-ttu-id="c5a30-103">Określa informacje o uruchamianiu środowiska wykonawczego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="c5a30-103">Specifies common language runtime startup information.</span></span>

[<span data-ttu-id="c5a30-104">**\<>konfiguracyjne**</span><span class="sxs-lookup"><span data-stu-id="c5a30-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="c5a30-105">&nbsp;&nbsp;**\<>uruchamiania**</span><span class="sxs-lookup"><span data-stu-id="c5a30-105">&nbsp;&nbsp;**\<startup>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="c5a30-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="c5a30-106">Syntax</span></span>

```xml
<startup useLegacyV2RuntimeActivationPolicy="true|false" >
</startup>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c5a30-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c5a30-107">Attributes and elements</span></span>

 <span data-ttu-id="c5a30-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c5a30-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c5a30-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c5a30-109">Attributes</span></span>

|<span data-ttu-id="c5a30-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c5a30-110">Attribute</span></span>|<span data-ttu-id="c5a30-111">Opis</span><span class="sxs-lookup"><span data-stu-id="c5a30-111">Description</span></span>|
|---------------|-----------------|
|`useLegacyV2RuntimeActivationPolicy`|<span data-ttu-id="c5a30-112">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="c5a30-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="c5a30-113">Określa, czy włączyć zasady aktywacji środowiska uruchomieniowego programu .NET Framework 2.0, czy użyć zasad aktywacji programu .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="c5a30-113">Specifies whether to enable the .NET Framework 2.0 runtime activation policy or to use the .NET Framework 4 activation policy.</span></span>|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="c5a30-114">useLegacyV2RuntimeActivationPolicy atrybut</span><span class="sxs-lookup"><span data-stu-id="c5a30-114">useLegacyV2RuntimeActivationPolicy attribute</span></span>

|<span data-ttu-id="c5a30-115">Wartość</span><span class="sxs-lookup"><span data-stu-id="c5a30-115">Value</span></span>|<span data-ttu-id="c5a30-116">Opis</span><span class="sxs-lookup"><span data-stu-id="c5a30-116">Description</span></span>|
|-----------|-----------------|
|`true`|<span data-ttu-id="c5a30-117">Włącz zasady aktywacji środowiska uruchomieniowego .NET Framework 2.0 dla wybranego środowiska uruchomieniowego, które mają powiązać starsze techniki aktywacji środowiska uruchomieniowego (takie jak [funkcja CorBindToRuntimeEx)](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)ze środowiska wykonawczego wybranego z pliku konfiguracyjnego zamiast ograniczać je w wersji CLR 2.0.</span><span class="sxs-lookup"><span data-stu-id="c5a30-117">Enable .NET Framework 2.0 runtime activation policy for the chosen runtime, which is to bind legacy runtime activation techniques (such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) to the runtime chosen from the configuration file instead of capping them at CLR version 2.0.</span></span> <span data-ttu-id="c5a30-118">W związku z tym jeśli clr w wersji 4 lub nowszej jest wybrany z pliku konfiguracji, zestawy w trybie mieszanym utworzone z wcześniejszych wersji programu .NET Framework są ładowane z wybraną wersją CLR.</span><span class="sxs-lookup"><span data-stu-id="c5a30-118">Thus, if CLR version 4 or later is chosen from the configuration file, mixed-mode assemblies created with earlier versions of the .NET Framework are loaded with the chosen CLR version.</span></span> <span data-ttu-id="c5a30-119">Ustawienie tej wartości zapobiega wczytywanie clr w wersji 1.1 lub CLR w wersji 2.0 do tego samego procesu, skutecznie wyłączając funkcję w procesie obok siebie.</span><span class="sxs-lookup"><span data-stu-id="c5a30-119">Setting this value prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature.</span></span>|
|`false`|<span data-ttu-id="c5a30-120">Użyj domyślnych zasad aktywacji dla programu .NET Framework 4 lub nowszych, które umożliwiają starsze techniki aktywacji środowiska uruchomieniowego w celu załadowania do procesu programu CLR w wersji 1.1 lub 2.0.</span><span class="sxs-lookup"><span data-stu-id="c5a30-120">Use the default activation policy for the .NET Framework 4 and later, which is to allow legacy runtime activation techniques to load CLR version 1.1 or 2.0 into the process.</span></span> <span data-ttu-id="c5a30-121">Ustawienie tej wartości zapobiega zestawom w trybie mieszanym ładowania do programu .NET Framework 4 lub nowszego, chyba że zostały one utworzone za pomocą programu .NET Framework 4 lub nowszego.</span><span class="sxs-lookup"><span data-stu-id="c5a30-121">Setting this value prevents mixed-mode assemblies from loading into the .NET Framework 4 or later unless they were built with the .NET Framework 4 or later.</span></span> <span data-ttu-id="c5a30-122">Ta wartość jest domyślna.</span><span class="sxs-lookup"><span data-stu-id="c5a30-122">This value is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="c5a30-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c5a30-123">Child elements</span></span>

|<span data-ttu-id="c5a30-124">Element</span><span class="sxs-lookup"><span data-stu-id="c5a30-124">Element</span></span>|<span data-ttu-id="c5a30-125">Opis</span><span class="sxs-lookup"><span data-stu-id="c5a30-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c5a30-126">\<wymaganeRuntime></span><span class="sxs-lookup"><span data-stu-id="c5a30-126">\<requiredRuntime></span></span>](requiredruntime-element.md)|<span data-ttu-id="c5a30-127">Określa, że aplikacja obsługuje tylko wersję 1.0 środowiska wykonawczego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="c5a30-127">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="c5a30-128">Aplikacje utworzone w wersji 1.1 lub \*\* \<\*\* nowszej powinny używać obsługiwanego elementu>.</span><span class="sxs-lookup"><span data-stu-id="c5a30-128">Applications built with runtime version 1.1 or later should use the **\<supportedRuntime>** element.</span></span>|
|[<span data-ttu-id="c5a30-129">\<obsługiwaneRuntime></span><span class="sxs-lookup"><span data-stu-id="c5a30-129">\<supportedRuntime></span></span>](supportedruntime-element.md)|<span data-ttu-id="c5a30-130">Określa wersje środowiska uruchomieniowego języka wspólnego, które obsługuje aplikacja.</span><span class="sxs-lookup"><span data-stu-id="c5a30-130">Specifies which versions of the common language runtime the application supports.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c5a30-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c5a30-131">Parent elements</span></span>

|<span data-ttu-id="c5a30-132">Element</span><span class="sxs-lookup"><span data-stu-id="c5a30-132">Element</span></span>|<span data-ttu-id="c5a30-133">Opis</span><span class="sxs-lookup"><span data-stu-id="c5a30-133">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="c5a30-134">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c5a30-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c5a30-135">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c5a30-135">Remarks</span></span>

 <span data-ttu-id="c5a30-136">\*\* \<Obsługiwanyruntime>\*\* element powinien być używany przez wszystkie aplikacje utworzone przy użyciu wersji 1.1 lub nowszej środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="c5a30-136">The **\<supportedRuntime>** element should be used by all applications built using version 1.1 or later of the runtime.</span></span> <span data-ttu-id="c5a30-137">Aplikacje utworzone w celu obsługi tylko wersji 1.0 środowiska wykonawczego należy użyć \*\* \<wymaganeRuntime>\*\* element.</span><span class="sxs-lookup"><span data-stu-id="c5a30-137">Applications built to support only version 1.0 of the runtime must use the **\<requiredRuntime>** element.</span></span>

 <span data-ttu-id="c5a30-138">Kod startowy aplikacji hostowanego w programie Microsoft Internet Explorer ignoruje element \*\* \<>uruchamiania\*\* i jego elementy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="c5a30-138">The startup code for an application hosted in Microsoft Internet Explorer ignores the **\<startup>** element and its child elements.</span></span>

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="c5a30-139">Atrybut useLegacyV2RuntimeActivationPolicy</span><span class="sxs-lookup"><span data-stu-id="c5a30-139">The useLegacyV2RuntimeActivationPolicy attribute</span></span>

 <span data-ttu-id="c5a30-140">Ten atrybut jest przydatny, jeśli aplikacja używa starszych ścieżek aktywacji, takich jak [Funkcja CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), i chcesz, aby te ścieżki aktywować wersję 4 programu CLR zamiast wcześniejszej wersji lub jeśli aplikacja jest zbudowana za pomocą programu .NET Framework 4, ale ma zależność od zestawu trybu mieszanego utworzonego z wcześniejszą wersją programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c5a30-140">This attribute is useful if your application uses legacy activation paths, such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), and you want those paths to activate version 4 of the CLR instead of an earlier version, or if your application is built with the .NET Framework 4 but has a dependency on a mixed-mode assembly built with an earlier version of the .NET Framework.</span></span> <span data-ttu-id="c5a30-141">W tych scenariuszach ustaw atrybut `true`na .</span><span class="sxs-lookup"><span data-stu-id="c5a30-141">In those scenarios, set the attribute to `true`.</span></span>

> [!NOTE]
> <span data-ttu-id="c5a30-142">Ustawienie atrybutu `true` zapobiega ładowaniu clr w wersji 1.1 lub CLR w wersji 2.0 do tego samego procesu, skutecznie wyłączając funkcję side-by-side w procesie (patrz [Wykonanie side-by-Side dla COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).</span><span class="sxs-lookup"><span data-stu-id="c5a30-142">Setting the attribute to `true` prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature (see [Side-by-Side Execution for COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).</span></span>

## <a name="example"></a><span data-ttu-id="c5a30-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="c5a30-143">Example</span></span>

 <span data-ttu-id="c5a30-144">W poniższym przykładzie pokazano, jak określić wersję środowiska wykonawczego w pliku konfiguracyjnym.</span><span class="sxs-lookup"><span data-stu-id="c5a30-144">The following example shows how to specify the runtime version in a configuration file.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c5a30-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c5a30-145">See also</span></span>

- [<span data-ttu-id="c5a30-146">Schemat ustawień uruchamiania</span><span class="sxs-lookup"><span data-stu-id="c5a30-146">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c5a30-147">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="c5a30-147">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="c5a30-148">Jak: Konfigurowanie aplikacji do obsługi wersji programu .NET Framework 4 lub nowszych</span><span class="sxs-lookup"><span data-stu-id="c5a30-148">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- <span data-ttu-id="c5a30-149">[Wykonanie side-by-side dla com interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c5a30-149">[Side-by-Side Execution for COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span></span>
- [<span data-ttu-id="c5a30-150">Wykonywanie równoczesne i wewnątrzprocesowe</span><span class="sxs-lookup"><span data-stu-id="c5a30-150">In-Process Side-by-Side Execution</span></span>](../../../deployment/in-process-side-by-side-execution.md)
