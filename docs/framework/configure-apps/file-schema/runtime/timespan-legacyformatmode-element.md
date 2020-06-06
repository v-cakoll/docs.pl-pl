---
title: <TimeSpan_LegacyFormatMode>, element
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <TimeSpan_LegacyFormatMode> element
- TimeSpan_LegacyFormatMode element
ms.assetid: 865e7207-d050-4442-b574-57ea29d5e2d6
ms.openlocfilehash: 9d9eedf52f5d711412e4549e39e6ea23abb68ff3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73968906"
---
# <a name="timespan_legacyformatmode-element"></a><span data-ttu-id="3f9dc-102">\<TimeSpan_LegacyFormatMode> Element</span><span class="sxs-lookup"><span data-stu-id="3f9dc-102">\<TimeSpan_LegacyFormatMode> Element</span></span>

<span data-ttu-id="3f9dc-103">Określa, czy środowisko uruchomieniowe zachowuje starsze zachowanie w operacjach formatowania z <xref:System.TimeSpan?displayProperty=nameWithType> wartościami.</span><span class="sxs-lookup"><span data-stu-id="3f9dc-103">Determines whether the runtime preserves legacy behavior in formatting operations with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<TimeSpan_LegacyFormatMode>**  

## <a name="syntax"></a><span data-ttu-id="3f9dc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3f9dc-104">Syntax</span></span>

```xml
<TimeSpan_LegacyFormatMode
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3f9dc-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3f9dc-105">Attributes and Elements</span></span>

<span data-ttu-id="3f9dc-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3f9dc-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="3f9dc-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3f9dc-107">Attributes</span></span>

|<span data-ttu-id="3f9dc-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3f9dc-108">Attribute</span></span>|<span data-ttu-id="3f9dc-109">Opis</span><span class="sxs-lookup"><span data-stu-id="3f9dc-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="3f9dc-110">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="3f9dc-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="3f9dc-111">Określa, czy środowisko uruchomieniowe korzysta ze starszego zachowania formatowania z <xref:System.TimeSpan?displayProperty=nameWithType> wartościami.</span><span class="sxs-lookup"><span data-stu-id="3f9dc-111">Specifies whether the runtime uses legacy formatting behavior with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="3f9dc-112">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="3f9dc-112">enabled Attribute</span></span>

|<span data-ttu-id="3f9dc-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="3f9dc-113">Value</span></span>|<span data-ttu-id="3f9dc-114">Opis</span><span class="sxs-lookup"><span data-stu-id="3f9dc-114">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="3f9dc-115">Środowisko uruchomieniowe nie przywraca starszego zachowania formatowania.</span><span class="sxs-lookup"><span data-stu-id="3f9dc-115">The runtime does not restore legacy formatting behavior.</span></span>|
|`true`|<span data-ttu-id="3f9dc-116">Środowisko uruchomieniowe przywraca starsze zachowanie podczas formatowania.</span><span class="sxs-lookup"><span data-stu-id="3f9dc-116">The runtime restores legacy formatting behavior.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="3f9dc-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3f9dc-117">Child Elements</span></span>

<span data-ttu-id="3f9dc-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="3f9dc-118">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3f9dc-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3f9dc-119">Parent Elements</span></span>

|<span data-ttu-id="3f9dc-120">Element</span><span class="sxs-lookup"><span data-stu-id="3f9dc-120">Element</span></span>|<span data-ttu-id="3f9dc-121">Opis</span><span class="sxs-lookup"><span data-stu-id="3f9dc-121">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="3f9dc-122">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3f9dc-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="3f9dc-123">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="3f9dc-123">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3f9dc-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3f9dc-124">Remarks</span></span>

<span data-ttu-id="3f9dc-125">Począwszy od .NET Framework 4, <xref:System.TimeSpan?displayProperty=nameWithType> struktura implementuje <xref:System.IFormattable> interfejs i obsługuje operacje formatowania przy użyciu standardowych i niestandardowych ciągów formatu.</span><span class="sxs-lookup"><span data-stu-id="3f9dc-125">Starting with the .NET Framework 4, the <xref:System.TimeSpan?displayProperty=nameWithType> structure implements the <xref:System.IFormattable> interface and supports formatting operations with standard and custom format strings.</span></span> <span data-ttu-id="3f9dc-126">Jeśli metoda analizy napotka nieobsługiwany specyfikator formatu lub ciąg formatu, zgłasza <xref:System.FormatException> .</span><span class="sxs-lookup"><span data-stu-id="3f9dc-126">If a parsing method encounters an unsupported format specifier or format string, it throws a <xref:System.FormatException>.</span></span>

<span data-ttu-id="3f9dc-127">W poprzednich wersjach .NET Framework <xref:System.TimeSpan> Struktura nie została zaimplementowana <xref:System.IFormattable> i nie obsługuje ciągów formatu.</span><span class="sxs-lookup"><span data-stu-id="3f9dc-127">In previous versions of the .NET Framework, the <xref:System.TimeSpan> structure did not implement <xref:System.IFormattable> and did not support format strings.</span></span> <span data-ttu-id="3f9dc-128">Jednak w przypadku wielu programistów założono, że program <xref:System.TimeSpan> obsługiwał zestaw ciągów formatu i użył ich w [operacjach formatowania złożonego](../../../../standard/base-types/composite-formatting.md) z metodami takimi jak <xref:System.String.Format%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="3f9dc-128">However, many developers mistakenly assumed that <xref:System.TimeSpan> did support a set of format strings and used them in [composite formatting operations](../../../../standard/base-types/composite-formatting.md) with methods such as <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3f9dc-129">Zwykle, jeśli typ implementuje <xref:System.IFormattable> i obsługuje ciągi formatowania, wywołania metod formatowania z nieobsługiwanymi ciągami formatu zwykle generują <xref:System.FormatException> .</span><span class="sxs-lookup"><span data-stu-id="3f9dc-129">Ordinarily, if a type implements <xref:System.IFormattable> and supports format strings, calls to formatting methods with unsupported format strings usually throw a <xref:System.FormatException>.</span></span> <span data-ttu-id="3f9dc-130">Jednak ponieważ <xref:System.TimeSpan> nie została zaimplementowana <xref:System.IFormattable> , środowisko uruchomieniowe zignorował ciąg formatu i zamiast niego nazywa <xref:System.TimeSpan.ToString?displayProperty=nameWithType> metodę.</span><span class="sxs-lookup"><span data-stu-id="3f9dc-130">However, because <xref:System.TimeSpan> did not implement <xref:System.IFormattable>, the runtime ignored the format string and instead called the <xref:System.TimeSpan.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="3f9dc-131">Oznacza to, że chociaż ciągi formatu nie miały wpływu na operację formatowania, ich obecność nie spowodowało <xref:System.FormatException> .</span><span class="sxs-lookup"><span data-stu-id="3f9dc-131">This means that, although the format strings had no effect on the formatting operation, their presence did not result in a <xref:System.FormatException>.</span></span>

<span data-ttu-id="3f9dc-132">W przypadkach, w których starszy kod przekazuje metodę formatowania złożonego i nieprawidłowy ciąg formatu, a ten kod nie może zostać ponownie skompilowany, można użyć `<TimeSpan_LegacyFormatMode>` elementu, aby przywrócić starsze <xref:System.TimeSpan> zachowanie.</span><span class="sxs-lookup"><span data-stu-id="3f9dc-132">For cases in which legacy code passes a composite formatting method and an invalid format string, and that code cannot be recompiled, you can use the `<TimeSpan_LegacyFormatMode>` element to restore the legacy <xref:System.TimeSpan> behavior.</span></span> <span data-ttu-id="3f9dc-133">Po ustawieniu `enabled` atrybutu tego elementu na `true` , Metoda formatowania złożonego powoduje wywołanie <xref:System.TimeSpan.ToString?displayProperty=nameWithType> zamiast <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> i <xref:System.FormatException> nie jest generowane.</span><span class="sxs-lookup"><span data-stu-id="3f9dc-133">When you set the `enabled` attribute of this element to `true`, the composite formatting method results in a call to <xref:System.TimeSpan.ToString?displayProperty=nameWithType> rather than <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, and a <xref:System.FormatException> is not thrown.</span></span>

## <a name="example"></a><span data-ttu-id="3f9dc-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="3f9dc-134">Example</span></span>

<span data-ttu-id="3f9dc-135">Poniższy przykład tworzy wystąpienie <xref:System.TimeSpan> obiektu i próbuje sformatować go za pomocą <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> metody przy użyciu nieobsługiwanego ciągu formatu standardowego.</span><span class="sxs-lookup"><span data-stu-id="3f9dc-135">The following example instantiates a <xref:System.TimeSpan> object and attempts to format it with the <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> method by using an unsupported standard format string.</span></span>

[!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
[!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]

<span data-ttu-id="3f9dc-136">Po uruchomieniu przykładu w .NET Framework 3,5 lub we wcześniejszej wersji zostaną wyświetlone następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="3f9dc-136">When you run the example on the .NET Framework 3.5 or on an earlier version, it displays the following output:</span></span>

```console
12:30:45
```

<span data-ttu-id="3f9dc-137">Różni się to od danych wyjściowych w przypadku uruchomienia przykładu w .NET Framework 4 lub jego nowszej wersji:</span><span class="sxs-lookup"><span data-stu-id="3f9dc-137">This differs markedly from the output if you run the example on the .NET Framework 4 or later version:</span></span>

```console
Invalid Format
```

<span data-ttu-id="3f9dc-138">Jeśli jednak dodasz następujący plik konfiguracji do katalogu przykładu, a następnie uruchomisz przykład w .NET Framework 4 lub nowszej wersji, dane wyjściowe są identyczne z tym, które zostały utworzone przez przykład w przypadku uruchomienia na .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="3f9dc-138">However, if you add the following configuration file to the example's directory and then run the example on the .NET Framework 4 or later version, the output is identical to that produced by the example when it is run on .NET Framework 3.5.</span></span>

```xml
<?xml version ="1.0"?>
<configuration>
   <runtime>
      <TimeSpan_LegacyFormatMode enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="3f9dc-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3f9dc-139">See also</span></span>

- [<span data-ttu-id="3f9dc-140">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="3f9dc-140">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="3f9dc-141">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="3f9dc-141">Configuration File Schema</span></span>](../index.md)
