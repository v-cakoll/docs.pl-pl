---
title: 'Instrukcje: Odwoływanie się do bieżącego wystąpienia obiektu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances [Visual Basic], referring to current
- current instance
- object variables [Visual Basic]
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
ms.openlocfilehash: d166ce62a2bb0522d1ca7011aeff7afe076c2d8e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54542200"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a><span data-ttu-id="4c9e4-102">Instrukcje: Odwoływanie się do bieżącego wystąpienia obiektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c9e4-102">How to: Refer to the Current Instance of an Object (Visual Basic)</span></span>
<span data-ttu-id="4c9e4-103">*Bieżącego wystąpienia* obiektu zasady jest wystąpienie, w którym aktualnie wykonuje kod.</span><span class="sxs-lookup"><span data-stu-id="4c9e4-103">The *current instance* of an object is the instance in which the code is currently executing.</span></span>  
  
 <span data-ttu-id="4c9e4-104">Możesz użyć `Me` — słowo kluczowe do odwoływania się do bieżącego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="4c9e4-104">You use the `Me` keyword to refer to the current instance.</span></span>  
  
### <a name="to-refer-to-the-current-instance"></a><span data-ttu-id="4c9e4-105">Aby odwołać się do bieżącego wystąpienia</span><span class="sxs-lookup"><span data-stu-id="4c9e4-105">To refer to the current instance</span></span>  
  
-   <span data-ttu-id="4c9e4-106">Użyj `Me` — słowo kluczowe, których nazwa zmiennej obiektu zwykle są używane.</span><span class="sxs-lookup"><span data-stu-id="4c9e4-106">Use the `Me` keyword where you would normally use the name of an object variable.</span></span>  
  
    ```  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     <span data-ttu-id="4c9e4-107">Mimo że `Me` zachowuje się jak obiekt zmiennej, nie można zadeklarować ją lub przypisać niczego do niej.</span><span class="sxs-lookup"><span data-stu-id="4c9e4-107">Although `Me` behaves like an object variable, you cannot declare it or assign anything to it.</span></span> <span data-ttu-id="4c9e4-108">`Me` zawsze odwołuje się do bieżącego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="4c9e4-108">`Me` always refers to the current instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c9e4-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4c9e4-109">See also</span></span>
- [<span data-ttu-id="4c9e4-110">Zmienne obiektów</span><span class="sxs-lookup"><span data-stu-id="4c9e4-110">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="4c9e4-111">Przypisanie zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="4c9e4-111">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="4c9e4-112">Me, My, MyBase i MyClass</span><span class="sxs-lookup"><span data-stu-id="4c9e4-112">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
