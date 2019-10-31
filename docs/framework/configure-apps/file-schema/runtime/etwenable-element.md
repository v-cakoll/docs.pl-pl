---
title: <etwEnable> Element
ms.date: 03/30/2017
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
ms.openlocfilehash: 14cea171a4a25e148ea32f75a8ef09b83a4ec8ad
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73117398"
---
# <a name="etwenable-element"></a><span data-ttu-id="9b167-102">\<element > etwEnable</span><span class="sxs-lookup"><span data-stu-id="9b167-102">\<etwEnable> Element</span></span>
<span data-ttu-id="9b167-103">Określa, czy włączyć śledzenie zdarzeń systemu Windows (ETW) dla zdarzeń środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="9b167-103">Specifies whether to enable event tracing for Windows (ETW) for common language runtime events.</span></span>  
  
<span data-ttu-id="9b167-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="9b167-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9b167-105">&nbsp;&nbsp;[ **\<środowiska uruchomieniowego >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="9b167-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="9b167-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<etwEnabled >**</span><span class="sxs-lookup"><span data-stu-id="9b167-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<etwEnabled>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b167-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="9b167-107">Syntax</span></span>  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9b167-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9b167-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9b167-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9b167-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9b167-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9b167-110">Attributes</span></span>  
  
|<span data-ttu-id="9b167-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9b167-111">Attribute</span></span>|<span data-ttu-id="9b167-112">Opis</span><span class="sxs-lookup"><span data-stu-id="9b167-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9b167-113">dostępny</span><span class="sxs-lookup"><span data-stu-id="9b167-113">enabled</span></span>|<span data-ttu-id="9b167-114">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="9b167-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="9b167-115">Określa, czy funkcja ETW powinna być włączona.</span><span class="sxs-lookup"><span data-stu-id="9b167-115">Specifies whether ETW should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="9b167-116">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="9b167-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="9b167-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="9b167-117">Value</span></span>|<span data-ttu-id="9b167-118">Opis</span><span class="sxs-lookup"><span data-stu-id="9b167-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9b167-119">true</span><span class="sxs-lookup"><span data-stu-id="9b167-119">true</span></span>|<span data-ttu-id="9b167-120">Włącz funkcję ETW.</span><span class="sxs-lookup"><span data-stu-id="9b167-120">Enable ETW.</span></span> <span data-ttu-id="9b167-121">Jest to wartość domyślna dla wersji systemu Windows, począwszy od systemów operacyjnych Windows Vista i Windows Server 2008.</span><span class="sxs-lookup"><span data-stu-id="9b167-121">This is the default for versions of Windows beginning with the Windows Vista and Windows Server 2008 operating systems.</span></span>|  
|<span data-ttu-id="9b167-122">false</span><span class="sxs-lookup"><span data-stu-id="9b167-122">false</span></span>|<span data-ttu-id="9b167-123">Wyłącz funkcję ETW.</span><span class="sxs-lookup"><span data-stu-id="9b167-123">Disable ETW.</span></span> <span data-ttu-id="9b167-124">Jest to wartość domyślna dla wcześniejszych wersji systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="9b167-124">This is the default for earlier versions of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9b167-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9b167-125">Child Elements</span></span>  
 <span data-ttu-id="9b167-126">Brak.</span><span class="sxs-lookup"><span data-stu-id="9b167-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9b167-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9b167-127">Parent Elements</span></span>  
  
|<span data-ttu-id="9b167-128">Element</span><span class="sxs-lookup"><span data-stu-id="9b167-128">Element</span></span>|<span data-ttu-id="9b167-129">Opis</span><span class="sxs-lookup"><span data-stu-id="9b167-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9b167-130">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9b167-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="9b167-131">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="9b167-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9b167-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9b167-132">Remarks</span></span>  
 <span data-ttu-id="9b167-133">Począwszy od systemu Windows Vista, funkcja ETW jest domyślnie włączona.</span><span class="sxs-lookup"><span data-stu-id="9b167-133">Beginning with Windows Vista, ETW is enabled by default.</span></span> <span data-ttu-id="9b167-134">Użyj tego elementu, aby wyłączyć funkcję ETW dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9b167-134">Use this element to disable ETW for an application.</span></span> <span data-ttu-id="9b167-135">We wcześniejszych wersjach systemu Windows Użyj tego elementu, aby włączyć funkcję ETW dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9b167-135">In earlier versions of Windows, use this element to enable ETW for an application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9b167-136">Funkcję ETW można włączyć lub wyłączyć globalnie na serwerze przy użyciu ustawienia rejestru.</span><span class="sxs-lookup"><span data-stu-id="9b167-136">ETW can be enabled or disabled globally on a server by using a registry setting.</span></span> <span data-ttu-id="9b167-137">Zobacz [kontrolowanie rejestrowania .NET Framework](../../../performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="9b167-137">See [Controlling .NET Framework Logging](../../../performance/controlling-logging.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b167-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="9b167-138">Example</span></span>  
 <span data-ttu-id="9b167-139">Poniższy przykład pokazuje, jak włączyć śledzenie ETW dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9b167-139">The following example shows how to enable ETW tracing for an application.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9b167-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9b167-140">See also</span></span>

- [<span data-ttu-id="9b167-141">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="9b167-141">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="9b167-142">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="9b167-142">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="9b167-143">Kontrolowanie logowania w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9b167-143">Controlling .NET Framework Logging</span></span>](../../../performance/controlling-logging.md)
