---
title: Oczekiwano inicjatora
ms.date: 07/20/2015
f1_keywords:
- vbc30996
- bc30996
helpviewer_keywords:
- BC30996
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
ms.openlocfilehash: 0795fdc1c4b177e13979d7555cd7588217b8cb4c
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59334968"
---
# <a name="initializer-expected"></a><span data-ttu-id="bf932-102">Oczekiwano inicjatora</span><span class="sxs-lookup"><span data-stu-id="bf932-102">Initializer expected</span></span>
<span data-ttu-id="bf932-103">Próbowano deklarować wystąpienia klasy za pomocą inicjatora obiektów, w którym listy inicjowania jest pusta, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="bf932-103">You have tried to declare an instance of a class by using an object initializer in which the initialization list is empty, as shown in the following example.</span></span>  
  
 `' Not valid.`  
  
 `' Dim aStudent As New Student With {}`  
  
 <span data-ttu-id="bf932-104">Co najmniej jedno pole lub właściwość musi być zainicjowany na liście inicjatora, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="bf932-104">At least one field or property must be initialized in the initializer list, as shown in the following example.</span></span>  
  
 `Dim aStudent As New Student With {.year = "Senior"}`  
  
 <span data-ttu-id="bf932-105">**Identyfikator błędu:** BC30996</span><span class="sxs-lookup"><span data-stu-id="bf932-105">**Error ID:** BC30996</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bf932-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="bf932-106">To correct this error</span></span>  
  
1. <span data-ttu-id="bf932-107">Inicjowanie co najmniej jednego pola lub właściwości w inicjatorze lub nie należy używać inicjatora obiektów.</span><span class="sxs-lookup"><span data-stu-id="bf932-107">Initialize at least one field or property in the initializer, or do not use an object initializer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf932-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bf932-108">See also</span></span>

- [<span data-ttu-id="bf932-109">Inicjatory obiektów: Typy nazwane i anonimowe</span><span class="sxs-lookup"><span data-stu-id="bf932-109">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="bf932-110">Instrukcje: Deklarowanie obiektu za pomocą inicjatora obiektów</span><span class="sxs-lookup"><span data-stu-id="bf932-110">How to: Declare an Object by Using an Object Initializer</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
