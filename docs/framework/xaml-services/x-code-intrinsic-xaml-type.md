---
title: "x:Code — Typ funkcji XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Code
- x:Code
- xCode
helpviewer_keywords:
- Code directive in XAML [XAML Services]
- x:Code XAML directive element [XAML Services]
- XAML [XAML Services], x:Code directive element
ms.assetid: 87986b13-1a2e-4830-ae36-15f9dc5629e8
caps.latest.revision: "19"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: d1b21e2a654b18547c8da7da724c87946724f71f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="xcode-intrinsic-xaml-type"></a><span data-ttu-id="f5f2b-102">x:Code — Typ funkcji XAML</span><span class="sxs-lookup"><span data-stu-id="f5f2b-102">x:Code Intrinsic XAML Type</span></span>
<span data-ttu-id="f5f2b-103">Umożliwia umieszczanie kod w produkcji XAML.</span><span class="sxs-lookup"><span data-stu-id="f5f2b-103">Allows placement of code within a XAML production.</span></span> <span data-ttu-id="f5f2b-104">Taki kod albo mogą być kompilowane przez kompilowany XAML, lub do lewej w środowisku produkcyjnym XAML dla nowszej zastosowań, takich jak interpretacji przez środowisko uruchomieniowe implementacji procesora XAML.</span><span class="sxs-lookup"><span data-stu-id="f5f2b-104">Such code can either be compiled by any XAML processor implementation that compiles XAML, or left in the XAML production for later uses such as interpretation by a runtime.</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="f5f2b-105">Użycie elementu obiektu języka XAML</span><span class="sxs-lookup"><span data-stu-id="f5f2b-105">XAML Object Element Usage</span></span>  
  
```  
<x:Code>  
   // code instructions, usually enclosed by CDATA...  
</x:Code>  
```  
  
## <a name="remarks"></a><span data-ttu-id="f5f2b-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f5f2b-106">Remarks</span></span>  
 <span data-ttu-id="f5f2b-107">Kod w `x:Code` element dyrektywy XAML jest nadal interpretowana w głównej przestrzeni nazw XML i przestrzeni nazw XAML, pod warunkiem.</span><span class="sxs-lookup"><span data-stu-id="f5f2b-107">The code within the `x:Code` XAML directive element is still interpreted within the general XML namespace and the XAML namespaces provided.</span></span> <span data-ttu-id="f5f2b-108">W związku z tym jest zazwyczaj konieczne do kod używany do `x:Code` wewnątrz `CDATA` segmentu.</span><span class="sxs-lookup"><span data-stu-id="f5f2b-108">Therefore, it is usually necessary to enclose the code used for `x:Code` inside a `CDATA` segment.</span></span>  
  
 <span data-ttu-id="f5f2b-109">`x:Code`nie jest dozwolona dla wszystkich mechanizmów wdrażania produkcji XAML.</span><span class="sxs-lookup"><span data-stu-id="f5f2b-109">`x:Code` is not permitted for all possible deployment mechanisms of a XAML production.</span></span> <span data-ttu-id="f5f2b-110">W określonych platform (na przykład WPF) musi być skompilowany kod.</span><span class="sxs-lookup"><span data-stu-id="f5f2b-110">In specific frameworks (for example WPF) the code must be compiled.</span></span> <span data-ttu-id="f5f2b-111">W innych platform `x:Code` obciążenie może być zwykle niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="f5f2b-111">In other frameworks, `x:Code` usage might be generally disallowed.</span></span>  
  
 <span data-ttu-id="f5f2b-112">Dla struktur, pozwalające zarządzanych `x:Code` zawartości kompilatora właściwy język do użycia na potrzeby `x:Code` zawartości jest określany przez ustawienia i elementy docelowe projektu zawierającego, która jest używana do kompilowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f5f2b-112">For frameworks that permit managed `x:Code` content, the correct language compiler to use for `x:Code` content is determined by settings and targets of the containing project that is used to compile the application.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="f5f2b-113">Uwagi dotyczące użycia WPF</span><span class="sxs-lookup"><span data-stu-id="f5f2b-113">WPF Usage Notes</span></span>  
 <span data-ttu-id="f5f2b-114">Kod zadeklarowana wewnątrz `x:Code` WPF ma kilka istotnych ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="f5f2b-114">Code declared within `x:Code` for WPF has several notable limitations:</span></span>  
  
-   <span data-ttu-id="f5f2b-115">`x:Code` Dyrektywy element musi być elementem podrzędnym natychmiastowego elementu głównego XAML produkcji.</span><span class="sxs-lookup"><span data-stu-id="f5f2b-115">The `x:Code` directive element must be an immediate child element of the root element of the XAML production.</span></span>  
  
-   <span data-ttu-id="f5f2b-116">[x: Class — dyrektywa](../../../docs/framework/xaml-services/x-class-directive.md) należy podać dla nadrzędnego elementu głównego.</span><span class="sxs-lookup"><span data-stu-id="f5f2b-116">[x:Class Directive](../../../docs/framework/xaml-services/x-class-directive.md) must be provided on the parent root element.</span></span>  
  
-   <span data-ttu-id="f5f2b-117">Kod umieszczony `x:Code` , będą traktowane w kompilacji muszą mieścić się w zakresie częściowej klasy, która została właśnie utworzona dla tej strony XAML.</span><span class="sxs-lookup"><span data-stu-id="f5f2b-117">The code placed within `x:Code` will be treated by compilation to be within the scope of the partial class that is already being created for that XAML page.</span></span> <span data-ttu-id="f5f2b-118">W związku z tym całego kodu, który należy zdefiniować musi być elementów członkowskich lub zmienne dla tej klasy częściowej.</span><span class="sxs-lookup"><span data-stu-id="f5f2b-118">Therefore all code you define must be members or variables of that partial class.</span></span>  
  
-   <span data-ttu-id="f5f2b-119">Nie można zdefiniować dodatkowe klasy, innych niż zagnieżdżanie klasy wewnątrz klasy częściowej (zagnieżdżanie jest dozwolone, ale nie jest typowe ponieważ zagnieżdżonych klas nie może być przywoływany w języku XAML).</span><span class="sxs-lookup"><span data-stu-id="f5f2b-119">You cannot define additional classes, other than by nesting a class inside the partial class (nesting is allowed, but it is not typical because nested classes cannot be referenced in XAML).</span></span> <span data-ttu-id="f5f2b-120">Przestrzenie nazw CLR innych niż przestrzeni nazw, która jest używana dla istniejącej klasy częściowe nie może być zdefiniowany ani dodawane do.</span><span class="sxs-lookup"><span data-stu-id="f5f2b-120">CLR namespaces other than the namespace that is used for the existing partial class cannot be defined or added to.</span></span>  
  
-   <span data-ttu-id="f5f2b-121">Odwołania do jednostek kodu poza przestrzeń nazw środowiska CLR klasy częściowej muszą być wszystkie FQDN.</span><span class="sxs-lookup"><span data-stu-id="f5f2b-121">References to code entities outside the partial class CLR namespace must all be fully qualified.</span></span> <span data-ttu-id="f5f2b-122">Elementy członkowskie został zadeklarowany w przypadku zastąpienia do klasy częściowej członków możliwym do zastąpienia, to należy określić przy użyciu słowa kluczowego override specyficzny dla języka.</span><span class="sxs-lookup"><span data-stu-id="f5f2b-122">If members being declared are overrides to the partial class overridable members, this must be specified with the language-specific override keyword.</span></span> <span data-ttu-id="f5f2b-123">Elementy członkowskie zadeklarowana w `x:Code` zakresu powodują konflikt z członkami klasy częściowej utworzony poza XAML, w taki sposób, że kompilator zgłasza konfliktu, plik XAML nie można skompilować lub obciążenia.</span><span class="sxs-lookup"><span data-stu-id="f5f2b-123">If members declared in `x:Code` scope conflict with members of the partial class created out of the XAML, in such a way that the compiler reports the conflict, the XAML file cannot compile or load.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5f2b-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f5f2b-124">See Also</span></span>  
 [<span data-ttu-id="f5f2b-125">x: Class — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="f5f2b-125">x:Class Directive</span></span>](../../../docs/framework/xaml-services/x-class-directive.md)  
 [<span data-ttu-id="f5f2b-126">Związane z kodem i języka XAML w WPF</span><span class="sxs-lookup"><span data-stu-id="f5f2b-126">Code-Behind and XAML in WPF</span></span>](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)  
 [<span data-ttu-id="f5f2b-127">Omówienie XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="f5f2b-127">XAML Overview (WPF)</span></span>](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
