---
title: /optionstrict
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: /optionstrict
helpviewer_keywords:
- -optionstrict compiler option [Visual Basic]
- optionstrict compiler option [Visual Basic]
- /optionstrict compiler option [Visual Basic]
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f783cc5b20c4fe6d7812a05a66cbc4cdfc0b9395
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="optionstrict"></a><span data-ttu-id="9e5b8-102">/optionstrict</span><span class="sxs-lookup"><span data-stu-id="9e5b8-102">/optionstrict</span></span>
<span data-ttu-id="9e5b8-103">Wymusza ścisłe zasady semantyki ograniczyć niejawne konwersje typów.</span><span class="sxs-lookup"><span data-stu-id="9e5b8-103">Enforces strict type semantics to restrict implicit type conversions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e5b8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9e5b8-104">Syntax</span></span>  
  
```  
/optionstrict[+ | -]  
/optionstrict[:custom]  
```  
  
## <a name="arguments"></a><span data-ttu-id="9e5b8-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="9e5b8-105">Arguments</span></span>  
 <span data-ttu-id="9e5b8-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="9e5b8-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="9e5b8-107">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="9e5b8-107">Optional.</span></span> <span data-ttu-id="9e5b8-108">`/optionstrict+` Opcja ogranicza niejawna konwersja typu.</span><span class="sxs-lookup"><span data-stu-id="9e5b8-108">The `/optionstrict+` option restricts implicit type conversion.</span></span> <span data-ttu-id="9e5b8-109">Wartość domyślna dla tej opcji to `/optionstrict-`.</span><span class="sxs-lookup"><span data-stu-id="9e5b8-109">The default for this option is `/optionstrict-`.</span></span> <span data-ttu-id="9e5b8-110">`/optionstrict+` Opcji jest taka sama jak `/optionstrict`.</span><span class="sxs-lookup"><span data-stu-id="9e5b8-110">The `/optionstrict+` option is the same as `/optionstrict`.</span></span> <span data-ttu-id="9e5b8-111">Można użyć zarówno dla typu ograniczająca semantyki.</span><span class="sxs-lookup"><span data-stu-id="9e5b8-111">You can use both for permissive type semantics.</span></span>  
  
 `custom`  
 <span data-ttu-id="9e5b8-112">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="9e5b8-112">Required.</span></span> <span data-ttu-id="9e5b8-113">Ostrzegaj, gdy ścisła semantyka języka nie są przestrzegane.</span><span class="sxs-lookup"><span data-stu-id="9e5b8-113">Warn when strict language semantics are not respected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e5b8-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9e5b8-114">Remarks</span></span>  
 <span data-ttu-id="9e5b8-115">Gdy `/optionstrict+` w efekcie jest niejawnie może być utworzona tylko rozszerzającą konwersje typów.</span><span class="sxs-lookup"><span data-stu-id="9e5b8-115">When `/optionstrict+` is in effect, only widening type conversions can be made implicitly.</span></span> <span data-ttu-id="9e5b8-116">Zawężanie konwersji typu, takich jak przypisywanie niejawne `Decimal` typ obiektu do obiektu typu Liczba całkowita, są raportowane klientowi jako błędy.</span><span class="sxs-lookup"><span data-stu-id="9e5b8-116">Implicit narrowing type conversions, such as assigning a `Decimal` type object to an integer type object, are reported as errors.</span></span>  
  
 <span data-ttu-id="9e5b8-117">Aby wygenerować ostrzeżenia dla niejawnej konwersji zawężającej typu, należy użyć `/optionstrict:custom`.</span><span class="sxs-lookup"><span data-stu-id="9e5b8-117">To generate warnings for implicit narrowing type conversions, use `/optionstrict:custom`.</span></span> <span data-ttu-id="9e5b8-118">Użyj `/nowarn:numberlist` ignorowania ostrzeżeń dotyczących określonego i `/warnaserror:numberlist` traktować określonego ostrzeżenia jako błędy.</span><span class="sxs-lookup"><span data-stu-id="9e5b8-118">Use `/nowarn:numberlist` to ignore particular warnings and `/warnaserror:numberlist` to treat particular warnings as errors.</span></span>  
  
### <a name="to-set-optionstrict-in-the-visual-studio-ide"></a><span data-ttu-id="9e5b8-119">Aby ustawić/optionstrict — w programie Visual Studio IDE</span><span class="sxs-lookup"><span data-stu-id="9e5b8-119">To set /optionstrict in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="9e5b8-120">Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="9e5b8-120">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="9e5b8-121">Na **projektu** menu, kliknij przycisk **właściwości.**</span><span class="sxs-lookup"><span data-stu-id="9e5b8-121">On the **Project** menu, click **Properties.**</span></span> <span data-ttu-id="9e5b8-122">Aby uzyskać więcej informacji, zobacz [wprowadzenie do projektanta projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="9e5b8-122">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="9e5b8-123">Kliknij przycisk **skompilować** kartę.</span><span class="sxs-lookup"><span data-stu-id="9e5b8-123">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="9e5b8-124">Zmodyfikuj wartość w **Option Strict** pole.</span><span class="sxs-lookup"><span data-stu-id="9e5b8-124">Modify the value in the **Option Strict** box.</span></span>  
  
### <a name="to-set-optionstrict-programmatically"></a><span data-ttu-id="9e5b8-125">Aby ustawić/optionstrict — programowo</span><span class="sxs-lookup"><span data-stu-id="9e5b8-125">To set /optionstrict programmatically</span></span>  
  
-   <span data-ttu-id="9e5b8-126">Zobacz [Option Strict — instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9e5b8-126">See [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e5b8-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="9e5b8-127">Example</span></span>  
 <span data-ttu-id="9e5b8-128">Poniższy kod kompiluje `Test.vb` za pomocą semantyki typu strict.</span><span class="sxs-lookup"><span data-stu-id="9e5b8-128">The following code compiles `Test.vb` using strict type semantics.</span></span>  
  
```  
vbc /optionstrict+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="9e5b8-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9e5b8-129">See Also</span></span>  
 [<span data-ttu-id="9e5b8-130">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9e5b8-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="9e5b8-131">/ optioncompare</span><span class="sxs-lookup"><span data-stu-id="9e5b8-131">/optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [<span data-ttu-id="9e5b8-132">/ optionexplicit</span><span class="sxs-lookup"><span data-stu-id="9e5b8-132">/optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [<span data-ttu-id="9e5b8-133">/ optioninfer</span><span class="sxs-lookup"><span data-stu-id="9e5b8-133">/optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="9e5b8-134">/ nowarn</span><span class="sxs-lookup"><span data-stu-id="9e5b8-134">/nowarn</span></span>](../../../visual-basic/reference/command-line-compiler/nowarn.md)  
 [<span data-ttu-id="9e5b8-135">/ warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e5b8-135">/warnaserror (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/warnaserror.md)  
 [<span data-ttu-id="9e5b8-136">Kompilacja przykładów — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="9e5b8-136">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="9e5b8-137">Option Strict — instrukcja</span><span class="sxs-lookup"><span data-stu-id="9e5b8-137">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="9e5b8-138">Okno dialogowe Opcje domyślne, projektów, Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9e5b8-138">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
