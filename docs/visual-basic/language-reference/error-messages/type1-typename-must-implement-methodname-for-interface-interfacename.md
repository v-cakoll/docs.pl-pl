---
title: <type1>'<typename>musi implementować<methodname>'dla interfejsu'<interfacename>'
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: c387b0225375f4675042bef593b23a084305b4fd
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591596"
---
# <a name="type1typename-must-implement-methodname-for-interface-interfacename"></a><span data-ttu-id="191d7-102">\<type1 > '\<typename >' musi implementować '\<methodname >' dla interfejsu '\<interfacename >'</span><span class="sxs-lookup"><span data-stu-id="191d7-102">\<type1>'\<typename>' must implement '\<methodname>' for interface '\<interfacename>'</span></span>
<span data-ttu-id="191d7-103">Klasa lub struktura oświadczenia do implementacji interfejsu, ale nie implementuje procedury zdefiniowanej przez interfejs.</span><span class="sxs-lookup"><span data-stu-id="191d7-103">A class or structure claims to implement an interface but does not implement a procedure defined by the interface.</span></span> <span data-ttu-id="191d7-104">Każdy element członkowski interfejsu musi być zaimplementowany.</span><span class="sxs-lookup"><span data-stu-id="191d7-104">Every member of the interface must be implemented.</span></span>  
  
 <span data-ttu-id="191d7-105">**Identyfikator błędu:** BC30149</span><span class="sxs-lookup"><span data-stu-id="191d7-105">**Error ID:** BC30149</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="191d7-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="191d7-106">To correct this error</span></span>  
  
1. <span data-ttu-id="191d7-107">Zadeklaruj procedurę o tej samej nazwie i podpisie, zgodnie z definicją w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="191d7-107">Declare a procedure with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="191d7-108">Pamiętaj, aby uwzględnić co najmniej następującą instrukcję `End Function` lub `End Sub`.</span><span class="sxs-lookup"><span data-stu-id="191d7-108">Be sure to include at least the `End Function` or `End Sub` statement.</span></span>  
  
2. <span data-ttu-id="191d7-109">Dodaj klauzulę `Implements` na końcu instrukcji `Function` lub `Sub`.</span><span class="sxs-lookup"><span data-stu-id="191d7-109">Add an `Implements` clause to the end of the `Function` or `Sub` statement.</span></span> <span data-ttu-id="191d7-110">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="191d7-110">For example:</span></span>  
  
    ```vb  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="191d7-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="191d7-111">See also</span></span>

- [<span data-ttu-id="191d7-112">Implements, instrukcja</span><span class="sxs-lookup"><span data-stu-id="191d7-112">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
- [<span data-ttu-id="191d7-113">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="191d7-113">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
