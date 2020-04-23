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
ms.openlocfilehash: 4da72ed630c1df001e3fd6c7e55f866b94c4d9b1
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071557"
---
# <a name="xcode-intrinsic-xaml-type"></a><span data-ttu-id="17846-102">x:Code — Typ funkcji XAML</span><span class="sxs-lookup"><span data-stu-id="17846-102">x:Code Intrinsic XAML Type</span></span>
<span data-ttu-id="17846-103">Umożliwia umieszczenie kodu w środowisku produkcyjnym XAML.</span><span class="sxs-lookup"><span data-stu-id="17846-103">Allows placement of code within a XAML production.</span></span> <span data-ttu-id="17846-104">Taki kod może być skompilowany przez dowolną implementację procesora XAML, który kompiluje XAML, lub pozostawiony w produkcji XAML do późniejszych zastosowań, takich jak interpretacja przez środowisko wykonawcze.</span><span class="sxs-lookup"><span data-stu-id="17846-104">Such code can either be compiled by any XAML processor implementation that compiles XAML, or left in the XAML production for later uses such as interpretation by a runtime.</span></span>

## <a name="xaml-object-element-usage"></a><span data-ttu-id="17846-105">Użycie elementu obiektu języka XAML</span><span class="sxs-lookup"><span data-stu-id="17846-105">XAML Object Element Usage</span></span>

```xaml
<x:Code>
   // code instructions, usually enclosed by CDATA...
</x:Code>
```

## <a name="remarks"></a><span data-ttu-id="17846-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="17846-106">Remarks</span></span>

<span data-ttu-id="17846-107">Kod w `x:Code` elemencie dyrektywy XAML jest nadal interpretowany w ogólnej przestrzeni nazw XML i dostarczonych przestrzeniach nazw XAML.</span><span class="sxs-lookup"><span data-stu-id="17846-107">The code within the `x:Code` XAML directive element is still interpreted within the general XML namespace and the XAML namespaces provided.</span></span> <span data-ttu-id="17846-108">W związku z tym zwykle konieczne jest `x:Code` ująć kod używany do wewnątrz segmentu. `CDATA`</span><span class="sxs-lookup"><span data-stu-id="17846-108">Therefore, it is usually necessary to enclose the code used for `x:Code` inside a `CDATA` segment.</span></span>

<span data-ttu-id="17846-109">`x:Code`nie jest dozwolone dla wszystkich możliwych mechanizmów wdrażania produkcji XAML.</span><span class="sxs-lookup"><span data-stu-id="17846-109">`x:Code` is not permitted for all possible deployment mechanisms of a XAML production.</span></span> <span data-ttu-id="17846-110">W określonych ramach (na przykład WPF) kod musi być skompilowany.</span><span class="sxs-lookup"><span data-stu-id="17846-110">In specific frameworks (for example WPF) the code must be compiled.</span></span> <span data-ttu-id="17846-111">W innych ramach `x:Code` użycie może być ogólnie niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="17846-111">In other frameworks, `x:Code` usage might be generally disallowed.</span></span>

<span data-ttu-id="17846-112">Dla struktur, które `x:Code` zezwalają na zawartość zarządzaną kompilatora poprawnego języka do użycia dla `x:Code` zawartości jest określana przez ustawienia i obiekty docelowe zawierającego projektu, który jest używany do kompilowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="17846-112">For frameworks that permit managed `x:Code` content, the correct language compiler to use for `x:Code` content is determined by settings and targets of the containing project that is used to compile the application.</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="17846-113">Uwagi dotyczące użycia WPF</span><span class="sxs-lookup"><span data-stu-id="17846-113">WPF Usage Notes</span></span>

<span data-ttu-id="17846-114">Kod zadeklarowany w ramach `x:Code` WPF ma kilka znaczących ograniczeń:</span><span class="sxs-lookup"><span data-stu-id="17846-114">Code declared within `x:Code` for WPF has several notable limitations:</span></span>

- <span data-ttu-id="17846-115">Element `x:Code` dyrektywy musi być bezpośrednim elementem podrzędnym elementu głównego produkcji XAML.</span><span class="sxs-lookup"><span data-stu-id="17846-115">The `x:Code` directive element must be an immediate child element of the root element of the XAML production.</span></span>

- <span data-ttu-id="17846-116">[x:Dyrektywa klasy](xclass-directive.md) musi być podana w nadrzędnym elemencie głównym.</span><span class="sxs-lookup"><span data-stu-id="17846-116">[x:Class Directive](xclass-directive.md) must be provided on the parent root element.</span></span>

- <span data-ttu-id="17846-117">Kod umieszczony `x:Code` w zostaną potraktowane przez kompilację, aby mieszcząć się w zakresie klasy częściowej, która jest już tworzona dla tej strony XAML.</span><span class="sxs-lookup"><span data-stu-id="17846-117">The code placed within `x:Code` will be treated by compilation to be within the scope of the partial class that is already being created for that XAML page.</span></span> <span data-ttu-id="17846-118">W związku z tym cały kod, który definiujesz musi być członkami lub zmienne tej klasy częściowej.</span><span class="sxs-lookup"><span data-stu-id="17846-118">Therefore all code you define must be members or variables of that partial class.</span></span>

- <span data-ttu-id="17846-119">Nie można zdefiniować dodatkowych klas, innych niż zagnieżdżanie klasy wewnątrz klasy częściowej (zagnieżdżanie jest dozwolone, ale nie jest typowe, ponieważ nie można odwoływać się do klas zagnieżdżonych w XAML).</span><span class="sxs-lookup"><span data-stu-id="17846-119">You cannot define additional classes, other than by nesting a class inside the partial class (nesting is allowed, but it is not typical because nested classes cannot be referenced in XAML).</span></span> <span data-ttu-id="17846-120">Nie można zdefiniować ani dodać do innych obszarów nazw clr innych niż obszar nazw używany dla istniejącej klasy częściowej.</span><span class="sxs-lookup"><span data-stu-id="17846-120">CLR namespaces other than the namespace that is used for the existing partial class cannot be defined or added to.</span></span>

- <span data-ttu-id="17846-121">Odwołania do jednostek kodu poza obszarem nazw klasy częściowej CLR muszą być w pełni kwalifikowane.</span><span class="sxs-lookup"><span data-stu-id="17846-121">References to code entities outside the partial class CLR namespace must all be fully qualified.</span></span> <span data-ttu-id="17846-122">Jeśli elementy członkowskie są zadeklarowane są zastąpienia częściowej klasy nadrzędnych elementów członkowskich, to musi być określona za pomocą słowa kluczowego zastąpienia specyficzne dla języka.</span><span class="sxs-lookup"><span data-stu-id="17846-122">If members being declared are overrides to the partial class overridable members, this must be specified with the language-specific override keyword.</span></span> <span data-ttu-id="17846-123">Jeśli elementy `x:Code` członkowskie zadeklarowane w zakresie są w konflikcie z członkami klasy częściowej utworzonej z XAML, w taki sposób, że kompilator zgłasza konflikt, plik XAML nie może skompilować ani załadować.</span><span class="sxs-lookup"><span data-stu-id="17846-123">If members declared in `x:Code` scope conflict with members of the partial class created out of the XAML, in such a way that the compiler reports the conflict, the XAML file cannot compile or load.</span></span>

## <a name="see-also"></a><span data-ttu-id="17846-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="17846-124">See also</span></span>

- [<span data-ttu-id="17846-125">x:Class — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="17846-125">x:Class Directive</span></span>](xclass-directive.md)
- [<span data-ttu-id="17846-126">Związane z kodem i XAML w WPF</span><span class="sxs-lookup"><span data-stu-id="17846-126">Code-Behind and XAML in WPF</span></span>](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [<span data-ttu-id="17846-127">Omówienie XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="17846-127">XAML Overview (WPF)</span></span>](../fundamentals/xaml.md)
