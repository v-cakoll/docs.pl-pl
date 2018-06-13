---
title: Nieprawidłowa konwencja wywoływania biblioteki DLL
ms.date: 07/20/2015
f1_keywords:
- vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
ms.openlocfilehash: d8c7f7aea46162215115689305f4010cb513b020
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583841"
---
# <a name="bad-dll-calling-convention"></a><span data-ttu-id="763ac-102">Nieprawidłowa konwencja wywoływania biblioteki DLL</span><span class="sxs-lookup"><span data-stu-id="763ac-102">Bad DLL calling convention</span></span>
<span data-ttu-id="763ac-103">Argumenty przekazane do biblioteki dołączanej (dynamicznie DLL) musi dokładnie odpowiadać wartości oczekiwanych przez procedurę.</span><span class="sxs-lookup"><span data-stu-id="763ac-103">Arguments passed to a dynamic-link library (DLL) must exactly match those expected by the routine.</span></span> <span data-ttu-id="763ac-104">Konwencje wywoływania uwzględniać liczbę, typ i kolejność argumentów.</span><span class="sxs-lookup"><span data-stu-id="763ac-104">Calling conventions deal with number, type, and order of arguments.</span></span> <span data-ttu-id="763ac-105">Program może wywołania procedury w bibliotece DLL, który jest przekazywany nieprawidłowego typu lub liczba argumentów.</span><span class="sxs-lookup"><span data-stu-id="763ac-105">Your program may be calling a routine in a DLL that is being passed the wrong type or number of arguments.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="763ac-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="763ac-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="763ac-107">Upewnij się, że wszystkie typy argumentów są zgodne z danymi określony w deklaracji procedury, która jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="763ac-107">Make sure all argument types agree with those specified in the declaration of the routine that you are calling.</span></span>  
  
2.  <span data-ttu-id="763ac-108">Upewnij się, że przekazywane taką samą liczbę argumentów wskazanych w deklaracji procedury, które są nawiązywane.</span><span class="sxs-lookup"><span data-stu-id="763ac-108">Make sure you are passing the same number of arguments indicated in the declaration of the routine that you are calling.</span></span>  
  
3.  <span data-ttu-id="763ac-109">Jeśli procedura DLL oczekuje argumentów według wartości, upewnij się, `ByVal` dla tych argumentów w deklaracji dla procedury określono.</span><span class="sxs-lookup"><span data-stu-id="763ac-109">If the DLL routine expects arguments by value, make sure `ByVal` is specified for those arguments in the declaration for the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="763ac-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="763ac-110">See Also</span></span>  
 [<span data-ttu-id="763ac-111">Typy błędów</span><span class="sxs-lookup"><span data-stu-id="763ac-111">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [<span data-ttu-id="763ac-112">Call, instrukcja</span><span class="sxs-lookup"><span data-stu-id="763ac-112">Call Statement</span></span>](../../../visual-basic/language-reference/statements/call-statement.md)  
 [<span data-ttu-id="763ac-113">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="763ac-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
