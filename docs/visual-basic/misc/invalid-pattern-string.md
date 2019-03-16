---
title: Nieprawidłowy ciąg wzorca
ms.date: 07/20/2015
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
ms.openlocfilehash: bc2e91060ca1b0e21ea28b0f08febc3e0c54f4f1
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2019
ms.locfileid: "58027318"
---
# <a name="invalid-pattern-string"></a><span data-ttu-id="57c2d-102">Nieprawidłowy ciąg wzorca</span><span class="sxs-lookup"><span data-stu-id="57c2d-102">Invalid pattern string</span></span>
<span data-ttu-id="57c2d-103">Ciągu wzorca określonego w `Like` operacji wyszukiwania jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="57c2d-103">The pattern string specified in the `Like` operation of a search is invalid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="57c2d-104">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="57c2d-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="57c2d-105">Sprawdź prawidłowe znaki listy wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="57c2d-105">Review the valid characters for list expressions.</span></span>  
  
2.  <span data-ttu-id="57c2d-106">W zakresie wzorzec, upewnij się, że znaku zakresu początkowego jest mniejszy niż końcowy znak zakresu, podobnie jak w `[a-z]`.</span><span class="sxs-lookup"><span data-stu-id="57c2d-106">In the pattern range, ensure that the start range character is less than the end range character, as in `[a-z]`.</span></span>  
  
3.  <span data-ttu-id="57c2d-107">W zakresie wzorzec, upewnij się, że nie wielu łączników obok siebie, podobnie jak w `[a--z]`.</span><span class="sxs-lookup"><span data-stu-id="57c2d-107">In the pattern range, ensure that there are not multiple hyphens next to each other, as in `[a--z]`.</span></span>  
  
4.  <span data-ttu-id="57c2d-108">Końcowa wzorzec zakresów nawias zamykający.</span><span class="sxs-lookup"><span data-stu-id="57c2d-108">End pattern ranges with a closing bracket.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57c2d-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="57c2d-109">See also</span></span>

- [<span data-ttu-id="57c2d-110">Like, operator</span><span class="sxs-lookup"><span data-stu-id="57c2d-110">Like Operator</span></span>](../../visual-basic/language-reference/operators/like-operator.md)
