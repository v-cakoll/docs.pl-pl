---
title: '&lt;requiredRuntime&gt; — element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requiredRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/requiredRuntime
helpviewer_keywords:
- requiredRuntime element
- <requiredRuntime> element
- container tags, <requiredRuntime> element
ms.assetid: 9fa1639e-beb8-43be-b7a4-12f7b229c34b
ms.openlocfilehash: 66de3e30ce862cd317e80ea267bf22ce728aca82
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2019
ms.locfileid: "54222132"
---
# <a name="ltrequiredruntimegt-element"></a><span data-ttu-id="e461e-102">&lt;requiredRuntime&gt; — element</span><span class="sxs-lookup"><span data-stu-id="e461e-102">&lt;requiredRuntime&gt; element</span></span>

<span data-ttu-id="e461e-103">Określa, że aplikacja obsługuje tylko wersję 1.0 środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="e461e-103">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="e461e-104">Ten element jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="e461e-104">This element is deprecated and should no longer be used.</span></span> <span data-ttu-id="e461e-105">[ `supportedRuntime` ](supportedruntime-element.md) Zamiast tego należy użyć elementu.</span><span class="sxs-lookup"><span data-stu-id="e461e-105">The [`supportedRuntime`](supportedruntime-element.md) element should be used instead.</span></span>

<span data-ttu-id="e461e-106">\<Konfiguracja > \<uruchamiania > \<requiredRuntime ></span><span class="sxs-lookup"><span data-stu-id="e461e-106">\<configuration> \<startup> \<requiredRuntime></span></span>

## <a name="syntax"></a><span data-ttu-id="e461e-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="e461e-107">Syntax</span></span>

```xml
   <requiredRuntime  
version="runtime version"
safemode="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e461e-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e461e-108">Attributes and elements</span></span>

<span data-ttu-id="e461e-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e461e-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="e461e-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e461e-110">Attributes</span></span>

|<span data-ttu-id="e461e-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e461e-111">Attribute</span></span>|<span data-ttu-id="e461e-112">Opis</span><span class="sxs-lookup"><span data-stu-id="e461e-112">Description</span></span>|
|---------------|-----------------|
|`version`|<span data-ttu-id="e461e-113">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="e461e-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="e461e-114">Wartość ciągu określająca wersję programu .NET Framework, którą obsługuje ta aplikacja.</span><span class="sxs-lookup"><span data-stu-id="e461e-114">A string value that specifies the version of the .NET Framework that this application supports.</span></span> <span data-ttu-id="e461e-115">Wartość ciągu musi odpowiadać nazwa katalogu znajdują się w katalogu głównym instalacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e461e-115">The string value must match the directory name found under the .NET Framework installation root.</span></span> <span data-ttu-id="e461e-116">Zawartość wartości ciągu nie są analizowane.</span><span class="sxs-lookup"><span data-stu-id="e461e-116">The contents of the string value are not parsed.</span></span>|
|`safemode`|<span data-ttu-id="e461e-117">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="e461e-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="e461e-118">Określa, czy kod uruchamiający środowisko uruchomieniowe wyszukuje rejestr w celu ustalenia wersji środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="e461e-118">Specifies whether the runtime startup code searches the registry to determine the runtime version.</span></span>|

## <a name="safemode-attribute"></a><span data-ttu-id="e461e-119">safemode — atrybut</span><span class="sxs-lookup"><span data-stu-id="e461e-119">safemode attribute</span></span>

|<span data-ttu-id="e461e-120">Wartość</span><span class="sxs-lookup"><span data-stu-id="e461e-120">Value</span></span>|<span data-ttu-id="e461e-121">Opis</span><span class="sxs-lookup"><span data-stu-id="e461e-121">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="e461e-122">Kod uruchamiający środowisko uruchomieniowe wyszukuje w rejestrze.</span><span class="sxs-lookup"><span data-stu-id="e461e-122">The runtime startup code looks in the registry.</span></span> <span data-ttu-id="e461e-123">Jest to wartość domyślna.</span><span class="sxs-lookup"><span data-stu-id="e461e-123">This is the default value.</span></span>|
|`true`|<span data-ttu-id="e461e-124">Kod startowy środowiska uruchomieniowego nie znajduje się w rejestrze.</span><span class="sxs-lookup"><span data-stu-id="e461e-124">The runtime startup code does not look in the registry.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="e461e-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e461e-125">Child elements</span></span>

<span data-ttu-id="e461e-126">Brak.</span><span class="sxs-lookup"><span data-stu-id="e461e-126">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e461e-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e461e-127">Parent elements</span></span>

|<span data-ttu-id="e461e-128">Element</span><span class="sxs-lookup"><span data-stu-id="e461e-128">Element</span></span>|<span data-ttu-id="e461e-129">Opis</span><span class="sxs-lookup"><span data-stu-id="e461e-129">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="e461e-130">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e461e-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`startup`|<span data-ttu-id="e461e-131">Zawiera `<requiredRuntime>` elementu.</span><span class="sxs-lookup"><span data-stu-id="e461e-131">Contains the `<requiredRuntime>` element.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e461e-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e461e-132">Remarks</span></span>
 <span data-ttu-id="e461e-133">Aplikacje stworzone z myślą o obsługiwały tylko wersję 1.0 środowiska uruchomieniowego muszą używać `<requiredRuntime>` elementu.</span><span class="sxs-lookup"><span data-stu-id="e461e-133">Applications built to support only version 1.0 of the runtime must use the `<requiredRuntime>` element.</span></span> <span data-ttu-id="e461e-134">Aplikacje utworzone przy użyciu wersji 1.1 lub nowszej środowiska uruchomieniowego muszą używać `<supportedRuntime>` elementu.</span><span class="sxs-lookup"><span data-stu-id="e461e-134">Applications built using version 1.1 or later of the runtime must use the `<supportedRuntime>` element.</span></span>

> [!NOTE]
> <span data-ttu-id="e461e-135">Jeśli używasz [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) funkcji, aby określić plik konfiguracji, należy użyć `<requiredRuntime>` elementu dla wszystkich wersji środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="e461e-135">If you use the [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) function to specify the configuration file, you must use the `<requiredRuntime>` element for all versions of the runtime.</span></span> <span data-ttu-id="e461e-136">`<supportedRuntime>` Element jest ignorowany, gdy używasz [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span><span class="sxs-lookup"><span data-stu-id="e461e-136">The `<supportedRuntime>` element is ignored when you use [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span></span>

 <span data-ttu-id="e461e-137">`version` Ciągu atrybutu musi odpowiadać nazwie folder instalacji dla określonej wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e461e-137">The `version` attribute string must match the installation folder name for the specified version of the .NET Framework.</span></span> <span data-ttu-id="e461e-138">Ten ciąg nie jest interpretowany.</span><span class="sxs-lookup"><span data-stu-id="e461e-138">This string is not interpreted.</span></span> <span data-ttu-id="e461e-139">Jeśli kod startowy środowiska uruchomieniowego nie znajdzie folderem dopasowania, środowisko uruchomieniowe nie jest załadowany; kod startowy pokazuje komunikat o błędzie i kończy działanie.</span><span class="sxs-lookup"><span data-stu-id="e461e-139">If the runtime startup code does not find a matching folder, the runtime is not loaded; the startup code shows an error message and quits.</span></span>

> [!NOTE]
> <span data-ttu-id="e461e-140">Ignoruje kodu startowego dla aplikacji, która jest obsługiwana w programie Internet Explorer `<requiredRuntime>` elementu.</span><span class="sxs-lookup"><span data-stu-id="e461e-140">The startup code for an application that is hosted in Microsoft Internet Explorer ignores the `<requiredRuntime>` element.</span></span>

## <a name="example"></a><span data-ttu-id="e461e-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="e461e-141">Example</span></span>

<span data-ttu-id="e461e-142">Poniższy przykład pokazuje, jak określić wersji środowiska uruchomieniowego w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e461e-142">The following example shows how to specify the runtime version in a configuration file.</span></span>

```xml
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="e461e-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e461e-143">See also</span></span>

- [<span data-ttu-id="e461e-144">Schemat ustawień uruchamiania</span><span class="sxs-lookup"><span data-stu-id="e461e-144">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e461e-145">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e461e-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="e461e-146">Instrukcje: Konfigurowanie aplikacji do obsługi w programie .NET Framework 4 lub nowszy</span><span class="sxs-lookup"><span data-stu-id="e461e-146">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)