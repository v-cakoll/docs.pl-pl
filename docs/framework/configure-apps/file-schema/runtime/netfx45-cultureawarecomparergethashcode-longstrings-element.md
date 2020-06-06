---
title: <NetFx45_CultureAwareComparerGetHashCode_LongStrings>, element
ms.date: 03/30/2017
helpviewer_keywords:
- NetFx45_CultureAwareComparerGetHashCode_LongStrings element
- <NetFx45_CultureAwareComparerGetHashCode_LongStrings> element
- GetHashCode method
- hash codes, calculating
ms.assetid: 3a5f38d1-ebc8-44de-aaeb-2929f6e6b48f
ms.openlocfilehash: 413eb6c6e61b509135601c65cf045eabd849e8b3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "74802112"
---
# <a name="netfx45_cultureawarecomparergethashcode_longstrings-element"></a><span data-ttu-id="a8230-102">\<NetFx45_CultureAwareComparerGetHashCode_LongStrings> Element</span><span class="sxs-lookup"><span data-stu-id="a8230-102">\<NetFx45_CultureAwareComparerGetHashCode_LongStrings> Element</span></span>

<span data-ttu-id="a8230-103">Określa, czy środowisko uruchomieniowe używa stałej ilości pamięci do obliczenia kodów skrótów dla <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="a8230-103">Specifies whether the runtime uses a fixed amount of memory to calculate hash codes for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<NetFx45_CultureAwareComparerGetHashCode_LongStrings>**  

## <a name="syntax"></a><span data-ttu-id="a8230-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a8230-104">Syntax</span></span>

```xml
<NetFx45_CultureAwareComparerGetHashCode_LongStrings enabled="0|1">
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a8230-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a8230-105">Attributes and Elements</span></span>

<span data-ttu-id="a8230-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a8230-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="a8230-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a8230-107">Attributes</span></span>

|<span data-ttu-id="a8230-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a8230-108">Attribute</span></span>|<span data-ttu-id="a8230-109">Opis</span><span class="sxs-lookup"><span data-stu-id="a8230-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="a8230-110">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="a8230-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="a8230-111">Określa, czy środowisko uruchomieniowe języka wspólnego przydziela stałą ilość pamięci podczas obliczania kodów wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="a8230-111">Specifies whether the common language runtime allocates a fixed amount of memory when calculating hash codes.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="a8230-112">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="a8230-112">enabled Attribute</span></span>

|<span data-ttu-id="a8230-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="a8230-113">Value</span></span>|<span data-ttu-id="a8230-114">Opis</span><span class="sxs-lookup"><span data-stu-id="a8230-114">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="a8230-115">0</span><span class="sxs-lookup"><span data-stu-id="a8230-115">0</span></span>|<span data-ttu-id="a8230-116">Środowisko uruchomieniowe języka wspólnego przydziela zmienną ilość pamięci dla <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metody do obliczania kodów skrótów.</span><span class="sxs-lookup"><span data-stu-id="a8230-116">The common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span> <span data-ttu-id="a8230-117">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="a8230-117">This is the default.</span></span>|
|<span data-ttu-id="a8230-118">1</span><span class="sxs-lookup"><span data-stu-id="a8230-118">1</span></span>|<span data-ttu-id="a8230-119">Środowisko uruchomieniowe języka wspólnego przydziela stałą ilość pamięci dla <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metody w celu obliczenia kodów skrótów.</span><span class="sxs-lookup"><span data-stu-id="a8230-119">The common language runtime allocates a fixed amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="a8230-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a8230-120">Child Elements</span></span>

<span data-ttu-id="a8230-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="a8230-121">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a8230-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a8230-122">Parent Elements</span></span>

|<span data-ttu-id="a8230-123">Element</span><span class="sxs-lookup"><span data-stu-id="a8230-123">Element</span></span>|<span data-ttu-id="a8230-124">Opis</span><span class="sxs-lookup"><span data-stu-id="a8230-124">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="a8230-125">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a8230-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="a8230-126">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="a8230-126">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a8230-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a8230-127">Remarks</span></span>

<span data-ttu-id="a8230-128">Domyślnie środowisko uruchomieniowe języka wspólnego przydziela zmienną ilość pamięci dla <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metody i <xref:System.ArgumentException> może zostać zgłoszone, gdy metoda próbuje obliczyć kod skrótu bardzo dużych ciągów (ponad kilka milionów znaków).</span><span class="sxs-lookup"><span data-stu-id="a8230-128">By default, the common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method, and an <xref:System.ArgumentException> can be thrown when the method attempts to compute the hash code of very large strings (over several million characters long).</span></span> <span data-ttu-id="a8230-129">Dodając ten element do pliku konfiguracji aplikacji i ustawiając jego `enabled` atrybut na wartość "1", można określić, że <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> Metoda użyje alternatywnego algorytmu, który przydziela stałą ilość pamięci do obliczeń kodów skrótów.</span><span class="sxs-lookup"><span data-stu-id="a8230-129">By adding this element to an application configuration file and setting its `enabled` attribute to "1", you can specify that the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method use an alternate algorithm that allocates a fixed amount of memory for the computation of hash codes.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a8230-130">`<NetFx45_CultureAwareComparerGetHashCode_LongStrings>`Element nie jest używany w systemie Windows 8 i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="a8230-130">The `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` element is not used in Windows 8 and later versions.</span></span>

## <a name="see-also"></a><span data-ttu-id="a8230-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a8230-131">See also</span></span>

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- [<span data-ttu-id="a8230-132">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="a8230-132">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a8230-133">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a8230-133">Configuration File Schema</span></span>](../index.md)
