---
title: -optioncompare
ms.date: 07/20/2015
f1_keywords:
- /optioncompare
- -optioncompare
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
ms.openlocfilehash: ee130073b95dfbab5616a54c188b09fa92ccc930
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005364"
---
# <a name="-optioncompare"></a><span data-ttu-id="281d3-102">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="281d3-102">-optioncompare</span></span>
<span data-ttu-id="281d3-103">Określa sposób, w jaki są wykonywane porównania ciągów.</span><span class="sxs-lookup"><span data-stu-id="281d3-103">Specifies how string comparisons are made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="281d3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="281d3-104">Syntax</span></span>  
  
```console  
-optioncompare:{binary | text}  
```  
  
## <a name="remarks"></a><span data-ttu-id="281d3-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="281d3-105">Remarks</span></span>  
 <span data-ttu-id="281d3-106">Można określić `-optioncompare` w jednej z dwóch form: `-optioncompare:binary`, aby użyć porównań ciągów binarnych i `-optioncompare:text` do użycia porównania ciągów tekstowych.</span><span class="sxs-lookup"><span data-stu-id="281d3-106">You can specify `-optioncompare` in one of two forms: `-optioncompare:binary` to use binary string comparisons, and `-optioncompare:text` to use text string comparisons.</span></span> <span data-ttu-id="281d3-107">Domyślnie kompilator używa `-optioncompare:binary`.</span><span class="sxs-lookup"><span data-stu-id="281d3-107">By default, the compiler uses `-optioncompare:binary`.</span></span>  
  
 <span data-ttu-id="281d3-108">W systemie Microsoft Windows bieżąca strona kodowa Określa binarny porządek sortowania.</span><span class="sxs-lookup"><span data-stu-id="281d3-108">In Microsoft Windows, the current code page determines the binary sort order.</span></span> <span data-ttu-id="281d3-109">Typowa binarna kolejność sortowania jest następująca:</span><span class="sxs-lookup"><span data-stu-id="281d3-109">A typical binary sort order is as follows:</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="281d3-110">Porównania ciągów tekstowych są oparte na kolejności sortowania tekstu bez uwzględniania wielkości liter, która zależy od ustawień regionalnych systemu.</span><span class="sxs-lookup"><span data-stu-id="281d3-110">Text-based string comparisons are based on a case-insensitive text sort order determined by your system's locale.</span></span> <span data-ttu-id="281d3-111">Typowy porządek sortowania tekstu jest następujący:</span><span class="sxs-lookup"><span data-stu-id="281d3-111">A typical text sort order is as follows:</span></span>  
  
 `(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
### <a name="to-set--optioncompare-in-the-visual-studio-ide"></a><span data-ttu-id="281d3-112">Aby ustawić-optioncompare w środowisku IDE programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="281d3-112">To set -optioncompare in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="281d3-113">Zaznaczono projekt w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="281d3-113">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="281d3-114">W menu **projekt** kliknij polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="281d3-114">On the **Project** menu, click **Properties**.</span></span>   
  
2. <span data-ttu-id="281d3-115">Kliknij kartę **kompilacja** .</span><span class="sxs-lookup"><span data-stu-id="281d3-115">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="281d3-116">Zmodyfikuj wartość w polu **PORÓWNAJ opcję** .</span><span class="sxs-lookup"><span data-stu-id="281d3-116">Modify the value in the **Option Compare** box.</span></span>  
  
### <a name="to-set--optioncompare-programmatically"></a><span data-ttu-id="281d3-117">Aby programowo ustawić — optioncompare</span><span class="sxs-lookup"><span data-stu-id="281d3-117">To set -optioncompare programmatically</span></span>  
  
- <span data-ttu-id="281d3-118">Zobacz [Option Compare instrukcji](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="281d3-118">See [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="281d3-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="281d3-119">Example</span></span>  
 <span data-ttu-id="281d3-120">Poniższy kod kompiluje `ProjFile.vb` i używa porównywania ciągów binarnych.</span><span class="sxs-lookup"><span data-stu-id="281d3-120">The following code compiles `ProjFile.vb` and uses binary string comparisons.</span></span>  
  
```console
vbc -optioncompare:binary projFile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="281d3-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="281d3-121">See also</span></span>

- [<span data-ttu-id="281d3-122">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="281d3-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="281d3-123">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="281d3-123">-optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [<span data-ttu-id="281d3-124">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="281d3-124">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="281d3-125">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="281d3-125">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="281d3-126">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="281d3-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="281d3-127">Option Compare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="281d3-127">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="281d3-128">Domyślne ustawienia programu Visual Basic, Projekty, Opcje — okno dialogowe</span><span class="sxs-lookup"><span data-stu-id="281d3-128">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
