---
title: Nie można wywołać funkcji zaprzyjaźnionej dla obiektu, który nie jest wystąpieniem klasy definiującej
ms.date: 07/20/2015
f1_keywords:
- vbrID97
ms.assetid: b9d821f0-8565-4f15-bb35-184789c69662
ms.openlocfilehash: c18c04470c4c49113e8195b92185326c5c4197c1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400851"
---
# <a name="cannot-call-friend-function-on-object-which-is-not-an-instance-of-defining-class"></a><span data-ttu-id="2d62b-102">Nie można wywołać funkcji zaprzyjaźnionej dla obiektu, który nie jest wystąpieniem klasy definiującej</span><span class="sxs-lookup"><span data-stu-id="2d62b-102">Cannot call friend function on object which is not an instance of defining class</span></span>
<span data-ttu-id="2d62b-103">Podjęto próbę wywołania `Friend` procedury klasy lub nastąpiła próba uzyskania dostępu do `Friend` właściwości lub metody albo dla wielu wątków.</span><span class="sxs-lookup"><span data-stu-id="2d62b-103">Either you tried to call the `Friend` procedure of a class, or you tried to access a `Friend` property or method either cross-process or cross-thread.</span></span> <span data-ttu-id="2d62b-104">`Friend`Procedura jest wywoływana z modułu poza klasą, ale jest częścią projektu, w którym jest zdefiniowana Klasa.</span><span class="sxs-lookup"><span data-stu-id="2d62b-104">A `Friend` procedure is callable from a module outside the class, but is part of the project in which the class is defined.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2d62b-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="2d62b-105">To correct this error</span></span>  
  
- <span data-ttu-id="2d62b-106">Upewnij się, że wywołujesz lub uzyskujesz dostęp do procedury z modułu, który jest częścią projektu, w którym zdefiniowano klasę.</span><span class="sxs-lookup"><span data-stu-id="2d62b-106">Ensure that you are calling or accessing the procedure from a module that is part of the project in which the class is defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d62b-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d62b-107">See also</span></span>

- [<span data-ttu-id="2d62b-108">Osoby</span><span class="sxs-lookup"><span data-stu-id="2d62b-108">Friend</span></span>](../language-reference/modifiers/friend.md)
