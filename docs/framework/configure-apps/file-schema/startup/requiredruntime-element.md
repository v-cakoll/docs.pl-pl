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
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697485"
---
# <a name="requiredruntime-element"></a><span data-ttu-id="89489-102">\<element > requiredRuntime</span><span class="sxs-lookup"><span data-stu-id="89489-102">\<requiredRuntime> element</span></span>

<span data-ttu-id="89489-103">Określa, że aplikacja obsługuje tylko wersję 1,0 środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="89489-103">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="89489-104">Ten element jest przestarzały i nie powinien już być używany.</span><span class="sxs-lookup"><span data-stu-id="89489-104">This element is deprecated and should no longer be used.</span></span> <span data-ttu-id="89489-105">Zamiast tego należy użyć elementu [`supportedRuntime`](supportedruntime-element.md) .</span><span class="sxs-lookup"><span data-stu-id="89489-105">The [`supportedRuntime`](supportedruntime-element.md) element should be used instead.</span></span>

[<span data-ttu-id="89489-106"> **> konfiguracji \<** </span><span class="sxs-lookup"><span data-stu-id="89489-106">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="89489-107">&nbsp;&nbsp;[ **> uruchamiania\<** ](startup-element.md)</span><span class="sxs-lookup"><span data-stu-id="89489-107">&nbsp;&nbsp;[**\<startup>**](startup-element.md)</span></span>  
<span data-ttu-id="89489-108">&nbsp;&nbsp;&nbsp;&nbsp; **\<requiredRuntime >**</span><span class="sxs-lookup"><span data-stu-id="89489-108">&nbsp;&nbsp;&nbsp;&nbsp;**\<requiredRuntime>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="89489-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="89489-109">Syntax</span></span>

```xml
   <requiredRuntime  
version="runtime version"
safemode="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="89489-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="89489-110">Attributes and elements</span></span>

<span data-ttu-id="89489-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="89489-111">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="89489-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="89489-112">Attributes</span></span>

|<span data-ttu-id="89489-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="89489-113">Attribute</span></span>|<span data-ttu-id="89489-114">Opis</span><span class="sxs-lookup"><span data-stu-id="89489-114">Description</span></span>|
|---------------|-----------------|
|`version`|<span data-ttu-id="89489-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="89489-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="89489-116">Wartość ciągu określająca wersję .NET Framework obsługiwanej przez tę aplikację.</span><span class="sxs-lookup"><span data-stu-id="89489-116">A string value that specifies the version of the .NET Framework that this application supports.</span></span> <span data-ttu-id="89489-117">Wartość ciągu musi być zgodna z nazwą katalogu znajdującą się w katalogu głównym instalacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="89489-117">The string value must match the directory name found under the .NET Framework installation root.</span></span> <span data-ttu-id="89489-118">Zawartość ciągu nie jest analizowana.</span><span class="sxs-lookup"><span data-stu-id="89489-118">The contents of the string value are not parsed.</span></span>|
|`safemode`|<span data-ttu-id="89489-119">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="89489-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="89489-120">Określa, czy kod uruchomienia środowiska uruchomieniowego przeszukuje rejestr w celu określenia wersji środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="89489-120">Specifies whether the runtime startup code searches the registry to determine the runtime version.</span></span>|

## <a name="safemode-attribute"></a><span data-ttu-id="89489-121">safemode — atrybut</span><span class="sxs-lookup"><span data-stu-id="89489-121">safemode attribute</span></span>

|<span data-ttu-id="89489-122">Value</span><span class="sxs-lookup"><span data-stu-id="89489-122">Value</span></span>|<span data-ttu-id="89489-123">Opis</span><span class="sxs-lookup"><span data-stu-id="89489-123">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="89489-124">Kod uruchomienia środowiska uruchomieniowego przeszukuje rejestr.</span><span class="sxs-lookup"><span data-stu-id="89489-124">The runtime startup code looks in the registry.</span></span> <span data-ttu-id="89489-125">Jest to wartość domyślna.</span><span class="sxs-lookup"><span data-stu-id="89489-125">This is the default value.</span></span>|
|`true`|<span data-ttu-id="89489-126">Kod uruchomienia środowiska uruchomieniowego nie przeszukuje rejestru.</span><span class="sxs-lookup"><span data-stu-id="89489-126">The runtime startup code does not look in the registry.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="89489-127">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="89489-127">Child elements</span></span>

<span data-ttu-id="89489-128">Brak.</span><span class="sxs-lookup"><span data-stu-id="89489-128">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="89489-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="89489-129">Parent elements</span></span>

|<span data-ttu-id="89489-130">Element</span><span class="sxs-lookup"><span data-stu-id="89489-130">Element</span></span>|<span data-ttu-id="89489-131">Opis</span><span class="sxs-lookup"><span data-stu-id="89489-131">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="89489-132">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="89489-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`startup`|<span data-ttu-id="89489-133">Zawiera element `<requiredRuntime>`.</span><span class="sxs-lookup"><span data-stu-id="89489-133">Contains the `<requiredRuntime>` element.</span></span>|

## <a name="remarks"></a><span data-ttu-id="89489-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="89489-134">Remarks</span></span>
 <span data-ttu-id="89489-135">Aplikacje skompilowane do obsługi tylko wersji 1,0 środowiska uruchomieniowego muszą używać elementu `<requiredRuntime>`.</span><span class="sxs-lookup"><span data-stu-id="89489-135">Applications built to support only version 1.0 of the runtime must use the `<requiredRuntime>` element.</span></span> <span data-ttu-id="89489-136">Aplikacje skompilowane przy użyciu wersji 1,1 lub nowszej środowiska uruchomieniowego muszą używać elementu `<supportedRuntime>`.</span><span class="sxs-lookup"><span data-stu-id="89489-136">Applications built using version 1.1 or later of the runtime must use the `<supportedRuntime>` element.</span></span>

> [!NOTE]
> <span data-ttu-id="89489-137">W przypadku użycia funkcji [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) w celu określenia pliku konfiguracji należy użyć elementu `<requiredRuntime>` dla wszystkich wersji środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="89489-137">If you use the [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) function to specify the configuration file, you must use the `<requiredRuntime>` element for all versions of the runtime.</span></span> <span data-ttu-id="89489-138">Element `<supportedRuntime>` jest ignorowany w przypadku korzystania z [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span><span class="sxs-lookup"><span data-stu-id="89489-138">The `<supportedRuntime>` element is ignored when you use [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span></span>

 <span data-ttu-id="89489-139">Ciąg atrybutu `version` musi być zgodny z nazwą folderu instalacji określonej wersji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="89489-139">The `version` attribute string must match the installation folder name for the specified version of the .NET Framework.</span></span> <span data-ttu-id="89489-140">Ten ciąg nie jest interpretowany.</span><span class="sxs-lookup"><span data-stu-id="89489-140">This string is not interpreted.</span></span> <span data-ttu-id="89489-141">Jeśli kod uruchomienia środowiska uruchomieniowego nie odnajdzie pasującego folderu, środowisko uruchomieniowe nie zostanie załadowane; kod uruchamiania pokazuje komunikat o błędzie i kończy pracę.</span><span class="sxs-lookup"><span data-stu-id="89489-141">If the runtime startup code does not find a matching folder, the runtime is not loaded; the startup code shows an error message and quits.</span></span>

> [!NOTE]
> <span data-ttu-id="89489-142">Kod uruchamiania aplikacji hostowanej w programie Microsoft Internet Explorer ignoruje `<requiredRuntime>` elementu.</span><span class="sxs-lookup"><span data-stu-id="89489-142">The startup code for an application that is hosted in Microsoft Internet Explorer ignores the `<requiredRuntime>` element.</span></span>

## <a name="example"></a><span data-ttu-id="89489-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="89489-143">Example</span></span>

<span data-ttu-id="89489-144">Poniższy przykład pokazuje, jak określić wersję środowiska uruchomieniowego w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="89489-144">The following example shows how to specify the runtime version in a configuration file.</span></span>

```xml
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="89489-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="89489-145">See also</span></span>

- [<span data-ttu-id="89489-146">Schemat ustawień uruchamiania</span><span class="sxs-lookup"><span data-stu-id="89489-146">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="89489-147">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="89489-147">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="89489-148">Instrukcje: Konfigurowanie aplikacji do obsługi .NET Framework 4 lub nowszej wersji</span><span class="sxs-lookup"><span data-stu-id="89489-148">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
