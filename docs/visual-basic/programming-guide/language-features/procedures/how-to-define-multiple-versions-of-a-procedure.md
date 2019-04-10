---
title: 'Instrukcje: Definiowanie wielu wersji procedury (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- procedure overloading [Visual Basic], multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
ms.openlocfilehash: fc7a8e18394b904f0c22a80f71dee091d4f786ab
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59324035"
---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a><span data-ttu-id="2ba56-102">Instrukcje: Definiowanie wielu wersji procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2ba56-102">How to: Define Multiple Versions of a Procedure (Visual Basic)</span></span>
<span data-ttu-id="2ba56-103">Procedurę można zdefiniować w wielu wersjach, *przeciążenie* go przy użyciu tej samej nazwie, ale inną listą parametrów dla każdej wersji.</span><span class="sxs-lookup"><span data-stu-id="2ba56-103">You can define a procedure in multiple versions by *overloading* it, using the same name but a different parameter list for each version.</span></span> <span data-ttu-id="2ba56-104">Przeciążanie ma na celu zdefiniować kilka wersji ściśle powiązanych procedury bez konieczności odróżnić je według nazwy.</span><span class="sxs-lookup"><span data-stu-id="2ba56-104">The purpose of overloading is to define several closely related versions of a procedure without having to differentiate them by name.</span></span>  
  
 <span data-ttu-id="2ba56-105">Aby uzyskać więcej informacji, zobacz [przeciążanie procedury](./procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="2ba56-105">For more information, see [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a><span data-ttu-id="2ba56-106">Aby zdefiniować wielu wersji procedury</span><span class="sxs-lookup"><span data-stu-id="2ba56-106">To define multiple versions of a procedure</span></span>  
  
1. <span data-ttu-id="2ba56-107">Zapis `Sub` lub `Function` instrukcji deklaracji dla każdej wersji procedury, aby zdefiniować.</span><span class="sxs-lookup"><span data-stu-id="2ba56-107">Write a `Sub` or `Function` declaration statement for each version of the procedure you want to define.</span></span> <span data-ttu-id="2ba56-108">Użyj tej samej nazwy procedury w każdej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="2ba56-108">Use the same procedure name in every declaration.</span></span>  
  
2. <span data-ttu-id="2ba56-109">Należy poprzedzić `Sub` lub `Function` — słowo kluczowe w każdej deklaracji z [przeciążenia](../../../../visual-basic/language-reference/modifiers/overloads.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="2ba56-109">Precede the `Sub` or `Function` keyword in each declaration with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span> <span data-ttu-id="2ba56-110">Opcjonalnie można pominąć `Overloads` w deklaracji, ale jeśli należy uwzględnić w deklaracji, należy ją dołączyć w każdej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="2ba56-110">You can optionally omit `Overloads` in the declarations, but if you include it in any of the declarations, you must include it in every declaration.</span></span>  
  
3. <span data-ttu-id="2ba56-111">Po każdej instrukcji deklaracji napisać kod procedury obsługi konkretnego przypadku, gdy kod wywołujący dostarcza argumentów dopasowania na liście parametrów tej wersji.</span><span class="sxs-lookup"><span data-stu-id="2ba56-111">Following each declaration statement, write procedure code to handle the specific case where the calling code supplies arguments matching that version's parameter list.</span></span> <span data-ttu-id="2ba56-112">Nie masz do testowania dla parametrów, które udostępnił kodu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="2ba56-112">You do not have to test for which parameters the calling code has supplied.</span></span> <span data-ttu-id="2ba56-113">Visual Basic przekazuje sterowanie do tej samej wersji odpowiedniej procedury.</span><span class="sxs-lookup"><span data-stu-id="2ba56-113">Visual Basic passes control to the matching version of your procedure.</span></span>  
  
4. <span data-ttu-id="2ba56-114">Zakończenie każdą wersję procedury z `End Sub` lub `End Function` instrukcji zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="2ba56-114">Terminate each version of the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ba56-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="2ba56-115">Example</span></span>  
 <span data-ttu-id="2ba56-116">W poniższym przykładzie zdefiniowano `Sub` procedury, aby transakcję przed saldo odbiorcy.</span><span class="sxs-lookup"><span data-stu-id="2ba56-116">The following example defines a `Sub` procedure to post a transaction against a customer's balance.</span></span> <span data-ttu-id="2ba56-117">Używa ona `Overloads` — słowo kluczowe, aby zdefiniować dwie wersje procedury, taki, który akceptuje klientów według nazwy i innych przez numer konta.</span><span class="sxs-lookup"><span data-stu-id="2ba56-117">It uses the `Overloads` keyword to define two versions of the procedure, one that accepts the customer by name and the other by account number.</span></span>  
  
 [!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]  
  
 <span data-ttu-id="2ba56-118">Kod wywołujący można uzyskać identyfikator klienta jako `String` lub `Integer`, a następnie użyć tej samej instrukcji wywołujące w obu przypadkach.</span><span class="sxs-lookup"><span data-stu-id="2ba56-118">The calling code can obtain the customer identification as either a `String` or an `Integer`, and then use the same calling statement in either case.</span></span>  
  
 <span data-ttu-id="2ba56-119">Aby uzyskać informacje dotyczące wywołań te wersje programu `post` procedury, zobacz [jak: Wywoływanie procedury przeciążenia](./how-to-call-an-overloaded-procedure.md).</span><span class="sxs-lookup"><span data-stu-id="2ba56-119">For information on how to call these versions of the `post` procedure, see [How to: Call an Overloaded Procedure](./how-to-call-an-overloaded-procedure.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2ba56-120">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="2ba56-120">Compiling the Code</span></span>  
 <span data-ttu-id="2ba56-121">Upewnij się, że każdy z usługi przeciążone wersje ma taką samą nazwę procedury, ale z inną listą parametrów.</span><span class="sxs-lookup"><span data-stu-id="2ba56-121">Make sure each of your overloaded versions has the same procedure name but a different parameter list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ba56-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2ba56-122">See also</span></span>

- [<span data-ttu-id="2ba56-123">Procedury</span><span class="sxs-lookup"><span data-stu-id="2ba56-123">Procedures</span></span>](./index.md)
- [<span data-ttu-id="2ba56-124">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="2ba56-124">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="2ba56-125">Rozwiązywanie problemów z procedurami</span><span class="sxs-lookup"><span data-stu-id="2ba56-125">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="2ba56-126">Instrukcje: Przeciążanie procedury korzystającej z parametrów opcjonalnych</span><span class="sxs-lookup"><span data-stu-id="2ba56-126">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="2ba56-127">Instrukcje: Przeciążanie procedury korzystającej z nieskończonej liczby parametrów</span><span class="sxs-lookup"><span data-stu-id="2ba56-127">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="2ba56-128">Zagadnienia dotyczące przeciążania procedur</span><span class="sxs-lookup"><span data-stu-id="2ba56-128">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="2ba56-129">Rozpoznanie przeciążenia</span><span class="sxs-lookup"><span data-stu-id="2ba56-129">Overload Resolution</span></span>](./overload-resolution.md)
