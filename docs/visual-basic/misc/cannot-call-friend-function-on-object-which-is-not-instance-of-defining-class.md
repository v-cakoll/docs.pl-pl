---
title: Nie można wywołać funkcji zaprzyjaźnionej dla obiektu, który nie jest wystąpieniem klasy definiującej
ms.date: 07/20/2015
f1_keywords:
- vbrID97
ms.assetid: b9d821f0-8565-4f15-bb35-184789c69662
ms.openlocfilehash: a655207110d512805490b693e413b1d22b0367ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cannot-call-friend-function-on-object-which-is-not-an-instance-of-defining-class"></a><span data-ttu-id="a95d1-102">Nie można wywołać funkcji zaprzyjaźnionej dla obiektu, który nie jest wystąpieniem klasy definiującej</span><span class="sxs-lookup"><span data-stu-id="a95d1-102">Cannot call friend function on object which is not an instance of defining class</span></span>
<span data-ttu-id="a95d1-103">Albo próbował wywołać `Friend` procedury klasy lub użytkownik próbował uzyskać dostęp do `Friend` właściwości lub metody międzyprocesowa lub między wątkami.</span><span class="sxs-lookup"><span data-stu-id="a95d1-103">Either you tried to call the `Friend` procedure of a class, or you tried to access a `Friend` property or method either cross-process or cross-thread.</span></span> <span data-ttu-id="a95d1-104">A `Friend` procedury z modułu poza klasą, ale jest częścią projektu, w którym klasa jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="a95d1-104">A `Friend` procedure is callable from a module outside the class, but is part of the project in which the class is defined.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a95d1-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="a95d1-105">To correct this error</span></span>  
  
-   <span data-ttu-id="a95d1-106">Upewnij się, że wywoływania lub uzyskiwania dostępu do procedury z moduł, który jest częścią projektu, w którym zdefiniowana jest klasa.</span><span class="sxs-lookup"><span data-stu-id="a95d1-106">Ensure that you are calling or accessing the procedure from a module that is part of the project in which the class is defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a95d1-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a95d1-107">See Also</span></span>  
 [<span data-ttu-id="a95d1-108">Friend</span><span class="sxs-lookup"><span data-stu-id="a95d1-108">Friend</span></span>](../../visual-basic/language-reference/modifiers/friend.md)
