---
title: Nazwę zmiennej zakresu można wywnioskować tylko na podstawie prostej lub kwalifikowanej nazwy bez argumentów
ms.date: 07/20/2015
f1_keywords:
- vbc36599
- bc36599
helpviewer_keywords:
- BC36599
ms.assetid: 17763dbe-f74f-4ccb-8086-cb7e45ec4d12
ms.openlocfilehash: 8b95bb3c53210cc11966466d32924c13aee8234b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54581952"
---
# <a name="range-variable-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a><span data-ttu-id="2f99c-102">Nazwę zmiennej zakresu można wywnioskować tylko na podstawie prostej lub kwalifikowanej nazwy bez argumentów</span><span class="sxs-lookup"><span data-stu-id="2f99c-102">Range variable name can be inferred only from a simple or qualified name with no arguments</span></span>
<span data-ttu-id="2f99c-103">Element programowania, który przyjmuje jeden lub więcej argumentów znajduje się w zapytaniu programu LINQ.</span><span class="sxs-lookup"><span data-stu-id="2f99c-103">A programming element that takes one or more arguments is included in a LINQ query.</span></span> <span data-ttu-id="2f99c-104">Kompilator nie może wywnioskować zmienną zakresu, z tym elementem programowania.</span><span class="sxs-lookup"><span data-stu-id="2f99c-104">The compiler is unable to infer a range variable from that programming element.</span></span>  
  
 <span data-ttu-id="2f99c-105">**Identyfikator błędu:** BC36599</span><span class="sxs-lookup"><span data-stu-id="2f99c-105">**Error ID:** BC36599</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2f99c-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="2f99c-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="2f99c-107">Jawna nazwa zmiennej elementu programistycznego, należy podać, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="2f99c-107">Supply an explicit variable name for the programming element, as shown in the following code:</span></span>  
  
```  
Dim query = From var1 In collection1   
            Select VariableAlias= SampleFunction(var1), var1  
```  
  
## <a name="see-also"></a><span data-ttu-id="2f99c-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2f99c-108">See also</span></span>
- [<span data-ttu-id="2f99c-109">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2f99c-109">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="2f99c-110">Select, klauzula</span><span class="sxs-lookup"><span data-stu-id="2f99c-110">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
