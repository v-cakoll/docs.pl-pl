---
title: <type1>"<typename>musi implementować<methodname>"dla interfejsu"<interfacename>"
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: 432f089bc77928308820d7456d930fba8dc513f7
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59304912"
---
# <a name="type1typename-must-implement-methodname-for-interface-interfacename"></a><span data-ttu-id="af327-102">\<type1 > "\<typename >" musi implementować "\<methodname >" dla interfejsu "\<interfacename >"</span><span class="sxs-lookup"><span data-stu-id="af327-102">\<type1>'\<typename>' must implement '\<methodname>' for interface '\<interfacename>'</span></span>
<span data-ttu-id="af327-103">Klasa lub struktura oświadczeń zaimplementować interfejs, ale nie implementuje określonymi przez interfejs.</span><span class="sxs-lookup"><span data-stu-id="af327-103">A class or structure claims to implement an interface but does not implement a procedure defined by the interface.</span></span> <span data-ttu-id="af327-104">Należy zaimplementować każdego członka interfejsu.</span><span class="sxs-lookup"><span data-stu-id="af327-104">Every member of the interface must be implemented.</span></span>  
  
 <span data-ttu-id="af327-105">**Identyfikator błędu:** BC30149</span><span class="sxs-lookup"><span data-stu-id="af327-105">**Error ID:** BC30149</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="af327-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="af327-106">To correct this error</span></span>  
  
1. <span data-ttu-id="af327-107">Zadeklaruj procedury o tej samej nazwie i podpisie, zgodnie z definicją w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="af327-107">Declare a procedure with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="af327-108">Pamiętaj uwzględnić co najmniej `End Function` lub `End Sub` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="af327-108">Be sure to include at least the `End Function` or `End Sub` statement.</span></span>  
  
2. <span data-ttu-id="af327-109">Dodaj `Implements` klauzulę na końcu `Function` lub `Sub` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="af327-109">Add an `Implements` clause to the end of the `Function` or `Sub` statement.</span></span> <span data-ttu-id="af327-110">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="af327-110">For example:</span></span>  
  
    ```  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="af327-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="af327-111">See also</span></span>

- [<span data-ttu-id="af327-112">Implements — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="af327-112">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
- [<span data-ttu-id="af327-113">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="af327-113">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
