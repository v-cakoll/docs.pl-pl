---
title: 'Instrukcje: Przerywanie i łączenie instrukcji w Code (Visual Basic)'
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
ms.openlocfilehash: 680084c39b90d4f664f48559fa21388ce192d999
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58837744"
---
# <a name="how-to-break-and-combine-statements-in-code-visual-basic"></a><span data-ttu-id="1c679-102">Instrukcje: Przerywanie i łączenie instrukcji w Code (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1c679-102">How to: Break and Combine Statements in Code (Visual Basic)</span></span>
<span data-ttu-id="1c679-103">Podczas pisania kodu, można utworzyć w czasie długich instrukcji, które wymagają przewijanie w poziomie w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="1c679-103">When writing your code, you might at times create lengthy statements that necessitate horizontal scrolling in the Code Editor.</span></span> <span data-ttu-id="1c679-104">Mimo że to nie ma wpływu na sposób działania kodu, jego utrudnia nikogo odczytać kodu znajdującego się na monitor.</span><span class="sxs-lookup"><span data-stu-id="1c679-104">Although this doesn't affect the way your code runs, it makes it difficult for you or anyone else to read the code as it appears on the monitor.</span></span> <span data-ttu-id="1c679-105">W takich przypadkach należy rozważyć podzielenie pojedynczej instrukcji długich na kilka wierszy.</span><span class="sxs-lookup"><span data-stu-id="1c679-105">In such cases, you should consider breaking the single long statement into several lines.</span></span>  
  
### <a name="to-break-a-single-statement-into-multiple-lines"></a><span data-ttu-id="1c679-106">Aby przerwać pojedynczej instrukcji wiele wierszy</span><span class="sxs-lookup"><span data-stu-id="1c679-106">To break a single statement into multiple lines</span></span>  
  
-   <span data-ttu-id="1c679-107">Użyj znaku kontynuacji wiersza, który jest znakiem podkreślenia (`_`), w momencie, dla której ma zostać na podział wiersza.</span><span class="sxs-lookup"><span data-stu-id="1c679-107">Use the line-continuation character, which is an underscore (`_`), at the point at which you want the line to break.</span></span> <span data-ttu-id="1c679-108">Znak podkreślenia należy natychmiast poprzedzone spację i bezpośrednio po nim terminator wiersza (powrót karetki).</span><span class="sxs-lookup"><span data-stu-id="1c679-108">The underscore must be immediately preceded by a space and immediately followed by a line terminator (carriage return).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1c679-109">W niektórych przypadkach Jeśli pominięto znak kontynuacji wiersza, kompilator Visual Basic będą nadal w następnym wierszu kodu niejawnie instrukcji.</span><span class="sxs-lookup"><span data-stu-id="1c679-109">In some cases, if you omit the line-continuation character, the Visual Basic compiler will implicitly continue the statement on the next line of code.</span></span> <span data-ttu-id="1c679-110">Aby uzyskać listę elementy składni, dla których można pominąć znak kontynuacji wiersza, zobacz "Niejawnej kontynuacji wiersza" w [instrukcji](../../../visual-basic/programming-guide/language-features/statements.md).</span><span class="sxs-lookup"><span data-stu-id="1c679-110">For a list of syntax elements for which you can omit the line-continuation character, see "Implicit Line Continuation" in [Statements](../../../visual-basic/programming-guide/language-features/statements.md).</span></span>  
  
     <span data-ttu-id="1c679-111">W poniższym przykładzie instrukcja jest dzielony na cztery wiersze ze znakami kontynuacji wiersza przerywa wszystkie, ale ostatni wiersz.</span><span class="sxs-lookup"><span data-stu-id="1c679-111">In the following example, the statement is broken into four lines with line-continuation characters terminating all but the last line.</span></span>  
  
     [!code-vb[VbVbcnConventions#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#20)]  
  
     <span data-ttu-id="1c679-112">Za pomocą tej sekwencji sprawia, że Twój kod łatwiejsza do odczytania, zarówno online, jak i kiedy wydrukowany.</span><span class="sxs-lookup"><span data-stu-id="1c679-112">Using this sequence makes your code easier to read, both online and when printed.</span></span>  
  
     <span data-ttu-id="1c679-113">Znak kontynuacji wiersza musi być ostatnim znakiem w wierszu.</span><span class="sxs-lookup"><span data-stu-id="1c679-113">The line-continuation character must be the last character on a line.</span></span> <span data-ttu-id="1c679-114">Nie można wykonać to z jakichkolwiek innych czynności w tym samym wierszu.</span><span class="sxs-lookup"><span data-stu-id="1c679-114">You can't follow it with anything else on the same line.</span></span>  
  
     <span data-ttu-id="1c679-115">Istnieje pewne ograniczenia, do których można użyć znaku kontynuacji wiersza; na przykład nie można go użyć w środku nazwę argumentu.</span><span class="sxs-lookup"><span data-stu-id="1c679-115">Some limitations exist as to where you can use the line-continuation character; for example, you can't use it in the middle of an argument name.</span></span> <span data-ttu-id="1c679-116">Możesz przerwać listy argumentów znakiem kontynuacji wiersza, ale poszczególne nazwy argumentów musi pozostać bez zmian.</span><span class="sxs-lookup"><span data-stu-id="1c679-116">You can break an argument list with the line-continuation character, but the individual names of the arguments must remain intact.</span></span>  
  
     <span data-ttu-id="1c679-117">Komentarz nie może kontynuować, za pomocą znaku kontynuacji wiersza.</span><span class="sxs-lookup"><span data-stu-id="1c679-117">You can't continue a comment by using a line-continuation character.</span></span> <span data-ttu-id="1c679-118">Kompilator nie zbadać znaki w komentarzu do specjalnego znaczenia.</span><span class="sxs-lookup"><span data-stu-id="1c679-118">The compiler doesn't examine the characters in a comment for special meaning.</span></span> <span data-ttu-id="1c679-119">Komentarz do wielu linii, powtórz symbol komentarza (`'`) w każdym wierszu.</span><span class="sxs-lookup"><span data-stu-id="1c679-119">For a multiple-line comment, repeat the comment symbol (`'`) on each line.</span></span>  
  
 <span data-ttu-id="1c679-120">Mimo że zaleca się umieszczenie każdej instrukcji w osobnym wierszu, Visual Basic umożliwia również umieścić użycie wielu instrukcji w tym samym wierszu.</span><span class="sxs-lookup"><span data-stu-id="1c679-120">Although placing each statement on a separate line is the recommended method, Visual Basic also allows you to place multiple statements on the same line.</span></span>  
  
### <a name="to-place-multiple-statements-on-the-same-line"></a><span data-ttu-id="1c679-121">Aby umieścić użycie wielu instrukcji w tym samym wierszu</span><span class="sxs-lookup"><span data-stu-id="1c679-121">To place multiple statements on the same line</span></span>  
  
-   <span data-ttu-id="1c679-122">Instrukcje należy oddzielić średnikiem (`:`), jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1c679-122">Separate the statements with a colon (`:`), as in the following example.</span></span>  
  
     [!code-vb[VbVbcnConventions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="1c679-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1c679-123">See also</span></span>

- [<span data-ttu-id="1c679-124">Konwencje dotyczące struktury programów i kodu</span><span class="sxs-lookup"><span data-stu-id="1c679-124">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [<span data-ttu-id="1c679-125">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="1c679-125">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
