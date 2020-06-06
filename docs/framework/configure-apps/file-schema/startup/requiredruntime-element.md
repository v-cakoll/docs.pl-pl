---
title: <requiredRuntime>, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requiredRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/requiredRuntime
helpviewer_keywords:
- requiredRuntime element
- <requiredRuntime> element
- container tags, <requiredRuntime> element
ms.assetid: 9fa1639e-beb8-43be-b7a4-12f7b229c34b
ms.openlocfilehash: fe96673b95f48cb75d36662a680bf56a59363f9f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "71697485"
---
# <a name="requiredruntime-element"></a><span data-ttu-id="4e962-102">\<requiredRuntime>, element</span><span class="sxs-lookup"><span data-stu-id="4e962-102">\<requiredRuntime> element</span></span>

<span data-ttu-id="4e962-103">Określa, że aplikacja obsługuje tylko wersję 1,0 środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="4e962-103">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="4e962-104">Ten element jest przestarzały i nie powinien już być używany.</span><span class="sxs-lookup"><span data-stu-id="4e962-104">This element is deprecated and should no longer be used.</span></span> <span data-ttu-id="4e962-105">[`supportedRuntime`](supportedruntime-element.md)Zamiast tego należy użyć elementu.</span><span class="sxs-lookup"><span data-stu-id="4e962-105">The [`supportedRuntime`](supportedruntime-element.md) element should be used instead.</span></span>

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<startup>**](startup-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<requiredRuntime>**  

## <a name="syntax"></a><span data-ttu-id="4e962-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="4e962-106">Syntax</span></span>

```xml
   <requiredRuntime  
version="runtime version"
safemode="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4e962-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4e962-107">Attributes and elements</span></span>

<span data-ttu-id="4e962-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4e962-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="4e962-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4e962-109">Attributes</span></span>

|<span data-ttu-id="4e962-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4e962-110">Attribute</span></span>|<span data-ttu-id="4e962-111">Opis</span><span class="sxs-lookup"><span data-stu-id="4e962-111">Description</span></span>|
|---------------|-----------------|
|`version`|<span data-ttu-id="4e962-112">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="4e962-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="4e962-113">Wartość ciągu określająca wersję .NET Framework obsługiwanej przez tę aplikację.</span><span class="sxs-lookup"><span data-stu-id="4e962-113">A string value that specifies the version of the .NET Framework that this application supports.</span></span> <span data-ttu-id="4e962-114">Wartość ciągu musi być zgodna z nazwą katalogu znajdującą się w katalogu głównym instalacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4e962-114">The string value must match the directory name found under the .NET Framework installation root.</span></span> <span data-ttu-id="4e962-115">Zawartość ciągu nie jest analizowana.</span><span class="sxs-lookup"><span data-stu-id="4e962-115">The contents of the string value are not parsed.</span></span>|
|`safemode`|<span data-ttu-id="4e962-116">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="4e962-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="4e962-117">Określa, czy kod uruchomienia środowiska uruchomieniowego przeszukuje rejestr w celu określenia wersji środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="4e962-117">Specifies whether the runtime startup code searches the registry to determine the runtime version.</span></span>|

## <a name="safemode-attribute"></a><span data-ttu-id="4e962-118">safemode — atrybut</span><span class="sxs-lookup"><span data-stu-id="4e962-118">safemode attribute</span></span>

|<span data-ttu-id="4e962-119">Wartość</span><span class="sxs-lookup"><span data-stu-id="4e962-119">Value</span></span>|<span data-ttu-id="4e962-120">Opis</span><span class="sxs-lookup"><span data-stu-id="4e962-120">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="4e962-121">Kod uruchomienia środowiska uruchomieniowego przeszukuje rejestr.</span><span class="sxs-lookup"><span data-stu-id="4e962-121">The runtime startup code looks in the registry.</span></span> <span data-ttu-id="4e962-122">Jest to wartość domyślna.</span><span class="sxs-lookup"><span data-stu-id="4e962-122">This is the default value.</span></span>|
|`true`|<span data-ttu-id="4e962-123">Kod uruchomienia środowiska uruchomieniowego nie przeszukuje rejestru.</span><span class="sxs-lookup"><span data-stu-id="4e962-123">The runtime startup code does not look in the registry.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="4e962-124">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4e962-124">Child elements</span></span>

<span data-ttu-id="4e962-125">Brak.</span><span class="sxs-lookup"><span data-stu-id="4e962-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4e962-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4e962-126">Parent elements</span></span>

|<span data-ttu-id="4e962-127">Element</span><span class="sxs-lookup"><span data-stu-id="4e962-127">Element</span></span>|<span data-ttu-id="4e962-128">Opis</span><span class="sxs-lookup"><span data-stu-id="4e962-128">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="4e962-129">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4e962-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`startup`|<span data-ttu-id="4e962-130">Zawiera `<requiredRuntime>` element.</span><span class="sxs-lookup"><span data-stu-id="4e962-130">Contains the `<requiredRuntime>` element.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4e962-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4e962-131">Remarks</span></span>
 <span data-ttu-id="4e962-132">Aplikacje skompilowane do obsługi tylko wersji 1,0 środowiska uruchomieniowego muszą używać `<requiredRuntime>` elementu.</span><span class="sxs-lookup"><span data-stu-id="4e962-132">Applications built to support only version 1.0 of the runtime must use the `<requiredRuntime>` element.</span></span> <span data-ttu-id="4e962-133">Aplikacje skompilowane przy użyciu wersji 1,1 lub nowszej środowiska uruchomieniowego muszą używać `<supportedRuntime>` elementu.</span><span class="sxs-lookup"><span data-stu-id="4e962-133">Applications built using version 1.1 or later of the runtime must use the `<supportedRuntime>` element.</span></span>

> [!NOTE]
> <span data-ttu-id="4e962-134">Jeśli używasz funkcji [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) do określenia pliku konfiguracji, musisz użyć `<requiredRuntime>` elementu dla wszystkich wersji środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="4e962-134">If you use the [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) function to specify the configuration file, you must use the `<requiredRuntime>` element for all versions of the runtime.</span></span> <span data-ttu-id="4e962-135">`<supportedRuntime>`Element jest ignorowany w przypadku korzystania z [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span><span class="sxs-lookup"><span data-stu-id="4e962-135">The `<supportedRuntime>` element is ignored when you use [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span></span>

 <span data-ttu-id="4e962-136">`version`Ciąg atrybutu musi być zgodny z nazwą folderu instalacji określonej wersji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4e962-136">The `version` attribute string must match the installation folder name for the specified version of the .NET Framework.</span></span> <span data-ttu-id="4e962-137">Ten ciąg nie jest interpretowany.</span><span class="sxs-lookup"><span data-stu-id="4e962-137">This string is not interpreted.</span></span> <span data-ttu-id="4e962-138">Jeśli kod uruchomienia środowiska uruchomieniowego nie odnajdzie pasującego folderu, środowisko uruchomieniowe nie zostanie załadowane; kod uruchamiania pokazuje komunikat o błędzie i kończy pracę.</span><span class="sxs-lookup"><span data-stu-id="4e962-138">If the runtime startup code does not find a matching folder, the runtime is not loaded; the startup code shows an error message and quits.</span></span>

> [!NOTE]
> <span data-ttu-id="4e962-139">Kod uruchamiania aplikacji hostowanej w programie Microsoft Internet Explorer ignoruje `<requiredRuntime>` element.</span><span class="sxs-lookup"><span data-stu-id="4e962-139">The startup code for an application that is hosted in Microsoft Internet Explorer ignores the `<requiredRuntime>` element.</span></span>

## <a name="example"></a><span data-ttu-id="4e962-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="4e962-140">Example</span></span>

<span data-ttu-id="4e962-141">Poniższy przykład pokazuje, jak określić wersję środowiska uruchomieniowego w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4e962-141">The following example shows how to specify the runtime version in a configuration file.</span></span>

```xml
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="4e962-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4e962-142">See also</span></span>

- [<span data-ttu-id="4e962-143">Schemat ustawień uruchamiania</span><span class="sxs-lookup"><span data-stu-id="4e962-143">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="4e962-144">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="4e962-144">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="4e962-145">Instrukcje: Konfigurowanie aplikacji do obsługi .NET Framework 4 lub nowszej wersji</span><span class="sxs-lookup"><span data-stu-id="4e962-145">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
