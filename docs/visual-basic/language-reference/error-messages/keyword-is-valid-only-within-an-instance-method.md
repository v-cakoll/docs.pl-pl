---
title: Element „<keyword>” jest prawidłowy tylko wewnątrz metody wystąpienia
ms.date: 07/20/2015
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
ms.openlocfilehash: 5ff82b932f9bea4c7fd087651e34277ef94bc27c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58820723"
---
# <a name="keyword-is-valid-only-within-an-instance-method"></a><span data-ttu-id="6f977-102">"\<— słowo kluczowe >" jest prawidłowy tylko wewnątrz metody wystąpienia</span><span class="sxs-lookup"><span data-stu-id="6f977-102">'\<keyword>' is valid only within an instance method</span></span>
<span data-ttu-id="6f977-103">`Me`, `MyClass`, I `MyBase` słów kluczowych, zapoznaj się z wystąpieniami określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="6f977-103">The `Me`, `MyClass`, and `MyBase` keywords refer to specific class instances.</span></span> <span data-ttu-id="6f977-104">Nie można ich używać w udostępnionej `Function` lub `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="6f977-104">You cannot use them inside a shared `Function` or `Sub` procedure.</span></span>  
  
 <span data-ttu-id="6f977-105">**Identyfikator błędu:** BC30043</span><span class="sxs-lookup"><span data-stu-id="6f977-105">**Error ID:** BC30043</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6f977-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="6f977-106">To correct this error</span></span>  
  
-   <span data-ttu-id="6f977-107">Usuń słowo kluczowe z procedury lub usunąć `Shared` słowo kluczowe z deklaracja procedury.</span><span class="sxs-lookup"><span data-stu-id="6f977-107">Remove the keyword from the procedure, or remove the `Shared` keyword from the procedure declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f977-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6f977-108">See also</span></span>

- [<span data-ttu-id="6f977-109">Przypisanie zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="6f977-109">Object Variable Assignment</span></span>](../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="6f977-110">Me, My, MyBase i MyClass</span><span class="sxs-lookup"><span data-stu-id="6f977-110">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="6f977-111">Podstawowe informacje o dziedziczeniu</span><span class="sxs-lookup"><span data-stu-id="6f977-111">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
