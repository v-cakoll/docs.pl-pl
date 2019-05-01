---
title: Nie można wywołać funkcji zaprzyjaźnionej dla obiektu, który nie jest wystąpieniem klasy definiującej
ms.date: 07/20/2015
f1_keywords:
- vbrID97
ms.assetid: b9d821f0-8565-4f15-bb35-184789c69662
ms.openlocfilehash: c65bbb5028cf042b702bb2b8336d40512c980790
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61912694"
---
# <a name="cannot-call-friend-function-on-object-which-is-not-an-instance-of-defining-class"></a><span data-ttu-id="abe0a-102">Nie można wywołać funkcji zaprzyjaźnionej dla obiektu, który nie jest wystąpieniem klasy definiującej</span><span class="sxs-lookup"><span data-stu-id="abe0a-102">Cannot call friend function on object which is not an instance of defining class</span></span>
<span data-ttu-id="abe0a-103">Albo próbowaliśmy połączyć się z `Friend` procedury klasy lub użytkownik próbował uzyskać dostęp do `Friend` właściwość lub metoda między procesami lub między wątkami.</span><span class="sxs-lookup"><span data-stu-id="abe0a-103">Either you tried to call the `Friend` procedure of a class, or you tried to access a `Friend` property or method either cross-process or cross-thread.</span></span> <span data-ttu-id="abe0a-104">A `Friend` procedura jest wywoływane z modułu poza klasą, ale jest częścią projektu, w którym klasa jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="abe0a-104">A `Friend` procedure is callable from a module outside the class, but is part of the project in which the class is defined.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="abe0a-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="abe0a-105">To correct this error</span></span>  
  
- <span data-ttu-id="abe0a-106">Upewnij się, że podczas wywoływania lub uzyskiwania dostępu do procedury z modułu, który jest częścią projektu, w którym zdefiniowano klasy.</span><span class="sxs-lookup"><span data-stu-id="abe0a-106">Ensure that you are calling or accessing the procedure from a module that is part of the project in which the class is defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abe0a-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="abe0a-107">See also</span></span>

- [<span data-ttu-id="abe0a-108">Friend</span><span class="sxs-lookup"><span data-stu-id="abe0a-108">Friend</span></span>](../../visual-basic/language-reference/modifiers/friend.md)
