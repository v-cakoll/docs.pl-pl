---
title: -optionstrict —
ms.date: 07/20/2015
f1_keywords:
- -optionstrict
helpviewer_keywords:
- -optionstrict compiler option [Visual Basic]
- optionstrict compiler option [Visual Basic]
- /optionstrict compiler option [Visual Basic]
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
ms.openlocfilehash: fdea071f8c41f2e707d10c96c8b6ab1fbb44bad0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54733314"
---
# <a name="-optionstrict"></a><span data-ttu-id="52c19-102">-optionstrict —</span><span class="sxs-lookup"><span data-stu-id="52c19-102">-optionstrict</span></span>
<span data-ttu-id="52c19-103">Wymusza semantykę typów ścisłych w celu ograniczenia niejawnych konwersji typów.</span><span class="sxs-lookup"><span data-stu-id="52c19-103">Enforces strict type semantics to restrict implicit type conversions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52c19-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="52c19-104">Syntax</span></span>  
  
```  
-optionstrict[+ | -]  
-optionstrict[:custom]  
```  
  
## <a name="arguments"></a><span data-ttu-id="52c19-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="52c19-105">Arguments</span></span>  
 <span data-ttu-id="52c19-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="52c19-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="52c19-107">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="52c19-107">Optional.</span></span> <span data-ttu-id="52c19-108">`-optionstrict+` Opcja ogranicza niejawna konwersja typu.</span><span class="sxs-lookup"><span data-stu-id="52c19-108">The `-optionstrict+` option restricts implicit type conversion.</span></span> <span data-ttu-id="52c19-109">Wartość domyślna tej opcji to `-optionstrict-`.</span><span class="sxs-lookup"><span data-stu-id="52c19-109">The default for this option is `-optionstrict-`.</span></span> <span data-ttu-id="52c19-110">`-optionstrict+` Opcja jest taka sama jak `-optionstrict`.</span><span class="sxs-lookup"><span data-stu-id="52c19-110">The `-optionstrict+` option is the same as `-optionstrict`.</span></span> <span data-ttu-id="52c19-111">Można użyć obu tych opcji dla semantyka typów ograniczająca.</span><span class="sxs-lookup"><span data-stu-id="52c19-111">You can use both for permissive type semantics.</span></span>  
  
 `custom`  
 <span data-ttu-id="52c19-112">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="52c19-112">Required.</span></span> <span data-ttu-id="52c19-113">Ostrzegaj, gdy nie są przestrzegane ścisłą semantykę języka.</span><span class="sxs-lookup"><span data-stu-id="52c19-113">Warn when strict language semantics are not respected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52c19-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="52c19-114">Remarks</span></span>  
 <span data-ttu-id="52c19-115">Gdy `-optionstrict+` obowiązuje, tylko konwersje rozszerzające możliwe niejawnie.</span><span class="sxs-lookup"><span data-stu-id="52c19-115">When `-optionstrict+` is in effect, only widening type conversions can be made implicitly.</span></span> <span data-ttu-id="52c19-116">Niejawne zawężanie konwersji typów, takich jak przypisywanie `Decimal` typ obiektu do obiektu typu Liczba całkowita, są zgłaszane jako błędy.</span><span class="sxs-lookup"><span data-stu-id="52c19-116">Implicit narrowing type conversions, such as assigning a `Decimal` type object to an integer type object, are reported as errors.</span></span>  
  
 <span data-ttu-id="52c19-117">Aby wygenerować ostrzeżeń dotyczących niejawnych konwersji zawężających typu, należy użyć `-optionstrict:custom`.</span><span class="sxs-lookup"><span data-stu-id="52c19-117">To generate warnings for implicit narrowing type conversions, use `-optionstrict:custom`.</span></span> <span data-ttu-id="52c19-118">Użyj `-nowarn:numberlist` ignorowania ostrzeżeń dotyczących określonego i `-warnaserror:numberlist` do traktowania określonego ostrzeżenia jako błędy.</span><span class="sxs-lookup"><span data-stu-id="52c19-118">Use `-nowarn:numberlist` to ignore particular warnings and `-warnaserror:numberlist` to treat particular warnings as errors.</span></span>  
  
### <a name="to-set--optionstrict-in-the-visual-studio-ide"></a><span data-ttu-id="52c19-119">Aby ustawić - optionstrict — w środowisku IDE programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="52c19-119">To set -optionstrict in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="52c19-120">Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="52c19-120">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="52c19-121">Na **projektu** menu, kliknij przycisk **właściwości.**</span><span class="sxs-lookup"><span data-stu-id="52c19-121">On the **Project** menu, click **Properties.**</span></span>   
  
2.  <span data-ttu-id="52c19-122">Kliknij przycisk **skompilować** kartę.</span><span class="sxs-lookup"><span data-stu-id="52c19-122">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="52c19-123">Zmodyfikuj wartość w **Option Strict** pole.</span><span class="sxs-lookup"><span data-stu-id="52c19-123">Modify the value in the **Option Strict** box.</span></span>  
  
### <a name="to-set--optionstrict-programmatically"></a><span data-ttu-id="52c19-124">Aby programowo ustawić - optionstrict —</span><span class="sxs-lookup"><span data-stu-id="52c19-124">To set -optionstrict programmatically</span></span>  
  
-   <span data-ttu-id="52c19-125">Zobacz [Option Strict — instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="52c19-125">See [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="52c19-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="52c19-126">Example</span></span>  
 <span data-ttu-id="52c19-127">Poniższy kod kompiluje `Test.vb` semantykę typów ścisłych w użyciu.</span><span class="sxs-lookup"><span data-stu-id="52c19-127">The following code compiles `Test.vb` using strict type semantics.</span></span>  
  
```console
vbc -optionstrict+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="52c19-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="52c19-128">See also</span></span>
- [<span data-ttu-id="52c19-129">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="52c19-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="52c19-130">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="52c19-130">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="52c19-131">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="52c19-131">-optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [<span data-ttu-id="52c19-132">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="52c19-132">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="52c19-133">-nowarn</span><span class="sxs-lookup"><span data-stu-id="52c19-133">-nowarn</span></span>](../../../visual-basic/reference/command-line-compiler/nowarn.md)
- [<span data-ttu-id="52c19-134">-warnaserror — (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52c19-134">-warnaserror (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/warnaserror.md)
- [<span data-ttu-id="52c19-135">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="52c19-135">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="52c19-136">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="52c19-136">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="52c19-137">Domyślne ustawienia programu Visual Basic, Projekty, Opcje — okno dialogowe</span><span class="sxs-lookup"><span data-stu-id="52c19-137">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
