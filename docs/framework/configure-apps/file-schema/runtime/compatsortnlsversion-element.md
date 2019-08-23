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
ms.openlocfilehash: e3a348ac8da855e458b6208c51f9c51b48da3134
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927450"
---
# <a name="compatsortnlsversion-element"></a><span data-ttu-id="9d972-102">\<CompatSortNLSVersion, element ></span><span class="sxs-lookup"><span data-stu-id="9d972-102">\<CompatSortNLSVersion> Element</span></span>
<span data-ttu-id="9d972-103">Określa, że środowisko uruchomieniowe ma używać starszych kolejności sortowania podczas porównywania ciągów.</span><span class="sxs-lookup"><span data-stu-id="9d972-103">Specifies that the runtime should use legacy sort orders when performing string comparisons.</span></span>  
  
 <span data-ttu-id="9d972-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="9d972-104">\<configuration></span></span>  
<span data-ttu-id="9d972-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="9d972-105">\<runtime></span></span>  
<span data-ttu-id="9d972-106">\<CompatSortNLSVersion, element ></span><span class="sxs-lookup"><span data-stu-id="9d972-106">\<CompatSortNLSVersion> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d972-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="9d972-107">Syntax</span></span>  
  
```xml  
<CompatSortNLSVersion    
   enabled="4096"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9d972-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9d972-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9d972-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9d972-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9d972-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9d972-110">Attributes</span></span>  
  
|<span data-ttu-id="9d972-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9d972-111">Attribute</span></span>|<span data-ttu-id="9d972-112">Opis</span><span class="sxs-lookup"><span data-stu-id="9d972-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="9d972-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="9d972-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="9d972-114">Określa identyfikator ustawień regionalnych, które będą określać używaną kolejność sortowania.</span><span class="sxs-lookup"><span data-stu-id="9d972-114">Specifies the locale ID whose sort order is to be used.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="9d972-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="9d972-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="9d972-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="9d972-116">Value</span></span>|<span data-ttu-id="9d972-117">Opis</span><span class="sxs-lookup"><span data-stu-id="9d972-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9d972-118">4096</span><span class="sxs-lookup"><span data-stu-id="9d972-118">4096</span></span>|<span data-ttu-id="9d972-119">Identyfikator ustawień regionalnych reprezentujący alternatywną kolejność sortowania.</span><span class="sxs-lookup"><span data-stu-id="9d972-119">The locale ID that represents an alternate sort order.</span></span> <span data-ttu-id="9d972-120">W tym przypadku 4096 reprezentuje porządek sortowania .NET Framework 3,5 i starszych wersji.</span><span class="sxs-lookup"><span data-stu-id="9d972-120">In this case, 4096 represents the sort order of the .NET Framework 3.5 and earlier versions.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9d972-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9d972-121">Child Elements</span></span>  
 <span data-ttu-id="9d972-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="9d972-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9d972-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9d972-123">Parent Elements</span></span>  
  
|<span data-ttu-id="9d972-124">Element</span><span class="sxs-lookup"><span data-stu-id="9d972-124">Element</span></span>|<span data-ttu-id="9d972-125">Opis</span><span class="sxs-lookup"><span data-stu-id="9d972-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9d972-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9d972-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="9d972-127">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="9d972-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d972-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9d972-128">Remarks</span></span>  
 <span data-ttu-id="9d972-129">Ponieważ operacje porównywania ciągów, sortowania i wielkości liter wykonywane przez <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> klasę w .NET Framework 4 są zgodne ze standardem Unicode 5,1, wyniki metod porównywania ciągów, takie jak <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> i <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> mogą się różnić od poprzednie wersje .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9d972-129">Because string comparison, sorting, and casing operations performed by the <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> class in the .NET Framework 4 conform to the Unicode 5.1 standard, the results of string comparison methods such as <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> and <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> may differ from previous versions of the .NET Framework.</span></span> <span data-ttu-id="9d972-130">Jeśli aplikacja jest zależna od zachowania starszej wersji, można przywrócić porównanie ciągów i reguły sortowania używane w .NET Framework 3,5 i wcześniejszych wersjach przez dołączenie `<CompatSortNLSVersion>` elementu w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9d972-130">If your application depends on legacy behavior, you can restore the string comparison and sorting rules used in the .NET Framework 3.5 and earlier versions by including the `<CompatSortNLSVersion>` element in your application's configuration file.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9d972-131">Przywrócenie starszych reguł porównywania ciągów i sortowania powoduje też, że w systemie lokalnym musi być dostępna dołączana dynamicznie biblioteka sort00001000.dll.</span><span class="sxs-lookup"><span data-stu-id="9d972-131">Restoring legacy string comparison and sorting rules also requires the sort00001000.dll dynamic link library to be available on the local system.</span></span>  
  
 <span data-ttu-id="9d972-132">Można również użyć starszych reguł sortowania i porównywania ciągów w określonej domenie aplikacji, przekazując ciąg "NetFx40_Legacy20SortingBehavior" do <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> metody podczas tworzenia domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9d972-132">You can also use legacy string sorting and comparison rules in a specific application domain by passing the string "NetFx40_Legacy20SortingBehavior" to the <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> method when you create the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d972-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="9d972-133">Example</span></span>  
 <span data-ttu-id="9d972-134">Poniższy przykład tworzy wystąpienie dwóch <xref:System.String> obiektów i <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> wywołuje metodę w celu porównania ich przy użyciu Konwencji bieżącej kultury.</span><span class="sxs-lookup"><span data-stu-id="9d972-134">The following example instantiates two <xref:System.String> objects and calls the <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> method to compare them by using the conventions of the current culture.</span></span>  
  
 [!code-csharp[String.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/string.breakingchanges/cs/example1.cs#1)]
 [!code-vb[String.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/string.breakingchanges/vb/example1.vb#1)]  
  
 <span data-ttu-id="9d972-135">Po uruchomieniu przykładu na .NET Framework 4 zostanie wyświetlone następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="9d972-135">When you run the example on the .NET Framework 4, it displays the following output.</span></span>  
  
```  
sta follows a in the sort order.  
```  
  
 <span data-ttu-id="9d972-136">Jest to zupełnie inne niż dane wyjściowe, które są wyświetlane po uruchomieniu przykładu na .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="9d972-136">This is completely different from the output that is displayed when you run the example on the .NET Framework 3.5.</span></span>  
  
```  
sta equals a in the sort order.  
```  
  
 <span data-ttu-id="9d972-137">Jeśli jednak dodasz następujący plik konfiguracji do katalogu przykładu, a następnie uruchomisz przykład na .NET Framework 4, dane wyjściowe są identyczne z tym, które zostały utworzone przez przykład w przypadku uruchomienia na .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="9d972-137">However, if you add the following configuration file to the example's directory and then run the example on the .NET Framework 4, the output is identical to that produced by the example when it is run on the .NET Framework 3.5.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <CompatSortNLSVersion enabled="4096"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9d972-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9d972-138">See also</span></span>

- [<span data-ttu-id="9d972-139">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="9d972-139">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="9d972-140">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="9d972-140">Configuration File Schema</span></span>](../index.md)
