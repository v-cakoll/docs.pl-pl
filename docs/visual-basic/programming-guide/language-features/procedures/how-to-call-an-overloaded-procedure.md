---
title: 'Porady: wywoływanie procedury przeciążenia'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedures [Visual Basic], multiple versions
- procedure calls [Visual Basic], overloaded
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
ms.openlocfilehash: d983f5f6183c33141079ed35171f7a73f254450f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340209"
---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a><span data-ttu-id="6ec26-102">Porady: wywoływanie procedury przeciążenia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6ec26-102">How to: Call an Overloaded Procedure (Visual Basic)</span></span>
<span data-ttu-id="6ec26-103">Zaletą przeładowania procedury jest elastyczność wywołania.</span><span class="sxs-lookup"><span data-stu-id="6ec26-103">The advantage of overloading a procedure is in the flexibility of the call.</span></span> <span data-ttu-id="6ec26-104">Kod wywołujący może uzyskać informacje potrzebne do przekazania do procedury, a następnie wywołać pojedynczą nazwę procedury, niezależnie od tego, jakie argumenty są przekazywane.</span><span class="sxs-lookup"><span data-stu-id="6ec26-104">The calling code can obtain the information it needs to pass to the procedure and then call a single procedure name, no matter what arguments it is passing.</span></span>  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a><span data-ttu-id="6ec26-105">Aby wywołać procedurę, która ma zdefiniowaną więcej niż jedną wersję</span><span class="sxs-lookup"><span data-stu-id="6ec26-105">To call a procedure that has more than one version defined</span></span>  
  
1. <span data-ttu-id="6ec26-106">W kodzie wywołującym Określ, które dane mają zostać przekazane do procedury.</span><span class="sxs-lookup"><span data-stu-id="6ec26-106">In the calling code, determine which data to pass to the procedure.</span></span>  
  
2. <span data-ttu-id="6ec26-107">Napisz wywołanie procedury w zwykły sposób, prezentując dane na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="6ec26-107">Write the procedure call in the normal way, presenting the data in the argument list.</span></span> <span data-ttu-id="6ec26-108">Upewnij się, że argumenty pasują do listy parametrów w jednej z wersji zdefiniowanych dla procedury.</span><span class="sxs-lookup"><span data-stu-id="6ec26-108">Be sure the arguments match the parameter list in one of the versions defined for the procedure.</span></span>  
  
3. <span data-ttu-id="6ec26-109">Nie ma potrzeby określania, która wersja procedury ma być wywoływana.</span><span class="sxs-lookup"><span data-stu-id="6ec26-109">You do not have to determine which version of the procedure to call.</span></span> <span data-ttu-id="6ec26-110">Visual Basic przekazuje kontrolę do wersji zgodnej z listą argumentów.</span><span class="sxs-lookup"><span data-stu-id="6ec26-110">Visual Basic passes control to the version matching your argument list.</span></span>  
  
     <span data-ttu-id="6ec26-111">Poniższy przykład wywołuje procedurę `post` zadeklarowaną w [instrukcje: definiowanie wielu wersji procedury](./how-to-define-multiple-versions-of-a-procedure.md).</span><span class="sxs-lookup"><span data-stu-id="6ec26-111">The following example calls the `post` procedure declared in [How to: Define Multiple Versions of a Procedure](./how-to-define-multiple-versions-of-a-procedure.md).</span></span> <span data-ttu-id="6ec26-112">Uzyskuje identyfikację klienta, określa, czy jest to `String` czy `Integer`, a następnie w obu przypadkach wywołuje tę samą procedurę.</span><span class="sxs-lookup"><span data-stu-id="6ec26-112">It obtains the customer identification, determines whether it is a `String` or an `Integer`, and then in either case calls the same procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]  
  
     [!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]  
  
## <a name="see-also"></a><span data-ttu-id="6ec26-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6ec26-113">See also</span></span>

- [<span data-ttu-id="6ec26-114">Procedury</span><span class="sxs-lookup"><span data-stu-id="6ec26-114">Procedures</span></span>](./index.md)
- [<span data-ttu-id="6ec26-115">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="6ec26-115">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="6ec26-116">Przeciążanie procedury</span><span class="sxs-lookup"><span data-stu-id="6ec26-116">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="6ec26-117">Rozwiązywanie problemów z procedurami</span><span class="sxs-lookup"><span data-stu-id="6ec26-117">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="6ec26-118">Instrukcje: definiowanie wielu wersji procedury</span><span class="sxs-lookup"><span data-stu-id="6ec26-118">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="6ec26-119">Instrukcje: przeciążanie procedury korzystającej z parametrów opcjonalnych</span><span class="sxs-lookup"><span data-stu-id="6ec26-119">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="6ec26-120">Instrukcje: przeciążanie procedury korzystającej z nieokreślonej liczby parametrów</span><span class="sxs-lookup"><span data-stu-id="6ec26-120">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="6ec26-121">Zagadnienia dotyczące przeciążania procedur</span><span class="sxs-lookup"><span data-stu-id="6ec26-121">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="6ec26-122">Rozpoznanie przeciążenia</span><span class="sxs-lookup"><span data-stu-id="6ec26-122">Overload Resolution</span></span>](./overload-resolution.md)
- [<span data-ttu-id="6ec26-123">Overloads</span><span class="sxs-lookup"><span data-stu-id="6ec26-123">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)
