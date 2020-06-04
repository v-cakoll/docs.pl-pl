---
title: 'Porady: definiowanie wielu wersji procedury'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- procedure overloading [Visual Basic], multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
ms.openlocfilehash: 870a18dbf3a7e28b7d7b612e853beeec6908cf6f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387936"
---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a><span data-ttu-id="2c637-102">Porady: definiowanie wielu wersji procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2c637-102">How to: Define Multiple Versions of a Procedure (Visual Basic)</span></span>
<span data-ttu-id="2c637-103">Można zdefiniować procedurę w wielu wersjach przez *przekazanie* jej przy użyciu tej samej nazwy, ale innej listy parametrów dla każdej wersji.</span><span class="sxs-lookup"><span data-stu-id="2c637-103">You can define a procedure in multiple versions by *overloading* it, using the same name but a different parameter list for each version.</span></span> <span data-ttu-id="2c637-104">Przeciążanie polega na zdefiniowaniu kilku ściśle powiązanych wersji procedury bez konieczności odróżnienia ich według nazwy.</span><span class="sxs-lookup"><span data-stu-id="2c637-104">The purpose of overloading is to define several closely related versions of a procedure without having to differentiate them by name.</span></span>  
  
 <span data-ttu-id="2c637-105">Aby uzyskać więcej informacji, zobacz [przeciążanie procedur](./procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="2c637-105">For more information, see [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a><span data-ttu-id="2c637-106">Aby zdefiniować wiele wersji procedury</span><span class="sxs-lookup"><span data-stu-id="2c637-106">To define multiple versions of a procedure</span></span>  
  
1. <span data-ttu-id="2c637-107">Napisz `Sub` instrukcję lub `Function` deklaracji dla każdej wersji procedury, która ma zostać zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="2c637-107">Write a `Sub` or `Function` declaration statement for each version of the procedure you want to define.</span></span> <span data-ttu-id="2c637-108">Użyj tej samej nazwy procedury w każdej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="2c637-108">Use the same procedure name in every declaration.</span></span>  
  
2. <span data-ttu-id="2c637-109">Poprzedź `Sub` `Function` słowo kluczowe or w każdej deklaracji za pomocą słowa kluczowego [overloads](../../../language-reference/modifiers/overloads.md) .</span><span class="sxs-lookup"><span data-stu-id="2c637-109">Precede the `Sub` or `Function` keyword in each declaration with the [Overloads](../../../language-reference/modifiers/overloads.md) keyword.</span></span> <span data-ttu-id="2c637-110">Opcjonalnie możesz pominąć `Overloads` deklaracje, ale jeśli zostanie on uwzględniony w dowolnej deklaracji, należy uwzględnić ją w każdej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="2c637-110">You can optionally omit `Overloads` in the declarations, but if you include it in any of the declarations, you must include it in every declaration.</span></span>  
  
3. <span data-ttu-id="2c637-111">Zgodnie z każdą instrukcją deklaracji Napisz kod procedury, aby obsłużyć konkretny przypadek, w którym wywoływany kod dostarcza argumenty pasujące do listy parametrów tej wersji.</span><span class="sxs-lookup"><span data-stu-id="2c637-111">Following each declaration statement, write procedure code to handle the specific case where the calling code supplies arguments matching that version's parameter list.</span></span> <span data-ttu-id="2c637-112">Nie trzeba testować, dla którego parametrów dostarczono kod wywołujący.</span><span class="sxs-lookup"><span data-stu-id="2c637-112">You do not have to test for which parameters the calling code has supplied.</span></span> <span data-ttu-id="2c637-113">Visual Basic przekazuje kontrolę do zgodnej wersji procedury.</span><span class="sxs-lookup"><span data-stu-id="2c637-113">Visual Basic passes control to the matching version of your procedure.</span></span>  
  
4. <span data-ttu-id="2c637-114">Przerwij każdą wersję procedury z `End Sub` instrukcją lub, `End Function` zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="2c637-114">Terminate each version of the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c637-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="2c637-115">Example</span></span>  
 <span data-ttu-id="2c637-116">W poniższym przykładzie zdefiniowano `Sub` procedurę publikowania transakcji na podstawie salda klienta.</span><span class="sxs-lookup"><span data-stu-id="2c637-116">The following example defines a `Sub` procedure to post a transaction against a customer's balance.</span></span> <span data-ttu-id="2c637-117">Używa `Overloads` słowa kluczowego, aby zdefiniować dwie wersje procedury, jedną, która akceptuje klienta według nazwy i innych według numeru konta.</span><span class="sxs-lookup"><span data-stu-id="2c637-117">It uses the `Overloads` keyword to define two versions of the procedure, one that accepts the customer by name and the other by account number.</span></span>  
  
 [!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]  
  
 <span data-ttu-id="2c637-118">Kod wywołujący może uzyskać identyfikację klienta jako `String` lub `Integer` , a następnie użyć tej samej instrukcji wywołującej w obu przypadkach.</span><span class="sxs-lookup"><span data-stu-id="2c637-118">The calling code can obtain the customer identification as either a `String` or an `Integer`, and then use the same calling statement in either case.</span></span>  
  
 <span data-ttu-id="2c637-119">Aby uzyskać informacje na temat sposobu wywoływania tych wersji `post` procedury, zobacz [How to: calling a przeciążona procedura](./how-to-call-an-overloaded-procedure.md).</span><span class="sxs-lookup"><span data-stu-id="2c637-119">For information on how to call these versions of the `post` procedure, see [How to: Call an Overloaded Procedure](./how-to-call-an-overloaded-procedure.md).</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="2c637-120">Kompiluj kod</span><span class="sxs-lookup"><span data-stu-id="2c637-120">Compile the code</span></span>  
 <span data-ttu-id="2c637-121">Upewnij się, że każda ze przeciążonych wersji ma taką samą nazwę procedury, ale inną listę parametrów.</span><span class="sxs-lookup"><span data-stu-id="2c637-121">Make sure each of your overloaded versions has the same procedure name but a different parameter list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c637-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2c637-122">See also</span></span>

- [<span data-ttu-id="2c637-123">Procedury</span><span class="sxs-lookup"><span data-stu-id="2c637-123">Procedures</span></span>](./index.md)
- [<span data-ttu-id="2c637-124">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="2c637-124">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="2c637-125">Rozwiązywanie problemów z procedurami</span><span class="sxs-lookup"><span data-stu-id="2c637-125">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="2c637-126">Instrukcje: przeciążanie procedury korzystającej z parametrów opcjonalnych</span><span class="sxs-lookup"><span data-stu-id="2c637-126">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="2c637-127">Porady: przeciążanie procedury wykorzystującej nieokreśloną liczbę parametrów</span><span class="sxs-lookup"><span data-stu-id="2c637-127">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="2c637-128">Zagadnienia dotyczące przeciążania procedur</span><span class="sxs-lookup"><span data-stu-id="2c637-128">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="2c637-129">Rozpoznanie przeciążenia</span><span class="sxs-lookup"><span data-stu-id="2c637-129">Overload Resolution</span></span>](./overload-resolution.md)
