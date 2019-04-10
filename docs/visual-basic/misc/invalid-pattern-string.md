---
title: Nieprawidłowy ciąg wzorca
ms.date: 07/20/2015
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
ms.openlocfilehash: 7390b9b32eea248969813b52f8d9799798718de0
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59298685"
---
# <a name="invalid-pattern-string"></a><span data-ttu-id="202eb-102">Nieprawidłowy ciąg wzorca</span><span class="sxs-lookup"><span data-stu-id="202eb-102">Invalid pattern string</span></span>
<span data-ttu-id="202eb-103">Ciągu wzorca określonego w `Like` operacji wyszukiwania jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="202eb-103">The pattern string specified in the `Like` operation of a search is invalid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="202eb-104">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="202eb-104">To correct this error</span></span>  
  
1. <span data-ttu-id="202eb-105">Sprawdź prawidłowe znaki listy wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="202eb-105">Review the valid characters for list expressions.</span></span>  
  
2. <span data-ttu-id="202eb-106">W zakresie wzorzec, upewnij się, że znaku zakresu początkowego jest mniejszy niż końcowy znak zakresu, podobnie jak w `[a-z]`.</span><span class="sxs-lookup"><span data-stu-id="202eb-106">In the pattern range, ensure that the start range character is less than the end range character, as in `[a-z]`.</span></span>  
  
3. <span data-ttu-id="202eb-107">W zakresie wzorzec, upewnij się, że nie wielu łączników obok siebie, podobnie jak w `[a--z]`.</span><span class="sxs-lookup"><span data-stu-id="202eb-107">In the pattern range, ensure that there are not multiple hyphens next to each other, as in `[a--z]`.</span></span>  
  
4. <span data-ttu-id="202eb-108">Końcowa wzorzec zakresów nawias zamykający.</span><span class="sxs-lookup"><span data-stu-id="202eb-108">End pattern ranges with a closing bracket.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="202eb-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="202eb-109">See also</span></span>

- [<span data-ttu-id="202eb-110">Like — Operator</span><span class="sxs-lookup"><span data-stu-id="202eb-110">Like Operator</span></span>](../../visual-basic/language-reference/operators/like-operator.md)
