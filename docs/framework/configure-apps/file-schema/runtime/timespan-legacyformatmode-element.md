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
ms.openlocfilehash: 38adde3cd51a96f0e15ed5a0c539e088f2d3b480
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164557"
---
# <a name="timespanlegacyformatmode-element"></a><span data-ttu-id="1a4b5-102">\<TimeSpan_LegacyFormatMode> Element</span><span class="sxs-lookup"><span data-stu-id="1a4b5-102">\<TimeSpan_LegacyFormatMode> Element</span></span>
<span data-ttu-id="1a4b5-103">Określa, czy środowisko uruchomieniowe pozwala zachować starsze zachowanie w operacjach przy użyciu formatowania <xref:System.TimeSpan?displayProperty=nameWithType> wartości.</span><span class="sxs-lookup"><span data-stu-id="1a4b5-103">Determines whether the runtime preserves legacy behavior in formatting operations with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>  
  
 <span data-ttu-id="1a4b5-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="1a4b5-104">\<configuration></span></span>  
<span data-ttu-id="1a4b5-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="1a4b5-105">\<runtime></span></span>  
<span data-ttu-id="1a4b5-106"><TimeSpan_LegacyFormatMode></span><span class="sxs-lookup"><span data-stu-id="1a4b5-106"><TimeSpan_LegacyFormatMode></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a4b5-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="1a4b5-107">Syntax</span></span>  
  
```xml  
<TimeSpan_LegacyFormatMode    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1a4b5-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1a4b5-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1a4b5-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1a4b5-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1a4b5-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1a4b5-110">Attributes</span></span>  
  
|<span data-ttu-id="1a4b5-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1a4b5-111">Attribute</span></span>|<span data-ttu-id="1a4b5-112">Opis</span><span class="sxs-lookup"><span data-stu-id="1a4b5-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="1a4b5-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="1a4b5-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="1a4b5-114">Określa, czy środowisko wykonawcze używa starszego formatowania działania z <xref:System.TimeSpan?displayProperty=nameWithType> wartości.</span><span class="sxs-lookup"><span data-stu-id="1a4b5-114">Specifies whether the runtime uses legacy formatting behavior with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="1a4b5-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="1a4b5-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="1a4b5-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="1a4b5-116">Value</span></span>|<span data-ttu-id="1a4b5-117">Opis</span><span class="sxs-lookup"><span data-stu-id="1a4b5-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="1a4b5-118">Środowisko wykonawcze nie przywrócić starsze zachowanie formatowania.</span><span class="sxs-lookup"><span data-stu-id="1a4b5-118">The runtime does not restore legacy formatting behavior.</span></span>|  
|`true`|<span data-ttu-id="1a4b5-119">Środowisko uruchomieniowe przywraca starsze zachowanie formatowania.</span><span class="sxs-lookup"><span data-stu-id="1a4b5-119">The runtime restores legacy formatting behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1a4b5-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1a4b5-120">Child Elements</span></span>  
 <span data-ttu-id="1a4b5-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="1a4b5-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1a4b5-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1a4b5-122">Parent Elements</span></span>  
  
|<span data-ttu-id="1a4b5-123">Element</span><span class="sxs-lookup"><span data-stu-id="1a4b5-123">Element</span></span>|<span data-ttu-id="1a4b5-124">Opis</span><span class="sxs-lookup"><span data-stu-id="1a4b5-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1a4b5-125">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1a4b5-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="1a4b5-126">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="1a4b5-126">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a4b5-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1a4b5-127">Remarks</span></span>  
 <span data-ttu-id="1a4b5-128">Począwszy od [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], <xref:System.TimeSpan?displayProperty=nameWithType> struktury implementuje <xref:System.IFormattable> interfejsu i obsługuje formatowanie operacji za pomocą ciągów formatu standardowego i niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="1a4b5-128">Starting with the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], the <xref:System.TimeSpan?displayProperty=nameWithType> structure implements the <xref:System.IFormattable> interface and supports formatting operations with standard and custom format strings.</span></span> <span data-ttu-id="1a4b5-129">Jeśli metoda analizowania napotka specyfikator nieobsługiwany format lub ciąg formatu, zgłasza <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="1a4b5-129">If a parsing method encounters an unsupported format specifier or format string, it throws a <xref:System.FormatException>.</span></span>  
  
 <span data-ttu-id="1a4b5-130">W poprzednich wersjach programu .NET Framework <xref:System.TimeSpan> struktury nie implementuje <xref:System.IFormattable> i nie obsługują ciągi formatu.</span><span class="sxs-lookup"><span data-stu-id="1a4b5-130">In previous versions of the .NET Framework, the <xref:System.TimeSpan> structure did not implement <xref:System.IFormattable> and did not support format strings.</span></span> <span data-ttu-id="1a4b5-131">Jednak wielu deweloperów przez pomyłkę przyjąć, że <xref:System.TimeSpan> obsługiwać zestaw ciągów formatu i używać ich w [operacji formatowania złożonego](../../../../../docs/standard/base-types/composite-formatting.md) za pomocą metod, takich jak <xref:System.String.Format%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1a4b5-131">However, many developers mistakenly assumed that <xref:System.TimeSpan> did support a set of format strings and used them in [composite formatting operations](../../../../../docs/standard/base-types/composite-formatting.md) with methods such as <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1a4b5-132">Normalnie Jeśli typ implementuje <xref:System.IFormattable> i obsługuje formatowanie ciągów, wywołania do metod formatowania z nieobsługiwany format ciągów zazwyczaj generują <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="1a4b5-132">Ordinarily, if a type implements <xref:System.IFormattable> and supports format strings, calls to formatting methods with unsupported format strings usually throw a <xref:System.FormatException>.</span></span> <span data-ttu-id="1a4b5-133">Jednak ponieważ <xref:System.TimeSpan> nie zaimplementował <xref:System.IFormattable>, środowisko uruchomieniowe ignorowane w formacie ciągu i zamiast tego wywołuje <xref:System.TimeSpan.ToString?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="1a4b5-133">However, because <xref:System.TimeSpan> did not implement <xref:System.IFormattable>, the runtime ignored the format string and instead called the <xref:System.TimeSpan.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="1a4b5-134">Oznacza to, że chociaż ciągi formatu nie miało wpływu na operacji formatowania, ich obecność nie powoduje <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="1a4b5-134">This means that, although the format strings had no effect on the formatting operation, their presence did not result in a <xref:System.FormatException>.</span></span>  
  
 <span data-ttu-id="1a4b5-135">W przypadkach, w których starszego kodu przekazuje formatowania, metoda i nieprawidłowy ciąg formatu złożonego, a ten kod nie może być ponownie kompilowane, można użyć `<TimeSpan_LegacyFormatMode>` elementu do przywrócenia starszej wersji <xref:System.TimeSpan> zachowanie.</span><span class="sxs-lookup"><span data-stu-id="1a4b5-135">For cases in which legacy code passes a composite formatting method and an invalid format string, and that code cannot be recompiled, you can use the `<TimeSpan_LegacyFormatMode>` element to restore the legacy <xref:System.TimeSpan> behavior.</span></span> <span data-ttu-id="1a4b5-136">Po ustawieniu `enabled` atrybutu tego elementu `true`, metoda powoduje wywołanie w celu formatowania złożonego <xref:System.TimeSpan.ToString?displayProperty=nameWithType> zamiast <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, a <xref:System.FormatException> nie jest zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="1a4b5-136">When you set the `enabled` attribute of this element to `true`, the composite formatting method results in a call to <xref:System.TimeSpan.ToString?displayProperty=nameWithType> rather than <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, and a <xref:System.FormatException> is not thrown.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a4b5-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="1a4b5-137">Example</span></span>  
 <span data-ttu-id="1a4b5-138">Poniższy przykład tworzy wystąpienie <xref:System.TimeSpan> obiektu i próbuje sformatować je za pomocą <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> metody przy użyciu nieobsługiwanego standardowym ciągiem formatującym.</span><span class="sxs-lookup"><span data-stu-id="1a4b5-138">The following example instantiates a <xref:System.TimeSpan> object and attempts to format it with the <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> method by using an unsupported standard format string.</span></span>  
  
 [!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
 [!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]  
  
 <span data-ttu-id="1a4b5-139">Po uruchomieniu przykładu w [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] lub starszą wersję, wyświetla następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="1a4b5-139">When you run the example on the [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] or on an earlier version, it displays the following output:</span></span>  
  
```  
12:30:45  
```  
  
 <span data-ttu-id="1a4b5-140">To znacznie różni się od dane wyjściowe po uruchomieniu przykładu w [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] lub nowszej wersji:</span><span class="sxs-lookup"><span data-stu-id="1a4b5-140">This differs markedly from the output if you run the example on the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] or later version:</span></span>  
  
```  
Invalid Format  
```  
  
 <span data-ttu-id="1a4b5-141">Jednak jeśli dodasz następujący plik konfiguracji do przykładu katalogu, a następnie uruchom przykład na [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] lub nowszej wersji, dane wyjściowe jest taka sama jak wytworzonego przez w przykładzie, gdy jest uruchamiany na [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1a4b5-141">However, if you add the following configuration file to the example's directory and then run the example on the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] or later version, the output is identical to that produced by the example when it is run on [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <TimeSpan_LegacyFormatMode enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1a4b5-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1a4b5-142">See also</span></span>

- [<span data-ttu-id="1a4b5-143">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="1a4b5-143">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="1a4b5-144">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="1a4b5-144">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
