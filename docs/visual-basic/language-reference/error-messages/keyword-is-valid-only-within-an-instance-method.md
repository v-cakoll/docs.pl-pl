---
title: Element „<keyword>” jest prawidłowy tylko wewnątrz metody wystąpienia
ms.date: 07/20/2015
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
ms.openlocfilehash: af3bc95e2db88577c7c53e4b58fb60aed8a83453
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55267654"
---
# <a name="keyword-is-valid-only-within-an-instance-method"></a><span data-ttu-id="70b71-102">"\<— słowo kluczowe >" jest prawidłowy tylko wewnątrz metody wystąpienia</span><span class="sxs-lookup"><span data-stu-id="70b71-102">'\<keyword>' is valid only within an instance method</span></span>
<span data-ttu-id="70b71-103">`Me`, `MyClass`, I `MyBase` słów kluczowych, zapoznaj się z wystąpieniami określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="70b71-103">The `Me`, `MyClass`, and `MyBase` keywords refer to specific class instances.</span></span> <span data-ttu-id="70b71-104">Nie można ich używać w udostępnionej `Function` lub `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="70b71-104">You cannot use them inside a shared `Function` or `Sub` procedure.</span></span>  
  
 <span data-ttu-id="70b71-105">**Identyfikator błędu:** BC30043</span><span class="sxs-lookup"><span data-stu-id="70b71-105">**Error ID:** BC30043</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="70b71-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="70b71-106">To correct this error</span></span>  
  
-   <span data-ttu-id="70b71-107">Usuń słowo kluczowe z procedury lub usunąć `Shared` słowo kluczowe z deklaracja procedury.</span><span class="sxs-lookup"><span data-stu-id="70b71-107">Remove the keyword from the procedure, or remove the `Shared` keyword from the procedure declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70b71-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="70b71-108">See also</span></span>
- [<span data-ttu-id="70b71-109">Przypisanie zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="70b71-109">Object Variable Assignment</span></span>](../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="70b71-110">Me, My, MyBase i MyClass</span><span class="sxs-lookup"><span data-stu-id="70b71-110">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="70b71-111">Podstawowe informacje o dziedziczeniu</span><span class="sxs-lookup"><span data-stu-id="70b71-111">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
