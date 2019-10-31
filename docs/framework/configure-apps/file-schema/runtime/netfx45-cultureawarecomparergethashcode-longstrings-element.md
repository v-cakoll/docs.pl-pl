---
title: <NetFx45_CultureAwareComparerGetHashCode_LongStrings>, element
ms.date: 03/30/2017
helpviewer_keywords:
- NetFx45_CultureAwareComparerGetHashCode_LongStrings element
- <NetFx45_CultureAwareComparerGetHashCode_LongStrings> element
- GetHashCode method
- hash codes, calculating
ms.assetid: 3a5f38d1-ebc8-44de-aaeb-2929f6e6b48f
ms.openlocfilehash: 193f9a15768e4060d977063117c07558bbb1d766
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116127"
---
# <a name="netfx45_cultureawarecomparergethashcode_longstrings-element"></a><span data-ttu-id="ba170-102">\<element > NetFx45_CultureAwareComparerGetHashCode_LongStrings</span><span class="sxs-lookup"><span data-stu-id="ba170-102">\<NetFx45_CultureAwareComparerGetHashCode_LongStrings> Element</span></span>

<span data-ttu-id="ba170-103">Określa, czy środowisko uruchomieniowe używa stałej ilości pamięci do obliczenia kodów skrótów dla metody <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ba170-103">Specifies whether the runtime uses a fixed amount of memory to calculate hash codes for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="ba170-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="ba170-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ba170-105">&nbsp;&nbsp;[ **\<środowiska uruchomieniowego >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="ba170-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="ba170-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<NetFx45_CultureAwareComparerGetHashCode_LongStrings >**</span><span class="sxs-lookup"><span data-stu-id="ba170-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<NetFx45_CultureAwareComparerGetHashCode_LongStrings>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="ba170-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="ba170-107">Syntax</span></span>

```xml
<NetFx45_CultureAwareComparerGetHashCode_LongStrings enabled="0|1">
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ba170-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ba170-108">Attributes and Elements</span></span>

<span data-ttu-id="ba170-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ba170-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ba170-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ba170-110">Attributes</span></span>

|<span data-ttu-id="ba170-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ba170-111">Attribute</span></span>|<span data-ttu-id="ba170-112">Opis</span><span class="sxs-lookup"><span data-stu-id="ba170-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="ba170-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="ba170-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="ba170-114">Określa, czy środowisko uruchomieniowe języka wspólnego przydziela stałą ilość pamięci podczas obliczania kodów wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="ba170-114">Specifies whether the common language runtime allocates a fixed amount of memory when calculating hash codes.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="ba170-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="ba170-115">enabled Attribute</span></span>

|<span data-ttu-id="ba170-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="ba170-116">Value</span></span>|<span data-ttu-id="ba170-117">Opis</span><span class="sxs-lookup"><span data-stu-id="ba170-117">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="ba170-118">0</span><span class="sxs-lookup"><span data-stu-id="ba170-118">0</span></span>|<span data-ttu-id="ba170-119">Środowisko uruchomieniowe języka wspólnego przydziela zmienną ilość pamięci dla metody <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>, aby obliczyć kody skrótów.</span><span class="sxs-lookup"><span data-stu-id="ba170-119">The common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span> <span data-ttu-id="ba170-120">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="ba170-120">This is the default.</span></span>|
|<span data-ttu-id="ba170-121">1</span><span class="sxs-lookup"><span data-stu-id="ba170-121">1</span></span>|<span data-ttu-id="ba170-122">Środowisko uruchomieniowe języka wspólnego przydziela stałą ilość pamięci dla metody <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>, aby obliczyć kody skrótów.</span><span class="sxs-lookup"><span data-stu-id="ba170-122">The common language runtime allocates a fixed amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="ba170-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ba170-123">Child Elements</span></span>

<span data-ttu-id="ba170-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="ba170-124">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ba170-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ba170-125">Parent Elements</span></span>

|<span data-ttu-id="ba170-126">Element</span><span class="sxs-lookup"><span data-stu-id="ba170-126">Element</span></span>|<span data-ttu-id="ba170-127">Opis</span><span class="sxs-lookup"><span data-stu-id="ba170-127">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="ba170-128">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ba170-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="ba170-129">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="ba170-129">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ba170-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ba170-130">Remarks</span></span>

<span data-ttu-id="ba170-131">Domyślnie środowisko uruchomieniowe języka wspólnego przydziela zmienną ilość pamięci dla metody <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> i <xref:System.ArgumentException> może być zgłaszane, gdy metoda próbuje obliczyć kod skrótu bardzo dużych ciągów (ponad kilka milionów znaków).</span><span class="sxs-lookup"><span data-stu-id="ba170-131">By default, the common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method, and an <xref:System.ArgumentException> can be thrown when the method attempts to compute the hash code of very large strings (over several million characters long).</span></span> <span data-ttu-id="ba170-132">Dodając ten element do pliku konfiguracji aplikacji i ustawiając jego atrybut `enabled` na wartość "1", można określić, że metoda <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> użyć alternatywnego algorytmu, który przydziela stałą ilość pamięci do obliczeń kodów skrótów.</span><span class="sxs-lookup"><span data-stu-id="ba170-132">By adding this element to an application configuration file and setting its `enabled` attribute to "1", you can specify that the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method use an alternate algorithm that allocates a fixed amount of memory for the computation of hash codes.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ba170-133">Element `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` nie jest używany w [!INCLUDE[win8](../../../../../includes/win8-md.md)] i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="ba170-133">The `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` element is not used in [!INCLUDE[win8](../../../../../includes/win8-md.md)] and later versions.</span></span>

## <a name="see-also"></a><span data-ttu-id="ba170-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ba170-134">See also</span></span>

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- [<span data-ttu-id="ba170-135">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="ba170-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ba170-136">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ba170-136">Configuration File Schema</span></span>](../index.md)
