---
title: Nazwy przestrzeni nazw
ms.date: 03/30/2017
helpviewer_keywords:
- names [.NET Framework], conflicts
- names [.NET Framework], namespaces
- type names, conflicts
- namespaces [.NET Framework], names
- names [.NET Framework], type names
ms.assetid: a49058d2-0276-43a7-9502-04adddf857b2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6d68966f60c5039fd67195a03facc1586b9ed154
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45591727"
---
# <a name="names-of-namespaces"></a><span data-ttu-id="755a6-102">Nazwy przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="755a6-102">Names of Namespaces</span></span>
<span data-ttu-id="755a6-103">Jako przy użyciu innych zasadach nazywania celem podczas nadawania nazw przestrzeni nazw jest utworzenie przejrzystości wystarczające do programisty należy od razu wiedzieć, co to jest prawdopodobnie zawartości przestrzeni nazw przy użyciu platformy.</span><span class="sxs-lookup"><span data-stu-id="755a6-103">As with other naming guidelines, the goal when naming namespaces is creating sufficient clarity for the programmer using the framework to immediately know what the content of the namespace is likely to be.</span></span> <span data-ttu-id="755a6-104">Następujący szablon określa zasady nazewnictwa przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="755a6-104">The following template specifies the general rule for naming namespaces:</span></span>  
  
 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`  
  
 <span data-ttu-id="755a6-105">Poniżej przedstawiono przykłady:</span><span class="sxs-lookup"><span data-stu-id="755a6-105">The following are examples:</span></span>  
  
 `Fabrikam.Math`  
 `Litware.Security`  
  
 <span data-ttu-id="755a6-106">**✓ DO** prefiksu nazwy przestrzeni nazw o nazwie firmy, aby zapobiec przestrzenie nazw różnych firm z o tej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="755a6-106">**✓ DO** prefix namespace names with a company name to prevent namespaces from different companies from having the same name.</span></span>  
  
 <span data-ttu-id="755a6-107">**✓ DO** użyć nazwy stabilny, niezależny od wersji produktu w drugiej nazwy przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="755a6-107">**✓ DO** use a stable, version-independent product name at the second level of a namespace name.</span></span>  
  
 <span data-ttu-id="755a6-108">**X DO NOT** Użyj hierarchii organizacji na podstawie nazw w hierarchii obszaru nazw, ponieważ nazwy grup w ramach firmy mogą być krótkotrwały.</span><span class="sxs-lookup"><span data-stu-id="755a6-108">**X DO NOT** use organizational hierarchies as the basis for names in namespace hierarchies, because group names within corporations tend to be short-lived.</span></span> <span data-ttu-id="755a6-109">Organizuj hierarchii przestrzenie nazw wokół grup powiązanych technologii.</span><span class="sxs-lookup"><span data-stu-id="755a6-109">Organize the hierarchy of namespaces around groups of related technologies.</span></span>  
  
 <span data-ttu-id="755a6-110">**✓ DO** PascalCasing i składniki oddzielne przestrzeni nazw za pomocą kropek (np. `Microsoft.Office.PowerPoint`).</span><span class="sxs-lookup"><span data-stu-id="755a6-110">**✓ DO** use PascalCasing, and separate namespace components with periods (e.g., `Microsoft.Office.PowerPoint`).</span></span> <span data-ttu-id="755a6-111">Jeśli swoją markę wykorzystuje nietradycyjnych wielkości liter, powinien być zgodny definicją Twojej marki wielkości liter, nawet wtedy, gdy odbiega od wielkość liter w wyrazie normalne przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="755a6-111">If your brand employs nontraditional casing, you should follow the casing defined by your brand, even if it deviates from normal namespace casing.</span></span>  
  
 <span data-ttu-id="755a6-112">**✓ CONSIDER** przy użyciu nazwy przestrzeni nazw w liczbie mnogiej, gdzie jest to odpowiednie.</span><span class="sxs-lookup"><span data-stu-id="755a6-112">**✓ CONSIDER** using plural namespace names where appropriate.</span></span>  
  
 <span data-ttu-id="755a6-113">Na przykład użyć `System.Collections` zamiast `System.Collection`.</span><span class="sxs-lookup"><span data-stu-id="755a6-113">For example, use `System.Collections` instead of `System.Collection`.</span></span> <span data-ttu-id="755a6-114">Nazw marek i akronimów są jednak wyjątki od tej reguły.</span><span class="sxs-lookup"><span data-stu-id="755a6-114">Brand names and acronyms are exceptions to this rule, however.</span></span> <span data-ttu-id="755a6-115">Na przykład użyć `System.IO` zamiast `System.IOs`.</span><span class="sxs-lookup"><span data-stu-id="755a6-115">For example, use `System.IO` instead of `System.IOs`.</span></span>  
  
 <span data-ttu-id="755a6-116">**X DO NOT** Użyj takiej samej nazwy przestrzeni nazw i typ w tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="755a6-116">**X DO NOT** use the same name for a namespace and a type in that namespace.</span></span>  
  
 <span data-ttu-id="755a6-117">Na przykład nie używaj `Debug` jako przestrzeń nazw nazwę, a także podać klasę o nazwie `Debug` w tej samej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="755a6-117">For example, do not use `Debug` as a namespace name and then also provide a class named `Debug` in the same namespace.</span></span> <span data-ttu-id="755a6-118">Kompilatory kilka wymagają takich typów być w pełni kwalifikowana.</span><span class="sxs-lookup"><span data-stu-id="755a6-118">Several compilers require such types to be fully qualified.</span></span>  
  
### <a name="namespaces-and-type-name-conflicts"></a><span data-ttu-id="755a6-119">Przestrzenie nazw i typ konflikty nazw</span><span class="sxs-lookup"><span data-stu-id="755a6-119">Namespaces and Type Name Conflicts</span></span>  
 <span data-ttu-id="755a6-120">**X DO NOT** wprowadzenie nazwy typu ogólnego, takich jak `Element`, `Node`, `Log`, i `Message`.</span><span class="sxs-lookup"><span data-stu-id="755a6-120">**X DO NOT** introduce generic type names such as `Element`, `Node`, `Log`, and `Message`.</span></span>  
  
 <span data-ttu-id="755a6-121">Istnieje wysokie prawdopodobieństwo, że w ten sposób doprowadzi do wpisz nazwę powoduje konflikt w typowych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="755a6-121">There is a very high probability that doing so will lead to type name conflicts in common scenarios.</span></span> <span data-ttu-id="755a6-122">Należy kwalifikowania nazwy typów ogólnych (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).</span><span class="sxs-lookup"><span data-stu-id="755a6-122">You should qualify the generic type names (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).</span></span>  
  
 <span data-ttu-id="755a6-123">Istnieją konkretne wskazówki dotyczące unikanie konflikt nazw typu różne kategorie przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="755a6-123">There are specific guidelines for avoiding type name conflicts for different categories of namespaces.</span></span>  
  
-   <span data-ttu-id="755a6-124">**Przestrzenie nazw modelu aplikacji**</span><span class="sxs-lookup"><span data-stu-id="755a6-124">**Application model namespaces**</span></span>  
  
     <span data-ttu-id="755a6-125">Przestrzenie nazw należących do modelu jednej aplikacji są bardzo często używane ze sobą, ale prawie nigdy nie są one używane przestrzenie nazw innych modeli aplikacji.</span><span class="sxs-lookup"><span data-stu-id="755a6-125">Namespaces belonging to a single application model are very often used together, but they are almost never used with namespaces of other application models.</span></span> <span data-ttu-id="755a6-126">Na przykład <xref:System.Windows.Forms?displayProperty=nameWithType> przestrzeni nazw jest bardzo rzadko używana razem z <xref:System.Web.UI?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="755a6-126">For example, the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace is very rarely used together with the <xref:System.Web.UI?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="755a6-127">Oto lista aplikacji dobrze znanego modelu przestrzeni nazw grup:</span><span class="sxs-lookup"><span data-stu-id="755a6-127">The following is a list of well-known application model namespace groups:</span></span>  
  
     `System.Windows*`   
     `System.Web.UI*`  
  
     <span data-ttu-id="755a6-128">**X DO NOT** nadać tej samej nazwy dla typów w przestrzeniach nazw w obrębie modelu pojedynczej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="755a6-128">**X DO NOT** give the same name to types in namespaces within a single application model.</span></span>  
  
     <span data-ttu-id="755a6-129">Na przykład, należy dodawać typu o nazwie `Page` do <xref:System.Web.UI.Adapters?displayProperty=nameWithType> przestrzeni nazw, ponieważ <xref:System.Web.UI?displayProperty=nameWithType> przestrzeń nazw zawiera już typ o nazwie `Page`.</span><span class="sxs-lookup"><span data-stu-id="755a6-129">For example, do not add a type named `Page` to the <xref:System.Web.UI.Adapters?displayProperty=nameWithType> namespace, because the <xref:System.Web.UI?displayProperty=nameWithType> namespace already contains a type named `Page`.</span></span>  
  
-   <span data-ttu-id="755a6-130">**Przestrzenie nazw infrastruktury**</span><span class="sxs-lookup"><span data-stu-id="755a6-130">**Infrastructure namespaces**</span></span>  
  
     <span data-ttu-id="755a6-131">Ta grupa zawiera przestrzenie nazw, które rzadko są importowane podczas tworzenia typowych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="755a6-131">This group contains namespaces that are rarely imported during development of common applications.</span></span> <span data-ttu-id="755a6-132">Na przykład `.Design` przestrzenie nazw są używane głównie podczas tworzenia programowania narzędzi.</span><span class="sxs-lookup"><span data-stu-id="755a6-132">For example, `.Design` namespaces are mainly used when developing programming tools.</span></span> <span data-ttu-id="755a6-133">Unikanie konfliktów z typami w tych obszarach nazw nie jest krytyczny.</span><span class="sxs-lookup"><span data-stu-id="755a6-133">Avoiding conflicts with types in these namespaces is not critical.</span></span>  
  
-   <span data-ttu-id="755a6-134">**Przestrzenie nazw Core**</span><span class="sxs-lookup"><span data-stu-id="755a6-134">**Core namespaces**</span></span>  
  
     <span data-ttu-id="755a6-135">Przestrzenie nazw Core obejmuje wszystkie `System` przestrzeni nazw, z wyłączeniem przestrzeni nazw modeli aplikacji i infrastruktury przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="755a6-135">Core namespaces include all `System` namespaces, excluding namespaces of the application models and the Infrastructure namespaces.</span></span> <span data-ttu-id="755a6-136">Przestrzenie nazw Core należą między innymi, `System`, `System.IO`, `System.Xml`, i `System.Net`.</span><span class="sxs-lookup"><span data-stu-id="755a6-136">Core namespaces include, among others, `System`, `System.IO`, `System.Xml`, and `System.Net`.</span></span>  
  
     <span data-ttu-id="755a6-137">**X DO NOT** zapewnia typy nazw, które spowodowałoby to konflikt z dowolnego typu w przestrzeniach nazw Core.</span><span class="sxs-lookup"><span data-stu-id="755a6-137">**X DO NOT** give types names that would conflict with any type in the Core namespaces.</span></span>  
  
     <span data-ttu-id="755a6-138">Na przykład nie wolno używać `Stream` jako nazwy typu.</span><span class="sxs-lookup"><span data-stu-id="755a6-138">For example, never use `Stream` as a type name.</span></span> <span data-ttu-id="755a6-139">Spowodowałoby to konflikt z <xref:System.IO.Stream?displayProperty=nameWithType>, bardzo często używane typu.</span><span class="sxs-lookup"><span data-stu-id="755a6-139">It would conflict with <xref:System.IO.Stream?displayProperty=nameWithType>, a very commonly used type.</span></span>  
  
-   <span data-ttu-id="755a6-140">**Technologia przestrzeni nazw grup**</span><span class="sxs-lookup"><span data-stu-id="755a6-140">**Technology namespace groups**</span></span>  
  
     <span data-ttu-id="755a6-141">Ta kategoria zawiera wszystkie przestrzenie nazw przy użyciu tego samego pierwsze dwa węzły przestrzeni nazw `(<Company>.<Technology>*`), takie jak `Microsoft.Build.Utilities` i `Microsoft.Build.Tasks`.</span><span class="sxs-lookup"><span data-stu-id="755a6-141">This category includes all namespaces with the same first two namespace nodes `(<Company>.<Technology>*`), such as `Microsoft.Build.Utilities` and `Microsoft.Build.Tasks`.</span></span> <span data-ttu-id="755a6-142">Należy pamiętać, że typy należące do pojedynczego technologia nie kolidują ze sobą.</span><span class="sxs-lookup"><span data-stu-id="755a6-142">It is important that types belonging to a single technology do not conflict with each other.</span></span>  
  
     <span data-ttu-id="755a6-143">**X DO NOT** przypisać nazwy typów, które spowodowałoby to konflikt z innymi typami w ramach pojedynczego technologii.</span><span class="sxs-lookup"><span data-stu-id="755a6-143">**X DO NOT** assign type names that would conflict with other types within a single technology.</span></span>  
  
     <span data-ttu-id="755a6-144">**X DO NOT** wprowadzenie typu konfliktów nazw między typami w przestrzeniach nazw technologii i przestrzeń nazw modelu aplikacji (chyba że technologii nie jest przeznaczona do użycia z modelem aplikacji).</span><span class="sxs-lookup"><span data-stu-id="755a6-144">**X DO NOT** introduce type name conflicts between types in technology namespaces and an application model namespace (unless the technology is not intended to be used with the application model).</span></span>  
  
 <span data-ttu-id="755a6-145">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="755a6-145">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="755a6-146">*Przedrukowano przez uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: konwencje Idiomy i wzorce wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams opublikowane 22 Oct 2008 przez Professional Addison Wesley jako część serii rozwoju Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="755a6-146">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="755a6-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="755a6-147">See also</span></span>

- [<span data-ttu-id="755a6-148">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="755a6-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="755a6-149">Wskazówki dotyczące nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="755a6-149">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
