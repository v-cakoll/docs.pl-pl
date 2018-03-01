---
title: "&#39; &lt;typename&gt;&#39; nie może dziedziczyć po &lt;typu&gt; &#39;&lt; basetypename&gt;&#39; ponieważ rozszerza on dostęp podstawowego &lt;typu&gt; poza zestaw"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d01981d3136968ae2534539b8eccab4c5c535fbc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="39lttypenamegt39-cannot-inherit-from-lttypegt-39ltbasetypenamegt39-because-it-expands-the-access-of-the-base-lttypegt-outside-the-assembly"></a><span data-ttu-id="da487-102">&#39; &lt;typename&gt;&#39; nie może dziedziczyć po &lt;typu&gt; &#39;&lt; basetypename&gt;&#39; ponieważ rozszerza on dostęp podstawowego &lt;typu&gt; poza zestaw</span><span class="sxs-lookup"><span data-stu-id="da487-102">&#39;&lt;typename&gt;&#39; cannot inherit from &lt;type&gt; &#39;&lt;basetypename&gt;&#39; because it expands the access of the base &lt;type&gt; outside the assembly</span></span>
<span data-ttu-id="da487-103">Klasy lub interfejsu dziedziczy z klasy podstawowej lub interfejsu, ale ma mniej restrykcyjną poziom dostępu.</span><span class="sxs-lookup"><span data-stu-id="da487-103">A class or interface inherits from a base class or interface but has a less restrictive access level.</span></span>  
  
 <span data-ttu-id="da487-104">Na przykład `Public` dziedziczy interfejs `Friend` interfejsu, lub `Protected` klasa dziedziczy `Private` klasy.</span><span class="sxs-lookup"><span data-stu-id="da487-104">For example, a `Public` interface inherits from a `Friend` interface, or a `Protected` class inherits from a `Private` class.</span></span> <span data-ttu-id="da487-105">Udostępnia to klasy podstawowej lub interfejsu dostępu poza poziomem przeznaczone do.</span><span class="sxs-lookup"><span data-stu-id="da487-105">This exposes the base class or interface to access beyond the intended level.</span></span>  
  
 <span data-ttu-id="da487-106">**Identyfikator błędu:** BC30910</span><span class="sxs-lookup"><span data-stu-id="da487-106">**Error ID:** BC30910</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="da487-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="da487-107">To correct this error</span></span>  
  
-   <span data-ttu-id="da487-108">Zmień poziom dostępu do klasy pochodnej lub interfejsu się co najmniej stosować jak największe restrykcje klasy podstawowej lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="da487-108">Change the access level of the derived class or interface to be at least as restrictive as that of the base class or interface.</span></span>  
  
     <span data-ttu-id="da487-109">—lub—</span><span class="sxs-lookup"><span data-stu-id="da487-109">-or-</span></span>  
  
-   <span data-ttu-id="da487-110">Jeśli potrzebujesz poziom dostępu mniej restrykcyjny, Usuń `Inherits` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="da487-110">If you require the less restrictive access level, remove the `Inherits` statement.</span></span> <span data-ttu-id="da487-111">Nie można dziedziczyć bardziej ograniczony w klasie podstawowej lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="da487-111">You cannot inherit from a more restricted base class or interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da487-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="da487-112">See Also</span></span>  
 [<span data-ttu-id="da487-113">Class — instrukcja</span><span class="sxs-lookup"><span data-stu-id="da487-113">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
 [<span data-ttu-id="da487-114">Interface — instrukcja</span><span class="sxs-lookup"><span data-stu-id="da487-114">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [<span data-ttu-id="da487-115">Inherits — instrukcja</span><span class="sxs-lookup"><span data-stu-id="da487-115">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [<span data-ttu-id="da487-116">Poziomy dostępu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="da487-116">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
