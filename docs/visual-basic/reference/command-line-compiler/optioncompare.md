---
title: /optioncompare
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: /optioncompare
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a6f602e0b0b23345bf1f5aae843bd44bd2642bc9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="optioncompare"></a><span data-ttu-id="9c9e6-102">/optioncompare</span><span class="sxs-lookup"><span data-stu-id="9c9e6-102">/optioncompare</span></span>
<span data-ttu-id="9c9e6-103">Określa, jak zostały wprowadzone porównywania ciągów.</span><span class="sxs-lookup"><span data-stu-id="9c9e6-103">Specifies how string comparisons are made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c9e6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9c9e6-104">Syntax</span></span>  
  
```  
/optioncompare:{binary | text}  
```  
  
## <a name="remarks"></a><span data-ttu-id="9c9e6-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9c9e6-105">Remarks</span></span>  
 <span data-ttu-id="9c9e6-106">Można określić `/optioncompare` w jednym z dwóch formach: `/optioncompare:binary` do używania porównania ciągu binarnego i `/optioncompare:text` do używania porównania ciągów tekstu.</span><span class="sxs-lookup"><span data-stu-id="9c9e6-106">You can specify `/optioncompare` in one of two forms: `/optioncompare:binary` to use binary string comparisons, and `/optioncompare:text` to use text string comparisons.</span></span> <span data-ttu-id="9c9e6-107">Domyślnie używa kompilator `/optioncompare:binary`.</span><span class="sxs-lookup"><span data-stu-id="9c9e6-107">By default, the compiler uses `/optioncompare:binary`.</span></span>  
  
 <span data-ttu-id="9c9e6-108">W systemie Microsoft Windows strona kodowa używana Określa binarny porządek sortowania.</span><span class="sxs-lookup"><span data-stu-id="9c9e6-108">In Microsoft Windows, the code page being used determines the binary sort order.</span></span> <span data-ttu-id="9c9e6-109">Typowy binarny porządek sortowania jest następujący:</span><span class="sxs-lookup"><span data-stu-id="9c9e6-109">A typical binary sort order is as follows:</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="9c9e6-110">Porównywanie ciągów tekstowych są oparte na porządek sortowania bez uwzględniania wielkości liter tekstu ustaleniami ustawień regionalnych systemu.</span><span class="sxs-lookup"><span data-stu-id="9c9e6-110">Text-based string comparisons are based on a case-insensitive text sort order determined by your system's locale.</span></span> <span data-ttu-id="9c9e6-111">Typowy tekstowy porządek sortowania jest następujący:</span><span class="sxs-lookup"><span data-stu-id="9c9e6-111">A typical text sort order is as follows:</span></span>  
  
 `(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
### <a name="to-set-optioncompare-in-the-visual-studio-ide"></a><span data-ttu-id="9c9e6-112">Aby ustawić/optioncompare w środowisku IDE programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9c9e6-112">To set /optioncompare in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="9c9e6-113">Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="9c9e6-113">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="9c9e6-114">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="9c9e6-114">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="9c9e6-115">Aby uzyskać więcej informacji, zobacz [wprowadzenie do projektanta projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="9c9e6-115">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="9c9e6-116">Kliknij przycisk **skompilować** kartę.</span><span class="sxs-lookup"><span data-stu-id="9c9e6-116">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="9c9e6-117">Zmodyfikuj wartość w **Option Compare** pole.</span><span class="sxs-lookup"><span data-stu-id="9c9e6-117">Modify the value in the **Option Compare** box.</span></span>  
  
### <a name="to-set-optioncompare-programmatically"></a><span data-ttu-id="9c9e6-118">Aby ustawić/optioncompare programowo</span><span class="sxs-lookup"><span data-stu-id="9c9e6-118">To set /optioncompare programmatically</span></span>  
  
-   <span data-ttu-id="9c9e6-119">Zobacz [Option Compare — instrukcja](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9c9e6-119">See [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c9e6-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="9c9e6-120">Example</span></span>  
 <span data-ttu-id="9c9e6-121">Poniższy kod kompiluje `ProjFile.vb` i używa porównania ciągu binarnego.</span><span class="sxs-lookup"><span data-stu-id="9c9e6-121">The following code compiles `ProjFile.vb` and uses binary string comparisons.</span></span>  
  
```  
vbc /optioncompare:binary projFile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="9c9e6-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9c9e6-122">See Also</span></span>  
 [<span data-ttu-id="9c9e6-123">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9c9e6-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="9c9e6-124">/ optionexplicit</span><span class="sxs-lookup"><span data-stu-id="9c9e6-124">/optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [<span data-ttu-id="9c9e6-125">/ optionstrict —</span><span class="sxs-lookup"><span data-stu-id="9c9e6-125">/optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [<span data-ttu-id="9c9e6-126">/ optioninfer</span><span class="sxs-lookup"><span data-stu-id="9c9e6-126">/optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="9c9e6-127">Kompilacja przykładów — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="9c9e6-127">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="9c9e6-128">Option Compare — instrukcja</span><span class="sxs-lookup"><span data-stu-id="9c9e6-128">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [<span data-ttu-id="9c9e6-129">Okno dialogowe Opcje domyślne, projektów, Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9c9e6-129">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
