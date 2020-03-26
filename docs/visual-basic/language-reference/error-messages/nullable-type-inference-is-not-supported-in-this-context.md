---
title: Wnioskowanie typu zerowalnego nie jest obsługiwane w tym kontekście
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: 42bde0b1843e52bbc16118bb056ade791591904e
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249503"
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a><span data-ttu-id="66e4d-102">Wnioskowanie typu zerowalnego nie jest obsługiwane w tym kontekście</span><span class="sxs-lookup"><span data-stu-id="66e4d-102">Nullable type inference is not supported in this context</span></span>
<span data-ttu-id="66e4d-103">Typy wartości i struktury mogą być zadeklarowane nullable.</span><span class="sxs-lookup"><span data-stu-id="66e4d-103">Value types and structures can be declared nullable.</span></span>  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 <span data-ttu-id="66e4d-104">Jednak nie można użyć nullable deklaracji w połączeniu z wnioskowania o typie.</span><span class="sxs-lookup"><span data-stu-id="66e4d-104">However, you cannot use the nullable declaration in combination with type inference.</span></span> <span data-ttu-id="66e4d-105">Poniższe przykłady powodują ten błąd.</span><span class="sxs-lookup"><span data-stu-id="66e4d-105">The following examples cause this error.</span></span>  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 <span data-ttu-id="66e4d-106">**Identyfikator błędu:** Bc36629</span><span class="sxs-lookup"><span data-stu-id="66e4d-106">**Error ID:** BC36629</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="66e4d-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="66e4d-107">To correct this error</span></span>  
  
- <span data-ttu-id="66e4d-108">Użyj `As` klauzuli, aby zadeklarować zmienną jako typ wartości możliwej do wartości null.</span><span class="sxs-lookup"><span data-stu-id="66e4d-108">Use an `As` clause to declare the variable as a nullable value type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66e4d-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="66e4d-109">See also</span></span>

- [<span data-ttu-id="66e4d-110">Typy o wartości zerowalnej</span><span class="sxs-lookup"><span data-stu-id="66e4d-110">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="66e4d-111">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="66e4d-111">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
