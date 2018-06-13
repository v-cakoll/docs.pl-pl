---
title: '&#39;Opcjonalne&#39; oczekiwano'
ms.date: 07/20/2015
f1_keywords:
- bc30202
- vbc30202
helpviewer_keywords:
- BC30202
ms.assetid: 6f75060c-2db4-4a79-b5d1-5780c09a74cd
ms.openlocfilehash: 52e4288255a246f78730b33beb55f6d2d83ff214
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593957"
---
# <a name="39optional39-expected"></a><span data-ttu-id="9c175-102">&#39;Opcjonalne&#39; oczekiwano</span><span class="sxs-lookup"><span data-stu-id="9c175-102">&#39;Optional&#39; expected</span></span>
<span data-ttu-id="9c175-103">Opcjonalny argument w deklaracji procedury następuje wymaganego argumentu.</span><span class="sxs-lookup"><span data-stu-id="9c175-103">An optional argument in a procedure declaration is followed by a required argument.</span></span> <span data-ttu-id="9c175-104">Każdy argument po opcjonalny argument musi być również opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="9c175-104">Every argument following an optional argument must also be optional.</span></span>  
  
 <span data-ttu-id="9c175-105">**Identyfikator błędu:** BC30202</span><span class="sxs-lookup"><span data-stu-id="9c175-105">**Error ID:** BC30202</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9c175-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="9c175-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="9c175-107">Jeśli argument ma być wymagane, przenieś go do poprzedź pierwszy argument opcjonalne na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="9c175-107">If the argument is intended to be required, move it to precede the first optional argument in the argument list.</span></span>  
  
2.  <span data-ttu-id="9c175-108">Jeśli argument ma być opcjonalne, użyj `Optional` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="9c175-108">If the argument is intended to be optional, use the `Optional` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c175-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9c175-109">See Also</span></span>  
 [<span data-ttu-id="9c175-110">Parametry opcjonalne</span><span class="sxs-lookup"><span data-stu-id="9c175-110">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
