---
title: Nieprawidłowa konwencja wywoływania biblioteki DLL
ms.date: 07/20/2015
f1_keywords:
- vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
ms.openlocfilehash: f7b0c3a6edbe0b950195306fa66287ff9b209bfe
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59306628"
---
# <a name="bad-dll-calling-convention"></a><span data-ttu-id="42f68-102">Nieprawidłowa konwencja wywoływania biblioteki DLL</span><span class="sxs-lookup"><span data-stu-id="42f68-102">Bad DLL calling convention</span></span>
<span data-ttu-id="42f68-103">Argumenty przekazane do biblioteki dołączanej (dynamicznie DLL) musi dokładnie odpowiadać ich z oczekiwanymi przez procedura.</span><span class="sxs-lookup"><span data-stu-id="42f68-103">Arguments passed to a dynamic-link library (DLL) must exactly match those expected by the routine.</span></span> <span data-ttu-id="42f68-104">Konwencje wywoływania zajmuje się numer, typ i kolejność argumentów.</span><span class="sxs-lookup"><span data-stu-id="42f68-104">Calling conventions deal with number, type, and order of arguments.</span></span> <span data-ttu-id="42f68-105">Program może wywołania procedury w bibliotekę DLL, która jest przekazywana nieprawidłowego typu lub liczbę argumentów.</span><span class="sxs-lookup"><span data-stu-id="42f68-105">Your program may be calling a routine in a DLL that is being passed the wrong type or number of arguments.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="42f68-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="42f68-106">To correct this error</span></span>  
  
1. <span data-ttu-id="42f68-107">Upewnij się, że wszystkie typy argumentów zgadzają się z tymi określonym w deklaracji procedury, którą wywołujesz.</span><span class="sxs-lookup"><span data-stu-id="42f68-107">Make sure all argument types agree with those specified in the declaration of the routine that you are calling.</span></span>  
  
2. <span data-ttu-id="42f68-108">Upewnij się, że przekazujesz taką samą liczbę argumentów wskazane w deklaracji procedury, którą wywołujesz.</span><span class="sxs-lookup"><span data-stu-id="42f68-108">Make sure you are passing the same number of arguments indicated in the declaration of the routine that you are calling.</span></span>  
  
3. <span data-ttu-id="42f68-109">Jeśli procedura DLL oczekuje argumentów według wartości, upewnij się, `ByVal` dla tych argumentów w deklaracji dla procedury określono.</span><span class="sxs-lookup"><span data-stu-id="42f68-109">If the DLL routine expects arguments by value, make sure `ByVal` is specified for those arguments in the declaration for the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42f68-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="42f68-110">See also</span></span>

- [<span data-ttu-id="42f68-111">Error — Typy</span><span class="sxs-lookup"><span data-stu-id="42f68-111">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
- [<span data-ttu-id="42f68-112">Call — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="42f68-112">Call Statement</span></span>](../../../visual-basic/language-reference/statements/call-statement.md)
- [<span data-ttu-id="42f68-113">Declare — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="42f68-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
