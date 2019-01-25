---
title: Wnioskowanie typu zerowalnego nie jest obsługiwane w tym kontekście
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: 7dffc5233656257cd892f573a2f8b9f91d781c21
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611894"
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a><span data-ttu-id="499ad-102">Wnioskowanie typu zerowalnego nie jest obsługiwane w tym kontekście</span><span class="sxs-lookup"><span data-stu-id="499ad-102">Nullable type inference is not supported in this context</span></span>
<span data-ttu-id="499ad-103">Typy wartości i struktury można zadeklarować dopuszczającego wartość null.</span><span class="sxs-lookup"><span data-stu-id="499ad-103">Value types and structures can be declared nullable.</span></span>  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 <span data-ttu-id="499ad-104">Jednak nie można użyć deklaracji dopuszczającego wartość null w połączeniu z wnioskowanie o typie.</span><span class="sxs-lookup"><span data-stu-id="499ad-104">However, you cannot use the nullable declaration in combination with type inference.</span></span> <span data-ttu-id="499ad-105">Poniższe przykłady przyczyny wystąpienia tego błędu.</span><span class="sxs-lookup"><span data-stu-id="499ad-105">The following examples cause this error.</span></span>  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 <span data-ttu-id="499ad-106">**Identyfikator błędu:** BC36629</span><span class="sxs-lookup"><span data-stu-id="499ad-106">**Error ID:** BC36629</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="499ad-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="499ad-107">To correct this error</span></span>  
  
-   <span data-ttu-id="499ad-108">Użyj `As` klauzulę, aby zadeklarować zmienną jako dopuszczającego wartość null.</span><span class="sxs-lookup"><span data-stu-id="499ad-108">Use an `As` clause to declare the variable as nullable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="499ad-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="499ad-109">See also</span></span>
- [<span data-ttu-id="499ad-110">Typy wartości dopuszczających wartości null</span><span class="sxs-lookup"><span data-stu-id="499ad-110">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="499ad-111">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="499ad-111">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
