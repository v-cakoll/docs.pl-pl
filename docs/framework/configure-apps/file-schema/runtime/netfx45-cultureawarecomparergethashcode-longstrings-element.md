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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674050"
---
# <a name="netfx45cultureawarecomparergethashcodelongstrings-element"></a><span data-ttu-id="a216b-102">\<NetFx45_CultureAwareComparerGetHashCode_LongStrings> Element</span><span class="sxs-lookup"><span data-stu-id="a216b-102">\<NetFx45_CultureAwareComparerGetHashCode_LongStrings> Element</span></span>
<span data-ttu-id="a216b-103">Określa, czy środowisko uruchomieniowe używa stałej ilości pamięci do obliczania kodów wartości skrótu dla <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="a216b-103">Specifies whether the runtime uses a fixed amount of memory to calculate hash codes for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="a216b-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="a216b-104">\<configuration></span></span>  
<span data-ttu-id="a216b-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="a216b-105">\<runtime></span></span>  
<span data-ttu-id="a216b-106"><NetFx45_CultureAwareComparerGetHashCode_LongStrings></span><span class="sxs-lookup"><span data-stu-id="a216b-106"><NetFx45_CultureAwareComparerGetHashCode_LongStrings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a216b-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="a216b-107">Syntax</span></span>  
  
```xml
<NetFx45_CultureAwareComparerGetHashCode_LongStrings enabled="0|1">  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a216b-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a216b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a216b-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a216b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a216b-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a216b-110">Attributes</span></span>  
  
|<span data-ttu-id="a216b-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a216b-111">Attribute</span></span>|<span data-ttu-id="a216b-112">Opis</span><span class="sxs-lookup"><span data-stu-id="a216b-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="a216b-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="a216b-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="a216b-114">Określa, czy środowisko uruchomieniowe języka wspólnego przydziela stałą ilość pamięci podczas obliczania kodów wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="a216b-114">Specifies whether the common language runtime allocates a fixed amount of memory when calculating hash codes.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="a216b-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="a216b-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="a216b-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="a216b-116">Value</span></span>|<span data-ttu-id="a216b-117">Opis</span><span class="sxs-lookup"><span data-stu-id="a216b-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a216b-118">0</span><span class="sxs-lookup"><span data-stu-id="a216b-118">0</span></span>|<span data-ttu-id="a216b-119">Środowisko uruchomieniowe języka wspólnego przydziela zmienną ilość pamięci dla <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metodę obliczania kodów wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="a216b-119">The common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span> <span data-ttu-id="a216b-120">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="a216b-120">This is the default.</span></span>|  
|<span data-ttu-id="a216b-121">1</span><span class="sxs-lookup"><span data-stu-id="a216b-121">1</span></span>|<span data-ttu-id="a216b-122">Środowisko uruchomieniowe języka wspólnego przydziela stałą ilość pamięci dla <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metodę obliczania kodów wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="a216b-122">The common language runtime allocates a fixed amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a216b-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a216b-123">Child Elements</span></span>  
 <span data-ttu-id="a216b-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="a216b-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a216b-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a216b-125">Parent Elements</span></span>  
  
|<span data-ttu-id="a216b-126">Element</span><span class="sxs-lookup"><span data-stu-id="a216b-126">Element</span></span>|<span data-ttu-id="a216b-127">Opis</span><span class="sxs-lookup"><span data-stu-id="a216b-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a216b-128">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a216b-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="a216b-129">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="a216b-129">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a216b-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a216b-130">Remarks</span></span>  
 <span data-ttu-id="a216b-131">Domyślnie środowisko uruchomieniowe języka wspólnego przydziela zmienną ilość pamięci dla <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metody i <xref:System.ArgumentException> mogą być generowane, gdy metoda podejmuje próbę obliczenia kodu wartości skrótu bardzo dużych ciągów (za pośrednictwem kilka milionów znaków).</span><span class="sxs-lookup"><span data-stu-id="a216b-131">By default, the common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method, and an <xref:System.ArgumentException> can be thrown when the method attempts to compute the hash code of very large strings (over several million characters long).</span></span> <span data-ttu-id="a216b-132">Dodając ten element do pliku konfiguracji aplikacji i ustawienie jej `enabled` atrybut na wartość "1", można określić, że <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metoda używać alternatywnego algorytmu, który przydziela stałą ilość pamięci dla obliczania kodów wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="a216b-132">By adding this element to an application configuration file and setting its `enabled` attribute to "1", you can specify that the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method use an alternate algorithm that allocates a fixed amount of memory for the computation of hash codes.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a216b-133">`<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` Element nie jest używany w [!INCLUDE[win8](../../../../../includes/win8-md.md)] i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="a216b-133">The `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` element is not used in [!INCLUDE[win8](../../../../../includes/win8-md.md)] and later versions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a216b-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a216b-134">See also</span></span>

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- [<span data-ttu-id="a216b-135">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="a216b-135">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="a216b-136">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a216b-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
