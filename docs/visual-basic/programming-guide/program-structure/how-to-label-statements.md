---
title: 'Instrukcje: Instrukcje etykiet (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
ms.openlocfilehash: 9a5f2039716a18011cac3dfd9b011d5b3868c294
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054051"
---
# <a name="how-to-label-statements-visual-basic"></a><span data-ttu-id="2193d-102">Instrukcje: Instrukcje etykiet (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2193d-102">How to: Label Statements (Visual Basic)</span></span>

<span data-ttu-id="2193d-103">Bloki instrukcji składają się z wierszy kodu rozdzielanych średnikami.</span><span class="sxs-lookup"><span data-stu-id="2193d-103">Statement blocks are made up of lines of code delimited by colons.</span></span> <span data-ttu-id="2193d-104">Wiersze kodu poprzedzone ciągiem identyfikującym lub liczbą całkowitą są określane jako *etykiety*.</span><span class="sxs-lookup"><span data-stu-id="2193d-104">Lines of code preceded by an identifying string or integer are said to be *labeled*.</span></span> <span data-ttu-id="2193d-105">Etykiety instrukcji są używane do oznaczania wiersza kodu w celu zidentyfikowania go do użycia z instrukcjami takimi jak `On Error Goto`.</span><span class="sxs-lookup"><span data-stu-id="2193d-105">Statement labels are used to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>

<span data-ttu-id="2193d-106">Etykiety mogą być prawidłowymi identyfikatorami Visual Basic, takimi jak te, które identyfikują elementy programowania — lub literały całkowite.</span><span class="sxs-lookup"><span data-stu-id="2193d-106">Labels may be either valid Visual Basic identifiers—such as those that identify programming elements—or integer literals.</span></span> <span data-ttu-id="2193d-107">Etykieta musi znajdować się na początku wiersza kodu źródłowego i musi następować dwukropek, niezależnie od tego, czy występuje instrukcja w tym samym wierszu.</span><span class="sxs-lookup"><span data-stu-id="2193d-107">A label must appear at the beginning of a line of source code and must be followed by a colon, regardless of whether it is followed by a statement on the same line.</span></span>

<span data-ttu-id="2193d-108">Kompilator identyfikuje etykiety, sprawdzając, czy początek wiersza pasuje do żadnego już zdefiniowanego identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="2193d-108">The compiler identifies labels by checking whether the beginning of the line matches any already-defined identifier.</span></span> <span data-ttu-id="2193d-109">Jeśli nie, kompilator zakłada, że jest to etykieta.</span><span class="sxs-lookup"><span data-stu-id="2193d-109">If it does not, the compiler assumes it is a label.</span></span>

<span data-ttu-id="2193d-110">Etykiety mają własne miejsce deklaracji i nie zakłócają innych identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="2193d-110">Labels have their own declaration space and do not interfere with other identifiers.</span></span> <span data-ttu-id="2193d-111">Zakres etykiety jest treścią metody.</span><span class="sxs-lookup"><span data-stu-id="2193d-111">A label's scope is the body of the method.</span></span> <span data-ttu-id="2193d-112">Deklaracja etykiety ma pierwszeństwo w każdej niejednoznacznej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="2193d-112">Label declaration takes precedence in any ambiguous situation.</span></span>

> [!NOTE]
> <span data-ttu-id="2193d-113">Etykiet można używać tylko w instrukcjach wykonywalnych wewnątrz metod.</span><span class="sxs-lookup"><span data-stu-id="2193d-113">Labels can be used only on executable statements inside methods.</span></span>

## <a name="to-label-a-line-of-code"></a><span data-ttu-id="2193d-114">Aby oznaczyć wiersz kodu</span><span class="sxs-lookup"><span data-stu-id="2193d-114">To label a line of code</span></span>

<span data-ttu-id="2193d-115">Umieść identyfikator, po którym następuje dwukropek, na początku wiersza kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="2193d-115">Place an identifier, followed by a colon, at the beginning of the line of source code.</span></span>

<span data-ttu-id="2193d-116">Na przykład następujące wiersze kodu mają etykiety `Jump` i `120`, odpowiednio:</span><span class="sxs-lookup"><span data-stu-id="2193d-116">For example, the following lines of code are labeled with `Jump` and `120`, respectively:</span></span>

[!code-vb[VbVbalrStatements#708](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#708)]

## <a name="see-also"></a><span data-ttu-id="2193d-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2193d-117">See also</span></span>

- [<span data-ttu-id="2193d-118">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="2193d-118">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="2193d-119">Nazwy zadeklarowanych elementów</span><span class="sxs-lookup"><span data-stu-id="2193d-119">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="2193d-120">Konwencje dotyczące struktury programów i kodu</span><span class="sxs-lookup"><span data-stu-id="2193d-120">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
