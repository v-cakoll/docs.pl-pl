---
title: "&lt;requiredRuntime&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requiredRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/requiredRuntime
helpviewer_keywords:
- requiredRuntime element
- <requiredRuntime> element
- container tags, <requiredRuntime> element
ms.assetid: 9fa1639e-beb8-43be-b7a4-12f7b229c34b
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 2e864eec2ddf51d5cc88110654f6c23f146938d5
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="ltrequiredruntimegt-element"></a><span data-ttu-id="24364-102">&lt;requiredRuntime&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="24364-102">&lt;requiredRuntime&gt; Element</span></span>
<span data-ttu-id="24364-103">Określa, czy aplikacja obsługuje tylko wersję 1.0 środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="24364-103">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="24364-104">Ten element jest przestarzały i nie będzie można użyć.</span><span class="sxs-lookup"><span data-stu-id="24364-104">This element is deprecated and should no longer be used.</span></span> <span data-ttu-id="24364-105">[ `supportedRuntime` ](supportedruntime-element.md) Elementu należy użyć.</span><span class="sxs-lookup"><span data-stu-id="24364-105">The [`supportedRuntime`](supportedruntime-element.md) element should be used instead.</span></span>
  
 <span data-ttu-id="24364-106">\<configuration></span><span class="sxs-lookup"><span data-stu-id="24364-106">\<configuration></span></span>  
<span data-ttu-id="24364-107">\<startup></span><span class="sxs-lookup"><span data-stu-id="24364-107">\<startup></span></span>  
<span data-ttu-id="24364-108">\<requiredRuntime></span><span class="sxs-lookup"><span data-stu-id="24364-108">\<requiredRuntime></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24364-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="24364-109">Syntax</span></span>  
  
```xml  
   <requiredRuntime    
version="runtime version"  
safemode="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="24364-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="24364-110">Attributes and Elements</span></span>  
 <span data-ttu-id="24364-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="24364-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="24364-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="24364-112">Attributes</span></span>  
  
|<span data-ttu-id="24364-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="24364-113">Attribute</span></span>|<span data-ttu-id="24364-114">Opis</span><span class="sxs-lookup"><span data-stu-id="24364-114">Description</span></span>|  
|---------------|-----------------|  
|`version`|<span data-ttu-id="24364-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="24364-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="24364-116">Wartość ciągu, który określa wersję programu .NET Framework, która obsługuje tę aplikację.</span><span class="sxs-lookup"><span data-stu-id="24364-116">A string value that specifies the version of the .NET Framework that this application supports.</span></span> <span data-ttu-id="24364-117">Wartość ciągu musi odpowiadać nazwie katalogu znajdują się w katalogu instalacji platformy .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="24364-117">The string value must match the directory name found under the .NET Framework installation root.</span></span> <span data-ttu-id="24364-118">Zawartość wartości ciągu nie są przeanalizować.</span><span class="sxs-lookup"><span data-stu-id="24364-118">The contents of the string value are not parsed.</span></span>|  
|`safemode`|<span data-ttu-id="24364-119">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="24364-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="24364-120">Określa, czy kod uruchomienia środowiska uruchomieniowego wyszukuje rejestru można ustalić wersji środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="24364-120">Specifies whether the runtime startup code searches the registry to determine the runtime version.</span></span>|  
  
## <a name="safemode-attribute"></a><span data-ttu-id="24364-121">Tryb awaryjny atrybutu</span><span class="sxs-lookup"><span data-stu-id="24364-121">safemode Attribute</span></span>  
  
|<span data-ttu-id="24364-122">Wartość</span><span class="sxs-lookup"><span data-stu-id="24364-122">Value</span></span>|<span data-ttu-id="24364-123">Opis</span><span class="sxs-lookup"><span data-stu-id="24364-123">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="24364-124">Kod uruchomienia środowiska uruchomieniowego wyszukuje w rejestrze.</span><span class="sxs-lookup"><span data-stu-id="24364-124">The runtime startup code looks in the registry.</span></span> <span data-ttu-id="24364-125">Jest to wartość domyślna.</span><span class="sxs-lookup"><span data-stu-id="24364-125">This is the default value.</span></span>|  
|`true`|<span data-ttu-id="24364-126">Kod uruchomienia środowiska uruchomieniowego wygląda w rejestrze.</span><span class="sxs-lookup"><span data-stu-id="24364-126">The runtime startup code does not look in the registry.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="24364-127">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="24364-127">Child Elements</span></span>  
 <span data-ttu-id="24364-128">Brak.</span><span class="sxs-lookup"><span data-stu-id="24364-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="24364-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="24364-129">Parent Elements</span></span>  
  
|<span data-ttu-id="24364-130">Element</span><span class="sxs-lookup"><span data-stu-id="24364-130">Element</span></span>|<span data-ttu-id="24364-131">Opis</span><span class="sxs-lookup"><span data-stu-id="24364-131">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="24364-132">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="24364-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`startup`|<span data-ttu-id="24364-133">Zawiera `<requiredRuntime>` elementu.</span><span class="sxs-lookup"><span data-stu-id="24364-133">Contains the `<requiredRuntime>` element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="24364-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="24364-134">Remarks</span></span>  
 <span data-ttu-id="24364-135">Aplikacje przeznaczone do obsługi tylko wersję 1.0 środowiska uruchomieniowego musi używać `<requiredRuntime>` elementu.</span><span class="sxs-lookup"><span data-stu-id="24364-135">Applications built to support only version 1.0 of the runtime must use the `<requiredRuntime>` element.</span></span> <span data-ttu-id="24364-136">Należy użyć aplikacji utworzony za pomocą wersji 1.1 lub nowszej środowiska uruchomieniowego `<supportedRuntime>` elementu.</span><span class="sxs-lookup"><span data-stu-id="24364-136">Applications built using version 1.1 or later of the runtime must use the `<supportedRuntime>` element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="24364-137">Jeśli używasz [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md) funkcji, aby określić plik konfiguracji, należy użyć `<requiredRuntime>` elementu dla wszystkich wersji środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="24364-137">If you use the [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md) function to specify the configuration file, you must use the `<requiredRuntime>` element for all versions of the runtime.</span></span> <span data-ttu-id="24364-138">`<supportedRuntime>` Element jest ignorowana, korzystając z [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span><span class="sxs-lookup"><span data-stu-id="24364-138">The `<supportedRuntime>` element is ignored when you use [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span></span>  
  
 <span data-ttu-id="24364-139">`version` Ciąg atrybutu musi odpowiadać nazwie folder instalacji dla określonej wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="24364-139">The `version` attribute string must match the installation folder name for the specified version of the .NET Framework.</span></span> <span data-ttu-id="24364-140">Ten ciąg nie jest interpretowany.</span><span class="sxs-lookup"><span data-stu-id="24364-140">This string is not interpreted.</span></span> <span data-ttu-id="24364-141">Jeśli kod uruchomienia środowiska uruchomieniowego nie może znaleźć pasujących folderu, nie załadowano środowiska uruchomieniowego; Kod uruchomienia zawiera komunikat o błędzie i kończy działanie.</span><span class="sxs-lookup"><span data-stu-id="24364-141">If the runtime startup code does not find a matching folder, the runtime is not loaded; the startup code shows an error message and quits.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="24364-142">Kod uruchomienia dla aplikacji, która jest obsługiwana w programie Internet Explorer ignoruje `<requiredRuntime>` elementu.</span><span class="sxs-lookup"><span data-stu-id="24364-142">The startup code for an application that is hosted in Microsoft Internet Explorer ignores the `<requiredRuntime>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24364-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="24364-143">Example</span></span>  
 <span data-ttu-id="24364-144">Poniższy przykład pokazuje, jak do określania wersji środowiska uruchomieniowego w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="24364-144">The following example shows how to specify the runtime version in a configuration file.</span></span>  
  
```xml  
<configuration>  
   <startup>  
      <requiredRuntime version="v1.0.3705" safemode="true"/>  
   </startup>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="24364-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="24364-145">See Also</span></span>  
 [<span data-ttu-id="24364-146">Schemat ustawień uruchamiania</span><span class="sxs-lookup"><span data-stu-id="24364-146">Startup Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/index.md)  
 [<span data-ttu-id="24364-147">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="24364-147">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="24364-148">\<PaveOver > Określanie wersji środowiska uruchomieniowego do użycia</span><span class="sxs-lookup"><span data-stu-id="24364-148">\<PaveOver> Specifying Which Runtime Version to Use</span></span>](http://msdn.microsoft.com/library/c376208d-980d-42b4-865b-fbe0d9cc97c2)
