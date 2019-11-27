---
title: 'Porady: etykietowanie instrukcji'
ms.date: 07/20/2015
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
ms.openlocfilehash: be116ac8046c43e89e44c2d9127c6131e4dfaa52
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347380"
---
# <a name="how-to-label-statements-visual-basic"></a><span data-ttu-id="99f45-102">Porady: etykietowanie instrukcji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="99f45-102">How to: Label Statements (Visual Basic)</span></span>

<span data-ttu-id="99f45-103">Bloki instrukcji składają się z wierszy kodu rozdzielanych średnikami.</span><span class="sxs-lookup"><span data-stu-id="99f45-103">Statement blocks are made up of lines of code delimited by colons.</span></span> <span data-ttu-id="99f45-104">Wiersze kodu poprzedzone ciągiem identyfikującym lub liczbą całkowitą są określane jako *etykiety*.</span><span class="sxs-lookup"><span data-stu-id="99f45-104">Lines of code preceded by an identifying string or integer are said to be *labeled*.</span></span> <span data-ttu-id="99f45-105">Etykiety instrukcji są używane do oznaczania wiersza kodu w celu zidentyfikowania go do użycia z instrukcjami takimi jak `On Error Goto`.</span><span class="sxs-lookup"><span data-stu-id="99f45-105">Statement labels are used to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>

<span data-ttu-id="99f45-106">Etykiety mogą być prawidłowymi identyfikatorami Visual Basic, takimi jak te, które identyfikują elementy programowania — lub literały całkowite.</span><span class="sxs-lookup"><span data-stu-id="99f45-106">Labels may be either valid Visual Basic identifiers—such as those that identify programming elements—or integer literals.</span></span> <span data-ttu-id="99f45-107">Etykieta musi znajdować się na początku wiersza kodu źródłowego i musi następować dwukropek, niezależnie od tego, czy występuje instrukcja w tym samym wierszu.</span><span class="sxs-lookup"><span data-stu-id="99f45-107">A label must appear at the beginning of a line of source code and must be followed by a colon, regardless of whether it is followed by a statement on the same line.</span></span>

<span data-ttu-id="99f45-108">Kompilator identyfikuje etykiety, sprawdzając, czy początek wiersza pasuje do żadnego już zdefiniowanego identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="99f45-108">The compiler identifies labels by checking whether the beginning of the line matches any already-defined identifier.</span></span> <span data-ttu-id="99f45-109">Jeśli nie, kompilator zakłada, że jest to etykieta.</span><span class="sxs-lookup"><span data-stu-id="99f45-109">If it does not, the compiler assumes it is a label.</span></span>

<span data-ttu-id="99f45-110">Etykiety mają własne miejsce deklaracji i nie zakłócają innych identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="99f45-110">Labels have their own declaration space and do not interfere with other identifiers.</span></span> <span data-ttu-id="99f45-111">Zakres etykiety jest treścią metody.</span><span class="sxs-lookup"><span data-stu-id="99f45-111">A label's scope is the body of the method.</span></span> <span data-ttu-id="99f45-112">Deklaracja etykiety ma pierwszeństwo w każdej niejednoznacznej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="99f45-112">Label declaration takes precedence in any ambiguous situation.</span></span>

> [!NOTE]
> <span data-ttu-id="99f45-113">Etykiet można używać tylko w instrukcjach wykonywalnych wewnątrz metod.</span><span class="sxs-lookup"><span data-stu-id="99f45-113">Labels can be used only on executable statements inside methods.</span></span>

## <a name="to-label-a-line-of-code"></a><span data-ttu-id="99f45-114">Aby oznaczyć wiersz kodu</span><span class="sxs-lookup"><span data-stu-id="99f45-114">To label a line of code</span></span>

<span data-ttu-id="99f45-115">Umieść identyfikator, po którym następuje dwukropek, na początku wiersza kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="99f45-115">Place an identifier, followed by a colon, at the beginning of the line of source code.</span></span>

<span data-ttu-id="99f45-116">Na przykład następujące wiersze kodu są oznaczone odpowiednio `Jump` i `120`:</span><span class="sxs-lookup"><span data-stu-id="99f45-116">For example, the following lines of code are labeled with `Jump` and `120`, respectively:</span></span>

[!code-vb[VbVbalrStatements#708](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#708)]

## <a name="see-also"></a><span data-ttu-id="99f45-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="99f45-117">See also</span></span>

- [<span data-ttu-id="99f45-118">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="99f45-118">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="99f45-119">Nazwy zadeklarowanych elementów</span><span class="sxs-lookup"><span data-stu-id="99f45-119">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="99f45-120">Struktura programu i konwencje związane z kodami</span><span class="sxs-lookup"><span data-stu-id="99f45-120">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
