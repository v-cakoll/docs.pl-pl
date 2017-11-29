---
title: 'Porady: definiowanie wielu wersji procedury (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- procedure overloading [Visual Basic], multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1abeaa6806252005dd3abfab3ff60bafa0c0cef1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a><span data-ttu-id="3be0f-102">Porady: definiowanie wielu wersji procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3be0f-102">How to: Define Multiple Versions of a Procedure (Visual Basic)</span></span>
<span data-ttu-id="3be0f-103">Procedurę można zdefiniować w różnych wersjach przez *przeładowanie* go przy użyciu takiej samej nazwie, ale inną listą parametrów dla każdej wersji.</span><span class="sxs-lookup"><span data-stu-id="3be0f-103">You can define a procedure in multiple versions by *overloading* it, using the same name but a different parameter list for each version.</span></span> <span data-ttu-id="3be0f-104">Przeciążanie służy do definiowania kilka wersji blisko związane procedury bez konieczności odróżnić je według nazwy.</span><span class="sxs-lookup"><span data-stu-id="3be0f-104">The purpose of overloading is to define several closely related versions of a procedure without having to differentiate them by name.</span></span>  
  
 <span data-ttu-id="3be0f-105">Aby uzyskać więcej informacji, zobacz [przeciążanie procedury](./procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="3be0f-105">For more information, see [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a><span data-ttu-id="3be0f-106">Aby zdefiniować wielu wersji procedury</span><span class="sxs-lookup"><span data-stu-id="3be0f-106">To define multiple versions of a procedure</span></span>  
  
1.  <span data-ttu-id="3be0f-107">Zapis `Sub` lub `Function` instrukcji deklaracji dla każdej wersji procedury, które chcesz zdefiniować.</span><span class="sxs-lookup"><span data-stu-id="3be0f-107">Write a `Sub` or `Function` declaration statement for each version of the procedure you want to define.</span></span> <span data-ttu-id="3be0f-108">Użyj takiej samej nazwie procedury w każdej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="3be0f-108">Use the same procedure name in every declaration.</span></span>  
  
2.  <span data-ttu-id="3be0f-109">Należy poprzedzić `Sub` lub `Function` — słowo kluczowe w każdej deklaracji z [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="3be0f-109">Precede the `Sub` or `Function` keyword in each declaration with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span> <span data-ttu-id="3be0f-110">Opcjonalnie można pominąć `Overloads` w deklaracjach, ale jeśli należy uwzględnić w deklaracji, należy go dołączyć w każdej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="3be0f-110">You can optionally omit `Overloads` in the declarations, but if you include it in any of the declarations, you must include it in every declaration.</span></span>  
  
3.  <span data-ttu-id="3be0f-111">Po każdej instrukcji deklaracji napisać kod procedury obsługi konkretnego przypadku, gdy kod wywołujący dostarcza argumentów dopasowania listy parametrów w tej wersji.</span><span class="sxs-lookup"><span data-stu-id="3be0f-111">Following each declaration statement, write procedure code to handle the specific case where the calling code supplies arguments matching that version's parameter list.</span></span> <span data-ttu-id="3be0f-112">Nie masz do testowania dla parametrów, które dostarczył kodu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="3be0f-112">You do not have to test for which parameters the calling code has supplied.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="3be0f-113">formant przechodzi do tej samej wersji procedury.</span><span class="sxs-lookup"><span data-stu-id="3be0f-113"> passes control to the matching version of your procedure.</span></span>  
  
4.  <span data-ttu-id="3be0f-114">Zakończenie każdej wersji procedury z `End Sub` lub `End Function` oświadczenie zależnie od potrzeb.</span><span class="sxs-lookup"><span data-stu-id="3be0f-114">Terminate each version of the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3be0f-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="3be0f-115">Example</span></span>  
 <span data-ttu-id="3be0f-116">W poniższym przykładzie zdefiniowano `Sub` procedury można opublikować transakcji bilans klienta.</span><span class="sxs-lookup"><span data-stu-id="3be0f-116">The following example defines a `Sub` procedure to post a transaction against a customer's balance.</span></span> <span data-ttu-id="3be0f-117">Używa `Overloads` — słowo kluczowe, aby zdefiniować dwie wersje procedury, jeden akceptujący klienta wg nazwy oraz innych według konta.</span><span class="sxs-lookup"><span data-stu-id="3be0f-117">It uses the `Overloads` keyword to define two versions of the procedure, one that accepts the customer by name and the other by account number.</span></span>  
  
 [!code-vb[VbVbcnProcedures#72](./codesnippet/VisualBasic/how-to-define-multiple-versions-of-a-procedure_1.vb)]  
  
 <span data-ttu-id="3be0f-118">Kod wywołujący można uzyskać identyfikator klienta jako `String` lub `Integer`, a następnie użyć tej samej instrukcji wywoływania w każdym przypadku.</span><span class="sxs-lookup"><span data-stu-id="3be0f-118">The calling code can obtain the customer identification as either a `String` or an `Integer`, and then use the same calling statement in either case.</span></span>  
  
 <span data-ttu-id="3be0f-119">Aby uzyskać informacje dotyczące wywołania te wersje programu `post` procedury, zobacz [porady: wywoływanie procedury przeciążony](./how-to-call-an-overloaded-procedure.md).</span><span class="sxs-lookup"><span data-stu-id="3be0f-119">For information on how to call these versions of the `post` procedure, see [How to: Call an Overloaded Procedure](./how-to-call-an-overloaded-procedure.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3be0f-120">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="3be0f-120">Compiling the Code</span></span>  
 <span data-ttu-id="3be0f-121">Upewnij się, że każdy sieci przeciążona wersji ma taką samą nazwę procedury, ale inną listą parametrów.</span><span class="sxs-lookup"><span data-stu-id="3be0f-121">Make sure each of your overloaded versions has the same procedure name but a different parameter list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3be0f-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3be0f-122">See Also</span></span>  
 [<span data-ttu-id="3be0f-123">Procedury</span><span class="sxs-lookup"><span data-stu-id="3be0f-123">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="3be0f-124">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="3be0f-124">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="3be0f-125">Procedury rozwiązywania problemów</span><span class="sxs-lookup"><span data-stu-id="3be0f-125">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)  
 [<span data-ttu-id="3be0f-126">Porady: przeciążanie procedury wykorzystującej parametry opcjonalne</span><span class="sxs-lookup"><span data-stu-id="3be0f-126">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [<span data-ttu-id="3be0f-127">Porady: przeciążanie procedury wykorzystującej nieokreśloną liczbę parametrów</span><span class="sxs-lookup"><span data-stu-id="3be0f-127">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [<span data-ttu-id="3be0f-128">Zagadnienia dotyczące przeciążania procedur</span><span class="sxs-lookup"><span data-stu-id="3be0f-128">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)  
 [<span data-ttu-id="3be0f-129">Rozpoznanie przeciążenia</span><span class="sxs-lookup"><span data-stu-id="3be0f-129">Overload Resolution</span></span>](./overload-resolution.md)
