---
title: Wnioskowanie typu zerowalnego nie jest obsługiwane w tym kontekście
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: ea531c7be676e940a263b019a66cc80cf280a772
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a><span data-ttu-id="9247e-102">Wnioskowanie typu zerowalnego nie jest obsługiwane w tym kontekście</span><span class="sxs-lookup"><span data-stu-id="9247e-102">Nullable type inference is not supported in this context</span></span>
<span data-ttu-id="9247e-103">Typy wartości i struktury mogą być deklarowane wartości null.</span><span class="sxs-lookup"><span data-stu-id="9247e-103">Value types and structures can be declared nullable.</span></span>  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 <span data-ttu-id="9247e-104">Jednak wartości null deklaracji nie można używać w połączeniu z wnioskowanie o typie.</span><span class="sxs-lookup"><span data-stu-id="9247e-104">However, you cannot use the nullable declaration in combination with type inference.</span></span> <span data-ttu-id="9247e-105">Poniższe przykłady być przyczyną tego błędu.</span><span class="sxs-lookup"><span data-stu-id="9247e-105">The following examples cause this error.</span></span>  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 <span data-ttu-id="9247e-106">**Identyfikator błędu:** BC36629</span><span class="sxs-lookup"><span data-stu-id="9247e-106">**Error ID:** BC36629</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9247e-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="9247e-107">To correct this error</span></span>  
  
-   <span data-ttu-id="9247e-108">Użyj `As` klauzuli, aby zadeklarować zmiennej jako wartości null.</span><span class="sxs-lookup"><span data-stu-id="9247e-108">Use an `As` clause to declare the variable as nullable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9247e-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9247e-109">See Also</span></span>  
 [<span data-ttu-id="9247e-110">Typy wartości dopuszczających wartości null</span><span class="sxs-lookup"><span data-stu-id="9247e-110">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [<span data-ttu-id="9247e-111">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="9247e-111">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
