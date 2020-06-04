---
title: Nieprawidłowa konwencja wywoływania biblioteki DLL
ms.date: 07/20/2015
f1_keywords:
- vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
ms.openlocfilehash: a60e44ce92b1805b0a5a6f1d4ce397c295eef202
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409884"
---
# <a name="bad-dll-calling-convention"></a><span data-ttu-id="bb3e1-102">Nieprawidłowa konwencja wywoływania biblioteki DLL</span><span class="sxs-lookup"><span data-stu-id="bb3e1-102">Bad DLL calling convention</span></span>
<span data-ttu-id="bb3e1-103">Argumenty przekazane do biblioteki dołączanej dynamicznie (DLL) muszą dokładnie pasować do oczekiwanych przez procedurę.</span><span class="sxs-lookup"><span data-stu-id="bb3e1-103">Arguments passed to a dynamic-link library (DLL) must exactly match those expected by the routine.</span></span> <span data-ttu-id="bb3e1-104">Konwencje wywoływania dotyczą liczby, typu i kolejności argumentów.</span><span class="sxs-lookup"><span data-stu-id="bb3e1-104">Calling conventions deal with number, type, and order of arguments.</span></span> <span data-ttu-id="bb3e1-105">Program może wywołać procedurę w bibliotece DLL, która jest w trakcie przekazywania nieprawidłowego typu lub liczby argumentów.</span><span class="sxs-lookup"><span data-stu-id="bb3e1-105">Your program may be calling a routine in a DLL that is being passed the wrong type or number of arguments.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bb3e1-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="bb3e1-106">To correct this error</span></span>  
  
1. <span data-ttu-id="bb3e1-107">Upewnij się, że wszystkie typy argumentów zgadzają się z tymi określonymi w deklaracji wywoływanej procedury.</span><span class="sxs-lookup"><span data-stu-id="bb3e1-107">Make sure all argument types agree with those specified in the declaration of the routine that you are calling.</span></span>  
  
2. <span data-ttu-id="bb3e1-108">Upewnij się, że przekazujesz tę samą liczbę argumentów wskazanych w deklaracji wywoływanej procedury.</span><span class="sxs-lookup"><span data-stu-id="bb3e1-108">Make sure you are passing the same number of arguments indicated in the declaration of the routine that you are calling.</span></span>  
  
3. <span data-ttu-id="bb3e1-109">Jeśli procedura DLL oczekuje argumentów przez wartość, upewnij się, że `ByVal` określono dla tych argumentów w deklaracji procedury.</span><span class="sxs-lookup"><span data-stu-id="bb3e1-109">If the DLL routine expects arguments by value, make sure `ByVal` is specified for those arguments in the declaration for the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb3e1-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bb3e1-110">See also</span></span>

- [<span data-ttu-id="bb3e1-111">Typy błędów</span><span class="sxs-lookup"><span data-stu-id="bb3e1-111">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="bb3e1-112">Call, instrukcja</span><span class="sxs-lookup"><span data-stu-id="bb3e1-112">Call Statement</span></span>](../statements/call-statement.md)
- [<span data-ttu-id="bb3e1-113">Declare — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="bb3e1-113">Declare Statement</span></span>](../statements/declare-statement.md)
