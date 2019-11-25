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
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73968906"
---
# <a name="timespan_legacyformatmode-element"></a><span data-ttu-id="12dd1-102">\<TimeSpan_LegacyFormatMode > elementu</span><span class="sxs-lookup"><span data-stu-id="12dd1-102">\<TimeSpan_LegacyFormatMode> Element</span></span>

<span data-ttu-id="12dd1-103">Określa, czy środowisko uruchomieniowe zachowuje starsze zachowanie w operacjach formatowania przy użyciu wartości <xref:System.TimeSpan?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="12dd1-103">Determines whether the runtime preserves legacy behavior in formatting operations with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>

<span data-ttu-id="12dd1-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="12dd1-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="12dd1-105">&nbsp;&nbsp;[ **\<środowiska uruchomieniowego >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="12dd1-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="12dd1-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<** TimeSpan_LegacyFormatMode ></span><span class="sxs-lookup"><span data-stu-id="12dd1-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<TimeSpan_LegacyFormatMode>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="12dd1-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="12dd1-107">Syntax</span></span>

```xml
<TimeSpan_LegacyFormatMode
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="12dd1-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="12dd1-108">Attributes and Elements</span></span>

<span data-ttu-id="12dd1-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="12dd1-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="12dd1-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="12dd1-110">Attributes</span></span>

|<span data-ttu-id="12dd1-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="12dd1-111">Attribute</span></span>|<span data-ttu-id="12dd1-112">Opis</span><span class="sxs-lookup"><span data-stu-id="12dd1-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="12dd1-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="12dd1-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="12dd1-114">Określa, czy środowisko uruchomieniowe korzysta ze starszego zachowania formatowania z wartościami <xref:System.TimeSpan?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="12dd1-114">Specifies whether the runtime uses legacy formatting behavior with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="12dd1-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="12dd1-115">enabled Attribute</span></span>

|<span data-ttu-id="12dd1-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="12dd1-116">Value</span></span>|<span data-ttu-id="12dd1-117">Opis</span><span class="sxs-lookup"><span data-stu-id="12dd1-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="12dd1-118">Środowisko uruchomieniowe nie przywraca starszego zachowania formatowania.</span><span class="sxs-lookup"><span data-stu-id="12dd1-118">The runtime does not restore legacy formatting behavior.</span></span>|
|`true`|<span data-ttu-id="12dd1-119">Środowisko uruchomieniowe przywraca starsze zachowanie podczas formatowania.</span><span class="sxs-lookup"><span data-stu-id="12dd1-119">The runtime restores legacy formatting behavior.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="12dd1-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="12dd1-120">Child Elements</span></span>

<span data-ttu-id="12dd1-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="12dd1-121">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="12dd1-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="12dd1-122">Parent Elements</span></span>

|<span data-ttu-id="12dd1-123">Element</span><span class="sxs-lookup"><span data-stu-id="12dd1-123">Element</span></span>|<span data-ttu-id="12dd1-124">Opis</span><span class="sxs-lookup"><span data-stu-id="12dd1-124">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="12dd1-125">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="12dd1-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="12dd1-126">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="12dd1-126">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="12dd1-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="12dd1-127">Remarks</span></span>

<span data-ttu-id="12dd1-128">Począwszy od .NET Framework 4, struktura <xref:System.TimeSpan?displayProperty=nameWithType> implementuje interfejs <xref:System.IFormattable> i obsługuje operacje formatowania przy użyciu standardowych i niestandardowych ciągów formatu.</span><span class="sxs-lookup"><span data-stu-id="12dd1-128">Starting with the .NET Framework 4, the <xref:System.TimeSpan?displayProperty=nameWithType> structure implements the <xref:System.IFormattable> interface and supports formatting operations with standard and custom format strings.</span></span> <span data-ttu-id="12dd1-129">Jeśli metoda analizy napotka nieobsługiwany specyfikator formatu lub ciąg formatu, zgłasza <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="12dd1-129">If a parsing method encounters an unsupported format specifier or format string, it throws a <xref:System.FormatException>.</span></span>

<span data-ttu-id="12dd1-130">W poprzednich wersjach .NET Framework struktura <xref:System.TimeSpan> nie została zaimplementowana <xref:System.IFormattable> i nie obsługiwała ciągów formatowania.</span><span class="sxs-lookup"><span data-stu-id="12dd1-130">In previous versions of the .NET Framework, the <xref:System.TimeSpan> structure did not implement <xref:System.IFormattable> and did not support format strings.</span></span> <span data-ttu-id="12dd1-131">Jednak wielu programistów założono, że <xref:System.TimeSpan> obsłużył zestaw ciągów formatu i używały ich w [operacjach formatowania złożonego](../../../../standard/base-types/composite-formatting.md) z metodami takimi jak <xref:System.String.Format%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="12dd1-131">However, many developers mistakenly assumed that <xref:System.TimeSpan> did support a set of format strings and used them in [composite formatting operations](../../../../standard/base-types/composite-formatting.md) with methods such as <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="12dd1-132">Zwykle, jeśli typ implementuje <xref:System.IFormattable> i obsługuje ciągi formatu, wywołania metod formatowania z nieobsługiwanymi ciągami formatu zwykle generują <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="12dd1-132">Ordinarily, if a type implements <xref:System.IFormattable> and supports format strings, calls to formatting methods with unsupported format strings usually throw a <xref:System.FormatException>.</span></span> <span data-ttu-id="12dd1-133">Jednak ponieważ <xref:System.TimeSpan> nie zaimplementował <xref:System.IFormattable>, środowisko uruchomieniowe zignorował ciąg formatu i zamiast tego nazywa metodę <xref:System.TimeSpan.ToString?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="12dd1-133">However, because <xref:System.TimeSpan> did not implement <xref:System.IFormattable>, the runtime ignored the format string and instead called the <xref:System.TimeSpan.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="12dd1-134">Oznacza to, że chociaż ciągi formatu nie miały wpływu na operację formatowania, ich obecność nie powodowała <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="12dd1-134">This means that, although the format strings had no effect on the formatting operation, their presence did not result in a <xref:System.FormatException>.</span></span>

<span data-ttu-id="12dd1-135">W przypadkach, w których starszy kod przekazuje metodę formatowania złożonego i nieprawidłowy ciąg formatu, i nie można ponownie skompilować tego kodu, można użyć elementu `<TimeSpan_LegacyFormatMode>`, aby przywrócić zachowanie starszej <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="12dd1-135">For cases in which legacy code passes a composite formatting method and an invalid format string, and that code cannot be recompiled, you can use the `<TimeSpan_LegacyFormatMode>` element to restore the legacy <xref:System.TimeSpan> behavior.</span></span> <span data-ttu-id="12dd1-136">Po ustawieniu atrybutu `enabled` tego elementu na `true`, Metoda formatowania złożonego spowoduje wywołanie <xref:System.TimeSpan.ToString?displayProperty=nameWithType> zamiast <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>i <xref:System.FormatException> nie zostanie zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="12dd1-136">When you set the `enabled` attribute of this element to `true`, the composite formatting method results in a call to <xref:System.TimeSpan.ToString?displayProperty=nameWithType> rather than <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, and a <xref:System.FormatException> is not thrown.</span></span>

## <a name="example"></a><span data-ttu-id="12dd1-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="12dd1-137">Example</span></span>

<span data-ttu-id="12dd1-138">Poniższy przykład tworzy wystąpienie obiektu <xref:System.TimeSpan> i próbuje sformatować go za pomocą metody <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> za pomocą nieobsługiwanego ciągu formatu standardowego.</span><span class="sxs-lookup"><span data-stu-id="12dd1-138">The following example instantiates a <xref:System.TimeSpan> object and attempts to format it with the <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> method by using an unsupported standard format string.</span></span>

[!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
[!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]

<span data-ttu-id="12dd1-139">Po uruchomieniu przykładu w .NET Framework 3,5 lub we wcześniejszej wersji zostaną wyświetlone następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="12dd1-139">When you run the example on the .NET Framework 3.5 or on an earlier version, it displays the following output:</span></span>

```console
12:30:45
```

<span data-ttu-id="12dd1-140">Różni się to od danych wyjściowych w przypadku uruchomienia przykładu w .NET Framework 4 lub jego nowszej wersji:</span><span class="sxs-lookup"><span data-stu-id="12dd1-140">This differs markedly from the output if you run the example on the .NET Framework 4 or later version:</span></span>

```console
Invalid Format
```

<span data-ttu-id="12dd1-141">Jeśli jednak dodasz następujący plik konfiguracji do katalogu przykładu, a następnie uruchomisz przykład w .NET Framework 4 lub nowszej wersji, dane wyjściowe są identyczne z tym, które zostały utworzone przez przykład w przypadku uruchomienia na .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="12dd1-141">However, if you add the following configuration file to the example's directory and then run the example on the .NET Framework 4 or later version, the output is identical to that produced by the example when it is run on .NET Framework 3.5.</span></span>

```xml
<?xml version ="1.0"?>
<configuration>
   <runtime>
      <TimeSpan_LegacyFormatMode enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="12dd1-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="12dd1-142">See also</span></span>

- [<span data-ttu-id="12dd1-143">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="12dd1-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="12dd1-144">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="12dd1-144">Configuration File Schema</span></span>](../index.md)
