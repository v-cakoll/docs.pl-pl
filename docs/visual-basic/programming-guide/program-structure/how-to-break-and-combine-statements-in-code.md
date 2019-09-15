---
title: 'Instrukcje: Przerwij i Połącz instrukcje w kodzie (Visual Basic)'
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
ms.openlocfilehash: a0a77b161d81271a4cb7eecf2982a287debee6a5
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991727"
---
# <a name="how-to-break-and-combine-statements-in-code-visual-basic"></a><span data-ttu-id="f6828-102">Instrukcje: Przerwij i Połącz instrukcje w kodzie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6828-102">How to: Break and Combine Statements in Code (Visual Basic)</span></span>

<span data-ttu-id="f6828-103">Podczas pisania kodu można czasami tworzyć długie instrukcje, które wymagają przewijania w poziomie w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="f6828-103">When writing your code, you might at times create lengthy statements that necessitate horizontal scrolling in the Code Editor.</span></span> <span data-ttu-id="f6828-104">Chociaż nie ma to wpływu na sposób działania kodu, utrudnia użytkownikowi lub innym osobom odczytywanie kodu w postaci, w jakiej jest wyświetlany na monitorze.</span><span class="sxs-lookup"><span data-stu-id="f6828-104">Although this doesn't affect the way your code runs, it makes it difficult for you or anyone else to read the code as it appears on the monitor.</span></span> <span data-ttu-id="f6828-105">W takich przypadkach należy rozważyć rozdzielenie pojedynczej długiej instrukcji na kilka wierszy.</span><span class="sxs-lookup"><span data-stu-id="f6828-105">In such cases, you should consider breaking the single long statement into several lines.</span></span>

## <a name="to-break-a-single-statement-into-multiple-lines"></a><span data-ttu-id="f6828-106">Aby przerwać pojedynczą instrukcję do wielu wierszy</span><span class="sxs-lookup"><span data-stu-id="f6828-106">To break a single statement into multiple lines</span></span>

<span data-ttu-id="f6828-107">Użyj znaku kontynuacji wiersza, który jest podkreśleniem (`_`), w punkcie, w którym ma zostać przerwana linia.</span><span class="sxs-lookup"><span data-stu-id="f6828-107">Use the line-continuation character, which is an underscore (`_`), at the point at which you want the line to break.</span></span> <span data-ttu-id="f6828-108">Znak podkreślenia musi być bezpośrednio poprzedzony spacją, po którym następuje terminator wiersza (znak powrotu karetki) lub (począwszy od wersji 16,0) komentarz, po którym następuje znak powrotu karetki.</span><span class="sxs-lookup"><span data-stu-id="f6828-108">The underscore must be immediately preceded by a space and immediately followed by a line terminator (carriage return) or (starting with version 16.0) a comment followed by a carriage return.</span></span>

  > [!NOTE]
  > <span data-ttu-id="f6828-109">W niektórych przypadkach, jeśli pominięto znak kontynuacji wiersza, kompilator Visual Basic niejawnie kontynuuje instrukcję w następnym wierszu kodu.</span><span class="sxs-lookup"><span data-stu-id="f6828-109">In some cases, if you omit the line-continuation character, the Visual Basic compiler will implicitly continue the statement on the next line of code.</span></span> <span data-ttu-id="f6828-110">Aby uzyskać listę elementów składni, dla których można pominąć znak kontynuacji wiersza, zobacz "niejawne kontynuacja wiersza" w [instrukcjach](../../../visual-basic/programming-guide/language-features/statements.md).</span><span class="sxs-lookup"><span data-stu-id="f6828-110">For a list of syntax elements for which you can omit the line-continuation character, see "Implicit Line Continuation" in [Statements](../../../visual-basic/programming-guide/language-features/statements.md).</span></span>

  <span data-ttu-id="f6828-111">W poniższym przykładzie instrukcja jest dzielona na cztery wiersze z znakami kontynuacji wiersza kończącymi wszystkie oprócz ostatniego wiersza.</span><span class="sxs-lookup"><span data-stu-id="f6828-111">In the following example, the statement is broken into four lines with line-continuation characters terminating all but the last line.</span></span>

  [!code-vb[VbVbcnConventions#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#20)]

  <span data-ttu-id="f6828-112">Użycie tej sekwencji sprawia, że kod będzie łatwiejszy do odczytania, zarówno w trybie online, jak i podczas drukowania.</span><span class="sxs-lookup"><span data-stu-id="f6828-112">Using this sequence makes your code easier to read, both online and when printed.</span></span>

  <span data-ttu-id="f6828-113">Znak kontynuacji wiersza musi być ostatnim znakiem w wierszu.</span><span class="sxs-lookup"><span data-stu-id="f6828-113">The line-continuation character must be the last character on a line.</span></span> <span data-ttu-id="f6828-114">Nie można wykonać kolejnej czynności w tym samym wierszu.</span><span class="sxs-lookup"><span data-stu-id="f6828-114">You can't follow it with anything else on the same line.</span></span>

  <span data-ttu-id="f6828-115">Istnieją pewne ograniczenia, w których można użyć znaku kontynuacji wiersza; na przykład nie można użyć go w środku nazwy argumentu.</span><span class="sxs-lookup"><span data-stu-id="f6828-115">Some limitations exist as to where you can use the line-continuation character; for example, you can't use it in the middle of an argument name.</span></span> <span data-ttu-id="f6828-116">Możesz przerwać listę argumentów za pomocą znaku kontynuacji wiersza, ale poszczególne nazwy argumentów muszą pozostać nienaruszone.</span><span class="sxs-lookup"><span data-stu-id="f6828-116">You can break an argument list with the line-continuation character, but the individual names of the arguments must remain intact.</span></span>

  <span data-ttu-id="f6828-117">Nie można kontynuować komentarza przy użyciu znaku kontynuacji wiersza.</span><span class="sxs-lookup"><span data-stu-id="f6828-117">You can't continue a comment by using a line-continuation character.</span></span> <span data-ttu-id="f6828-118">Kompilator nie bada znaków w komentarzu pod kątem specjalnego znaczenia.</span><span class="sxs-lookup"><span data-stu-id="f6828-118">The compiler doesn't examine the characters in a comment for special meaning.</span></span> <span data-ttu-id="f6828-119">W przypadku komentarza z wieloma wierszami należy powtórzyć symbol`'`komentarza () w każdym wierszu.</span><span class="sxs-lookup"><span data-stu-id="f6828-119">For a multiple-line comment, repeat the comment symbol (`'`) on each line.</span></span>

 <span data-ttu-id="f6828-120">Chociaż umieszczenie każdej instrukcji w osobnym wierszu jest zalecaną metodą, Visual Basic umożliwia również umieszczenie wielu instrukcji w tym samym wierszu.</span><span class="sxs-lookup"><span data-stu-id="f6828-120">Although placing each statement on a separate line is the recommended method, Visual Basic also allows you to place multiple statements on the same line.</span></span>

## <a name="to-place-multiple-statements-on-the-same-line"></a><span data-ttu-id="f6828-121">Aby umieścić wiele instrukcji w tym samym wierszu</span><span class="sxs-lookup"><span data-stu-id="f6828-121">To place multiple statements on the same line</span></span>

<span data-ttu-id="f6828-122">Rozdziel instrukcje średnikami (`:`), jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="f6828-122">Separate the statements with a colon (`:`), as in the following example:</span></span>

  [!code-vb[VbVbcnConventions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#10)]

## <a name="see-also"></a><span data-ttu-id="f6828-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f6828-123">See also</span></span>

- [<span data-ttu-id="f6828-124">Konwencje dotyczące struktury programów i kodu</span><span class="sxs-lookup"><span data-stu-id="f6828-124">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [<span data-ttu-id="f6828-125">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="f6828-125">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
