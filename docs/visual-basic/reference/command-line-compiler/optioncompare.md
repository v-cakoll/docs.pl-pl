---
title: -optioncompare —
ms.date: 07/20/2015
f1_keywords:
- /optioncompare
- -optioncompare
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
ms.openlocfilehash: 1d50a3bb739bbde09fa10d2adf03ec7c1ff5d344
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50180803"
---
# <a name="-optioncompare"></a><span data-ttu-id="bafef-102">-optioncompare —</span><span class="sxs-lookup"><span data-stu-id="bafef-102">-optioncompare</span></span>
<span data-ttu-id="bafef-103">Określa, jak są wykonywane porównywania ciągów.</span><span class="sxs-lookup"><span data-stu-id="bafef-103">Specifies how string comparisons are made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bafef-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bafef-104">Syntax</span></span>  
  
```  
-optioncompare:{binary | text}  
```  
  
## <a name="remarks"></a><span data-ttu-id="bafef-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bafef-105">Remarks</span></span>  
 <span data-ttu-id="bafef-106">Można określić `-optioncompare` w jednej z dwóch formach: `-optioncompare:binary` używać ciąg binarny porównań, i `-optioncompare:text` używać porównania ciągów tekstu.</span><span class="sxs-lookup"><span data-stu-id="bafef-106">You can specify `-optioncompare` in one of two forms: `-optioncompare:binary` to use binary string comparisons, and `-optioncompare:text` to use text string comparisons.</span></span> <span data-ttu-id="bafef-107">Domyślnie kompilator używa `-optioncompare:binary`.</span><span class="sxs-lookup"><span data-stu-id="bafef-107">By default, the compiler uses `-optioncompare:binary`.</span></span>  
  
 <span data-ttu-id="bafef-108">W Windows firmy Microsoft w bieżącej stronie kodowej Określa binarny porządek sortowania.</span><span class="sxs-lookup"><span data-stu-id="bafef-108">In Microsoft Windows, the current code page determines the binary sort order.</span></span> <span data-ttu-id="bafef-109">Typowe binarny porządek sortowania jest następująca:</span><span class="sxs-lookup"><span data-stu-id="bafef-109">A typical binary sort order is as follows:</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="bafef-110">Porównywanie ciągów tekstowych opierają się na kolejność sortowania bez uwzględniania wielkości liter tekstu, określane przez ustawienia regionalne Twojego systemu.</span><span class="sxs-lookup"><span data-stu-id="bafef-110">Text-based string comparisons are based on a case-insensitive text sort order determined by your system's locale.</span></span> <span data-ttu-id="bafef-111">Typowe tekstowy porządek sortowania jest następująca:</span><span class="sxs-lookup"><span data-stu-id="bafef-111">A typical text sort order is as follows:</span></span>  
  
 `(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
### <a name="to-set--optioncompare-in-the-visual-studio-ide"></a><span data-ttu-id="bafef-112">Aby ustawić - optioncompare — w środowisku IDE programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bafef-112">To set -optioncompare in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="bafef-113">Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="bafef-113">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="bafef-114">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="bafef-114">On the **Project** menu, click **Properties**.</span></span>   
  
2.  <span data-ttu-id="bafef-115">Kliknij przycisk **skompilować** kartę.</span><span class="sxs-lookup"><span data-stu-id="bafef-115">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="bafef-116">Zmodyfikuj wartość w **Option Compare** pole.</span><span class="sxs-lookup"><span data-stu-id="bafef-116">Modify the value in the **Option Compare** box.</span></span>  
  
### <a name="to-set--optioncompare-programmatically"></a><span data-ttu-id="bafef-117">Aby programowo ustawić - optioncompare —</span><span class="sxs-lookup"><span data-stu-id="bafef-117">To set -optioncompare programmatically</span></span>  
  
-   <span data-ttu-id="bafef-118">Zobacz [Option Compare — instrukcja](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="bafef-118">See [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bafef-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="bafef-119">Example</span></span>  
 <span data-ttu-id="bafef-120">Poniższy kod kompiluje `ProjFile.vb` i używa porównania ciągów binarnych.</span><span class="sxs-lookup"><span data-stu-id="bafef-120">The following code compiles `ProjFile.vb` and uses binary string comparisons.</span></span>  
  
```console
vbc -optioncompare:binary projFile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="bafef-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bafef-121">See Also</span></span>  
 [<span data-ttu-id="bafef-122">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bafef-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="bafef-123">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="bafef-123">-optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [<span data-ttu-id="bafef-124">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="bafef-124">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [<span data-ttu-id="bafef-125">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="bafef-125">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="bafef-126">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="bafef-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="bafef-127">Option Compare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="bafef-127">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [<span data-ttu-id="bafef-128">Domyślne ustawienia programu Visual Basic, Projekty, Opcje — okno dialogowe</span><span class="sxs-lookup"><span data-stu-id="bafef-128">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
