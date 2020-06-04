---
title: Wnioskowanie typu zerowalnego nie jest obsługiwane w tym kontekście
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: 52e5391fbcf30a4dada4d64a0e810c900ea85806
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409390"
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a><span data-ttu-id="41c11-102">Wnioskowanie typu zerowalnego nie jest obsługiwane w tym kontekście</span><span class="sxs-lookup"><span data-stu-id="41c11-102">Nullable type inference is not supported in this context</span></span>
<span data-ttu-id="41c11-103">Typy wartości i struktury mogą być deklarowane jako dopuszczające wartość null.</span><span class="sxs-lookup"><span data-stu-id="41c11-103">Value types and structures can be declared nullable.</span></span>  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 <span data-ttu-id="41c11-104">Nie można jednak używać deklaracji wartości null w połączeniu z wnioskami o typie.</span><span class="sxs-lookup"><span data-stu-id="41c11-104">However, you cannot use the nullable declaration in combination with type inference.</span></span> <span data-ttu-id="41c11-105">Poniższe przykłady powodują wystąpienie tego błędu.</span><span class="sxs-lookup"><span data-stu-id="41c11-105">The following examples cause this error.</span></span>  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 <span data-ttu-id="41c11-106">**Identyfikator błędu:** BC36629</span><span class="sxs-lookup"><span data-stu-id="41c11-106">**Error ID:** BC36629</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="41c11-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="41c11-107">To correct this error</span></span>  
  
- <span data-ttu-id="41c11-108">Użyj `As` klauzuli, aby zadeklarować zmienną jako typ wartości null.</span><span class="sxs-lookup"><span data-stu-id="41c11-108">Use an `As` clause to declare the variable as a nullable value type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41c11-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="41c11-109">See also</span></span>

- [<span data-ttu-id="41c11-110">Typy wartości null</span><span class="sxs-lookup"><span data-stu-id="41c11-110">Nullable Value Types</span></span>](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="41c11-111">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="41c11-111">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
