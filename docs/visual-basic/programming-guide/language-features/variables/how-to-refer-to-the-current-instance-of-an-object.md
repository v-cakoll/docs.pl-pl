---
title: 'Porady: odwoływanie się do bieżącego wystąpienia obiektu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances [Visual Basic], referring to current
- current instance
- object variables [Visual Basic]
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
ms.openlocfilehash: c1b79f1b6a9768941d6fe966c5b5886ea742f808
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a><span data-ttu-id="25cb7-102">Porady: odwoływanie się do bieżącego wystąpienia obiektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="25cb7-102">How to: Refer to the Current Instance of an Object (Visual Basic)</span></span>
<span data-ttu-id="25cb7-103">*Bieżącego wystąpienia* obiektu jest wystąpienie, w którym kod jest aktualnie wykonywany.</span><span class="sxs-lookup"><span data-stu-id="25cb7-103">The *current instance* of an object is the instance in which the code is currently executing.</span></span>  
  
 <span data-ttu-id="25cb7-104">Możesz użyć `Me` — słowo kluczowe do odwoływania się do bieżącego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="25cb7-104">You use the `Me` keyword to refer to the current instance.</span></span>  
  
### <a name="to-refer-to-the-current-instance"></a><span data-ttu-id="25cb7-105">Aby odwołać się do bieżącego wystąpienia</span><span class="sxs-lookup"><span data-stu-id="25cb7-105">To refer to the current instance</span></span>  
  
-   <span data-ttu-id="25cb7-106">Użyj `Me` — słowo kluczowe zwykle użycia nazwę zmiennej obiektu.</span><span class="sxs-lookup"><span data-stu-id="25cb7-106">Use the `Me` keyword where you would normally use the name of an object variable.</span></span>  
  
    ```  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     <span data-ttu-id="25cb7-107">Mimo że `Me` zachowuje się jak obiekt zmiennej, nie można zadeklarować go lub niczego przypisać do niej.</span><span class="sxs-lookup"><span data-stu-id="25cb7-107">Although `Me` behaves like an object variable, you cannot declare it or assign anything to it.</span></span> <span data-ttu-id="25cb7-108">`Me` zawsze odwołuje się do bieżącego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="25cb7-108">`Me` always refers to the current instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25cb7-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="25cb7-109">See Also</span></span>  
 [<span data-ttu-id="25cb7-110">Zmienne obiektów</span><span class="sxs-lookup"><span data-stu-id="25cb7-110">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="25cb7-111">Przypisanie zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="25cb7-111">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [<span data-ttu-id="25cb7-112">Me, My, MyBase i MyClass</span><span class="sxs-lookup"><span data-stu-id="25cb7-112">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
