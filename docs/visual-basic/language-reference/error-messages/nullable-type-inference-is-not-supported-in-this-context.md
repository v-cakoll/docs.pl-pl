---
title: "Wnioskowanie typu zerowalnego nie jest obsługiwane w tym kontekście"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e7a5450d812260d3916296dff56abee27b3d586c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a><span data-ttu-id="e7d31-102">Wnioskowanie typu zerowalnego nie jest obsługiwane w tym kontekście</span><span class="sxs-lookup"><span data-stu-id="e7d31-102">Nullable type inference is not supported in this context</span></span>
<span data-ttu-id="e7d31-103">Typy wartości i struktury mogą być deklarowane wartości null.</span><span class="sxs-lookup"><span data-stu-id="e7d31-103">Value types and structures can be declared nullable.</span></span>  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 <span data-ttu-id="e7d31-104">Jednak wartości null deklaracji nie można używać w połączeniu z wnioskowanie o typie.</span><span class="sxs-lookup"><span data-stu-id="e7d31-104">However, you cannot use the nullable declaration in combination with type inference.</span></span> <span data-ttu-id="e7d31-105">Poniższe przykłady być przyczyną tego błędu.</span><span class="sxs-lookup"><span data-stu-id="e7d31-105">The following examples cause this error.</span></span>  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 <span data-ttu-id="e7d31-106">**Identyfikator błędu:** BC36629</span><span class="sxs-lookup"><span data-stu-id="e7d31-106">**Error ID:** BC36629</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e7d31-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="e7d31-107">To correct this error</span></span>  
  
-   <span data-ttu-id="e7d31-108">Użyj `As` klauzuli, aby zadeklarować zmiennej jako wartości null.</span><span class="sxs-lookup"><span data-stu-id="e7d31-108">Use an `As` clause to declare the variable as nullable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7d31-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e7d31-109">See Also</span></span>  
 [<span data-ttu-id="e7d31-110">Typy dopuszczające wartości zerowe wartości</span><span class="sxs-lookup"><span data-stu-id="e7d31-110">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [<span data-ttu-id="e7d31-111">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="e7d31-111">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
