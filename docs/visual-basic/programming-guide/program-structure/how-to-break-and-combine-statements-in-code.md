---
title: 'Porady: przerywanie i łączenie instrukcji w Code (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb._
helpviewer_keywords:
- colons (:)
- line continuation
- _ line-continuation character
- ': line separator character'
- Visual Basic code, line breaks in
- Visual Basic code, line breaks
- Visual Basic code, line continuation
- long lines of code
- line terminator
- line-continuation sequence
- underscores [Visual Basic], in code
- statements [Visual Basic], line continuation in
- line breaks [Visual Basic], in code
- line-continuation character [Visual Basic]
- Visual Basic code, line continuation in
- statements [Visual Basic], line breaks in
ms.assetid: dea01dad-a8ac-484a-bb3a-8c45a1b1eccc
ms.openlocfilehash: 6bca3d62cb3e886ee08b9169d63d4c3a38247f3f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651021"
---
# <a name="how-to-break-and-combine-statements-in-code-visual-basic"></a><span data-ttu-id="86838-102">Porady: przerywanie i łączenie instrukcji w Code (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="86838-102">How to: Break and Combine Statements in Code (Visual Basic)</span></span>
<span data-ttu-id="86838-103">Podczas pisania kodu, można utworzyć w czasie długich instrukcji, które wymagają przewijanie w poziomie w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="86838-103">When writing your code, you might at times create lengthy statements that necessitate horizontal scrolling in the Code Editor.</span></span> <span data-ttu-id="86838-104">Mimo że to nie wpływa na sposób działania kodu, go utrudnia nikogo odczytać kodu znajdującego się na monitora.</span><span class="sxs-lookup"><span data-stu-id="86838-104">Although this doesn't affect the way your code runs, it makes it difficult for you or anyone else to read the code as it appears on the monitor.</span></span> <span data-ttu-id="86838-105">W takim przypadku należy rozważyć dzielenie jednej instrukcji długa na kilka wierszy.</span><span class="sxs-lookup"><span data-stu-id="86838-105">In such cases, you should consider breaking the single long statement into several lines.</span></span>  
  
### <a name="to-break-a-single-statement-into-multiple-lines"></a><span data-ttu-id="86838-106">Aby podzielić jednej instrukcji na wiele wierszy</span><span class="sxs-lookup"><span data-stu-id="86838-106">To break a single statement into multiple lines</span></span>  
  
-   <span data-ttu-id="86838-107">Użyj znaku kontynuacji wiersza jest to znak podkreślenia (`_`), w momencie, w którym ma zostać na podział wiersza.</span><span class="sxs-lookup"><span data-stu-id="86838-107">Use the line-continuation character, which is an underscore (`_`), at the point at which you want the line to break.</span></span> <span data-ttu-id="86838-108">Podkreślenie musi być natychmiast poprzedzone spację i od razu następuje terminator wiersza (powrotu karetki).</span><span class="sxs-lookup"><span data-stu-id="86838-108">The underscore must be immediately preceded by a space and immediately followed by a line terminator (carriage return).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="86838-109">W niektórych przypadkach w przypadku pominięcia znak kontynuacji wiersza kompilator Visual Basic niejawnie będzie instrukcji w następnym wierszu kodu.</span><span class="sxs-lookup"><span data-stu-id="86838-109">In some cases, if you omit the line-continuation character, the Visual Basic compiler will implicitly continue the statement on the next line of code.</span></span> <span data-ttu-id="86838-110">Aby uzyskać listę elementy składni, w których można pominąć znak kontynuacji wiersza, zobacz "Niejawne kontynuacji wiersza" w [instrukcje](../../../visual-basic/programming-guide/language-features/statements.md).</span><span class="sxs-lookup"><span data-stu-id="86838-110">For a list of syntax elements for which you can omit the line-continuation character, see "Implicit Line Continuation" in [Statements](../../../visual-basic/programming-guide/language-features/statements.md).</span></span>  
  
     <span data-ttu-id="86838-111">W poniższym przykładzie instrukcja jest dzielony na cztery wiersze z przerywa wszystkie znaki kontynuacji wiersza, ale ostatniego wiersza.</span><span class="sxs-lookup"><span data-stu-id="86838-111">In the following example, the statement is broken into four lines with line-continuation characters terminating all but the last line.</span></span>  
  
     [!code-vb[VbVbcnConventions#20](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_1.vb)]  
  
     <span data-ttu-id="86838-112">Przy użyciu tej sekwencji ułatwia kodu do odczytu, online i po drukowaniu.</span><span class="sxs-lookup"><span data-stu-id="86838-112">Using this sequence makes your code easier to read, both online and when printed.</span></span>  
  
     <span data-ttu-id="86838-113">Znak kontynuacji wiersza musi być ostatnim znakiem w wierszu.</span><span class="sxs-lookup"><span data-stu-id="86838-113">The line-continuation character must be the last character on a line.</span></span> <span data-ttu-id="86838-114">Nie można wykonać jego się inaczej w tym samym wierszu.</span><span class="sxs-lookup"><span data-stu-id="86838-114">You can't follow it with anything else on the same line.</span></span>  
  
     <span data-ttu-id="86838-115">Istnieją pewne ograniczenia klienckiemu, których można użyć znaku kontynuacji wiersza; na przykład nie można go użyć w środku nazwy argumentu.</span><span class="sxs-lookup"><span data-stu-id="86838-115">Some limitations exist as to where you can use the line-continuation character; for example, you can't use it in the middle of an argument name.</span></span> <span data-ttu-id="86838-116">Lista argumentów znak kontynuacji wiersza mogą być dzielone, ale nazwy poszczególnych argumenty muszą pozostać bez zmian.</span><span class="sxs-lookup"><span data-stu-id="86838-116">You can break an argument list with the line-continuation character, but the individual names of the arguments must remain intact.</span></span>  
  
     <span data-ttu-id="86838-117">Nie można kontynuować komentarz przy użyciu znak kontynuacji wiersza.</span><span class="sxs-lookup"><span data-stu-id="86838-117">You can't continue a comment by using a line-continuation character.</span></span> <span data-ttu-id="86838-118">Kompilator nie Sprawdź, czy znaki w komentarz dotyczący specjalnego znaczenia.</span><span class="sxs-lookup"><span data-stu-id="86838-118">The compiler doesn't examine the characters in a comment for special meaning.</span></span> <span data-ttu-id="86838-119">Komentarz wielu linii, powtórz symbol komentarza (`'`) w każdym wierszu.</span><span class="sxs-lookup"><span data-stu-id="86838-119">For a multiple-line comment, repeat the comment symbol (`'`) on each line.</span></span>  
  
 <span data-ttu-id="86838-120">Jednak zaleca się umieszczenie każdej instrukcji w osobnym wierszu, Visual Basic umożliwia również umieścić użycie wielu instrukcji w tym samym wierszu.</span><span class="sxs-lookup"><span data-stu-id="86838-120">Although placing each statement on a separate line is the recommended method, Visual Basic also allows you to place multiple statements on the same line.</span></span>  
  
### <a name="to-place-multiple-statements-on-the-same-line"></a><span data-ttu-id="86838-121">Aby umieścić użycie wielu instrukcji w tym samym wierszu</span><span class="sxs-lookup"><span data-stu-id="86838-121">To place multiple statements on the same line</span></span>  
  
-   <span data-ttu-id="86838-122">Instrukcje należy oddzielić średnikiem (`:`), jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="86838-122">Separate the statements with a colon (`:`), as in the following example.</span></span>  
  
     [!code-vb[VbVbcnConventions#10](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="86838-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="86838-123">See Also</span></span>  
 [<span data-ttu-id="86838-124">Struktura programu i konwencje związane z kodami</span><span class="sxs-lookup"><span data-stu-id="86838-124">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [<span data-ttu-id="86838-125">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="86838-125">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
