---
title: 'Porady: etykietowanie instrukcji (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
ms.openlocfilehash: df368bdba73ca35dd70bdd2f4e88cc10af894b5a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-label-statements-visual-basic"></a><span data-ttu-id="525ca-102">Porady: etykietowanie instrukcji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="525ca-102">How to: Label Statements (Visual Basic)</span></span>
<span data-ttu-id="525ca-103">Bloki instrukcji składają się z wierszy kodu rozdzielone dwukropkiem.</span><span class="sxs-lookup"><span data-stu-id="525ca-103">Statement blocks are made up of lines of code delimited by colons.</span></span> <span data-ttu-id="525ca-104">Wiersze kodu poprzedzone identyfikujący ciąg lub liczba całkowita są określane jako *etykietą*.</span><span class="sxs-lookup"><span data-stu-id="525ca-104">Lines of code preceded by an identifying string or integer are said to be *labeled*.</span></span> <span data-ttu-id="525ca-105">Etykiety instrukcji są używane do oznaczenia wiersz kodu, aby zidentyfikować go do użytku w instrukcjach takich jak `On Error Goto`.</span><span class="sxs-lookup"><span data-stu-id="525ca-105">Statement labels are used to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>  
  
 <span data-ttu-id="525ca-106">Etykiety mogą być albo prawidłowych identyfikatorów języka Visual Basic — takich jak te, które identyfikują programistyczny — lub literały całkowite.</span><span class="sxs-lookup"><span data-stu-id="525ca-106">Labels may be either valid Visual Basic identifiers—such as those that identify programming elements—or integer literals.</span></span> <span data-ttu-id="525ca-107">Etykiety musi znajdować się na początku wiersza kodu źródłowego i musi być z dwukropkiem, niezależnie od tego, czy występuje po nim instrukcji w tym samym wierszu.</span><span class="sxs-lookup"><span data-stu-id="525ca-107">A label must appear at the beginning of a line of source code and must be followed by a colon, regardless of whether it is followed by a statement on the same line.</span></span>  
  
 <span data-ttu-id="525ca-108">Kompilator identyfikuje etykiety przez sprawdzenie, czy początek wiersza odpowiada żadnego identyfikatora już zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="525ca-108">The compiler identifies labels by checking whether the beginning of the line matches any already-defined identifier.</span></span> <span data-ttu-id="525ca-109">Jeśli nie, kompilator przyjęto założenie, że jest etykiety.</span><span class="sxs-lookup"><span data-stu-id="525ca-109">If it does not, the compiler assumes it is a label.</span></span>  
  
 <span data-ttu-id="525ca-110">Etykiety ma miejsce ich własnych deklaracji i nie zakłóca innych identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="525ca-110">Labels have their own declaration space and do not interfere with other identifiers.</span></span> <span data-ttu-id="525ca-111">Zakres etykiety jest treści metody.</span><span class="sxs-lookup"><span data-stu-id="525ca-111">A label's scope is the body of the method.</span></span> <span data-ttu-id="525ca-112">Deklaracja etykieta ma pierwszeństwo w każdej sytuacji niejednoznaczne.</span><span class="sxs-lookup"><span data-stu-id="525ca-112">Label declaration takes precedence in any ambiguous situation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="525ca-113">Etykiety może być używany tylko instrukcje wykonywalne wewnątrz metody.</span><span class="sxs-lookup"><span data-stu-id="525ca-113">Labels can be used only on executable statements inside methods.</span></span>  
  
### <a name="to-label-a-line-of-code"></a><span data-ttu-id="525ca-114">Aby dodać etykietę wiersza kodu</span><span class="sxs-lookup"><span data-stu-id="525ca-114">To label a line of code</span></span>  
  
-   <span data-ttu-id="525ca-115">Umieść identyfikator i dwukropek, na początku wiersza kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="525ca-115">Place an identifier, followed by a colon, at the beginning of the line of source code.</span></span>  
  
     <span data-ttu-id="525ca-116">Na przykład etykietą następujące wiersze kodu `Jump` i `120`odpowiednio:</span><span class="sxs-lookup"><span data-stu-id="525ca-116">For example, the following lines of code are labeled with `Jump` and `120`, respectively:</span></span>  
  
     [!code-vb[VbVbalrStatements#708](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/how-to-label-statements_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="525ca-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="525ca-117">See Also</span></span>  
 [<span data-ttu-id="525ca-118">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="525ca-118">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)  
 [<span data-ttu-id="525ca-119">Nazwy zadeklarowanych elementów</span><span class="sxs-lookup"><span data-stu-id="525ca-119">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="525ca-120">Struktura programu i konwencje związane z kodami</span><span class="sxs-lookup"><span data-stu-id="525ca-120">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
