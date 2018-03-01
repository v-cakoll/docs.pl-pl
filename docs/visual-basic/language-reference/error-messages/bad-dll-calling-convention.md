---
title: "Nieprawidłowa konwencja wywoływania biblioteki DLL"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: daa84e82d2fbe1041af56fdd5cc3855efd814ddf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="bad-dll-calling-convention"></a><span data-ttu-id="bb411-102">Nieprawidłowa konwencja wywoływania biblioteki DLL</span><span class="sxs-lookup"><span data-stu-id="bb411-102">Bad DLL calling convention</span></span>
<span data-ttu-id="bb411-103">Argumenty przekazane do biblioteki dołączanej (dynamicznie DLL) musi dokładnie odpowiadać wartości oczekiwanych przez procedurę.</span><span class="sxs-lookup"><span data-stu-id="bb411-103">Arguments passed to a dynamic-link library (DLL) must exactly match those expected by the routine.</span></span> <span data-ttu-id="bb411-104">Konwencje wywoływania uwzględniać liczbę, typ i kolejność argumentów.</span><span class="sxs-lookup"><span data-stu-id="bb411-104">Calling conventions deal with number, type, and order of arguments.</span></span> <span data-ttu-id="bb411-105">Program może wywołania procedury w bibliotece DLL, który jest przekazywany nieprawidłowego typu lub liczba argumentów.</span><span class="sxs-lookup"><span data-stu-id="bb411-105">Your program may be calling a routine in a DLL that is being passed the wrong type or number of arguments.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bb411-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="bb411-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="bb411-107">Upewnij się, że wszystkie typy argumentów są zgodne z danymi określony w deklaracji procedury, która jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="bb411-107">Make sure all argument types agree with those specified in the declaration of the routine that you are calling.</span></span>  
  
2.  <span data-ttu-id="bb411-108">Upewnij się, że przekazywane taką samą liczbę argumentów wskazanych w deklaracji procedury, które są nawiązywane.</span><span class="sxs-lookup"><span data-stu-id="bb411-108">Make sure you are passing the same number of arguments indicated in the declaration of the routine that you are calling.</span></span>  
  
3.  <span data-ttu-id="bb411-109">Jeśli procedura DLL oczekuje argumentów według wartości, upewnij się, `ByVal` dla tych argumentów w deklaracji dla procedury określono.</span><span class="sxs-lookup"><span data-stu-id="bb411-109">If the DLL routine expects arguments by value, make sure `ByVal` is specified for those arguments in the declaration for the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb411-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bb411-110">See Also</span></span>  
 [<span data-ttu-id="bb411-111">Error — typy</span><span class="sxs-lookup"><span data-stu-id="bb411-111">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [<span data-ttu-id="bb411-112">Call — instrukcja</span><span class="sxs-lookup"><span data-stu-id="bb411-112">Call Statement</span></span>](../../../visual-basic/language-reference/statements/call-statement.md)  
 [<span data-ttu-id="bb411-113">DECLARE — instrukcja</span><span class="sxs-lookup"><span data-stu-id="bb411-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
