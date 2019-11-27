---
title: Throw — Instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.Throw
helpviewer_keywords:
- structured exception handling, throw statements
- try-catch exception handling, throw statements
- throw statement [Visual Basic], about throw statements
- throwing exceptions, throw statement
- exception handling, throw statement
- On Error statement [Visual Basic], throwing exceptions
- throwing exceptions
- exception handling, unstructured
- throw statement [Visual Basic]
ms.assetid: a6e07406-5c8a-4498-87a2-8339f3651d62
ms.openlocfilehash: 147345990b625e034e651e69b322bc098d0bd8de
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352785"
---
# <a name="throw-statement-visual-basic"></a><span data-ttu-id="6b6a7-102">Throw — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6b6a7-102">Throw Statement (Visual Basic)</span></span>

<span data-ttu-id="6b6a7-103">Zgłasza wyjątek w ramach procedury.</span><span class="sxs-lookup"><span data-stu-id="6b6a7-103">Throws an exception within a procedure.</span></span>

## <a name="syntax"></a><span data-ttu-id="6b6a7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6b6a7-104">Syntax</span></span>

```vb
Throw [ expression ]
```

## <a name="part"></a><span data-ttu-id="6b6a7-105">Części</span><span class="sxs-lookup"><span data-stu-id="6b6a7-105">Part</span></span>

`expression`\
<span data-ttu-id="6b6a7-106">Zawiera informacje o wyjątku, który ma zostać zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="6b6a7-106">Provides information about the exception to be thrown.</span></span> <span data-ttu-id="6b6a7-107">Opcjonalne, gdy znajdują się w instrukcji `Catch`, w przeciwnym razie jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="6b6a7-107">Optional when residing in a `Catch` statement, otherwise required.</span></span>

## <a name="remarks"></a><span data-ttu-id="6b6a7-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6b6a7-108">Remarks</span></span>

<span data-ttu-id="6b6a7-109">Instrukcja `Throw` zgłasza wyjątek, który można obsłużyć za pomocą kodu obsługi wyjątków strukturalnych (`Try`...`Catch`...`Finally`) lub kodu obsługi wyjątków bez struktury (`On Error GoTo`).</span><span class="sxs-lookup"><span data-stu-id="6b6a7-109">The `Throw` statement throws an exception that you can handle with structured exception-handling code (`Try`...`Catch`...`Finally`) or unstructured exception-handling code (`On Error GoTo`).</span></span> <span data-ttu-id="6b6a7-110">Można użyć instrukcji `Throw`, aby zalewki błędów w kodzie, ponieważ Visual Basic przenosi stos wywołań do momentu znalezienia odpowiedniego kodu obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="6b6a7-110">You can use the `Throw` statement to trap errors within your code because Visual Basic moves up the call stack until it finds the appropriate exception-handling code.</span></span>

<span data-ttu-id="6b6a7-111">Instrukcji `Throw` bez wyrażenia można używać tylko w instrukcji `Catch`, w takim przypadku instrukcja ponownie zgłasza wyjątek, który jest obecnie obsługiwany przez instrukcję `Catch`.</span><span class="sxs-lookup"><span data-stu-id="6b6a7-111">A `Throw` statement with no expression can only be used in a `Catch` statement, in which case the statement rethrows the exception currently being handled by the `Catch` statement.</span></span>

<span data-ttu-id="6b6a7-112">Instrukcja `Throw` resetuje stos wywołań dla wyjątku `expression`.</span><span class="sxs-lookup"><span data-stu-id="6b6a7-112">The `Throw` statement resets the call stack for the `expression` exception.</span></span> <span data-ttu-id="6b6a7-113">Jeśli nie podano `expression`, stos wywołań zostanie pozostawiony bez zmian.</span><span class="sxs-lookup"><span data-stu-id="6b6a7-113">If `expression` is not provided, the call stack is left unchanged.</span></span> <span data-ttu-id="6b6a7-114">Możesz uzyskać dostęp do stosu wywołań dla wyjątku za pomocą właściwości <xref:System.Exception.StackTrace%2A>.</span><span class="sxs-lookup"><span data-stu-id="6b6a7-114">You can access the call stack for the exception through the <xref:System.Exception.StackTrace%2A> property.</span></span>

## <a name="example"></a><span data-ttu-id="6b6a7-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="6b6a7-115">Example</span></span>

<span data-ttu-id="6b6a7-116">Poniższy kod używa instrukcji `Throw`, aby zgłosić wyjątek:</span><span class="sxs-lookup"><span data-stu-id="6b6a7-116">The following code uses the `Throw` statement to throw an exception:</span></span>

[!code-vb[VbVbalrStatements#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#84)]

## <a name="see-also"></a><span data-ttu-id="6b6a7-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6b6a7-117">See also</span></span>

- [<span data-ttu-id="6b6a7-118">Try...Catch...Finally, instrukcja</span><span class="sxs-lookup"><span data-stu-id="6b6a7-118">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="6b6a7-119">On Error, instrukcja</span><span class="sxs-lookup"><span data-stu-id="6b6a7-119">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
