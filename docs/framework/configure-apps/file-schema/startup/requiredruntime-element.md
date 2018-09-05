---
title: '&lt;requiredRuntime&gt; — Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requiredRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/requiredRuntime
helpviewer_keywords:
- requiredRuntime element
- <requiredRuntime> element
- container tags, <requiredRuntime> element
ms.assetid: 9fa1639e-beb8-43be-b7a4-12f7b229c34b
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ac1e1f7bc36d8d2b12b99de2794bb0ba31ddbd7a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518650"
---
# <a name="ltrequiredruntimegt-element"></a><span data-ttu-id="b7bbc-102">&lt;requiredRuntime&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="b7bbc-102">&lt;requiredRuntime&gt; Element</span></span>
<span data-ttu-id="b7bbc-103">Określa, że aplikacja obsługuje tylko wersję 1.0 środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="b7bbc-103">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="b7bbc-104">Ten element jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="b7bbc-104">This element is deprecated and should no longer be used.</span></span> <span data-ttu-id="b7bbc-105">[ `supportedRuntime` ](supportedruntime-element.md) Zamiast tego należy użyć elementu.</span><span class="sxs-lookup"><span data-stu-id="b7bbc-105">The [`supportedRuntime`](supportedruntime-element.md) element should be used instead.</span></span>
  
 <span data-ttu-id="b7bbc-106">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="b7bbc-106">\<configuration></span></span>  
<span data-ttu-id="b7bbc-107">\<startup></span><span class="sxs-lookup"><span data-stu-id="b7bbc-107">\<startup></span></span>  
<span data-ttu-id="b7bbc-108">\<requiredRuntime ></span><span class="sxs-lookup"><span data-stu-id="b7bbc-108">\<requiredRuntime></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7bbc-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="b7bbc-109">Syntax</span></span>  
  
```xml  
   <requiredRuntime    
version="runtime version"  
safemode="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b7bbc-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b7bbc-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b7bbc-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b7bbc-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b7bbc-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b7bbc-112">Attributes</span></span>  
  
|<span data-ttu-id="b7bbc-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b7bbc-113">Attribute</span></span>|<span data-ttu-id="b7bbc-114">Opis</span><span class="sxs-lookup"><span data-stu-id="b7bbc-114">Description</span></span>|  
|---------------|-----------------|  
|`version`|<span data-ttu-id="b7bbc-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="b7bbc-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="b7bbc-116">Wartość ciągu określająca wersję programu .NET Framework, którą obsługuje ta aplikacja.</span><span class="sxs-lookup"><span data-stu-id="b7bbc-116">A string value that specifies the version of the .NET Framework that this application supports.</span></span> <span data-ttu-id="b7bbc-117">Wartość ciągu musi odpowiadać nazwa katalogu znajdują się w katalogu głównym instalacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b7bbc-117">The string value must match the directory name found under the .NET Framework installation root.</span></span> <span data-ttu-id="b7bbc-118">Zawartość wartości ciągu nie są analizowane.</span><span class="sxs-lookup"><span data-stu-id="b7bbc-118">The contents of the string value are not parsed.</span></span>|  
|`safemode`|<span data-ttu-id="b7bbc-119">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="b7bbc-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="b7bbc-120">Określa, czy kod uruchamiający środowisko uruchomieniowe wyszukuje rejestr w celu ustalenia wersji środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="b7bbc-120">Specifies whether the runtime startup code searches the registry to determine the runtime version.</span></span>|  
  
## <a name="safemode-attribute"></a><span data-ttu-id="b7bbc-121">safemode — atrybut</span><span class="sxs-lookup"><span data-stu-id="b7bbc-121">safemode Attribute</span></span>  
  
|<span data-ttu-id="b7bbc-122">Wartość</span><span class="sxs-lookup"><span data-stu-id="b7bbc-122">Value</span></span>|<span data-ttu-id="b7bbc-123">Opis</span><span class="sxs-lookup"><span data-stu-id="b7bbc-123">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="b7bbc-124">Kod uruchamiający środowisko uruchomieniowe wyszukuje w rejestrze.</span><span class="sxs-lookup"><span data-stu-id="b7bbc-124">The runtime startup code looks in the registry.</span></span> <span data-ttu-id="b7bbc-125">Jest to wartość domyślna.</span><span class="sxs-lookup"><span data-stu-id="b7bbc-125">This is the default value.</span></span>|  
|`true`|<span data-ttu-id="b7bbc-126">Kod startowy środowiska uruchomieniowego nie znajduje się w rejestrze.</span><span class="sxs-lookup"><span data-stu-id="b7bbc-126">The runtime startup code does not look in the registry.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b7bbc-127">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b7bbc-127">Child Elements</span></span>  
 <span data-ttu-id="b7bbc-128">Brak.</span><span class="sxs-lookup"><span data-stu-id="b7bbc-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b7bbc-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b7bbc-129">Parent Elements</span></span>  
  
|<span data-ttu-id="b7bbc-130">Element</span><span class="sxs-lookup"><span data-stu-id="b7bbc-130">Element</span></span>|<span data-ttu-id="b7bbc-131">Opis</span><span class="sxs-lookup"><span data-stu-id="b7bbc-131">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b7bbc-132">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b7bbc-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`startup`|<span data-ttu-id="b7bbc-133">Zawiera `<requiredRuntime>` elementu.</span><span class="sxs-lookup"><span data-stu-id="b7bbc-133">Contains the `<requiredRuntime>` element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7bbc-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b7bbc-134">Remarks</span></span>  
 <span data-ttu-id="b7bbc-135">Aplikacje stworzone z myślą o obsługiwały tylko wersję 1.0 środowiska uruchomieniowego muszą używać `<requiredRuntime>` elementu.</span><span class="sxs-lookup"><span data-stu-id="b7bbc-135">Applications built to support only version 1.0 of the runtime must use the `<requiredRuntime>` element.</span></span> <span data-ttu-id="b7bbc-136">Aplikacje utworzone przy użyciu wersji 1.1 lub nowszej środowiska uruchomieniowego muszą używać `<supportedRuntime>` elementu.</span><span class="sxs-lookup"><span data-stu-id="b7bbc-136">Applications built using version 1.1 or later of the runtime must use the `<supportedRuntime>` element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b7bbc-137">Jeśli używasz [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md) funkcji, aby określić plik konfiguracji, należy użyć `<requiredRuntime>` elementu dla wszystkich wersji środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="b7bbc-137">If you use the [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md) function to specify the configuration file, you must use the `<requiredRuntime>` element for all versions of the runtime.</span></span> <span data-ttu-id="b7bbc-138">`<supportedRuntime>` Element jest ignorowany, gdy używasz [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span><span class="sxs-lookup"><span data-stu-id="b7bbc-138">The `<supportedRuntime>` element is ignored when you use [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span></span>  
  
 <span data-ttu-id="b7bbc-139">`version` Ciągu atrybutu musi odpowiadać nazwie folder instalacji dla określonej wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b7bbc-139">The `version` attribute string must match the installation folder name for the specified version of the .NET Framework.</span></span> <span data-ttu-id="b7bbc-140">Ten ciąg nie jest interpretowany.</span><span class="sxs-lookup"><span data-stu-id="b7bbc-140">This string is not interpreted.</span></span> <span data-ttu-id="b7bbc-141">Jeśli kod startowy środowiska uruchomieniowego nie znajdzie folderem dopasowania, środowisko uruchomieniowe nie jest załadowany; kod startowy pokazuje komunikat o błędzie i kończy działanie.</span><span class="sxs-lookup"><span data-stu-id="b7bbc-141">If the runtime startup code does not find a matching folder, the runtime is not loaded; the startup code shows an error message and quits.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b7bbc-142">Ignoruje kodu startowego dla aplikacji, która jest obsługiwana w programie Internet Explorer `<requiredRuntime>` elementu.</span><span class="sxs-lookup"><span data-stu-id="b7bbc-142">The startup code for an application that is hosted in Microsoft Internet Explorer ignores the `<requiredRuntime>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7bbc-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="b7bbc-143">Example</span></span>  
 <span data-ttu-id="b7bbc-144">Poniższy przykład pokazuje, jak określić wersji środowiska uruchomieniowego w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b7bbc-144">The following example shows how to specify the runtime version in a configuration file.</span></span>  
  
```xml  
<configuration>  
   <startup>  
      <requiredRuntime version="v1.0.3705" safemode="true"/>  
   </startup>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b7bbc-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b7bbc-145">See Also</span></span>  
 [<span data-ttu-id="b7bbc-146">Schemat ustawień uruchamiania</span><span class="sxs-lookup"><span data-stu-id="b7bbc-146">Startup Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/index.md)  
 [<span data-ttu-id="b7bbc-147">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b7bbc-147">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="b7bbc-148">\<PaveOver > Określanie wersji środowiska uruchomieniowego, które ma być używana</span><span class="sxs-lookup"><span data-stu-id="b7bbc-148">\<PaveOver> Specifying Which Runtime Version to Use</span></span>](https://msdn.microsoft.com/library/c376208d-980d-42b4-865b-fbe0d9cc97c2)
