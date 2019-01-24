---
title: 'Instrukcje: Etykieta instrukcji (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
ms.openlocfilehash: 00a08bd3bd1f866cec883b6591b03ebd9d858b90
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54552267"
---
# <a name="how-to-label-statements-visual-basic"></a><span data-ttu-id="5e6e6-102">Instrukcje: Etykieta instrukcji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5e6e6-102">How to: Label Statements (Visual Basic)</span></span>
<span data-ttu-id="5e6e6-103">Bloki instrukcji składają się z wierszy kodu, rozdzielone średnikami.</span><span class="sxs-lookup"><span data-stu-id="5e6e6-103">Statement blocks are made up of lines of code delimited by colons.</span></span> <span data-ttu-id="5e6e6-104">Wiersze kodu poprzedzone identyfikujący ciąg lub liczba całkowita, są określane jako *etykietą*.</span><span class="sxs-lookup"><span data-stu-id="5e6e6-104">Lines of code preceded by an identifying string or integer are said to be *labeled*.</span></span> <span data-ttu-id="5e6e6-105">Etykiety instrukcji są używane w sposób znaczyć linię kodu w celu identyfikowania go do użycia przy użyciu instrukcji takich jak `On Error Goto`.</span><span class="sxs-lookup"><span data-stu-id="5e6e6-105">Statement labels are used to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>  
  
 <span data-ttu-id="5e6e6-106">Etykiety mogą być albo prawidłowych identyfikatorów języka Visual Basic — takich jak te, które identyfikują programistyczny — lub literały całkowite.</span><span class="sxs-lookup"><span data-stu-id="5e6e6-106">Labels may be either valid Visual Basic identifiers—such as those that identify programming elements—or integer literals.</span></span> <span data-ttu-id="5e6e6-107">Etykieta musi znajdować się na początku wiersza kodu źródłowego i musi być następuje dwukropek, niezależnie od tego, czy następuje instrukcji w tym samym wierszu.</span><span class="sxs-lookup"><span data-stu-id="5e6e6-107">A label must appear at the beginning of a line of source code and must be followed by a colon, regardless of whether it is followed by a statement on the same line.</span></span>  
  
 <span data-ttu-id="5e6e6-108">Kompilator identyfikuje etykiety, sprawdzając, czy początek wiersza pasuje do żadnego identyfikatora już zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="5e6e6-108">The compiler identifies labels by checking whether the beginning of the line matches any already-defined identifier.</span></span> <span data-ttu-id="5e6e6-109">Jeśli nie, kompilator zakłada, że jest etykietę.</span><span class="sxs-lookup"><span data-stu-id="5e6e6-109">If it does not, the compiler assumes it is a label.</span></span>  
  
 <span data-ttu-id="5e6e6-110">Etykiety mają własnej przestrzeni deklaracji i nie kolidują z innymi identyfikatorami.</span><span class="sxs-lookup"><span data-stu-id="5e6e6-110">Labels have their own declaration space and do not interfere with other identifiers.</span></span> <span data-ttu-id="5e6e6-111">Zakres etykiety jest treści metody.</span><span class="sxs-lookup"><span data-stu-id="5e6e6-111">A label's scope is the body of the method.</span></span> <span data-ttu-id="5e6e6-112">Deklaracja etykieta ma pierwszeństwo przed w każdej sytuacji niejednoznaczne.</span><span class="sxs-lookup"><span data-stu-id="5e6e6-112">Label declaration takes precedence in any ambiguous situation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e6e6-113">Etykiety mogą służyć tylko w instrukcji wykonywalnych wewnątrz metody.</span><span class="sxs-lookup"><span data-stu-id="5e6e6-113">Labels can be used only on executable statements inside methods.</span></span>  
  
### <a name="to-label-a-line-of-code"></a><span data-ttu-id="5e6e6-114">Aby dodać etykietę wiersza kodu</span><span class="sxs-lookup"><span data-stu-id="5e6e6-114">To label a line of code</span></span>  
  
-   <span data-ttu-id="5e6e6-115">Umieść identyfikator, następuje dwukropek, na początku wiersza kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="5e6e6-115">Place an identifier, followed by a colon, at the beginning of the line of source code.</span></span>  
  
     <span data-ttu-id="5e6e6-116">Na przykład następujące wiersze kodu są oznaczone za pomocą `Jump` i `120`odpowiednio:</span><span class="sxs-lookup"><span data-stu-id="5e6e6-116">For example, the following lines of code are labeled with `Jump` and `120`, respectively:</span></span>  
  
     [!code-vb[VbVbalrStatements#708](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/how-to-label-statements_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="5e6e6-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5e6e6-117">See also</span></span>
- [<span data-ttu-id="5e6e6-118">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="5e6e6-118">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="5e6e6-119">Nazwy zadeklarowanych elementów</span><span class="sxs-lookup"><span data-stu-id="5e6e6-119">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="5e6e6-120">Konwencje dotyczące struktury programów i kodu</span><span class="sxs-lookup"><span data-stu-id="5e6e6-120">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
