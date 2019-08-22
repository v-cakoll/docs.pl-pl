---
title: <TimeSpan_LegacyFormatMode> Element
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <TimeSpan_LegacyFormatMode> element
- TimeSpan_LegacyFormatMode element
ms.assetid: 865e7207-d050-4442-b574-57ea29d5e2d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2bd74460c7d5d077686c723936d140b07ac21dd0
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663394"
---
# <a name="timespan_legacyformatmode-element"></a><span data-ttu-id="fea59-102">\<TimeSpan_LegacyFormatMode> Element</span><span class="sxs-lookup"><span data-stu-id="fea59-102">\<TimeSpan_LegacyFormatMode> Element</span></span>

<span data-ttu-id="fea59-103">Określa, czy środowisko uruchomieniowe zachowuje starsze zachowanie w operacjach <xref:System.TimeSpan?displayProperty=nameWithType> formatowania z wartościami.</span><span class="sxs-lookup"><span data-stu-id="fea59-103">Determines whether the runtime preserves legacy behavior in formatting operations with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>

<span data-ttu-id="fea59-104">\<> konfiguracji </span><span class="sxs-lookup"><span data-stu-id="fea59-104">\<configuration></span></span>\
<span data-ttu-id="fea59-105">\<> środowiska uruchomieniowego </span><span class="sxs-lookup"><span data-stu-id="fea59-105">\<runtime></span></span>\
<span data-ttu-id="fea59-106">\<TimeSpan_LegacyFormatMode></span><span class="sxs-lookup"><span data-stu-id="fea59-106">\<TimeSpan_LegacyFormatMode></span></span>

## <a name="syntax"></a><span data-ttu-id="fea59-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="fea59-107">Syntax</span></span>

```xml
<TimeSpan_LegacyFormatMode
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fea59-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fea59-108">Attributes and Elements</span></span>

<span data-ttu-id="fea59-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fea59-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="fea59-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fea59-110">Attributes</span></span>

|<span data-ttu-id="fea59-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="fea59-111">Attribute</span></span>|<span data-ttu-id="fea59-112">Opis</span><span class="sxs-lookup"><span data-stu-id="fea59-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="fea59-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="fea59-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="fea59-114">Określa, czy środowisko uruchomieniowe korzysta ze starszego zachowania formatowania z <xref:System.TimeSpan?displayProperty=nameWithType> wartościami.</span><span class="sxs-lookup"><span data-stu-id="fea59-114">Specifies whether the runtime uses legacy formatting behavior with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="fea59-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="fea59-115">enabled Attribute</span></span>

|<span data-ttu-id="fea59-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="fea59-116">Value</span></span>|<span data-ttu-id="fea59-117">Opis</span><span class="sxs-lookup"><span data-stu-id="fea59-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="fea59-118">Środowisko uruchomieniowe nie przywraca starszego zachowania formatowania.</span><span class="sxs-lookup"><span data-stu-id="fea59-118">The runtime does not restore legacy formatting behavior.</span></span>|
|`true`|<span data-ttu-id="fea59-119">Środowisko uruchomieniowe przywraca starsze zachowanie podczas formatowania.</span><span class="sxs-lookup"><span data-stu-id="fea59-119">The runtime restores legacy formatting behavior.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="fea59-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fea59-120">Child Elements</span></span>

<span data-ttu-id="fea59-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="fea59-121">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fea59-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fea59-122">Parent Elements</span></span>

|<span data-ttu-id="fea59-123">Element</span><span class="sxs-lookup"><span data-stu-id="fea59-123">Element</span></span>|<span data-ttu-id="fea59-124">Opis</span><span class="sxs-lookup"><span data-stu-id="fea59-124">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="fea59-125">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fea59-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="fea59-126">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="fea59-126">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="fea59-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fea59-127">Remarks</span></span>

<span data-ttu-id="fea59-128">Począwszy od .NET Framework 4, <xref:System.TimeSpan?displayProperty=nameWithType> struktura <xref:System.IFormattable> implementuje interfejs i obsługuje operacje formatowania przy użyciu standardowych i niestandardowych ciągów formatu.</span><span class="sxs-lookup"><span data-stu-id="fea59-128">Starting with the .NET Framework 4, the <xref:System.TimeSpan?displayProperty=nameWithType> structure implements the <xref:System.IFormattable> interface and supports formatting operations with standard and custom format strings.</span></span> <span data-ttu-id="fea59-129">Jeśli metoda analizy napotka nieobsługiwany specyfikator formatu lub ciąg formatu, zgłasza <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="fea59-129">If a parsing method encounters an unsupported format specifier or format string, it throws a <xref:System.FormatException>.</span></span>

<span data-ttu-id="fea59-130">W poprzednich wersjach .NET Framework <xref:System.TimeSpan> struktura nie została zaimplementowana <xref:System.IFormattable> i nie obsługuje ciągów formatu.</span><span class="sxs-lookup"><span data-stu-id="fea59-130">In previous versions of the .NET Framework, the <xref:System.TimeSpan> structure did not implement <xref:System.IFormattable> and did not support format strings.</span></span> <span data-ttu-id="fea59-131">Jednak w przypadku wielu programistów założono, że program <xref:System.TimeSpan> obsługiwał zestaw ciągów formatu i użył ich w [operacjach formatowania złożonego](../../../../../docs/standard/base-types/composite-formatting.md) z metodami takimi <xref:System.String.Format%2A?displayProperty=nameWithType>jak.</span><span class="sxs-lookup"><span data-stu-id="fea59-131">However, many developers mistakenly assumed that <xref:System.TimeSpan> did support a set of format strings and used them in [composite formatting operations](../../../../../docs/standard/base-types/composite-formatting.md) with methods such as <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="fea59-132">Zwykle, jeśli typ implementuje <xref:System.IFormattable> i obsługuje ciągi formatowania, wywołania metod formatowania z nieobsługiwanymi ciągami formatu zwykle <xref:System.FormatException>generują.</span><span class="sxs-lookup"><span data-stu-id="fea59-132">Ordinarily, if a type implements <xref:System.IFormattable> and supports format strings, calls to formatting methods with unsupported format strings usually throw a <xref:System.FormatException>.</span></span> <span data-ttu-id="fea59-133">Jednak ponieważ <xref:System.TimeSpan> nie została zaimplementowana <xref:System.IFormattable>, środowisko uruchomieniowe zignorował <xref:System.TimeSpan.ToString?displayProperty=nameWithType> ciąg formatu i zamiast niego nazywa metodę.</span><span class="sxs-lookup"><span data-stu-id="fea59-133">However, because <xref:System.TimeSpan> did not implement <xref:System.IFormattable>, the runtime ignored the format string and instead called the <xref:System.TimeSpan.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="fea59-134">Oznacza to, że chociaż ciągi formatu nie miały wpływu na operację formatowania, ich obecność nie spowodowało <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="fea59-134">This means that, although the format strings had no effect on the formatting operation, their presence did not result in a <xref:System.FormatException>.</span></span>

<span data-ttu-id="fea59-135">W przypadkach, w których starszy kod przekazuje metodę formatowania złożonego i nieprawidłowy ciąg formatu, a ten kod nie może zostać ponownie skompilowany, można użyć `<TimeSpan_LegacyFormatMode>` elementu, aby przywrócić starsze <xref:System.TimeSpan> zachowanie.</span><span class="sxs-lookup"><span data-stu-id="fea59-135">For cases in which legacy code passes a composite formatting method and an invalid format string, and that code cannot be recompiled, you can use the `<TimeSpan_LegacyFormatMode>` element to restore the legacy <xref:System.TimeSpan> behavior.</span></span> <span data-ttu-id="fea59-136">Po `enabled` ustawieniu atrybutu tego elementu na `true`, Metoda formatowania złożonego <xref:System.TimeSpan.ToString?displayProperty=nameWithType> powoduje wywołanie zamiast <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>i <xref:System.FormatException> nie jest generowane.</span><span class="sxs-lookup"><span data-stu-id="fea59-136">When you set the `enabled` attribute of this element to `true`, the composite formatting method results in a call to <xref:System.TimeSpan.ToString?displayProperty=nameWithType> rather than <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, and a <xref:System.FormatException> is not thrown.</span></span>

## <a name="example"></a><span data-ttu-id="fea59-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="fea59-137">Example</span></span>

<span data-ttu-id="fea59-138">Poniższy przykład tworzy wystąpienie <xref:System.TimeSpan> obiektu i próbuje sformatować go <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> za pomocą metody przy użyciu nieobsługiwanego ciągu formatu standardowego.</span><span class="sxs-lookup"><span data-stu-id="fea59-138">The following example instantiates a <xref:System.TimeSpan> object and attempts to format it with the <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> method by using an unsupported standard format string.</span></span>

[!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
[!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]

<span data-ttu-id="fea59-139">Po uruchomieniu przykładu w .NET Framework 3,5 lub we wcześniejszej wersji zostaną wyświetlone następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="fea59-139">When you run the example on the .NET Framework 3.5 or on an earlier version, it displays the following output:</span></span>

```
12:30:45
```

<span data-ttu-id="fea59-140">Różni się to od danych wyjściowych w przypadku uruchomienia przykładu w .NET Framework 4 lub jego nowszej wersji:</span><span class="sxs-lookup"><span data-stu-id="fea59-140">This differs markedly from the output if you run the example on the .NET Framework 4 or later version:</span></span>

```
Invalid Format
```

<span data-ttu-id="fea59-141">Jeśli jednak dodasz następujący plik konfiguracji do katalogu przykładu, a następnie uruchomisz przykład w .NET Framework 4 lub nowszej wersji, dane wyjściowe są identyczne z tym, które zostały utworzone przez przykład w przypadku uruchomienia na .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="fea59-141">However, if you add the following configuration file to the example's directory and then run the example on the .NET Framework 4 or later version, the output is identical to that produced by the example when it is run on .NET Framework 3.5.</span></span>

```xml
<?xml version ="1.0"?>
<configuration>
   <runtime>
      <TimeSpan_LegacyFormatMode enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="fea59-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fea59-142">See also</span></span>

- [<span data-ttu-id="fea59-143">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="fea59-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="fea59-144">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="fea59-144">Configuration File Schema</span></span>](../index.md)
