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
ms.openlocfilehash: 6c216dbc59bcad7a9f24bb01f856c3d29c288dbb
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005653"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a><span data-ttu-id="1d8ab-102">Porady: odwoływanie się do bieżącego wystąpienia obiektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d8ab-102">How to: Refer to the Current Instance of an Object (Visual Basic)</span></span>
<span data-ttu-id="1d8ab-103">*Bieżące wystąpienie* obiektu to wystąpienie, w którym kod jest aktualnie wykonywany.</span><span class="sxs-lookup"><span data-stu-id="1d8ab-103">The *current instance* of an object is the instance in which the code is currently executing.</span></span>  
  
 <span data-ttu-id="1d8ab-104">Użyj słowa kluczowego `Me`, aby odwołać się do bieżącego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="1d8ab-104">You use the `Me` keyword to refer to the current instance.</span></span>  
  
### <a name="to-refer-to-the-current-instance"></a><span data-ttu-id="1d8ab-105">Aby odwołać się do bieżącego wystąpienia</span><span class="sxs-lookup"><span data-stu-id="1d8ab-105">To refer to the current instance</span></span>  
  
- <span data-ttu-id="1d8ab-106">Użyj słowa kluczowego `Me`, gdzie normalnie używasz nazwy zmiennej obiektu.</span><span class="sxs-lookup"><span data-stu-id="1d8ab-106">Use the `Me` keyword where you would normally use the name of an object variable.</span></span>  
  
    ```vb  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     <span data-ttu-id="1d8ab-107">Chociaż `Me` zachowuje się jak zmienna obiektu, nie można jej zadeklarować ani przypisać do niej niczego.</span><span class="sxs-lookup"><span data-stu-id="1d8ab-107">Although `Me` behaves like an object variable, you cannot declare it or assign anything to it.</span></span> <span data-ttu-id="1d8ab-108">`Me` zawsze odwołuje się do bieżącego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="1d8ab-108">`Me` always refers to the current instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d8ab-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1d8ab-109">See also</span></span>

- [<span data-ttu-id="1d8ab-110">Zmienne obiektów</span><span class="sxs-lookup"><span data-stu-id="1d8ab-110">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="1d8ab-111">Przypisanie zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="1d8ab-111">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="1d8ab-112">Me, My, MyBase i MyClass</span><span class="sxs-lookup"><span data-stu-id="1d8ab-112">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
