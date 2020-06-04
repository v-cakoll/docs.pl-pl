---
title: Oczekiwano instrukcji „Optional”
ms.date: 07/20/2015
f1_keywords:
- bc30202
- vbc30202
helpviewer_keywords:
- BC30202
ms.assetid: 6f75060c-2db4-4a79-b5d1-5780c09a74cd
ms.openlocfilehash: 411e3248409ab0184666f4efefb4ec4becf7cab1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409351"
---
# <a name="optional-expected"></a><span data-ttu-id="4ff60-102">Oczekiwano instrukcji „Optional”</span><span class="sxs-lookup"><span data-stu-id="4ff60-102">'Optional' expected</span></span>
<span data-ttu-id="4ff60-103">Po argumencie opcjonalnym w deklaracji procedury występuje wymagany argument.</span><span class="sxs-lookup"><span data-stu-id="4ff60-103">An optional argument in a procedure declaration is followed by a required argument.</span></span> <span data-ttu-id="4ff60-104">Każdy argument po opcjonalnym argumencie musi być również opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="4ff60-104">Every argument following an optional argument must also be optional.</span></span>  
  
 <span data-ttu-id="4ff60-105">**Identyfikator błędu:** BC30202</span><span class="sxs-lookup"><span data-stu-id="4ff60-105">**Error ID:** BC30202</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4ff60-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="4ff60-106">To correct this error</span></span>  
  
1. <span data-ttu-id="4ff60-107">Jeśli argument jest wymagany, przenieś go, aby poprzedzał pierwszy opcjonalny argument na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="4ff60-107">If the argument is intended to be required, move it to precede the first optional argument in the argument list.</span></span>  
  
2. <span data-ttu-id="4ff60-108">Jeśli argument jest zamierzony jako opcjonalny, użyj `Optional` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="4ff60-108">If the argument is intended to be optional, use the `Optional` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ff60-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4ff60-109">See also</span></span>

- [<span data-ttu-id="4ff60-110">Parametry opcjonalne</span><span class="sxs-lookup"><span data-stu-id="4ff60-110">Optional Parameters</span></span>](../../programming-guide/language-features/procedures/optional-parameters.md)
