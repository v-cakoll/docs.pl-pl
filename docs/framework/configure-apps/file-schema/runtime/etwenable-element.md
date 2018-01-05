---
title: "&lt;etwenable —&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1d94d49fcb2c395de5172a730923dbe42f67cf35
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltetwenablegt-element"></a><span data-ttu-id="6d69b-102">&lt;etwenable —&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="6d69b-102">&lt;etwEnable&gt; Element</span></span>
<span data-ttu-id="6d69b-103">Określa, czy włączyć śledzenie zdarzeń systemu Windows (ETW) dla zdarzenia środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="6d69b-103">Specifies whether to enable event tracing for Windows (ETW) for common language runtime events.</span></span>  
  
 <span data-ttu-id="6d69b-104">\<Konfiguracja > — Element</span><span class="sxs-lookup"><span data-stu-id="6d69b-104">\<configuration> Element</span></span>  
<span data-ttu-id="6d69b-105">\<środowisko uruchomieniowe > — Element</span><span class="sxs-lookup"><span data-stu-id="6d69b-105">\<runtime> Element</span></span>  
<span data-ttu-id="6d69b-106">\<etwEnabled ></span><span class="sxs-lookup"><span data-stu-id="6d69b-106">\<etwEnabled></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d69b-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="6d69b-107">Syntax</span></span>  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6d69b-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6d69b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="6d69b-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6d69b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6d69b-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6d69b-110">Attributes</span></span>  
  
|<span data-ttu-id="6d69b-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6d69b-111">Attribute</span></span>|<span data-ttu-id="6d69b-112">Opis</span><span class="sxs-lookup"><span data-stu-id="6d69b-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6d69b-113">włączone</span><span class="sxs-lookup"><span data-stu-id="6d69b-113">enabled</span></span>|<span data-ttu-id="6d69b-114">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="6d69b-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="6d69b-115">Określa, czy powinno być włączone ETW.</span><span class="sxs-lookup"><span data-stu-id="6d69b-115">Specifies whether ETW should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="6d69b-116">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="6d69b-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="6d69b-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="6d69b-117">Value</span></span>|<span data-ttu-id="6d69b-118">Opis</span><span class="sxs-lookup"><span data-stu-id="6d69b-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6d69b-119">true</span><span class="sxs-lookup"><span data-stu-id="6d69b-119">true</span></span>|<span data-ttu-id="6d69b-120">Włączanie funkcji ETW.</span><span class="sxs-lookup"><span data-stu-id="6d69b-120">Enable ETW.</span></span> <span data-ttu-id="6d69b-121">Jest to wartość domyślna dla wersji systemu Windows, począwszy od systemów operacyjnych Windows Vista i Windows Server 2008.</span><span class="sxs-lookup"><span data-stu-id="6d69b-121">This is the default for versions of Windows beginning with the Windows Vista and Windows Server 2008 operating systems.</span></span>|  
|<span data-ttu-id="6d69b-122">false</span><span class="sxs-lookup"><span data-stu-id="6d69b-122">false</span></span>|<span data-ttu-id="6d69b-123">Wyłączanie funkcji ETW.</span><span class="sxs-lookup"><span data-stu-id="6d69b-123">Disable ETW.</span></span> <span data-ttu-id="6d69b-124">Jest to wartość domyślna dla wcześniejszych wersji systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="6d69b-124">This is the default for earlier versions of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6d69b-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6d69b-125">Child Elements</span></span>  
 <span data-ttu-id="6d69b-126">Brak.</span><span class="sxs-lookup"><span data-stu-id="6d69b-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6d69b-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6d69b-127">Parent Elements</span></span>  
  
|<span data-ttu-id="6d69b-128">Element</span><span class="sxs-lookup"><span data-stu-id="6d69b-128">Element</span></span>|<span data-ttu-id="6d69b-129">Opis</span><span class="sxs-lookup"><span data-stu-id="6d69b-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6d69b-130">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6d69b-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="6d69b-131">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="6d69b-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d69b-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6d69b-132">Remarks</span></span>  
 <span data-ttu-id="6d69b-133">Począwszy od systemu Windows Vista, ETW jest domyślnie włączona.</span><span class="sxs-lookup"><span data-stu-id="6d69b-133">Beginning with Windows Vista, ETW is enabled by default.</span></span> <span data-ttu-id="6d69b-134">Ten element służy do wyłączenia funkcji ETW dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6d69b-134">Use this element to disable ETW for an application.</span></span> <span data-ttu-id="6d69b-135">We wcześniejszych wersjach systemu Windows użyj tego elementu, aby włączyć ETW dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6d69b-135">In earlier versions of Windows, use this element to enable ETW for an application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6d69b-136">ETW można włączać lub globalnie wyłączone na serwerze za pomocą ustawienia rejestru.</span><span class="sxs-lookup"><span data-stu-id="6d69b-136">ETW can be enabled or disabled globally on a server by using a registry setting.</span></span> <span data-ttu-id="6d69b-137">Zobacz [kontrolowanie .NET Framework rejestrowania](../../../../../docs/framework/performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="6d69b-137">See [Controlling .NET Framework Logging](../../../../../docs/framework/performance/controlling-logging.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d69b-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="6d69b-138">Example</span></span>  
 <span data-ttu-id="6d69b-139">Poniższy przykład pokazuje, jak włączyć śledzenie zdarzeń systemu Windows dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6d69b-139">The following example shows how to enable ETW tracing for an application.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6d69b-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6d69b-140">See Also</span></span>  
 [<span data-ttu-id="6d69b-141">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="6d69b-141">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="6d69b-142">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6d69b-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="6d69b-143">Kontrolowanie logowania w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6d69b-143">Controlling .NET Framework Logging</span></span>](../../../../../docs/framework/performance/controlling-logging.md)
