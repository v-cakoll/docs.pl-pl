---
title: Brak wyrażenia indeksu tablicy
ms.date: 07/20/2015
f1_keywords:
- bc30306
- vbc30306
helpviewer_keywords:
- BC30306
ms.assetid: 3c0d9732-ee37-436f-a1df-29d65712f48a
ms.openlocfilehash: f05416b467851af7b47919d05b2b91ab95ad6e24
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54638408"
---
# <a name="array-subscript-expression-missing"></a><span data-ttu-id="6f302-102">Brak wyrażenia indeksu tablicy</span><span class="sxs-lookup"><span data-stu-id="6f302-102">Array subscript expression missing</span></span>
<span data-ttu-id="6f302-103">Inicjowanie tablicy powoduje, że co najmniej jednym z indeksów dolnych, które określają granice tablicy.</span><span class="sxs-lookup"><span data-stu-id="6f302-103">An array initialization leaves out one or more of the subscripts that define the array bounds.</span></span> <span data-ttu-id="6f302-104">Na przykład instrukcja może zawierać wyrażenia `myArray (5,5,,10)`, który powoduje, że trzecie indeks dolny.</span><span class="sxs-lookup"><span data-stu-id="6f302-104">For example, the statement might contain the expression `myArray (5,5,,10)`, which leaves out the third subscript.</span></span>  
  
 <span data-ttu-id="6f302-105">**Identyfikator błędu:** BC30306</span><span class="sxs-lookup"><span data-stu-id="6f302-105">**Error ID:** BC30306</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6f302-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="6f302-106">To correct this error</span></span>  
  
-   <span data-ttu-id="6f302-107">Podaj brakujące indeks dolny.</span><span class="sxs-lookup"><span data-stu-id="6f302-107">Supply the missing subscript.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f302-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6f302-108">See also</span></span>
- [<span data-ttu-id="6f302-109">Tablice</span><span class="sxs-lookup"><span data-stu-id="6f302-109">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
