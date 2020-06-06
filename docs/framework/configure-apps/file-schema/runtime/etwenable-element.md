---
title: <etwEnable> Element
ms.date: 03/30/2017
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
ms.openlocfilehash: 14cea171a4a25e148ea32f75a8ef09b83a4ec8ad
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73117398"
---
# <a name="etwenable-element"></a><span data-ttu-id="d056a-102">\<etwEnable> Element</span><span class="sxs-lookup"><span data-stu-id="d056a-102">\<etwEnable> Element</span></span>
<span data-ttu-id="d056a-103">Określa, czy włączyć śledzenie zdarzeń systemu Windows (ETW) dla zdarzeń środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="d056a-103">Specifies whether to enable event tracing for Windows (ETW) for common language runtime events.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<etwEnabled>**  
  
## <a name="syntax"></a><span data-ttu-id="d056a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d056a-104">Syntax</span></span>  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d056a-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d056a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="d056a-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d056a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d056a-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d056a-107">Attributes</span></span>  
  
|<span data-ttu-id="d056a-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d056a-108">Attribute</span></span>|<span data-ttu-id="d056a-109">Opis</span><span class="sxs-lookup"><span data-stu-id="d056a-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d056a-110">enabled</span><span class="sxs-lookup"><span data-stu-id="d056a-110">enabled</span></span>|<span data-ttu-id="d056a-111">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="d056a-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="d056a-112">Określa, czy funkcja ETW powinna być włączona.</span><span class="sxs-lookup"><span data-stu-id="d056a-112">Specifies whether ETW should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="d056a-113">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="d056a-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="d056a-114">Wartość</span><span class="sxs-lookup"><span data-stu-id="d056a-114">Value</span></span>|<span data-ttu-id="d056a-115">Opis</span><span class="sxs-lookup"><span data-stu-id="d056a-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d056a-116">true</span><span class="sxs-lookup"><span data-stu-id="d056a-116">true</span></span>|<span data-ttu-id="d056a-117">Włącz funkcję ETW.</span><span class="sxs-lookup"><span data-stu-id="d056a-117">Enable ETW.</span></span> <span data-ttu-id="d056a-118">Jest to wartość domyślna dla wersji systemu Windows, począwszy od systemów operacyjnych Windows Vista i Windows Server 2008.</span><span class="sxs-lookup"><span data-stu-id="d056a-118">This is the default for versions of Windows beginning with the Windows Vista and Windows Server 2008 operating systems.</span></span>|  
|<span data-ttu-id="d056a-119">fałsz</span><span class="sxs-lookup"><span data-stu-id="d056a-119">false</span></span>|<span data-ttu-id="d056a-120">Wyłącz funkcję ETW.</span><span class="sxs-lookup"><span data-stu-id="d056a-120">Disable ETW.</span></span> <span data-ttu-id="d056a-121">Jest to wartość domyślna dla wcześniejszych wersji systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="d056a-121">This is the default for earlier versions of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d056a-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d056a-122">Child Elements</span></span>  
 <span data-ttu-id="d056a-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="d056a-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d056a-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d056a-124">Parent Elements</span></span>  
  
|<span data-ttu-id="d056a-125">Element</span><span class="sxs-lookup"><span data-stu-id="d056a-125">Element</span></span>|<span data-ttu-id="d056a-126">Opis</span><span class="sxs-lookup"><span data-stu-id="d056a-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d056a-127">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d056a-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="d056a-128">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="d056a-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d056a-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d056a-129">Remarks</span></span>  
 <span data-ttu-id="d056a-130">Począwszy od systemu Windows Vista, funkcja ETW jest domyślnie włączona.</span><span class="sxs-lookup"><span data-stu-id="d056a-130">Beginning with Windows Vista, ETW is enabled by default.</span></span> <span data-ttu-id="d056a-131">Użyj tego elementu, aby wyłączyć funkcję ETW dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d056a-131">Use this element to disable ETW for an application.</span></span> <span data-ttu-id="d056a-132">We wcześniejszych wersjach systemu Windows Użyj tego elementu, aby włączyć funkcję ETW dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d056a-132">In earlier versions of Windows, use this element to enable ETW for an application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d056a-133">Funkcję ETW można włączyć lub wyłączyć globalnie na serwerze przy użyciu ustawienia rejestru.</span><span class="sxs-lookup"><span data-stu-id="d056a-133">ETW can be enabled or disabled globally on a server by using a registry setting.</span></span> <span data-ttu-id="d056a-134">Zobacz [kontrolowanie rejestrowania .NET Framework](../../../performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="d056a-134">See [Controlling .NET Framework Logging](../../../performance/controlling-logging.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d056a-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="d056a-135">Example</span></span>  
 <span data-ttu-id="d056a-136">Poniższy przykład pokazuje, jak włączyć śledzenie ETW dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d056a-136">The following example shows how to enable ETW tracing for an application.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d056a-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d056a-137">See also</span></span>

- [<span data-ttu-id="d056a-138">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="d056a-138">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="d056a-139">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="d056a-139">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="d056a-140">Kontrolowanie logowania w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d056a-140">Controlling .NET Framework Logging</span></span>](../../../performance/controlling-logging.md)
