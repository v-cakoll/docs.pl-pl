---
title: '&lt;Compatsortnlsversion —&gt; — Element'
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
ms.openlocfilehash: e78106c4df2e1c414d00f18871566dd5906c54f2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32745711"
---
# <a name="ltcompatsortnlsversiongt-element"></a><span data-ttu-id="99639-102">&lt;Compatsortnlsversion —&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="99639-102">&lt;CompatSortNLSVersion&gt; Element</span></span>
<span data-ttu-id="99639-103">Określa, że środowisko uruchomieniowe ma używać starszych kolejności sortowania podczas porównywania ciągów.</span><span class="sxs-lookup"><span data-stu-id="99639-103">Specifies that the runtime should use legacy sort orders when performing string comparisons.</span></span>  
  
 <span data-ttu-id="99639-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="99639-104">\<configuration></span></span>  
<span data-ttu-id="99639-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="99639-105">\<runtime></span></span>  
<span data-ttu-id="99639-106">\<Compatsortnlsversion — > — Element</span><span class="sxs-lookup"><span data-stu-id="99639-106">\<CompatSortNLSVersion> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99639-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="99639-107">Syntax</span></span>  
  
```xml  
<CompatSortNLSVersion    
   enabled="4096"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="99639-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="99639-108">Attributes and Elements</span></span>  
 <span data-ttu-id="99639-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="99639-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="99639-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="99639-110">Attributes</span></span>  
  
|<span data-ttu-id="99639-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="99639-111">Attribute</span></span>|<span data-ttu-id="99639-112">Opis</span><span class="sxs-lookup"><span data-stu-id="99639-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="99639-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="99639-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="99639-114">Określa identyfikator ustawień regionalnych, które będą określać używaną kolejność sortowania.</span><span class="sxs-lookup"><span data-stu-id="99639-114">Specifies the locale ID whose sort order is to be used.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="99639-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="99639-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="99639-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="99639-116">Value</span></span>|<span data-ttu-id="99639-117">Opis</span><span class="sxs-lookup"><span data-stu-id="99639-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="99639-118">4096</span><span class="sxs-lookup"><span data-stu-id="99639-118">4096</span></span>|<span data-ttu-id="99639-119">Identyfikator ustawień regionalnych reprezentujący alternatywną kolejność sortowania.</span><span class="sxs-lookup"><span data-stu-id="99639-119">The locale ID that represents an alternate sort order.</span></span> <span data-ttu-id="99639-120">W takim przypadku 4096 reprezentuje kolejność sortowania [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] i starszych wersji.</span><span class="sxs-lookup"><span data-stu-id="99639-120">In this case, 4096 represents the sort order of the [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] and earlier versions.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="99639-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="99639-121">Child Elements</span></span>  
 <span data-ttu-id="99639-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="99639-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="99639-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="99639-123">Parent Elements</span></span>  
  
|<span data-ttu-id="99639-124">Element</span><span class="sxs-lookup"><span data-stu-id="99639-124">Element</span></span>|<span data-ttu-id="99639-125">Opis</span><span class="sxs-lookup"><span data-stu-id="99639-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="99639-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="99639-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="99639-127">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="99639-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99639-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="99639-128">Remarks</span></span>  
 <span data-ttu-id="99639-129">Ponieważ porównania ciągów, sortowanie i wielkości liter operacje wykonywane przez <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> klasy w [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] są zgodne z Unicode 5.1 standardowe, wyniki metod porównania ciągów, takich jak <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> i <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> może różnić się od poprzednie wersje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="99639-129">Because string comparison, sorting, and casing operations performed by the <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> class in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] conform to the Unicode 5.1 standard, the results of string comparison methods such as <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> and <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> may differ from previous versions of the .NET Framework.</span></span> <span data-ttu-id="99639-130">Jeśli aplikacja jest zależna od starsze zachowanie, można przywrócić porównania ciągów i reguł sortowania używane w [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] i wcześniejsze wersje, umieszczając w niej `<CompatSortNLSVersion>` elementu w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="99639-130">If your application depends on legacy behavior, you can restore the string comparison and sorting rules used in the [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] and earlier versions by including the `<CompatSortNLSVersion>` element in your application's configuration file.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="99639-131">Przywrócenie starszych reguł porównywania ciągów i sortowania powoduje też, że w systemie lokalnym musi być dostępna dołączana dynamicznie biblioteka sort00001000.dll.</span><span class="sxs-lookup"><span data-stu-id="99639-131">Restoring legacy string comparison and sorting rules also requires the sort00001000.dll dynamic link library to be available on the local system.</span></span>  
  
 <span data-ttu-id="99639-132">Umożliwia także reguły sortowania i porównywania ciągów starszej wersji w określonej domenie aplikacji przez przekazanie ciąg "NetFx40_Legacy20SortingBehavior" do <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> metody podczas tworzenia domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="99639-132">You can also use legacy string sorting and comparison rules in a specific application domain by passing the string "NetFx40_Legacy20SortingBehavior" to the <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> method when you create the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99639-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="99639-133">Example</span></span>  
 <span data-ttu-id="99639-134">Poniższy przykład tworzy dwa <xref:System.String> obiektów i wywołania <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> metodę, aby porównać je przy użyciu konwencji bieżącej kultury.</span><span class="sxs-lookup"><span data-stu-id="99639-134">The following example instantiates two <xref:System.String> objects and calls the <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> method to compare them by using the conventions of the current culture.</span></span>  
  
 [!code-csharp[String.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/string.breakingchanges/cs/example1.cs#1)]
 [!code-vb[String.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/string.breakingchanges/vb/example1.vb#1)]  
  
 <span data-ttu-id="99639-135">Po uruchomieniu przykładzie [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], wyświetla następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="99639-135">When you run the example on the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], it displays the following output.</span></span>  
  
```  
sta follows a in the sort order.  
```  
  
 <span data-ttu-id="99639-136">To jest całkowicie różni się od wynik wyświetlony po uruchomieniu przykładzie na [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="99639-136">This is completely different from the output that is displayed when you run the example on the [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span></span>  
  
```  
sta equals a in the sort order.  
```  
  
 <span data-ttu-id="99639-137">Jednak jeśli dodasz następującego pliku konfiguracji, na przykład do katalogu, a następnie uruchom przykładzie w [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], dane wyjściowe są takie same jak wytworzonego na przykładzie, gdy jest uruchamiany na [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="99639-137">However, if you add the following configuration file to the example's directory and then run the example on the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], the output is identical to that produced by the example when it is run on the [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <CompatSortNLSVersion enabled="4096"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="99639-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="99639-138">See Also</span></span>  
 [<span data-ttu-id="99639-139">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="99639-139">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="99639-140">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="99639-140">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
