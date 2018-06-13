---
title: '&#39;&lt;słowo kluczowe&gt; &#39; jest prawidłowy tylko wewnątrz metody wystąpienia'
ms.date: 07/20/2015
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
ms.openlocfilehash: 2d9e26aa7dccf1b9c6390a20a59b10a0d248969d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586363"
---
# <a name="39ltkeywordgt39-is-valid-only-within-an-instance-method"></a><span data-ttu-id="1d9be-102">&#39;&lt;słowo kluczowe&gt; &#39; jest prawidłowy tylko wewnątrz metody wystąpienia</span><span class="sxs-lookup"><span data-stu-id="1d9be-102">&#39;&lt;keyword&gt;&#39; is valid only within an instance method</span></span>
<span data-ttu-id="1d9be-103">`Me`, `MyClass`, I `MyBase` słowa kluczowe odwoływać się do wystąpień określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="1d9be-103">The `Me`, `MyClass`, and `MyBase` keywords refer to specific class instances.</span></span> <span data-ttu-id="1d9be-104">Nie można ich używać w udostępnionej `Function` lub `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="1d9be-104">You cannot use them inside a shared `Function` or `Sub` procedure.</span></span>  
  
 <span data-ttu-id="1d9be-105">**Identyfikator błędu:** BC30043</span><span class="sxs-lookup"><span data-stu-id="1d9be-105">**Error ID:** BC30043</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1d9be-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="1d9be-106">To correct this error</span></span>  
  
-   <span data-ttu-id="1d9be-107">Usuń słowo kluczowe z procedury lub usuń `Shared` — słowo kluczowe z deklaracji procedury.</span><span class="sxs-lookup"><span data-stu-id="1d9be-107">Remove the keyword from the procedure, or remove the `Shared` keyword from the procedure declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d9be-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1d9be-108">See Also</span></span>  
 [<span data-ttu-id="1d9be-109">Przypisanie zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="1d9be-109">Object Variable Assignment</span></span>](../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [<span data-ttu-id="1d9be-110">Me, My, MyBase i MyClass</span><span class="sxs-lookup"><span data-stu-id="1d9be-110">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [<span data-ttu-id="1d9be-111">Podstawowe informacje o dziedziczeniu</span><span class="sxs-lookup"><span data-stu-id="1d9be-111">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
