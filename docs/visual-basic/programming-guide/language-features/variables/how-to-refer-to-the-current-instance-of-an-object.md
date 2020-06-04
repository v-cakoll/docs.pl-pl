---
title: 'Porady: odwoływanie się do bieżącego wystąpienia obiektu'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances [Visual Basic], referring to current
- current instance
- object variables [Visual Basic]
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
ms.openlocfilehash: 43bfd54592fb1d26cbf7f268b7e098e01e3745d8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410428"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a><span data-ttu-id="e51aa-102">Porady: odwoływanie się do bieżącego wystąpienia obiektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e51aa-102">How to: Refer to the Current Instance of an Object (Visual Basic)</span></span>
<span data-ttu-id="e51aa-103">*Bieżące wystąpienie* obiektu to wystąpienie, w którym kod jest aktualnie wykonywany.</span><span class="sxs-lookup"><span data-stu-id="e51aa-103">The *current instance* of an object is the instance in which the code is currently executing.</span></span>  
  
 <span data-ttu-id="e51aa-104">Użyj `Me` słowa kluczowego, aby odwołać się do bieżącego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e51aa-104">You use the `Me` keyword to refer to the current instance.</span></span>  
  
### <a name="to-refer-to-the-current-instance"></a><span data-ttu-id="e51aa-105">Aby odwołać się do bieżącego wystąpienia</span><span class="sxs-lookup"><span data-stu-id="e51aa-105">To refer to the current instance</span></span>  
  
- <span data-ttu-id="e51aa-106">Użyj `Me` słowa kluczowego, gdzie normalnie używać nazwy zmiennej obiektu.</span><span class="sxs-lookup"><span data-stu-id="e51aa-106">Use the `Me` keyword where you would normally use the name of an object variable.</span></span>  
  
    ```vb  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     <span data-ttu-id="e51aa-107">Chociaż `Me` zachowuje się jak zmienna obiektu, nie można jej zadeklarować ani przypisać do niej niczego.</span><span class="sxs-lookup"><span data-stu-id="e51aa-107">Although `Me` behaves like an object variable, you cannot declare it or assign anything to it.</span></span> <span data-ttu-id="e51aa-108">`Me`zawsze odwołuje się do bieżącego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e51aa-108">`Me` always refers to the current instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e51aa-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e51aa-109">See also</span></span>

- [<span data-ttu-id="e51aa-110">Zmienne obiektów</span><span class="sxs-lookup"><span data-stu-id="e51aa-110">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="e51aa-111">Przypisanie zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="e51aa-111">Object Variable Assignment</span></span>](object-variable-assignment.md)
- [<span data-ttu-id="e51aa-112">Me, My, MyBase i MyClass</span><span class="sxs-lookup"><span data-stu-id="e51aa-112">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
