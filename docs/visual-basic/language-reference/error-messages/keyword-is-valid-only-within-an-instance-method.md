---
title: "&#39; &lt;— słowo kluczowe&gt;&#39; jest prawidłowy tylko wewnątrz metody wystąpienia"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a61314c036cec0fd1412a9c844a610fbd1401add
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="39ltkeywordgt39-is-valid-only-within-an-instance-method"></a><span data-ttu-id="19a4a-102">&#39; &lt;— słowo kluczowe&gt;&#39; jest prawidłowy tylko wewnątrz metody wystąpienia</span><span class="sxs-lookup"><span data-stu-id="19a4a-102">&#39;&lt;keyword&gt;&#39; is valid only within an instance method</span></span>
<span data-ttu-id="19a4a-103">`Me`, `MyClass`, I `MyBase` słowa kluczowe odwoływać się do wystąpień określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="19a4a-103">The `Me`, `MyClass`, and `MyBase` keywords refer to specific class instances.</span></span> <span data-ttu-id="19a4a-104">Nie można ich używać w udostępnionej `Function` lub `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="19a4a-104">You cannot use them inside a shared `Function` or `Sub` procedure.</span></span>  
  
 <span data-ttu-id="19a4a-105">**Identyfikator błędu:** BC30043</span><span class="sxs-lookup"><span data-stu-id="19a4a-105">**Error ID:** BC30043</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="19a4a-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="19a4a-106">To correct this error</span></span>  
  
-   <span data-ttu-id="19a4a-107">Usuń słowo kluczowe z procedury lub usuń `Shared` — słowo kluczowe z deklaracji procedury.</span><span class="sxs-lookup"><span data-stu-id="19a4a-107">Remove the keyword from the procedure, or remove the `Shared` keyword from the procedure declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19a4a-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="19a4a-108">See Also</span></span>  
 [<span data-ttu-id="19a4a-109">Przypisanie zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="19a4a-109">Object Variable Assignment</span></span>](../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [<span data-ttu-id="19a4a-110">Me, My, MyBase i MyClass</span><span class="sxs-lookup"><span data-stu-id="19a4a-110">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [<span data-ttu-id="19a4a-111">Podstawowe informacje o dziedziczeniu</span><span class="sxs-lookup"><span data-stu-id="19a4a-111">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
