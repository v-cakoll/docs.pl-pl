---
title: Nazwy przestrzeni nazw
description: Te wskazówki dotyczą nazewnictwa przestrzeni nazw w ramach wytycznych dotyczących projektowania bibliotek, które zwiększają i współpracują z bibliotekami platformy .NET.
ms.date: 10/22/2008
helpviewer_keywords:
- names [.NET Framework], conflicts
- names [.NET Framework], namespaces
- type names, conflicts
- namespaces [.NET Framework], names
- names [.NET Framework], type names
ms.assetid: a49058d2-0276-43a7-9502-04adddf857b2
ms.openlocfilehash: e435e0281165b4a9f12bbccbeb10401b57375dcb
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290204"
---
# <a name="names-of-namespaces"></a><span data-ttu-id="3e310-103">Nazwy przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="3e310-103">Names of Namespaces</span></span>
<span data-ttu-id="3e310-104">Podobnie jak w przypadku innych wytycznych dotyczących nazewnictwa, celem podczas nazewnictwa przestrzeni nazw jest utworzenie wystarczającej przejrzystości dla programisty korzystającego z platformy, aby natychmiast znać zawartość przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="3e310-104">As with other naming guidelines, the goal when naming namespaces is creating sufficient clarity for the programmer using the framework to immediately know what the content of the namespace is likely to be.</span></span> <span data-ttu-id="3e310-105">Następujący szablon określa ogólną regułę nazewnictwa przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="3e310-105">The following template specifies the general rule for naming namespaces:</span></span>

 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`

 <span data-ttu-id="3e310-106">Poniżej przedstawiono przykłady:</span><span class="sxs-lookup"><span data-stu-id="3e310-106">The following are examples:</span></span>

 <span data-ttu-id="3e310-107">`Fabrikam.Math` `Litware.Security`</span><span class="sxs-lookup"><span data-stu-id="3e310-107">`Fabrikam.Math` `Litware.Security`</span></span>

 <span data-ttu-id="3e310-108">✔️ NALEŻY prefiksować nazwy przestrzeni nazw z nazwą firmy, aby zapobiec istnieniu przez obszary nazw różnych firm.</span><span class="sxs-lookup"><span data-stu-id="3e310-108">✔️ DO prefix namespace names with a company name to prevent namespaces from different companies from having the same name.</span></span>

 <span data-ttu-id="3e310-109">✔️ Użyj stabilnej, niezależnej od wersji nazwy produktu na drugim poziomie nazwy przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="3e310-109">✔️ DO use a stable, version-independent product name at the second level of a namespace name.</span></span>

 <span data-ttu-id="3e310-110">❌NIE używaj hierarchii organizacyjnych jako podstawy nazw w hierarchiach przestrzeni nazw, ponieważ nazwy grup w firmach są ograniczone do krótkotrwałego życia.</span><span class="sxs-lookup"><span data-stu-id="3e310-110">❌ DO NOT use organizational hierarchies as the basis for names in namespace hierarchies, because group names within corporations tend to be short-lived.</span></span> <span data-ttu-id="3e310-111">Organizuj hierarchię przestrzeni nazw wokół grup powiązanych technologii.</span><span class="sxs-lookup"><span data-stu-id="3e310-111">Organize the hierarchy of namespaces around groups of related technologies.</span></span>

 <span data-ttu-id="3e310-112">✔️ używać PascalCasing i oddzielaj składniki przestrzeni nazw z okresami (np. `Microsoft.Office.PowerPoint` ).</span><span class="sxs-lookup"><span data-stu-id="3e310-112">✔️ DO use PascalCasing, and separate namespace components with periods (e.g., `Microsoft.Office.PowerPoint`).</span></span> <span data-ttu-id="3e310-113">Jeśli Marka używa nietradycyjnej wielkości liter, należy postępować zgodnie z wielkością liter zdefiniowaną przez markę, nawet jeśli odbiega od normalnej wielkości liter przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="3e310-113">If your brand employs nontraditional casing, you should follow the casing defined by your brand, even if it deviates from normal namespace casing.</span></span>

 <span data-ttu-id="3e310-114">✔️ ROZWAŻYĆ użycie nazw w liczbie mnogiej nazw, tam gdzie to konieczne.</span><span class="sxs-lookup"><span data-stu-id="3e310-114">✔️ CONSIDER using plural namespace names where appropriate.</span></span>

 <span data-ttu-id="3e310-115">Na przykład: użyj opcji `System.Collections` zamiast `System.Collection`.</span><span class="sxs-lookup"><span data-stu-id="3e310-115">For example, use `System.Collections` instead of `System.Collection`.</span></span> <span data-ttu-id="3e310-116">Jednak nazwy marki i akronimy są wyjątkami od tej reguły.</span><span class="sxs-lookup"><span data-stu-id="3e310-116">Brand names and acronyms are exceptions to this rule, however.</span></span> <span data-ttu-id="3e310-117">Na przykład: użyj opcji `System.IO` zamiast `System.IOs`.</span><span class="sxs-lookup"><span data-stu-id="3e310-117">For example, use `System.IO` instead of `System.IOs`.</span></span>

 <span data-ttu-id="3e310-118">❌NIE należy używać tej samej nazwy dla przestrzeni nazw i typu w tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="3e310-118">❌ DO NOT use the same name for a namespace and a type in that namespace.</span></span>

 <span data-ttu-id="3e310-119">Na przykład nie należy używać `Debug` jako nazwy przestrzeni nazw, a następnie dostarczać klasy o nazwie `Debug` w tej samej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="3e310-119">For example, do not use `Debug` as a namespace name and then also provide a class named `Debug` in the same namespace.</span></span> <span data-ttu-id="3e310-120">Kilka kompilatorów wymaga, aby te typy były w pełni kwalifikowane.</span><span class="sxs-lookup"><span data-stu-id="3e310-120">Several compilers require such types to be fully qualified.</span></span>

### <a name="namespaces-and-type-name-conflicts"></a><span data-ttu-id="3e310-121">Konflikty nazw i nazw typów</span><span class="sxs-lookup"><span data-stu-id="3e310-121">Namespaces and Type Name Conflicts</span></span>
 <span data-ttu-id="3e310-122">❌Nie należy wprowadzać nazw typów ogólnych, takich jak `Element` , `Node` , `Log` i `Message` .</span><span class="sxs-lookup"><span data-stu-id="3e310-122">❌ DO NOT introduce generic type names such as `Element`, `Node`, `Log`, and `Message`.</span></span>

 <span data-ttu-id="3e310-123">Istnieje bardzo wysokie prawdopodobieństwo, że spowoduje to powstanie konfliktów nazw typu w typowych scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="3e310-123">There is a very high probability that doing so will lead to type name conflicts in common scenarios.</span></span> <span data-ttu-id="3e310-124">Należy zakwalifikować nazwy typów ogólnych ( `FormElement` , `XmlNode` ,, `EventLog` `SoapMessage` ).</span><span class="sxs-lookup"><span data-stu-id="3e310-124">You should qualify the generic type names (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).</span></span>

 <span data-ttu-id="3e310-125">Istnieją szczegółowe wskazówki dotyczące unikania konfliktów nazw typów dla różnych kategorii przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="3e310-125">There are specific guidelines for avoiding type name conflicts for different categories of namespaces.</span></span>

- <span data-ttu-id="3e310-126">**Przestrzenie nazw modelu aplikacji**</span><span class="sxs-lookup"><span data-stu-id="3e310-126">**Application model namespaces**</span></span>

     <span data-ttu-id="3e310-127">Przestrzenie nazw należące do pojedynczego modelu aplikacji są często używane razem, ale są prawie nigdy nieużywane z przestrzeniami nazw innych modeli aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3e310-127">Namespaces belonging to a single application model are very often used together, but they are almost never used with namespaces of other application models.</span></span> <span data-ttu-id="3e310-128">Na przykład <xref:System.Windows.Forms?displayProperty=nameWithType> przestrzeń nazw jest bardzo rzadko używana razem z <xref:System.Web.UI?displayProperty=nameWithType> przestrzenią nazw.</span><span class="sxs-lookup"><span data-stu-id="3e310-128">For example, the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace is very rarely used together with the <xref:System.Web.UI?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="3e310-129">Poniżej znajduje się lista dobrze znanych grup przestrzeni nazw modelu aplikacji:</span><span class="sxs-lookup"><span data-stu-id="3e310-129">The following is a list of well-known application model namespace groups:</span></span>

     <span data-ttu-id="3e310-130">`System.Windows*` `System.Web.UI*`</span><span class="sxs-lookup"><span data-stu-id="3e310-130">`System.Windows*` `System.Web.UI*`</span></span>

     <span data-ttu-id="3e310-131">❌NIE należy dawać tej samej nazwy do typów w przestrzeniach nazw w ramach jednego modelu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3e310-131">❌ DO NOT give the same name to types in namespaces within a single application model.</span></span>

     <span data-ttu-id="3e310-132">Na przykład nie należy dodawać typu o nazwie `Page` do <xref:System.Web.UI.Adapters?displayProperty=nameWithType> przestrzeni nazw, ponieważ <xref:System.Web.UI?displayProperty=nameWithType> przestrzeń nazw zawiera już typ o nazwie `Page` .</span><span class="sxs-lookup"><span data-stu-id="3e310-132">For example, do not add a type named `Page` to the <xref:System.Web.UI.Adapters?displayProperty=nameWithType> namespace, because the <xref:System.Web.UI?displayProperty=nameWithType> namespace already contains a type named `Page`.</span></span>

- <span data-ttu-id="3e310-133">**Przestrzenie nazw infrastruktury**</span><span class="sxs-lookup"><span data-stu-id="3e310-133">**Infrastructure namespaces**</span></span>

     <span data-ttu-id="3e310-134">Ta grupa zawiera przestrzenie nazw, które są rzadko importowane podczas opracowywania typowych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3e310-134">This group contains namespaces that are rarely imported during development of common applications.</span></span> <span data-ttu-id="3e310-135">Na przykład `.Design` przestrzenie nazw są używane głównie podczas opracowywania narzędzi programistycznych.</span><span class="sxs-lookup"><span data-stu-id="3e310-135">For example, `.Design` namespaces are mainly used when developing programming tools.</span></span> <span data-ttu-id="3e310-136">Unikanie konfliktów z typami w tych obszarach nazw nie jest krytyczne.</span><span class="sxs-lookup"><span data-stu-id="3e310-136">Avoiding conflicts with types in these namespaces is not critical.</span></span>

- <span data-ttu-id="3e310-137">**Podstawowe przestrzenie nazw**</span><span class="sxs-lookup"><span data-stu-id="3e310-137">**Core namespaces**</span></span>

     <span data-ttu-id="3e310-138">Podstawowe przestrzenie nazw obejmują wszystkie `System` przestrzenie nazw, z wyłączeniem przestrzeni nazw modeli aplikacji i przestrzeni nazw infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="3e310-138">Core namespaces include all `System` namespaces, excluding namespaces of the application models and the Infrastructure namespaces.</span></span> <span data-ttu-id="3e310-139">Podstawowe przestrzenie nazw obejmują między innymi, `System` ,, `System.IO` `System.Xml` , i `System.Net` .</span><span class="sxs-lookup"><span data-stu-id="3e310-139">Core namespaces include, among others, `System`, `System.IO`, `System.Xml`, and `System.Net`.</span></span>

     <span data-ttu-id="3e310-140">❌NIE należy przyznawać nazw typów, które mogłyby powodować konflikt z dowolnym typem w podstawowych obszarach nazw.</span><span class="sxs-lookup"><span data-stu-id="3e310-140">❌ DO NOT give types names that would conflict with any type in the Core namespaces.</span></span>

     <span data-ttu-id="3e310-141">Na przykład nigdy nie używaj `Stream` jako nazwy typu.</span><span class="sxs-lookup"><span data-stu-id="3e310-141">For example, never use `Stream` as a type name.</span></span> <span data-ttu-id="3e310-142">Wystąpił konflikt z <xref:System.IO.Stream?displayProperty=nameWithType> , bardzo często używanym typem.</span><span class="sxs-lookup"><span data-stu-id="3e310-142">It would conflict with <xref:System.IO.Stream?displayProperty=nameWithType>, a very commonly used type.</span></span>

- <span data-ttu-id="3e310-143">**Grupy przestrzeni nazw technologii**</span><span class="sxs-lookup"><span data-stu-id="3e310-143">**Technology namespace groups**</span></span>

     <span data-ttu-id="3e310-144">Ta kategoria zawiera wszystkie przestrzenie nazw z tymi samymi dwoma węzłami przestrzeni nazw `(<Company>.<Technology>*` , takimi jak `Microsoft.Build.Utilities` i `Microsoft.Build.Tasks` .</span><span class="sxs-lookup"><span data-stu-id="3e310-144">This category includes all namespaces with the same first two namespace nodes `(<Company>.<Technology>*`), such as `Microsoft.Build.Utilities` and `Microsoft.Build.Tasks`.</span></span> <span data-ttu-id="3e310-145">Ważne jest, aby typy należące do jednej technologii nie powodowały konfliktów ze sobą.</span><span class="sxs-lookup"><span data-stu-id="3e310-145">It is important that types belonging to a single technology do not conflict with each other.</span></span>

     <span data-ttu-id="3e310-146">❌Nie przypisuj nazw typów, które mogłyby powodować konflikt z innymi typami w ramach jednej technologii.</span><span class="sxs-lookup"><span data-stu-id="3e310-146">❌ DO NOT assign type names that would conflict with other types within a single technology.</span></span>

     <span data-ttu-id="3e310-147">❌NIE wprowadzaj konfliktów nazw typów między typami w przestrzeni nazw technologii i przestrzeni nazw modelu aplikacji (chyba że technologia nie jest przeznaczona do użycia z modelem aplikacji).</span><span class="sxs-lookup"><span data-stu-id="3e310-147">❌ DO NOT introduce type name conflicts between types in technology namespaces and an application model namespace (unless the technology is not intended to be used with the application model).</span></span>

 <span data-ttu-id="3e310-148">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="3e310-148">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="3e310-149">*Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="3e310-149">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="3e310-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3e310-150">See also</span></span>

- [<span data-ttu-id="3e310-151">Wskazówki dotyczące projektowania struktury</span><span class="sxs-lookup"><span data-stu-id="3e310-151">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="3e310-152">Wskazówki dotyczące nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="3e310-152">Naming Guidelines</span></span>](naming-guidelines.md)
