---
title: '&#39; opcjonalne &#39; Oczekiwano'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30202
- vbc30202
helpviewer_keywords:
- BC30202
ms.assetid: 6f75060c-2db4-4a79-b5d1-5780c09a74cd
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e84371935fdd2d558e6828c05fa952b9cc4cf4f0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="39optional39-expected"></a><span data-ttu-id="e9c3f-102">&#39; opcjonalne &#39; Oczekiwano</span><span class="sxs-lookup"><span data-stu-id="e9c3f-102">&#39;Optional&#39; expected</span></span>
<span data-ttu-id="e9c3f-103">Opcjonalny argument w deklaracji procedury następuje wymaganego argumentu.</span><span class="sxs-lookup"><span data-stu-id="e9c3f-103">An optional argument in a procedure declaration is followed by a required argument.</span></span> <span data-ttu-id="e9c3f-104">Każdy argument po opcjonalny argument musi być również opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="e9c3f-104">Every argument following an optional argument must also be optional.</span></span>  
  
 <span data-ttu-id="e9c3f-105">**Identyfikator błędu:** BC30202</span><span class="sxs-lookup"><span data-stu-id="e9c3f-105">**Error ID:** BC30202</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e9c3f-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="e9c3f-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="e9c3f-107">Jeśli argument ma być wymagane, przenieś go do poprzedź pierwszy argument opcjonalne na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="e9c3f-107">If the argument is intended to be required, move it to precede the first optional argument in the argument list.</span></span>  
  
2.  <span data-ttu-id="e9c3f-108">Jeśli argument ma być opcjonalne, użyj `Optional` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="e9c3f-108">If the argument is intended to be optional, use the `Optional` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9c3f-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9c3f-109">See Also</span></span>  
 [<span data-ttu-id="e9c3f-110">Parametry opcjonalne</span><span class="sxs-lookup"><span data-stu-id="e9c3f-110">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
