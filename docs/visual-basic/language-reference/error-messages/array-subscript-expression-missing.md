---
title: Brak wyrażenia indeksu tablicy
ms.date: 07/20/2015
f1_keywords:
- bc30306
- vbc30306
helpviewer_keywords:
- BC30306
ms.assetid: 3c0d9732-ee37-436f-a1df-29d65712f48a
ms.openlocfilehash: 4dadad63f4321e88b79f2006a9e6b7befa27909a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61935346"
---
# <a name="array-subscript-expression-missing"></a><span data-ttu-id="ac08c-102">Brak wyrażenia indeksu tablicy</span><span class="sxs-lookup"><span data-stu-id="ac08c-102">Array subscript expression missing</span></span>
<span data-ttu-id="ac08c-103">Inicjowanie tablicy powoduje, że co najmniej jednym z indeksów dolnych, które określają granice tablicy.</span><span class="sxs-lookup"><span data-stu-id="ac08c-103">An array initialization leaves out one or more of the subscripts that define the array bounds.</span></span> <span data-ttu-id="ac08c-104">Na przykład instrukcja może zawierać wyrażenia `myArray (5,5,,10)`, który powoduje, że trzecie indeks dolny.</span><span class="sxs-lookup"><span data-stu-id="ac08c-104">For example, the statement might contain the expression `myArray (5,5,,10)`, which leaves out the third subscript.</span></span>  
  
 <span data-ttu-id="ac08c-105">**Identyfikator błędu:** BC30306</span><span class="sxs-lookup"><span data-stu-id="ac08c-105">**Error ID:** BC30306</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ac08c-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="ac08c-106">To correct this error</span></span>  
  
- <span data-ttu-id="ac08c-107">Podaj brakujące indeks dolny.</span><span class="sxs-lookup"><span data-stu-id="ac08c-107">Supply the missing subscript.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac08c-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ac08c-108">See also</span></span>

- [<span data-ttu-id="ac08c-109">Tablice</span><span class="sxs-lookup"><span data-stu-id="ac08c-109">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
