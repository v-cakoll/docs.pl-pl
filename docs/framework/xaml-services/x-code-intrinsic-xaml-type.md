---
title: x:Code — Typ funkcji XAML
ms.date: 03/30/2017
f1_keywords:
- Code
- x:Code
- xCode
helpviewer_keywords:
- Code directive in XAML [XAML Services]
- x:Code XAML directive element [XAML Services]
- XAML [XAML Services], x:Code directive element
ms.assetid: 87986b13-1a2e-4830-ae36-15f9dc5629e8
ms.openlocfilehash: 2b7713548b6269f079ef32b5bf1fe4fa630edcc8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053797"
---
# <a name="xcode-intrinsic-xaml-type"></a><span data-ttu-id="95388-102">x:Code — Typ funkcji XAML</span><span class="sxs-lookup"><span data-stu-id="95388-102">x:Code Intrinsic XAML Type</span></span>
<span data-ttu-id="95388-103">Umożliwia umieszczanie kodu w środowisku produkcyjnym XAML.</span><span class="sxs-lookup"><span data-stu-id="95388-103">Allows placement of code within a XAML production.</span></span> <span data-ttu-id="95388-104">Taki kod może być kompilowany przez dowolną implementację procesora XAML, która kompiluje kod XAML lub pozostawioną w środowisku produkcyjnym XAML w celu późniejszego użycia, na przykład interpretacji przez środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="95388-104">Such code can either be compiled by any XAML processor implementation that compiles XAML, or left in the XAML production for later uses such as interpretation by a runtime.</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="95388-105">Użycie elementu obiektu języka XAML</span><span class="sxs-lookup"><span data-stu-id="95388-105">XAML Object Element Usage</span></span>  
  
```xaml  
<x:Code>  
   // code instructions, usually enclosed by CDATA...  
</x:Code>  
```  
  
## <a name="remarks"></a><span data-ttu-id="95388-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="95388-106">Remarks</span></span>  
 <span data-ttu-id="95388-107">Kod wewnątrz `x:Code` elementu dyrektywy XAML jest nadal interpretowany w ogólnej przestrzeni nazw XML i udostępnionych przestrzeniach nazw XAML.</span><span class="sxs-lookup"><span data-stu-id="95388-107">The code within the `x:Code` XAML directive element is still interpreted within the general XML namespace and the XAML namespaces provided.</span></span> <span data-ttu-id="95388-108">W związku z tym zazwyczaj konieczne jest zawrzeć kod używany do `x:Code` `CDATA` wewnątrz segmentu.</span><span class="sxs-lookup"><span data-stu-id="95388-108">Therefore, it is usually necessary to enclose the code used for `x:Code` inside a `CDATA` segment.</span></span>  
  
 <span data-ttu-id="95388-109">`x:Code`nie jest dozwolony dla wszystkich możliwych mechanizmów wdrażania w środowisku produkcyjnym XAML.</span><span class="sxs-lookup"><span data-stu-id="95388-109">`x:Code` is not permitted for all possible deployment mechanisms of a XAML production.</span></span> <span data-ttu-id="95388-110">W określonych strukturach (na przykład WPF) kod musi być skompilowany.</span><span class="sxs-lookup"><span data-stu-id="95388-110">In specific frameworks (for example WPF) the code must be compiled.</span></span> <span data-ttu-id="95388-111">W innych strukturach `x:Code` użycie może być ogólnie niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="95388-111">In other frameworks, `x:Code` usage might be generally disallowed.</span></span>  
  
 <span data-ttu-id="95388-112">W przypadku struktur, które zezwalają na zawartość zarządzaną `x:Code` , prawidłowy kompilator języka do użycia w przypadku `x:Code` zawartości jest określany przez ustawienia i cele projektu zawierającego, który jest używany do kompilowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="95388-112">For frameworks that permit managed `x:Code` content, the correct language compiler to use for `x:Code` content is determined by settings and targets of the containing project that is used to compile the application.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="95388-113">Uwagi dotyczące użycia WPF</span><span class="sxs-lookup"><span data-stu-id="95388-113">WPF Usage Notes</span></span>  
 <span data-ttu-id="95388-114">Kod zadeklarowany `x:Code` w elemencie for WPF ma kilka istotnych ograniczeń:</span><span class="sxs-lookup"><span data-stu-id="95388-114">Code declared within `x:Code` for WPF has several notable limitations:</span></span>  
  
- <span data-ttu-id="95388-115">Element `x:Code` dyrektywy musi być bezpośrednim elementem podrzędnym elementu głównego w środowisku produkcyjnym XAML.</span><span class="sxs-lookup"><span data-stu-id="95388-115">The `x:Code` directive element must be an immediate child element of the root element of the XAML production.</span></span>  
  
- <span data-ttu-id="95388-116">dla nadrzędnego elementu głównego musi być podana [dyrektywa x:Class](x-class-directive.md) .</span><span class="sxs-lookup"><span data-stu-id="95388-116">[x:Class Directive](x-class-directive.md) must be provided on the parent root element.</span></span>  
  
- <span data-ttu-id="95388-117">Kod umieszczony w obszarze `x:Code` będzie traktowany przez kompilację, aby znajdować się w zakresie klasy częściowej, która jest już utworzona dla tej strony XAML.</span><span class="sxs-lookup"><span data-stu-id="95388-117">The code placed within `x:Code` will be treated by compilation to be within the scope of the partial class that is already being created for that XAML page.</span></span> <span data-ttu-id="95388-118">W związku z tym wszystkie zdefiniowane kody muszą być elementami członkowskimi lub zmiennymi tej klasy częściowej.</span><span class="sxs-lookup"><span data-stu-id="95388-118">Therefore all code you define must be members or variables of that partial class.</span></span>  
  
- <span data-ttu-id="95388-119">Nie można definiować dodatkowych klas, innych niż zagnieżdżanie klasy wewnątrz klasy częściowej (zagnieżdżanie jest dozwolone, ale nie jest typowe, ponieważ nie można odwoływać się do klas zagnieżdżonych w języku XAML).</span><span class="sxs-lookup"><span data-stu-id="95388-119">You cannot define additional classes, other than by nesting a class inside the partial class (nesting is allowed, but it is not typical because nested classes cannot be referenced in XAML).</span></span> <span data-ttu-id="95388-120">Przestrzenie nazw CLR inne niż przestrzeń nazw, która jest używana dla istniejącej klasy częściowej, nie mogą być zdefiniowane ani dodawane do.</span><span class="sxs-lookup"><span data-stu-id="95388-120">CLR namespaces other than the namespace that is used for the existing partial class cannot be defined or added to.</span></span>  
  
- <span data-ttu-id="95388-121">Odwołania do jednostek kodu spoza przestrzeni nazw CLR klasy częściowej muszą być w pełni kwalifikowane.</span><span class="sxs-lookup"><span data-stu-id="95388-121">References to code entities outside the partial class CLR namespace must all be fully qualified.</span></span> <span data-ttu-id="95388-122">Jeśli deklarowane składowe są zastąpienia do składowych klasy częściowej, należy określić za pomocą słowa kluczowego override określonego dla języka.</span><span class="sxs-lookup"><span data-stu-id="95388-122">If members being declared are overrides to the partial class overridable members, this must be specified with the language-specific override keyword.</span></span> <span data-ttu-id="95388-123">Jeśli elementy członkowskie zadeklarowane w `x:Code` zakresie powodują konflikt z elementami członkowskimi częściowej klasy utworzonej poza XAML, w taki sposób, aby kompilator zgłaszał konflikt, plik XAML nie może kompilować ani ładować.</span><span class="sxs-lookup"><span data-stu-id="95388-123">If members declared in `x:Code` scope conflict with members of the partial class created out of the XAML, in such a way that the compiler reports the conflict, the XAML file cannot compile or load.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95388-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="95388-124">See also</span></span>

- [<span data-ttu-id="95388-125">x:Class, dyrektywa</span><span class="sxs-lookup"><span data-stu-id="95388-125">x:Class Directive</span></span>](x-class-directive.md)
- [<span data-ttu-id="95388-126">Plik codebehind i XAML w WPF</span><span class="sxs-lookup"><span data-stu-id="95388-126">Code-Behind and XAML in WPF</span></span>](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [<span data-ttu-id="95388-127">Przegląd XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="95388-127">XAML Overview (WPF)</span></span>](../wpf/advanced/xaml-overview-wpf.md)
