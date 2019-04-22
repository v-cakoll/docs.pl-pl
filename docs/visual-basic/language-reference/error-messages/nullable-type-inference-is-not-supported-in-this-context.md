---
title: Wnioskowanie typu zerowalnego nie jest obsługiwane w tym kontekście
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: 9f7f878649d8b96f050b56d5b878eb3d67e027ff
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58819245"
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a><span data-ttu-id="b896d-102">Wnioskowanie typu zerowalnego nie jest obsługiwane w tym kontekście</span><span class="sxs-lookup"><span data-stu-id="b896d-102">Nullable type inference is not supported in this context</span></span>
<span data-ttu-id="b896d-103">Typy wartości i struktury można zadeklarować dopuszczającego wartość null.</span><span class="sxs-lookup"><span data-stu-id="b896d-103">Value types and structures can be declared nullable.</span></span>  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 <span data-ttu-id="b896d-104">Jednak nie można użyć deklaracji dopuszczającego wartość null w połączeniu z wnioskowanie o typie.</span><span class="sxs-lookup"><span data-stu-id="b896d-104">However, you cannot use the nullable declaration in combination with type inference.</span></span> <span data-ttu-id="b896d-105">Poniższe przykłady przyczyny wystąpienia tego błędu.</span><span class="sxs-lookup"><span data-stu-id="b896d-105">The following examples cause this error.</span></span>  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 <span data-ttu-id="b896d-106">**Identyfikator błędu:** BC36629</span><span class="sxs-lookup"><span data-stu-id="b896d-106">**Error ID:** BC36629</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b896d-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="b896d-107">To correct this error</span></span>  
  
-   <span data-ttu-id="b896d-108">Użyj `As` klauzulę, aby zadeklarować zmienną jako dopuszczającego wartość null.</span><span class="sxs-lookup"><span data-stu-id="b896d-108">Use an `As` clause to declare the variable as nullable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b896d-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b896d-109">See also</span></span>

- [<span data-ttu-id="b896d-110">Typy wartości dopuszczających wartości null</span><span class="sxs-lookup"><span data-stu-id="b896d-110">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="b896d-111">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="b896d-111">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
