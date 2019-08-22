---
title: <etwEnable>, element
ms.date: 03/30/2017
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f24e9a06137744dbc97d5f34cda7ad6eab873700
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663740"
---
# <a name="etwenable-element"></a><span data-ttu-id="ae96c-102">\<etwEnable, element ></span><span class="sxs-lookup"><span data-stu-id="ae96c-102">\<etwEnable> Element</span></span>
<span data-ttu-id="ae96c-103">Określa, czy włączyć śledzenie zdarzeń systemu Windows (ETW) dla zdarzeń środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="ae96c-103">Specifies whether to enable event tracing for Windows (ETW) for common language runtime events.</span></span>  
  
 <span data-ttu-id="ae96c-104">\<> elementu konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ae96c-104">\<configuration> Element</span></span>  
<span data-ttu-id="ae96c-105">\<Element > środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="ae96c-105">\<runtime> Element</span></span>  
<span data-ttu-id="ae96c-106">\<etwEnabled ></span><span class="sxs-lookup"><span data-stu-id="ae96c-106">\<etwEnabled></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae96c-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="ae96c-107">Syntax</span></span>  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ae96c-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ae96c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ae96c-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ae96c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ae96c-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ae96c-110">Attributes</span></span>  
  
|<span data-ttu-id="ae96c-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ae96c-111">Attribute</span></span>|<span data-ttu-id="ae96c-112">Opis</span><span class="sxs-lookup"><span data-stu-id="ae96c-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ae96c-113">dostępny</span><span class="sxs-lookup"><span data-stu-id="ae96c-113">enabled</span></span>|<span data-ttu-id="ae96c-114">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="ae96c-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="ae96c-115">Określa, czy funkcja ETW powinna być włączona.</span><span class="sxs-lookup"><span data-stu-id="ae96c-115">Specifies whether ETW should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="ae96c-116">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="ae96c-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="ae96c-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="ae96c-117">Value</span></span>|<span data-ttu-id="ae96c-118">Opis</span><span class="sxs-lookup"><span data-stu-id="ae96c-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ae96c-119">true</span><span class="sxs-lookup"><span data-stu-id="ae96c-119">true</span></span>|<span data-ttu-id="ae96c-120">Włącz funkcję ETW.</span><span class="sxs-lookup"><span data-stu-id="ae96c-120">Enable ETW.</span></span> <span data-ttu-id="ae96c-121">Jest to wartość domyślna dla wersji systemu Windows, począwszy od systemów operacyjnych Windows Vista i Windows Server 2008.</span><span class="sxs-lookup"><span data-stu-id="ae96c-121">This is the default for versions of Windows beginning with the Windows Vista and Windows Server 2008 operating systems.</span></span>|  
|<span data-ttu-id="ae96c-122">false</span><span class="sxs-lookup"><span data-stu-id="ae96c-122">false</span></span>|<span data-ttu-id="ae96c-123">Wyłącz funkcję ETW.</span><span class="sxs-lookup"><span data-stu-id="ae96c-123">Disable ETW.</span></span> <span data-ttu-id="ae96c-124">Jest to wartość domyślna dla wcześniejszych wersji systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ae96c-124">This is the default for earlier versions of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ae96c-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ae96c-125">Child Elements</span></span>  
 <span data-ttu-id="ae96c-126">Brak.</span><span class="sxs-lookup"><span data-stu-id="ae96c-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ae96c-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ae96c-127">Parent Elements</span></span>  
  
|<span data-ttu-id="ae96c-128">Element</span><span class="sxs-lookup"><span data-stu-id="ae96c-128">Element</span></span>|<span data-ttu-id="ae96c-129">Opis</span><span class="sxs-lookup"><span data-stu-id="ae96c-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ae96c-130">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ae96c-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ae96c-131">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="ae96c-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae96c-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ae96c-132">Remarks</span></span>  
 <span data-ttu-id="ae96c-133">Począwszy od systemu Windows Vista, funkcja ETW jest domyślnie włączona.</span><span class="sxs-lookup"><span data-stu-id="ae96c-133">Beginning with Windows Vista, ETW is enabled by default.</span></span> <span data-ttu-id="ae96c-134">Użyj tego elementu, aby wyłączyć funkcję ETW dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ae96c-134">Use this element to disable ETW for an application.</span></span> <span data-ttu-id="ae96c-135">We wcześniejszych wersjach systemu Windows Użyj tego elementu, aby włączyć funkcję ETW dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ae96c-135">In earlier versions of Windows, use this element to enable ETW for an application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ae96c-136">Funkcję ETW można włączyć lub wyłączyć globalnie na serwerze przy użyciu ustawienia rejestru.</span><span class="sxs-lookup"><span data-stu-id="ae96c-136">ETW can be enabled or disabled globally on a server by using a registry setting.</span></span> <span data-ttu-id="ae96c-137">Zobacz [kontrolowanie rejestrowania .NET Framework](../../../performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="ae96c-137">See [Controlling .NET Framework Logging](../../../performance/controlling-logging.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae96c-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="ae96c-138">Example</span></span>  
 <span data-ttu-id="ae96c-139">Poniższy przykład pokazuje, jak włączyć śledzenie ETW dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ae96c-139">The following example shows how to enable ETW tracing for an application.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ae96c-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ae96c-140">See also</span></span>

- [<span data-ttu-id="ae96c-141">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="ae96c-141">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ae96c-142">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ae96c-142">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="ae96c-143">Kontrolowanie logowania w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ae96c-143">Controlling .NET Framework Logging</span></span>](../../../performance/controlling-logging.md)
