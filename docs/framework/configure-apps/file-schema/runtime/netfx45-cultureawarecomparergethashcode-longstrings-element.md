---
title: "&lt;Netfx45_cultureawarecomparergethashcode_longstrings —&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- NetFx45_CultureAwareComparerGetHashCode_LongStrings element
- <NetFx45_CultureAwareComparerGetHashCode_LongStrings> element
- GetHashCode method
- hash codes, calculating
ms.assetid: 3a5f38d1-ebc8-44de-aaeb-2929f6e6b48f
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1c370bc9ea5f8c3cdbf8690c7e22788b1224f4df
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltnetfx45cultureawarecomparergethashcodelongstringsgt-element"></a><span data-ttu-id="ea34a-102">&lt;Netfx45_cultureawarecomparergethashcode_longstrings —&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="ea34a-102">&lt;NetFx45_CultureAwareComparerGetHashCode_LongStrings&gt; Element</span></span>
<span data-ttu-id="ea34a-103">Określa, czy środowisko uruchomieniowe używa stałej ilości pamięci do obliczania skrótu dla <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="ea34a-103">Specifies whether the runtime uses a fixed amount of memory to calculate hash codes for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="ea34a-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="ea34a-104">\<configuration></span></span>  
<span data-ttu-id="ea34a-105">\<Runtime ></span><span class="sxs-lookup"><span data-stu-id="ea34a-105">\<runtime></span></span>  
<span data-ttu-id="ea34a-106">< netfx45_cultureawarecomparergethashcode_longstrings — ></span><span class="sxs-lookup"><span data-stu-id="ea34a-106"><NetFx45_CultureAwareComparerGetHashCode_LongStrings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea34a-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="ea34a-107">Syntax</span></span>  
  
```xml
<NetFx45_CultureAwareComparerGetHashCode_LongStrings enabled="0|1">  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ea34a-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ea34a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ea34a-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ea34a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ea34a-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ea34a-110">Attributes</span></span>  
  
|<span data-ttu-id="ea34a-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ea34a-111">Attribute</span></span>|<span data-ttu-id="ea34a-112">Opis</span><span class="sxs-lookup"><span data-stu-id="ea34a-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="ea34a-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="ea34a-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="ea34a-114">Określa, czy środowisko uruchomieniowe języka wspólnego przydziela stałą ilość pamięci podczas obliczania kodów wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="ea34a-114">Specifies whether the common language runtime allocates a fixed amount of memory when calculating hash codes.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="ea34a-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="ea34a-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="ea34a-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="ea34a-116">Value</span></span>|<span data-ttu-id="ea34a-117">Opis</span><span class="sxs-lookup"><span data-stu-id="ea34a-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ea34a-118">0</span><span class="sxs-lookup"><span data-stu-id="ea34a-118">0</span></span>|<span data-ttu-id="ea34a-119">Środowisko uruchomieniowe języka wspólnego przydziela zmiennej ilość pamięci dla <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metodę obliczania skrótu.</span><span class="sxs-lookup"><span data-stu-id="ea34a-119">The common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span> <span data-ttu-id="ea34a-120">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="ea34a-120">This is the default.</span></span>|  
|<span data-ttu-id="ea34a-121">1</span><span class="sxs-lookup"><span data-stu-id="ea34a-121">1</span></span>|<span data-ttu-id="ea34a-122">Środowisko uruchomieniowe języka wspólnego przydziela stałej ilości pamięci dla <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metodę obliczania skrótu.</span><span class="sxs-lookup"><span data-stu-id="ea34a-122">The common language runtime allocates a fixed amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ea34a-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ea34a-123">Child Elements</span></span>  
 <span data-ttu-id="ea34a-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="ea34a-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ea34a-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ea34a-125">Parent Elements</span></span>  
  
|<span data-ttu-id="ea34a-126">Element</span><span class="sxs-lookup"><span data-stu-id="ea34a-126">Element</span></span>|<span data-ttu-id="ea34a-127">Opis</span><span class="sxs-lookup"><span data-stu-id="ea34a-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ea34a-128">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ea34a-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ea34a-129">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="ea34a-129">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ea34a-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ea34a-130">Remarks</span></span>  
 <span data-ttu-id="ea34a-131">Domyślnie środowisko uruchomieniowe języka wspólnego przydziela zmiennej ilość pamięci dla <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metody i <xref:System.ArgumentException> może zostać wygenerowany, gdy metoda próbuje Oblicz wartość skrótu ciągów bardzo duże (za pośrednictwem kilku milionów znaków).</span><span class="sxs-lookup"><span data-stu-id="ea34a-131">By default, the common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method, and an <xref:System.ArgumentException> can be thrown when the method attempts to compute the hash code of very large strings (over several million characters long).</span></span> <span data-ttu-id="ea34a-132">Dodając ten element do pliku konfiguracji aplikacji i ustawienie jej `enabled` atrybutu "1", można określić, że <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> — metoda przy użyciu alternatywnego algorytmu, który przydziela stałej ilości pamięci dla obliczania skrótu.</span><span class="sxs-lookup"><span data-stu-id="ea34a-132">By adding this element to an application configuration file and setting its `enabled` attribute to "1", you can specify that the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method use an alternate algorithm that allocates a fixed amount of memory for the computation of hash codes.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ea34a-133">`<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` Element nie jest używany w [!INCLUDE[win8](../../../../../includes/win8-md.md)] i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="ea34a-133">The `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` element is not used in [!INCLUDE[win8](../../../../../includes/win8-md.md)] and later versions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea34a-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ea34a-134">See Also</span></span>  
 <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="ea34a-135">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="ea34a-135">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="ea34a-136">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ea34a-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
