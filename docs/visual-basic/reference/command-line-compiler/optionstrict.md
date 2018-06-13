---
title: -optionstrict
ms.date: 07/20/2015
f1_keywords:
- -optionstrict
helpviewer_keywords:
- -optionstrict compiler option [Visual Basic]
- optionstrict compiler option [Visual Basic]
- /optionstrict compiler option [Visual Basic]
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
ms.openlocfilehash: da1bd6d3b6746561655a82cd49aa0014563a1d40
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652912"
---
# <a name="-optionstrict"></a><span data-ttu-id="fd474-102">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="fd474-102">-optionstrict</span></span>
<span data-ttu-id="fd474-103">Wymusza ścisłe zasady semantyki ograniczyć niejawne konwersje typów.</span><span class="sxs-lookup"><span data-stu-id="fd474-103">Enforces strict type semantics to restrict implicit type conversions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd474-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fd474-104">Syntax</span></span>  
  
```  
-optionstrict[+ | -]  
-optionstrict[:custom]  
```  
  
## <a name="arguments"></a><span data-ttu-id="fd474-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="fd474-105">Arguments</span></span>  
 <span data-ttu-id="fd474-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="fd474-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="fd474-107">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="fd474-107">Optional.</span></span> <span data-ttu-id="fd474-108">`-optionstrict+` Opcja ogranicza niejawna konwersja typu.</span><span class="sxs-lookup"><span data-stu-id="fd474-108">The `-optionstrict+` option restricts implicit type conversion.</span></span> <span data-ttu-id="fd474-109">Wartość domyślna dla tej opcji to `-optionstrict-`.</span><span class="sxs-lookup"><span data-stu-id="fd474-109">The default for this option is `-optionstrict-`.</span></span> <span data-ttu-id="fd474-110">`-optionstrict+` Opcji jest taka sama jak `-optionstrict`.</span><span class="sxs-lookup"><span data-stu-id="fd474-110">The `-optionstrict+` option is the same as `-optionstrict`.</span></span> <span data-ttu-id="fd474-111">Można użyć zarówno dla typu ograniczająca semantyki.</span><span class="sxs-lookup"><span data-stu-id="fd474-111">You can use both for permissive type semantics.</span></span>  
  
 `custom`  
 <span data-ttu-id="fd474-112">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="fd474-112">Required.</span></span> <span data-ttu-id="fd474-113">Ostrzegaj, gdy ścisła semantyka języka nie są przestrzegane.</span><span class="sxs-lookup"><span data-stu-id="fd474-113">Warn when strict language semantics are not respected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd474-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fd474-114">Remarks</span></span>  
 <span data-ttu-id="fd474-115">Gdy `-optionstrict+` w efekcie jest niejawnie może być utworzona tylko rozszerzającą konwersje typów.</span><span class="sxs-lookup"><span data-stu-id="fd474-115">When `-optionstrict+` is in effect, only widening type conversions can be made implicitly.</span></span> <span data-ttu-id="fd474-116">Zawężanie konwersji typu, takich jak przypisywanie niejawne `Decimal` typ obiektu do obiektu typu Liczba całkowita, są raportowane klientowi jako błędy.</span><span class="sxs-lookup"><span data-stu-id="fd474-116">Implicit narrowing type conversions, such as assigning a `Decimal` type object to an integer type object, are reported as errors.</span></span>  
  
 <span data-ttu-id="fd474-117">Aby wygenerować ostrzeżenia dla niejawnej konwersji zawężającej typu, należy użyć `-optionstrict:custom`.</span><span class="sxs-lookup"><span data-stu-id="fd474-117">To generate warnings for implicit narrowing type conversions, use `-optionstrict:custom`.</span></span> <span data-ttu-id="fd474-118">Użyj `-nowarn:numberlist` ignorowania ostrzeżeń dotyczących określonego i `-warnaserror:numberlist` traktować określonego ostrzeżenia jako błędy.</span><span class="sxs-lookup"><span data-stu-id="fd474-118">Use `-nowarn:numberlist` to ignore particular warnings and `-warnaserror:numberlist` to treat particular warnings as errors.</span></span>  
  
### <a name="to-set--optionstrict-in-the-visual-studio-ide"></a><span data-ttu-id="fd474-119">Aby ustawić - optionstrict w środowisku IDE programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fd474-119">To set -optionstrict in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="fd474-120">Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="fd474-120">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="fd474-121">Na **projektu** menu, kliknij przycisk **właściwości.**</span><span class="sxs-lookup"><span data-stu-id="fd474-121">On the **Project** menu, click **Properties.**</span></span>   
  
2.  <span data-ttu-id="fd474-122">Kliknij przycisk **skompilować** kartę.</span><span class="sxs-lookup"><span data-stu-id="fd474-122">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="fd474-123">Zmodyfikuj wartość w **Option Strict** pole.</span><span class="sxs-lookup"><span data-stu-id="fd474-123">Modify the value in the **Option Strict** box.</span></span>  
  
### <a name="to-set--optionstrict-programmatically"></a><span data-ttu-id="fd474-124">Aby ustawić programowo - optionstrict</span><span class="sxs-lookup"><span data-stu-id="fd474-124">To set -optionstrict programmatically</span></span>  
  
-   <span data-ttu-id="fd474-125">Zobacz [Option Strict — instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fd474-125">See [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd474-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="fd474-126">Example</span></span>  
 <span data-ttu-id="fd474-127">Poniższy kod kompiluje `Test.vb` za pomocą semantyki typu strict.</span><span class="sxs-lookup"><span data-stu-id="fd474-127">The following code compiles `Test.vb` using strict type semantics.</span></span>  
  
```console
vbc -optionstrict+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="fd474-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fd474-128">See Also</span></span>  
 [<span data-ttu-id="fd474-129">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fd474-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="fd474-130">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="fd474-130">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [<span data-ttu-id="fd474-131">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="fd474-131">-optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [<span data-ttu-id="fd474-132">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="fd474-132">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="fd474-133">-nowarn</span><span class="sxs-lookup"><span data-stu-id="fd474-133">-nowarn</span></span>](../../../visual-basic/reference/command-line-compiler/nowarn.md)  
 [<span data-ttu-id="fd474-134">-warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fd474-134">-warnaserror (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/warnaserror.md)  
 [<span data-ttu-id="fd474-135">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="fd474-135">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="fd474-136">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="fd474-136">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="fd474-137">Okno dialogowe Opcje domyślne, projektów, Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fd474-137">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
