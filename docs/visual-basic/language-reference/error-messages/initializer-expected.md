---
title: Oczekiwano inicjatora
ms.date: 07/20/2015
f1_keywords:
- vbc30996
- bc30996
helpviewer_keywords:
- BC30996
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
ms.openlocfilehash: 9d786fd1e929129c420b7bec62efd0bd445d85eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586389"
---
# <a name="initializer-expected"></a><span data-ttu-id="cc30c-102">Oczekiwano inicjatora</span><span class="sxs-lookup"><span data-stu-id="cc30c-102">Initializer expected</span></span>
<span data-ttu-id="cc30c-103">Nastąpiła próba Zadeklaruj wystąpienie klasy za pomocą inicjatora obiektów, w którym listy inicjowania jest pusta, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="cc30c-103">You have tried to declare an instance of a class by using an object initializer in which the initialization list is empty, as shown in the following example.</span></span>  
  
 `' Not valid.`  
  
 `' Dim aStudent As New Student With {}`  
  
 <span data-ttu-id="cc30c-104">Co najmniej jedno pole lub właściwość musi być zainicjowany na liście inicjatora, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="cc30c-104">At least one field or property must be initialized in the initializer list, as shown in the following example.</span></span>  
  
 `Dim aStudent As New Student With {.year = "Senior"}`  
  
 <span data-ttu-id="cc30c-105">**Identyfikator błędu:** BC30996</span><span class="sxs-lookup"><span data-stu-id="cc30c-105">**Error ID:** BC30996</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cc30c-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="cc30c-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="cc30c-107">Inicjowanie co najmniej jednego pola lub właściwości w inicjatorze, albo nie używaj inicjatora obiektu.</span><span class="sxs-lookup"><span data-stu-id="cc30c-107">Initialize at least one field or property in the initializer, or do not use an object initializer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc30c-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cc30c-108">See Also</span></span>  
 [<span data-ttu-id="cc30c-109">Inicjatory obiektów: typy nazwane i anonimowe</span><span class="sxs-lookup"><span data-stu-id="cc30c-109">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [<span data-ttu-id="cc30c-110">Instrukcje: deklarowanie obiektu za pomocą inicjatora obiektów</span><span class="sxs-lookup"><span data-stu-id="cc30c-110">How to: Declare an Object by Using an Object Initializer</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
