---
title: <CompatSortNLSVersion> Element
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <CompatSortNLSVersion> element
- CompatSortNLSVersion element
ms.assetid: 782cc82e-83f7-404a-80b7-6d3061a8b6e3
ms.openlocfilehash: 30afeb2ab9380db75cbeb723ea15a23e4313c9e8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154273"
---
# <a name="compatsortnlsversion-element"></a><span data-ttu-id="16464-102">\<CompatSortNLSVersion> Element</span><span class="sxs-lookup"><span data-stu-id="16464-102">\<CompatSortNLSVersion> Element</span></span>
<span data-ttu-id="16464-103">Określa, że środowisko uruchomieniowe ma używać starszych kolejności sortowania podczas porównywania ciągów.</span><span class="sxs-lookup"><span data-stu-id="16464-103">Specifies that the runtime should use legacy sort orders when performing string comparisons.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<CompatSortNLSVersion>**  
  
## <a name="syntax"></a><span data-ttu-id="16464-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="16464-104">Syntax</span></span>  
  
```xml  
<CompatSortNLSVersion
   enabled="4096"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="16464-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="16464-105">Attributes and Elements</span></span>  
 <span data-ttu-id="16464-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="16464-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="16464-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="16464-107">Attributes</span></span>  
  
|<span data-ttu-id="16464-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="16464-108">Attribute</span></span>|<span data-ttu-id="16464-109">Opis</span><span class="sxs-lookup"><span data-stu-id="16464-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="16464-110">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="16464-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="16464-111">Określa identyfikator ustawień regionalnych, które będą określać używaną kolejność sortowania.</span><span class="sxs-lookup"><span data-stu-id="16464-111">Specifies the locale ID whose sort order is to be used.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="16464-112">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="16464-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="16464-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="16464-113">Value</span></span>|<span data-ttu-id="16464-114">Opis</span><span class="sxs-lookup"><span data-stu-id="16464-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="16464-115">4096</span><span class="sxs-lookup"><span data-stu-id="16464-115">4096</span></span>|<span data-ttu-id="16464-116">Identyfikator ustawień regionalnych reprezentujący alternatywną kolejność sortowania.</span><span class="sxs-lookup"><span data-stu-id="16464-116">The locale ID that represents an alternate sort order.</span></span> <span data-ttu-id="16464-117">W tym przypadku 4096 reprezentuje porządek sortowania .NET Framework 3,5 i starszych wersji.</span><span class="sxs-lookup"><span data-stu-id="16464-117">In this case, 4096 represents the sort order of the .NET Framework 3.5 and earlier versions.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="16464-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="16464-118">Child Elements</span></span>  
 <span data-ttu-id="16464-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="16464-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="16464-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="16464-120">Parent Elements</span></span>  
  
|<span data-ttu-id="16464-121">Element</span><span class="sxs-lookup"><span data-stu-id="16464-121">Element</span></span>|<span data-ttu-id="16464-122">Opis</span><span class="sxs-lookup"><span data-stu-id="16464-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="16464-123">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="16464-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="16464-124">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="16464-124">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16464-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="16464-125">Remarks</span></span>  
 <span data-ttu-id="16464-126">Ponieważ porównania ciągów, sortowania i wielkości liter wykonywane przez <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> klasę w .NET Framework 4 są zgodne ze standardem Unicode 5,1, wyniki metod porównywania ciągów, takie jak <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> i <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> mogą się różnić od poprzednich wersji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="16464-126">Because string comparison, sorting, and casing operations performed by the <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> class in the .NET Framework 4 conform to the Unicode 5.1 standard, the results of string comparison methods such as <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> and <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> may differ from previous versions of the .NET Framework.</span></span> <span data-ttu-id="16464-127">Jeśli aplikacja jest zależna od zachowania starszej wersji, można przywrócić porównanie ciągów i reguły sortowania używane w .NET Framework 3,5 i wcześniejszych wersjach przez dołączenie `<CompatSortNLSVersion>` elementu w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="16464-127">If your application depends on legacy behavior, you can restore the string comparison and sorting rules used in the .NET Framework 3.5 and earlier versions by including the `<CompatSortNLSVersion>` element in your application's configuration file.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="16464-128">Przywrócenie starszych reguł porównywania ciągów i sortowania powoduje też, że w systemie lokalnym musi być dostępna dołączana dynamicznie biblioteka sort00001000.dll.</span><span class="sxs-lookup"><span data-stu-id="16464-128">Restoring legacy string comparison and sorting rules also requires the sort00001000.dll dynamic link library to be available on the local system.</span></span>  
  
 <span data-ttu-id="16464-129">Można również użyć starszych reguł sortowania i porównywania ciągów w określonej domenie aplikacji przez przekazanie ciągu "NetFx40_Legacy20SortingBehavior" do <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> metody podczas tworzenia domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="16464-129">You can also use legacy string sorting and comparison rules in a specific application domain by passing the string "NetFx40_Legacy20SortingBehavior" to the <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> method when you create the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16464-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="16464-130">Example</span></span>  
 <span data-ttu-id="16464-131">Poniższy przykład tworzy wystąpienie dwóch <xref:System.String> obiektów i wywołuje <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> metodę w celu porównania ich przy użyciu Konwencji bieżącej kultury.</span><span class="sxs-lookup"><span data-stu-id="16464-131">The following example instantiates two <xref:System.String> objects and calls the <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> method to compare them by using the conventions of the current culture.</span></span>  
  
 [!code-csharp[String.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/string.breakingchanges/cs/example1.cs#1)]
 [!code-vb[String.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/string.breakingchanges/vb/example1.vb#1)]  
  
 <span data-ttu-id="16464-132">Po uruchomieniu przykładu w .NET Framework 4 zostanie wyświetlone następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="16464-132">When you run the example on the .NET Framework 4, it displays the following output:</span></span>
  
```console
sta follows a in the sort order.  
```  
  
 <span data-ttu-id="16464-133">Jest to zupełnie inne niż dane wyjściowe, które są wyświetlane po uruchomieniu przykładu na .NET Framework 3,5:</span><span class="sxs-lookup"><span data-stu-id="16464-133">This is completely different from the output that is displayed when you run the example on the .NET Framework 3.5:</span></span>
  
```console
sta equals a in the sort order.  
```  
  
 <span data-ttu-id="16464-134">Jeśli jednak dodasz następujący plik konfiguracji do katalogu przykładu, a następnie uruchomisz przykład na .NET Framework 4, dane wyjściowe są identyczne z tym, które zostały utworzone przez przykład w przypadku uruchomienia na .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="16464-134">However, if you add the following configuration file to the example's directory and then run the example on the .NET Framework 4, the output is identical to that produced by the example when it is run on the .NET Framework 3.5.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <CompatSortNLSVersion enabled="4096"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="16464-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="16464-135">See also</span></span>

- [<span data-ttu-id="16464-136">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="16464-136">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="16464-137">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="16464-137">Configuration File Schema</span></span>](../index.md)
