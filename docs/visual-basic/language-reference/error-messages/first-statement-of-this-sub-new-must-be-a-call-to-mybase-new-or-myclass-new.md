---
title: Pierwsza instrukcja tego &#39;Sub New&#39; musi być wywołaniem do &#39;MyBase.New&#39; lub &#39;MyClass.New&#39; (nie jest dostępny konstruktor bez parametrów)
ms.date: 07/20/2015
f1_keywords:
- bc30148
- vbc30148
helpviewer_keywords:
- BC30148
ms.assetid: 4426e8fc-cb39-4eb8-ba95-503cd32fcc89
ms.openlocfilehash: 75832ae88908094c1cb74ce04ad84c0d2ae91e68
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54728898"
---
# <a name="first-statement-of-this-39sub-new39-must-be-a-call-to-39mybasenew39-or-39myclassnew39-no-accessible-constructor-without-parameters"></a><span data-ttu-id="c89b2-102">Pierwsza instrukcja tego &#39;Sub New&#39; musi być wywołaniem do &#39;MyBase.New&#39; lub &#39;MyClass.New&#39; (nie jest dostępny konstruktor bez parametrów)</span><span class="sxs-lookup"><span data-stu-id="c89b2-102">First statement of this &#39;Sub New&#39; must be a call to &#39;MyBase.New&#39; or &#39;MyClass.New&#39; (No Accessible Constructor Without Parameters)</span></span>
<span data-ttu-id="c89b2-103">Pierwsza instrukcja tego elementu "Sub New" musi być wywołaniem elementu "MyBase.New" lub "MyClass.New", ponieważ klasy bazowej\<basename > "z"\<derivedname > "nie ma dostępnego elementu"Sub New", który można wywołać bez argumentów.</span><span class="sxs-lookup"><span data-stu-id="c89b2-103">First statement of this 'Sub New' must be a call to 'MyBase.New' or 'MyClass.New' because base class '\<basename>' of '\<derivedname>' does not have an accessible 'Sub New' that can be called with no arguments.</span></span>  
  
 <span data-ttu-id="c89b2-104">W klasie pochodnej, co konstruktor musi wywołać konstruktora klasy bazowej (`MyBase.New`).</span><span class="sxs-lookup"><span data-stu-id="c89b2-104">In a derived class, every constructor must call a base class constructor (`MyBase.New`).</span></span> <span data-ttu-id="c89b2-105">Jeśli klasa bazowa ma konstruktora bez parametrów, który jest dostępny dla klasy pochodnej `MyBase.New` zostaje wywołana automatycznie.</span><span class="sxs-lookup"><span data-stu-id="c89b2-105">If the base class has a constructor with no parameters that is accessible to derived classes, `MyBase.New` can be called automatically.</span></span> <span data-ttu-id="c89b2-106">W przeciwnym razie konstruktora klasy bazowej, musi zostać wywołana z parametrami, a nie można tego zrobić automatycznie.</span><span class="sxs-lookup"><span data-stu-id="c89b2-106">If not, a base class constructor must be called with parameters, and this cannot be done automatically.</span></span> <span data-ttu-id="c89b2-107">W takim przypadku pierwsza instrukcja każdej konstruktora klasy pochodnej musi wywołania sparametryzowanego konstruktora dla klasy bazowej lub wywołanie innego konstruktora w klasie pochodnej, która sprawia, że wywołanie konstruktora klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="c89b2-107">In this case, the first statement of every derived class constructor must call a parameterized constructor on the base class, or call another constructor in the derived class that makes a base class constructor call.</span></span>  
  
 <span data-ttu-id="c89b2-108">**Identyfikator błędu:** BC30148</span><span class="sxs-lookup"><span data-stu-id="c89b2-108">**Error ID:** BC30148</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c89b2-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="c89b2-109">To correct this error</span></span>  
  
-   <span data-ttu-id="c89b2-110">Wywołać `MyBase.New` dostarczanie wymagane parametry lub wywołanie konstruktora elementu równorzędnego, który sprawia, że takie wywołania.</span><span class="sxs-lookup"><span data-stu-id="c89b2-110">Either call `MyBase.New` supplying the required parameters, or call a peer constructor that makes such a call.</span></span>  
  
     <span data-ttu-id="c89b2-111">Na przykład, jeśli klasa bazowa ma Konstruktor, który jest zadeklarowany jako `Public Sub New(ByVal index as Integer)`, pierwsza instrukcja w pochodnej konstruktora klasy może być `MyBase.New(100)`.</span><span class="sxs-lookup"><span data-stu-id="c89b2-111">For example, if the base class has a constructor that’s declared as `Public Sub New(ByVal index as Integer)`, the first statement in the derived class constructor might be `MyBase.New(100)`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c89b2-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c89b2-112">See also</span></span>
- [<span data-ttu-id="c89b2-113">Podstawowe informacje o dziedziczeniu</span><span class="sxs-lookup"><span data-stu-id="c89b2-113">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
