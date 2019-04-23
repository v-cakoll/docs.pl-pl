---
title: <NetFx45_CultureAwareComparerGetHashCode_LongStrings> Element
ms.date: 03/30/2017
helpviewer_keywords:
- NetFx45_CultureAwareComparerGetHashCode_LongStrings element
- <NetFx45_CultureAwareComparerGetHashCode_LongStrings> element
- GetHashCode method
- hash codes, calculating
ms.assetid: 3a5f38d1-ebc8-44de-aaeb-2929f6e6b48f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 854b58a1f57008326874b5e5ee60cc9e6297960b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59085912"
---
# <a name="netfx45cultureawarecomparergethashcodelongstrings-element"></a><span data-ttu-id="5c9ec-102">\<NetFx45_CultureAwareComparerGetHashCode_LongStrings> Element</span><span class="sxs-lookup"><span data-stu-id="5c9ec-102">\<NetFx45_CultureAwareComparerGetHashCode_LongStrings> Element</span></span>
<span data-ttu-id="5c9ec-103">Określa, czy środowisko uruchomieniowe używa stałej ilości pamięci do obliczania kodów wartości skrótu dla <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="5c9ec-103">Specifies whether the runtime uses a fixed amount of memory to calculate hash codes for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="5c9ec-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="5c9ec-104">\<configuration></span></span>  
<span data-ttu-id="5c9ec-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="5c9ec-105">\<runtime></span></span>  
<span data-ttu-id="5c9ec-106"><NetFx45_CultureAwareComparerGetHashCode_LongStrings></span><span class="sxs-lookup"><span data-stu-id="5c9ec-106"><NetFx45_CultureAwareComparerGetHashCode_LongStrings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c9ec-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="5c9ec-107">Syntax</span></span>  
  
```xml
<NetFx45_CultureAwareComparerGetHashCode_LongStrings enabled="0|1">  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5c9ec-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5c9ec-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5c9ec-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5c9ec-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5c9ec-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5c9ec-110">Attributes</span></span>  
  
|<span data-ttu-id="5c9ec-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5c9ec-111">Attribute</span></span>|<span data-ttu-id="5c9ec-112">Opis</span><span class="sxs-lookup"><span data-stu-id="5c9ec-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="5c9ec-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="5c9ec-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="5c9ec-114">Określa, czy środowisko uruchomieniowe języka wspólnego przydziela stałą ilość pamięci podczas obliczania kodów wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="5c9ec-114">Specifies whether the common language runtime allocates a fixed amount of memory when calculating hash codes.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="5c9ec-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="5c9ec-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="5c9ec-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="5c9ec-116">Value</span></span>|<span data-ttu-id="5c9ec-117">Opis</span><span class="sxs-lookup"><span data-stu-id="5c9ec-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5c9ec-118">0</span><span class="sxs-lookup"><span data-stu-id="5c9ec-118">0</span></span>|<span data-ttu-id="5c9ec-119">Środowisko uruchomieniowe języka wspólnego przydziela zmienną ilość pamięci dla <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metodę obliczania kodów wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="5c9ec-119">The common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span> <span data-ttu-id="5c9ec-120">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="5c9ec-120">This is the default.</span></span>|  
|<span data-ttu-id="5c9ec-121">1</span><span class="sxs-lookup"><span data-stu-id="5c9ec-121">1</span></span>|<span data-ttu-id="5c9ec-122">Środowisko uruchomieniowe języka wspólnego przydziela stałą ilość pamięci dla <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metodę obliczania kodów wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="5c9ec-122">The common language runtime allocates a fixed amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5c9ec-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5c9ec-123">Child Elements</span></span>  
 <span data-ttu-id="5c9ec-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="5c9ec-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5c9ec-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5c9ec-125">Parent Elements</span></span>  
  
|<span data-ttu-id="5c9ec-126">Element</span><span class="sxs-lookup"><span data-stu-id="5c9ec-126">Element</span></span>|<span data-ttu-id="5c9ec-127">Opis</span><span class="sxs-lookup"><span data-stu-id="5c9ec-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5c9ec-128">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5c9ec-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="5c9ec-129">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="5c9ec-129">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c9ec-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5c9ec-130">Remarks</span></span>  
 <span data-ttu-id="5c9ec-131">Domyślnie środowisko uruchomieniowe języka wspólnego przydziela zmienną ilość pamięci dla <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metody i <xref:System.ArgumentException> mogą być generowane, gdy metoda podejmuje próbę obliczenia kodu wartości skrótu bardzo dużych ciągów (za pośrednictwem kilka milionów znaków).</span><span class="sxs-lookup"><span data-stu-id="5c9ec-131">By default, the common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method, and an <xref:System.ArgumentException> can be thrown when the method attempts to compute the hash code of very large strings (over several million characters long).</span></span> <span data-ttu-id="5c9ec-132">Dodając ten element do pliku konfiguracji aplikacji i ustawienie jej `enabled` atrybut na wartość "1", można określić, że <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metoda używać alternatywnego algorytmu, który przydziela stałą ilość pamięci dla obliczania kodów wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="5c9ec-132">By adding this element to an application configuration file and setting its `enabled` attribute to "1", you can specify that the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method use an alternate algorithm that allocates a fixed amount of memory for the computation of hash codes.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5c9ec-133">`<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` Element nie jest używany w [!INCLUDE[win8](../../../../../includes/win8-md.md)] i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="5c9ec-133">The `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` element is not used in [!INCLUDE[win8](../../../../../includes/win8-md.md)] and later versions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c9ec-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5c9ec-134">See also</span></span>

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- [<span data-ttu-id="5c9ec-135">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="5c9ec-135">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="5c9ec-136">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="5c9ec-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
