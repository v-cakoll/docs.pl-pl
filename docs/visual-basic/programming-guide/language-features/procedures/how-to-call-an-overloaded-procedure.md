---
title: 'Instrukcje: Wywoływanie procedury przeciążenia (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedures [Visual Basic], multiple versions
- procedure calls [Visual Basic], overloaded
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
ms.openlocfilehash: 9dda0fbc0cffe8904ab97c46cea40d5cf00c91e9
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843789"
---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a><span data-ttu-id="d0166-102">Instrukcje: Wywoływanie procedury przeciążenia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d0166-102">How to: Call an Overloaded Procedure (Visual Basic)</span></span>
<span data-ttu-id="d0166-103">Zaletą przeciążanie procedury trwa elastyczność wywołania.</span><span class="sxs-lookup"><span data-stu-id="d0166-103">The advantage of overloading a procedure is in the flexibility of the call.</span></span> <span data-ttu-id="d0166-104">Kod wywołujący można uzyskać informacji potrzebnych do przekazania do procedury, a następnie wywołać nazwę samą procedurą, niezależnie od tego, jakie argumentów, go przechodzi.</span><span class="sxs-lookup"><span data-stu-id="d0166-104">The calling code can obtain the information it needs to pass to the procedure and then call a single procedure name, no matter what arguments it is passing.</span></span>  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a><span data-ttu-id="d0166-105">Aby wywołać procedurę, który ma więcej niż jedna wersja zdefiniowane</span><span class="sxs-lookup"><span data-stu-id="d0166-105">To call a procedure that has more than one version defined</span></span>  
  
1.  <span data-ttu-id="d0166-106">W wywoływanym kodzie określają, jakie dane do przekazania do procedury.</span><span class="sxs-lookup"><span data-stu-id="d0166-106">In the calling code, determine which data to pass to the procedure.</span></span>  
  
2.  <span data-ttu-id="d0166-107">Po wywołaniu procedury należy zapisać w normalny sposób prezentowania danych na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="d0166-107">Write the procedure call in the normal way, presenting the data in the argument list.</span></span> <span data-ttu-id="d0166-108">Upewnij się, że argumenty odpowiada liście parametrów, w wersjach zdefiniowane w procedurze.</span><span class="sxs-lookup"><span data-stu-id="d0166-108">Be sure the arguments match the parameter list in one of the versions defined for the procedure.</span></span>  
  
3.  <span data-ttu-id="d0166-109">Nie trzeba ustalić, która wersja procedury do wywołania.</span><span class="sxs-lookup"><span data-stu-id="d0166-109">You do not have to determine which version of the procedure to call.</span></span> <span data-ttu-id="d0166-110">Visual Basic przekazuje sterowanie do wersji dopasowania listy argumentów.</span><span class="sxs-lookup"><span data-stu-id="d0166-110">Visual Basic passes control to the version matching your argument list.</span></span>  
  
     <span data-ttu-id="d0166-111">Poniższy przykład wywołuje `post` procedury zadeklarowanych w [jak: Definiowanie wielu wersji procedury](./how-to-define-multiple-versions-of-a-procedure.md).</span><span class="sxs-lookup"><span data-stu-id="d0166-111">The following example calls the `post` procedure declared in [How to: Define Multiple Versions of a Procedure](./how-to-define-multiple-versions-of-a-procedure.md).</span></span> <span data-ttu-id="d0166-112">Uzyskuje identyfikator klienta, określa, czy jest `String` lub `Integer`, a następnie w obu przypadkach wywołuje tę samą procedurę.</span><span class="sxs-lookup"><span data-stu-id="d0166-112">It obtains the customer identification, determines whether it is a `String` or an `Integer`, and then in either case calls the same procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]  
  
     [!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]  
  
## <a name="see-also"></a><span data-ttu-id="d0166-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d0166-113">See also</span></span>

- [<span data-ttu-id="d0166-114">Procedury</span><span class="sxs-lookup"><span data-stu-id="d0166-114">Procedures</span></span>](./index.md)
- [<span data-ttu-id="d0166-115">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="d0166-115">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="d0166-116">Przeciążanie procedury</span><span class="sxs-lookup"><span data-stu-id="d0166-116">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="d0166-117">Rozwiązywanie problemów z procedurami</span><span class="sxs-lookup"><span data-stu-id="d0166-117">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="d0166-118">Instrukcje: Definiowanie wielu wersji procedury</span><span class="sxs-lookup"><span data-stu-id="d0166-118">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="d0166-119">Instrukcje: Przeciążanie procedury wykorzystującej parametry opcjonalne</span><span class="sxs-lookup"><span data-stu-id="d0166-119">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="d0166-120">Instrukcje: Przeciążanie procedury wykorzystującej nieokreśloną liczbę parametrów</span><span class="sxs-lookup"><span data-stu-id="d0166-120">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="d0166-121">Zagadnienia dotyczące przeciążania procedur</span><span class="sxs-lookup"><span data-stu-id="d0166-121">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="d0166-122">Rozpoznanie przeciążenia</span><span class="sxs-lookup"><span data-stu-id="d0166-122">Overload Resolution</span></span>](./overload-resolution.md)
- [<span data-ttu-id="d0166-123">Overloads</span><span class="sxs-lookup"><span data-stu-id="d0166-123">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)
