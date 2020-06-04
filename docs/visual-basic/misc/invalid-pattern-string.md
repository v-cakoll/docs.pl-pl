---
title: Nieprawidłowy ciąg wzorca
ms.date: 07/20/2015
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
ms.openlocfilehash: aa408f4cecc2a2774cb98cba96cd04a67afcc546
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402216"
---
# <a name="invalid-pattern-string"></a><span data-ttu-id="7f7a7-102">Nieprawidłowy ciąg wzorca</span><span class="sxs-lookup"><span data-stu-id="7f7a7-102">Invalid pattern string</span></span>
<span data-ttu-id="7f7a7-103">Ciąg wzorca określony w `Like` operacji wyszukiwania jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="7f7a7-103">The pattern string specified in the `Like` operation of a search is invalid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7f7a7-104">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="7f7a7-104">To correct this error</span></span>  
  
1. <span data-ttu-id="7f7a7-105">Przejrzyj prawidłowe znaki dla wyrażeń listy.</span><span class="sxs-lookup"><span data-stu-id="7f7a7-105">Review the valid characters for list expressions.</span></span>  
  
2. <span data-ttu-id="7f7a7-106">W zakresie wzorców upewnij się, że znak zakresu początkowego jest mniejszy niż znak zakresu końcowego, jak w `[a-z]` .</span><span class="sxs-lookup"><span data-stu-id="7f7a7-106">In the pattern range, ensure that the start range character is less than the end range character, as in `[a-z]`.</span></span>  
  
3. <span data-ttu-id="7f7a7-107">W zakresie wzorców upewnij się, że nie ma kilku łączników obok siebie, jak w `[a--z]` .</span><span class="sxs-lookup"><span data-stu-id="7f7a7-107">In the pattern range, ensure that there are not multiple hyphens next to each other, as in `[a--z]`.</span></span>  
  
4. <span data-ttu-id="7f7a7-108">Końcowe zakresy wzorców z nawiasem zamykającym.</span><span class="sxs-lookup"><span data-stu-id="7f7a7-108">End pattern ranges with a closing bracket.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f7a7-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7f7a7-109">See also</span></span>

- [<span data-ttu-id="7f7a7-110">Like — Operator</span><span class="sxs-lookup"><span data-stu-id="7f7a7-110">Like Operator</span></span>](../language-reference/operators/like-operator.md)
