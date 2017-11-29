---
title: "Nieprawidłowy ciąg znaków wzorca"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f824a5844d6d2b365358030119826266a4b42ef3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="invalid-pattern-string"></a><span data-ttu-id="2fa94-102">Nieprawidłowy ciąg znaków wzorca</span><span class="sxs-lookup"><span data-stu-id="2fa94-102">Invalid pattern string</span></span>
<span data-ttu-id="2fa94-103">Wzorzec ciągu określonego w `Like` operacji wyszukiwania jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="2fa94-103">The pattern string specified in the `Like` operation of a search is invalid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2fa94-104">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="2fa94-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="2fa94-105">Przejrzyj prawidłowe znaki listy wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="2fa94-105">Review the valid characters for list expressions.</span></span>  
  
2.  <span data-ttu-id="2fa94-106">W zakresie wzorzec, upewnij się, że początkowy znaku zakresu jest mniejsza niż końcowy znak zakresu, podobnie jak w `[a-z]`.</span><span class="sxs-lookup"><span data-stu-id="2fa94-106">In the pattern range, ensure that the start range character is less than the end range character, as in `[a-z]`.</span></span>  
  
3.  <span data-ttu-id="2fa94-107">W zakresie wzorzec, upewnij się, że nie ma wiele łączników obok siebie, podobnie jak w `[a--z]`.</span><span class="sxs-lookup"><span data-stu-id="2fa94-107">In the pattern range, ensure that there are not multiple hyphens next to each other, as in `[a--z]`.</span></span>  
  
4.  <span data-ttu-id="2fa94-108">Zakresów wzorzec końcowego nawiasu zamykającego.</span><span class="sxs-lookup"><span data-stu-id="2fa94-108">End pattern ranges with a closing bracket.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fa94-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2fa94-109">See Also</span></span>  
 [<span data-ttu-id="2fa94-110">Like — Operator</span><span class="sxs-lookup"><span data-stu-id="2fa94-110">Like Operator</span></span>](../../visual-basic/language-reference/operators/like-operator.md)
