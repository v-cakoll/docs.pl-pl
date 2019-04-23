---
title: <CompatSortNLSVersion>, element
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <CompatSortNLSVersion> element
- CompatSortNLSVersion element
ms.assetid: 782cc82e-83f7-404a-80b7-6d3061a8b6e3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dfd241056947fbf1daf48b84ff41e3f74ff7b8de
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59195777"
---
# <a name="compatsortnlsversion-element"></a><span data-ttu-id="740be-102">\<CompatSortNLSVersion > Element</span><span class="sxs-lookup"><span data-stu-id="740be-102">\<CompatSortNLSVersion> Element</span></span>
<span data-ttu-id="740be-103">Określa, że środowisko uruchomieniowe ma używać starszych kolejności sortowania podczas porównywania ciągów.</span><span class="sxs-lookup"><span data-stu-id="740be-103">Specifies that the runtime should use legacy sort orders when performing string comparisons.</span></span>  
  
 <span data-ttu-id="740be-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="740be-104">\<configuration></span></span>  
<span data-ttu-id="740be-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="740be-105">\<runtime></span></span>  
<span data-ttu-id="740be-106">\<CompatSortNLSVersion > Element</span><span class="sxs-lookup"><span data-stu-id="740be-106">\<CompatSortNLSVersion> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="740be-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="740be-107">Syntax</span></span>  
  
```xml  
<CompatSortNLSVersion    
   enabled="4096"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="740be-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="740be-108">Attributes and Elements</span></span>  
 <span data-ttu-id="740be-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="740be-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="740be-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="740be-110">Attributes</span></span>  
  
|<span data-ttu-id="740be-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="740be-111">Attribute</span></span>|<span data-ttu-id="740be-112">Opis</span><span class="sxs-lookup"><span data-stu-id="740be-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="740be-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="740be-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="740be-114">Określa identyfikator ustawień regionalnych, które będą określać używaną kolejność sortowania.</span><span class="sxs-lookup"><span data-stu-id="740be-114">Specifies the locale ID whose sort order is to be used.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="740be-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="740be-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="740be-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="740be-116">Value</span></span>|<span data-ttu-id="740be-117">Opis</span><span class="sxs-lookup"><span data-stu-id="740be-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="740be-118">4096</span><span class="sxs-lookup"><span data-stu-id="740be-118">4096</span></span>|<span data-ttu-id="740be-119">Identyfikator ustawień regionalnych reprezentujący alternatywną kolejność sortowania.</span><span class="sxs-lookup"><span data-stu-id="740be-119">The locale ID that represents an alternate sort order.</span></span> <span data-ttu-id="740be-120">W tym przypadku 4096 reprezentuje kolejność sortowania [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] i wcześniejszych wersji.</span><span class="sxs-lookup"><span data-stu-id="740be-120">In this case, 4096 represents the sort order of the [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] and earlier versions.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="740be-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="740be-121">Child Elements</span></span>  
 <span data-ttu-id="740be-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="740be-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="740be-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="740be-123">Parent Elements</span></span>  
  
|<span data-ttu-id="740be-124">Element</span><span class="sxs-lookup"><span data-stu-id="740be-124">Element</span></span>|<span data-ttu-id="740be-125">Opis</span><span class="sxs-lookup"><span data-stu-id="740be-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="740be-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="740be-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="740be-127">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="740be-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="740be-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="740be-128">Remarks</span></span>  
 <span data-ttu-id="740be-129">Ponieważ porównania ciągów, sortowanie i operacje dotyczące wielkości znaków wykonywane przez <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> klasy w [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] są zgodne ze standardem Unicode 5.1. wyniki metod porównujących, takich jak <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> i <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> może różnić się od poprzednie wersje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="740be-129">Because string comparison, sorting, and casing operations performed by the <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> class in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] conform to the Unicode 5.1 standard, the results of string comparison methods such as <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> and <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> may differ from previous versions of the .NET Framework.</span></span> <span data-ttu-id="740be-130">Jeśli aplikacja jest zależna od starszego zachowania, można przywrócić porównywania ciągów i reguł sortowania używanych w [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] i wcześniejszych wersjach, umieszczając `<CompatSortNLSVersion>` elementu w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="740be-130">If your application depends on legacy behavior, you can restore the string comparison and sorting rules used in the [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] and earlier versions by including the `<CompatSortNLSVersion>` element in your application's configuration file.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="740be-131">Przywrócenie starszych reguł porównywania ciągów i sortowania powoduje też, że w systemie lokalnym musi być dostępna dołączana dynamicznie biblioteka sort00001000.dll.</span><span class="sxs-lookup"><span data-stu-id="740be-131">Restoring legacy string comparison and sorting rules also requires the sort00001000.dll dynamic link library to be available on the local system.</span></span>  
  
 <span data-ttu-id="740be-132">Można również użyć reguł sortowania i porównywania ciągów starszej wersji w określonej domenie aplikacji, przekazując ciąg "NetFx40_Legacy20SortingBehavior", do <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> metody tworzenia domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="740be-132">You can also use legacy string sorting and comparison rules in a specific application domain by passing the string "NetFx40_Legacy20SortingBehavior" to the <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> method when you create the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="740be-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="740be-133">Example</span></span>  
 <span data-ttu-id="740be-134">Poniższy przykład tworzy dwie <xref:System.String> obiektów i wywołuje <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> metody w celu porównania ich przy użyciu konwencji bieżącej kultury.</span><span class="sxs-lookup"><span data-stu-id="740be-134">The following example instantiates two <xref:System.String> objects and calls the <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> method to compare them by using the conventions of the current culture.</span></span>  
  
 [!code-csharp[String.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/string.breakingchanges/cs/example1.cs#1)]
 [!code-vb[String.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/string.breakingchanges/vb/example1.vb#1)]  
  
 <span data-ttu-id="740be-135">Po uruchomieniu przykładu w [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], wyświetla następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="740be-135">When you run the example on the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], it displays the following output.</span></span>  
  
```  
sta follows a in the sort order.  
```  
  
 <span data-ttu-id="740be-136">Jest to zupełnie inne niż dane wyjściowe, która jest wyświetlana po uruchomieniu przykładu w [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="740be-136">This is completely different from the output that is displayed when you run the example on the [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span></span>  
  
```  
sta equals a in the sort order.  
```  
  
 <span data-ttu-id="740be-137">Jednak jeśli dodasz następujący plik konfiguracji do przykładu katalogu, a następnie uruchom przykład na [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], dane wyjściowe jest taka sama jak wytworzonego przez w przykładzie, gdy jest uruchamiany na [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="740be-137">However, if you add the following configuration file to the example's directory and then run the example on the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], the output is identical to that produced by the example when it is run on the [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <CompatSortNLSVersion enabled="4096"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="740be-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="740be-138">See also</span></span>

- [<span data-ttu-id="740be-139">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="740be-139">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="740be-140">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="740be-140">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
