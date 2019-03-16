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
ms.openlocfilehash: 8d0dbc03bb5eaedd89d5a6ce97d625a51507e820
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2019
ms.locfileid: "58050599"
---
# <a name="xcode-intrinsic-xaml-type"></a><span data-ttu-id="bc18e-102">x:Code — Typ funkcji XAML</span><span class="sxs-lookup"><span data-stu-id="bc18e-102">x:Code Intrinsic XAML Type</span></span>
<span data-ttu-id="bc18e-103">Umożliwia umieszczanie kodu w ramach produkcji XAML.</span><span class="sxs-lookup"><span data-stu-id="bc18e-103">Allows placement of code within a XAML production.</span></span> <span data-ttu-id="bc18e-104">Taki kod może być kompilowane albo przez dowolnego implementacji procesora XAML, który kompiluje XAML lub po lewej stronie w środowisku produkcyjnym XAML do nowszych zastosowań, takich jak interpretacji przez środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="bc18e-104">Such code can either be compiled by any XAML processor implementation that compiles XAML, or left in the XAML production for later uses such as interpretation by a runtime.</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="bc18e-105">Użycie elementu obiektu języka XAML</span><span class="sxs-lookup"><span data-stu-id="bc18e-105">XAML Object Element Usage</span></span>  
  
```  
<x:Code>  
   // code instructions, usually enclosed by CDATA...  
</x:Code>  
```  
  
## <a name="remarks"></a><span data-ttu-id="bc18e-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bc18e-106">Remarks</span></span>  
 <span data-ttu-id="bc18e-107">Kod w `x:Code` element dyrektywy XAML jest nadal interpretowany w głównej przestrzeni nazw XML i przestrzenie nazw XAML, pod warunkiem.</span><span class="sxs-lookup"><span data-stu-id="bc18e-107">The code within the `x:Code` XAML directive element is still interpreted within the general XML namespace and the XAML namespaces provided.</span></span> <span data-ttu-id="bc18e-108">Dlatego jest zazwyczaj konieczne dołączyć kod umożliwiający `x:Code` wewnątrz `CDATA` segmentu.</span><span class="sxs-lookup"><span data-stu-id="bc18e-108">Therefore, it is usually necessary to enclose the code used for `x:Code` inside a `CDATA` segment.</span></span>  
  
 <span data-ttu-id="bc18e-109">`x:Code` nie jest dozwolony dla wszystkich mechanizmów możliwe wdrożenie produkcyjne XAML.</span><span class="sxs-lookup"><span data-stu-id="bc18e-109">`x:Code` is not permitted for all possible deployment mechanisms of a XAML production.</span></span> <span data-ttu-id="bc18e-110">W określonych platform (na przykład WPF) musi zostać skompilowany kod.</span><span class="sxs-lookup"><span data-stu-id="bc18e-110">In specific frameworks (for example WPF) the code must be compiled.</span></span> <span data-ttu-id="bc18e-111">W innych platform tworzenia `x:Code` użycia może być zwykle niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="bc18e-111">In other frameworks, `x:Code` usage might be generally disallowed.</span></span>  
  
 <span data-ttu-id="bc18e-112">Dla platform zezwalające na zarządzanych `x:Code` zawartości kompilatora języka do użycia dla `x:Code` zawartość jest określana przez ustawienia i elementy docelowe projektu zawierającego, który służy do kompilowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bc18e-112">For frameworks that permit managed `x:Code` content, the correct language compiler to use for `x:Code` content is determined by settings and targets of the containing project that is used to compile the application.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="bc18e-113">Uwagi dotyczące użytkowania WPF</span><span class="sxs-lookup"><span data-stu-id="bc18e-113">WPF Usage Notes</span></span>  
 <span data-ttu-id="bc18e-114">Kod zadeklarowane wewnątrz `x:Code` WPF ma kilka znaczące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="bc18e-114">Code declared within `x:Code` for WPF has several notable limitations:</span></span>  
  
-   <span data-ttu-id="bc18e-115">`x:Code` Dyrektywy element musi być natychmiastowe podrzędnym elementem głównym elementem produkcji XAML.</span><span class="sxs-lookup"><span data-stu-id="bc18e-115">The `x:Code` directive element must be an immediate child element of the root element of the XAML production.</span></span>  
  
-   <span data-ttu-id="bc18e-116">[x: Class — dyrektywa](x-class-directive.md) musi być podana w elemencie głównym nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="bc18e-116">[x:Class Directive](x-class-directive.md) must be provided on the parent root element.</span></span>  
  
-   <span data-ttu-id="bc18e-117">Kod umieszczony w `x:Code` są traktowani kompilacji w zakresie częściową klasą, która jest już utworzony dla tej strony XAML.</span><span class="sxs-lookup"><span data-stu-id="bc18e-117">The code placed within `x:Code` will be treated by compilation to be within the scope of the partial class that is already being created for that XAML page.</span></span> <span data-ttu-id="bc18e-118">W związku z tym cały kod, który zdefiniujesz musi być członków lub zmiennych tej klasy częściowej.</span><span class="sxs-lookup"><span data-stu-id="bc18e-118">Therefore all code you define must be members or variables of that partial class.</span></span>  
  
-   <span data-ttu-id="bc18e-119">Nie można zdefiniować dodatkowe klasy, inne niż przez zagnieżdżanie klasy wewnątrz klasy częściowe (zagnieżdżanie jest dozwolone, ale nie jest typowym ponieważ klasy zagnieżdżone nie może być przywoływany w XAML).</span><span class="sxs-lookup"><span data-stu-id="bc18e-119">You cannot define additional classes, other than by nesting a class inside the partial class (nesting is allowed, but it is not typical because nested classes cannot be referenced in XAML).</span></span> <span data-ttu-id="bc18e-120">Przestrzeni nazw CLR innych niż przestrzeń nazw, która jest używana dla istniejącej klasy częściowe nie może być zdefiniowany ani dodawane do.</span><span class="sxs-lookup"><span data-stu-id="bc18e-120">CLR namespaces other than the namespace that is used for the existing partial class cannot be defined or added to.</span></span>  
  
-   <span data-ttu-id="bc18e-121">Odwołania do jednostek kodu poza przestrzeń nazw środowiska CLR klasy częściowej wszystkie muszą być w pełni kwalifikowana.</span><span class="sxs-lookup"><span data-stu-id="bc18e-121">References to code entities outside the partial class CLR namespace must all be fully qualified.</span></span> <span data-ttu-id="bc18e-122">Jeśli elementy członkowskie deklarowanej zastąpień do przesłonięcia elementów członkowskich klasy częściowej, to można określić za pomocą słowa kluczowego override specyficzny dla języka.</span><span class="sxs-lookup"><span data-stu-id="bc18e-122">If members being declared are overrides to the partial class overridable members, this must be specified with the language-specific override keyword.</span></span> <span data-ttu-id="bc18e-123">W przypadku elementów członkowskich zadeklarowanych w `x:Code` zakres elementów członkowskich klasy częściowej utworzony poza XAML różne, w taki sposób, że kompilator zgłasza konfliktu, plik XAML nie można skompilować lub obciążenia.</span><span class="sxs-lookup"><span data-stu-id="bc18e-123">If members declared in `x:Code` scope conflict with members of the partial class created out of the XAML, in such a way that the compiler reports the conflict, the XAML file cannot compile or load.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc18e-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bc18e-124">See also</span></span>
- [<span data-ttu-id="bc18e-125">x:Class, dyrektywa</span><span class="sxs-lookup"><span data-stu-id="bc18e-125">x:Class Directive</span></span>](x-class-directive.md)
- [<span data-ttu-id="bc18e-126">Plik codebehind i XAML w WPF</span><span class="sxs-lookup"><span data-stu-id="bc18e-126">Code-Behind and XAML in WPF</span></span>](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [<span data-ttu-id="bc18e-127">Przegląd XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="bc18e-127">XAML Overview (WPF)</span></span>](../wpf/advanced/xaml-overview-wpf.md)
