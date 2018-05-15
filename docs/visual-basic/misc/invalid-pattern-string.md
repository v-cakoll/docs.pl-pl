---
title: Nieprawidłowy ciąg znaków wzorca
ms.date: 07/20/2015
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
ms.openlocfilehash: 4905f74683989d8e1a2b041a8af4af4d7432ffab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="invalid-pattern-string"></a><span data-ttu-id="fb382-102">Nieprawidłowy ciąg znaków wzorca</span><span class="sxs-lookup"><span data-stu-id="fb382-102">Invalid pattern string</span></span>
<span data-ttu-id="fb382-103">Wzorzec ciągu określonego w `Like` operacji wyszukiwania jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="fb382-103">The pattern string specified in the `Like` operation of a search is invalid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fb382-104">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="fb382-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="fb382-105">Przejrzyj prawidłowe znaki listy wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="fb382-105">Review the valid characters for list expressions.</span></span>  
  
2.  <span data-ttu-id="fb382-106">W zakresie wzorzec, upewnij się, że początkowy znaku zakresu jest mniejsza niż końcowy znak zakresu, podobnie jak w `[a-z]`.</span><span class="sxs-lookup"><span data-stu-id="fb382-106">In the pattern range, ensure that the start range character is less than the end range character, as in `[a-z]`.</span></span>  
  
3.  <span data-ttu-id="fb382-107">W zakresie wzorzec, upewnij się, że nie ma wiele łączników obok siebie, podobnie jak w `[a--z]`.</span><span class="sxs-lookup"><span data-stu-id="fb382-107">In the pattern range, ensure that there are not multiple hyphens next to each other, as in `[a--z]`.</span></span>  
  
4.  <span data-ttu-id="fb382-108">Zakresów wzorzec końcowego nawiasu zamykającego.</span><span class="sxs-lookup"><span data-stu-id="fb382-108">End pattern ranges with a closing bracket.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb382-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fb382-109">See Also</span></span>  
 [<span data-ttu-id="fb382-110">Like, operator</span><span class="sxs-lookup"><span data-stu-id="fb382-110">Like Operator</span></span>](../../visual-basic/language-reference/operators/like-operator.md)
