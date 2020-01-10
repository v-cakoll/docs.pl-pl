---
title: Nazwy przestrzeni nazw
ms.date: 10/22/2008
helpviewer_keywords:
- names [.NET Framework], conflicts
- names [.NET Framework], namespaces
- type names, conflicts
- namespaces [.NET Framework], names
- names [.NET Framework], type names
ms.assetid: a49058d2-0276-43a7-9502-04adddf857b2
ms.openlocfilehash: 0678f695e3ae7c40660031862c9073a21fd72491
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709234"
---
# <a name="names-of-namespaces"></a><span data-ttu-id="82371-102">Nazwy przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="82371-102">Names of Namespaces</span></span>
<span data-ttu-id="82371-103">Podobnie jak w przypadku innych wytycznych dotyczących nazewnictwa, celem podczas nazewnictwa przestrzeni nazw jest utworzenie wystarczającej przejrzystości dla programisty korzystającego z platformy, aby natychmiast znać zawartość przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="82371-103">As with other naming guidelines, the goal when naming namespaces is creating sufficient clarity for the programmer using the framework to immediately know what the content of the namespace is likely to be.</span></span> <span data-ttu-id="82371-104">Następujący szablon określa ogólną regułę nazewnictwa przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="82371-104">The following template specifies the general rule for naming namespaces:</span></span>  
  
 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`  
  
 <span data-ttu-id="82371-105">Oto przykłady:</span><span class="sxs-lookup"><span data-stu-id="82371-105">The following are examples:</span></span>  
  
 `Fabrikam.Math`  
 `Litware.Security`  
  
 <span data-ttu-id="82371-106">**✓ DO** prefiksu nazwy przestrzeni nazw o nazwie firmy, aby zapobiec przestrzenie nazw różnych firm z o tej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="82371-106">**✓ DO** prefix namespace names with a company name to prevent namespaces from different companies from having the same name.</span></span>  
  
 <span data-ttu-id="82371-107">**✓ DO** użyć nazwy stabilny, niezależny od wersji produktu w drugiej nazwy przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="82371-107">**✓ DO** use a stable, version-independent product name at the second level of a namespace name.</span></span>  
  
 <span data-ttu-id="82371-108">**X DO NOT** Użyj hierarchii organizacji na podstawie nazw w hierarchii obszaru nazw, ponieważ nazwy grup w ramach firmy mogą być krótkotrwały.</span><span class="sxs-lookup"><span data-stu-id="82371-108">**X DO NOT** use organizational hierarchies as the basis for names in namespace hierarchies, because group names within corporations tend to be short-lived.</span></span> <span data-ttu-id="82371-109">Organizuj hierarchię przestrzeni nazw wokół grup powiązanych technologii.</span><span class="sxs-lookup"><span data-stu-id="82371-109">Organize the hierarchy of namespaces around groups of related technologies.</span></span>  
  
 <span data-ttu-id="82371-110">**✓ DO** PascalCasing i składniki oddzielne przestrzeni nazw za pomocą kropek (np. `Microsoft.Office.PowerPoint`).</span><span class="sxs-lookup"><span data-stu-id="82371-110">**✓ DO** use PascalCasing, and separate namespace components with periods (e.g., `Microsoft.Office.PowerPoint`).</span></span> <span data-ttu-id="82371-111">Jeśli Marka używa nietradycyjnej wielkości liter, należy postępować zgodnie z wielkością liter zdefiniowaną przez markę, nawet jeśli odbiega od normalnej wielkości liter przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="82371-111">If your brand employs nontraditional casing, you should follow the casing defined by your brand, even if it deviates from normal namespace casing.</span></span>  
  
 <span data-ttu-id="82371-112">**✓ CONSIDER** przy użyciu nazwy przestrzeni nazw w liczbie mnogiej, gdzie jest to odpowiednie.</span><span class="sxs-lookup"><span data-stu-id="82371-112">**✓ CONSIDER** using plural namespace names where appropriate.</span></span>  
  
 <span data-ttu-id="82371-113">Na przykład użyj `System.Collections`, a nie `System.Collection`.</span><span class="sxs-lookup"><span data-stu-id="82371-113">For example, use `System.Collections` instead of `System.Collection`.</span></span> <span data-ttu-id="82371-114">Jednak nazwy marki i akronimy są wyjątkami od tej reguły.</span><span class="sxs-lookup"><span data-stu-id="82371-114">Brand names and acronyms are exceptions to this rule, however.</span></span> <span data-ttu-id="82371-115">Na przykład użyj `System.IO`, a nie `System.IOs`.</span><span class="sxs-lookup"><span data-stu-id="82371-115">For example, use `System.IO` instead of `System.IOs`.</span></span>  
  
 <span data-ttu-id="82371-116">**X DO NOT** Użyj takiej samej nazwy przestrzeni nazw i typ w tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="82371-116">**X DO NOT** use the same name for a namespace and a type in that namespace.</span></span>  
  
 <span data-ttu-id="82371-117">Na przykład nie należy używać `Debug` jako nazwy przestrzeni nazw, a następnie dostarczać klasę o nazwie `Debug` w tej samej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="82371-117">For example, do not use `Debug` as a namespace name and then also provide a class named `Debug` in the same namespace.</span></span> <span data-ttu-id="82371-118">Kilka kompilatorów wymaga, aby te typy były w pełni kwalifikowane.</span><span class="sxs-lookup"><span data-stu-id="82371-118">Several compilers require such types to be fully qualified.</span></span>  
  
### <a name="namespaces-and-type-name-conflicts"></a><span data-ttu-id="82371-119">Konflikty nazw i nazw typów</span><span class="sxs-lookup"><span data-stu-id="82371-119">Namespaces and Type Name Conflicts</span></span>  
 <span data-ttu-id="82371-120">**X DO NOT** wprowadzenie nazwy typu ogólnego, takich jak `Element`, `Node`, `Log`, i `Message`.</span><span class="sxs-lookup"><span data-stu-id="82371-120">**X DO NOT** introduce generic type names such as `Element`, `Node`, `Log`, and `Message`.</span></span>  
  
 <span data-ttu-id="82371-121">Istnieje bardzo wysokie prawdopodobieństwo, że spowoduje to powstanie konfliktów nazw typu w typowych scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="82371-121">There is a very high probability that doing so will lead to type name conflicts in common scenarios.</span></span> <span data-ttu-id="82371-122">Należy zakwalifikować nazwy typów ogólnych (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).</span><span class="sxs-lookup"><span data-stu-id="82371-122">You should qualify the generic type names (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).</span></span>  
  
 <span data-ttu-id="82371-123">Istnieją szczegółowe wskazówki dotyczące unikania konfliktów nazw typów dla różnych kategorii przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="82371-123">There are specific guidelines for avoiding type name conflicts for different categories of namespaces.</span></span>  
  
- <span data-ttu-id="82371-124">**Przestrzenie nazw modelu aplikacji**</span><span class="sxs-lookup"><span data-stu-id="82371-124">**Application model namespaces**</span></span>  
  
     <span data-ttu-id="82371-125">Przestrzenie nazw należące do pojedynczego modelu aplikacji są często używane razem, ale są prawie nigdy nieużywane z przestrzeniami nazw innych modeli aplikacji.</span><span class="sxs-lookup"><span data-stu-id="82371-125">Namespaces belonging to a single application model are very often used together, but they are almost never used with namespaces of other application models.</span></span> <span data-ttu-id="82371-126">Na przykład przestrzeń nazw <xref:System.Windows.Forms?displayProperty=nameWithType> jest bardzo rzadko używana razem z przestrzenią nazw <xref:System.Web.UI?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="82371-126">For example, the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace is very rarely used together with the <xref:System.Web.UI?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="82371-127">Poniżej znajduje się lista dobrze znanych grup przestrzeni nazw modelu aplikacji:</span><span class="sxs-lookup"><span data-stu-id="82371-127">The following is a list of well-known application model namespace groups:</span></span>  
  
     `System.Windows*`   
     `System.Web.UI*`  
  
     <span data-ttu-id="82371-128">**X DO NOT** nadać tej samej nazwy dla typów w przestrzeniach nazw w obrębie modelu pojedynczej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="82371-128">**X DO NOT** give the same name to types in namespaces within a single application model.</span></span>  
  
     <span data-ttu-id="82371-129">Na przykład nie należy dodawać typu o nazwie `Page` do przestrzeni nazw <xref:System.Web.UI.Adapters?displayProperty=nameWithType>, ponieważ przestrzeń nazw <xref:System.Web.UI?displayProperty=nameWithType> zawiera już typ o nazwie `Page`.</span><span class="sxs-lookup"><span data-stu-id="82371-129">For example, do not add a type named `Page` to the <xref:System.Web.UI.Adapters?displayProperty=nameWithType> namespace, because the <xref:System.Web.UI?displayProperty=nameWithType> namespace already contains a type named `Page`.</span></span>  
  
- <span data-ttu-id="82371-130">**Przestrzenie nazw infrastruktury**</span><span class="sxs-lookup"><span data-stu-id="82371-130">**Infrastructure namespaces**</span></span>  
  
     <span data-ttu-id="82371-131">Ta grupa zawiera przestrzenie nazw, które są rzadko importowane podczas opracowywania typowych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="82371-131">This group contains namespaces that are rarely imported during development of common applications.</span></span> <span data-ttu-id="82371-132">Na przykład `.Design` przestrzenie nazw są używane głównie podczas opracowywania narzędzi programistycznych.</span><span class="sxs-lookup"><span data-stu-id="82371-132">For example, `.Design` namespaces are mainly used when developing programming tools.</span></span> <span data-ttu-id="82371-133">Unikanie konfliktów z typami w tych obszarach nazw nie jest krytyczne.</span><span class="sxs-lookup"><span data-stu-id="82371-133">Avoiding conflicts with types in these namespaces is not critical.</span></span>  
  
- <span data-ttu-id="82371-134">**Podstawowe przestrzenie nazw**</span><span class="sxs-lookup"><span data-stu-id="82371-134">**Core namespaces**</span></span>  
  
     <span data-ttu-id="82371-135">Podstawowe przestrzenie nazw obejmują wszystkie `System` przestrzenie nazw, z wyłączeniem przestrzeni nazw modeli aplikacji i przestrzeni nazw infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="82371-135">Core namespaces include all `System` namespaces, excluding namespaces of the application models and the Infrastructure namespaces.</span></span> <span data-ttu-id="82371-136">Podstawowe przestrzenie nazw obejmują między innymi `System`, `System.IO`, `System.Xml`i `System.Net`.</span><span class="sxs-lookup"><span data-stu-id="82371-136">Core namespaces include, among others, `System`, `System.IO`, `System.Xml`, and `System.Net`.</span></span>  
  
     <span data-ttu-id="82371-137">**X DO NOT** zapewnia typy nazw, które spowodowałoby to konflikt z dowolnego typu w przestrzeniach nazw Core.</span><span class="sxs-lookup"><span data-stu-id="82371-137">**X DO NOT** give types names that would conflict with any type in the Core namespaces.</span></span>  
  
     <span data-ttu-id="82371-138">Na przykład nigdy nie używaj `Stream` jako nazwy typu.</span><span class="sxs-lookup"><span data-stu-id="82371-138">For example, never use `Stream` as a type name.</span></span> <span data-ttu-id="82371-139">Wystąpił konflikt z <xref:System.IO.Stream?displayProperty=nameWithType>, bardzo często używanym typem.</span><span class="sxs-lookup"><span data-stu-id="82371-139">It would conflict with <xref:System.IO.Stream?displayProperty=nameWithType>, a very commonly used type.</span></span>  
  
- <span data-ttu-id="82371-140">**Grupy przestrzeni nazw technologii**</span><span class="sxs-lookup"><span data-stu-id="82371-140">**Technology namespace groups**</span></span>  
  
     <span data-ttu-id="82371-141">Ta kategoria zawiera wszystkie przestrzenie nazw zawierające te same dwa węzły przestrzeni nazw `(<Company>.<Technology>*`), takie jak `Microsoft.Build.Utilities` i `Microsoft.Build.Tasks`.</span><span class="sxs-lookup"><span data-stu-id="82371-141">This category includes all namespaces with the same first two namespace nodes `(<Company>.<Technology>*`), such as `Microsoft.Build.Utilities` and `Microsoft.Build.Tasks`.</span></span> <span data-ttu-id="82371-142">Ważne jest, aby typy należące do jednej technologii nie powodowały konfliktów ze sobą.</span><span class="sxs-lookup"><span data-stu-id="82371-142">It is important that types belonging to a single technology do not conflict with each other.</span></span>  
  
     <span data-ttu-id="82371-143">**X DO NOT** przypisać nazwy typów, które spowodowałoby to konflikt z innymi typami w ramach pojedynczego technologii.</span><span class="sxs-lookup"><span data-stu-id="82371-143">**X DO NOT** assign type names that would conflict with other types within a single technology.</span></span>  
  
     <span data-ttu-id="82371-144">**X DO NOT** wprowadzenie typu konfliktów nazw między typami w przestrzeniach nazw technologii i przestrzeń nazw modelu aplikacji (chyba że technologii nie jest przeznaczona do użycia z modelem aplikacji).</span><span class="sxs-lookup"><span data-stu-id="82371-144">**X DO NOT** introduce type name conflicts between types in technology namespaces and an application model namespace (unless the technology is not intended to be used with the application model).</span></span>  
  
 <span data-ttu-id="82371-145">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="82371-145">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="82371-146">*Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="82371-146">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82371-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="82371-147">See also</span></span>

- [<span data-ttu-id="82371-148">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="82371-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="82371-149">Wskazówki dotyczące nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="82371-149">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
