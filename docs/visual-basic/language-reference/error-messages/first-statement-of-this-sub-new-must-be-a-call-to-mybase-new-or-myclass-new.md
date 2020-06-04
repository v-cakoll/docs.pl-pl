---
title: Pierwsza instrukcja tego elementu „Sub New” musi być wywołaniem do „MyBase.New” lub „MyClass.New” (Nie jest dostępny żaden konstruktor bez parametrów)
ms.date: 07/20/2015
f1_keywords:
- bc30148
- vbc30148
helpviewer_keywords:
- BC30148
ms.assetid: 4426e8fc-cb39-4eb8-ba95-503cd32fcc89
ms.openlocfilehash: 2b9d2568fb64e4af72733ad1f3dee58aaee650e5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402982"
---
# <a name="first-statement-of-this-sub-new-must-be-a-call-to-mybasenew-or-myclassnew-no-accessible-constructor-without-parameters"></a><span data-ttu-id="da4a6-102">Pierwsza instrukcja tego elementu „Sub New” musi być wywołaniem do „MyBase.New” lub „MyClass.New” (Nie jest dostępny żaden konstruktor bez parametrów)</span><span class="sxs-lookup"><span data-stu-id="da4a6-102">First statement of this 'Sub New' must be a call to 'MyBase.New' or 'MyClass.New' (No Accessible Constructor Without Parameters)</span></span>
<span data-ttu-id="da4a6-103">Pierwsza instrukcja tego elementu "Sub New" musi być wywołaniem elementu "MyBase. New" lub "MyClass. New", ponieważ klasa bazowa " \<basename> " z " \<derivedname> " nie ma dostępnego elementu "Sub New", który można wywołać bez argumentów.</span><span class="sxs-lookup"><span data-stu-id="da4a6-103">First statement of this 'Sub New' must be a call to 'MyBase.New' or 'MyClass.New' because base class '\<basename>' of '\<derivedname>' does not have an accessible 'Sub New' that can be called with no arguments.</span></span>  
  
 <span data-ttu-id="da4a6-104">W klasie pochodnej każdy Konstruktor musi wywołać konstruktora klasy bazowej ( `MyBase.New` ).</span><span class="sxs-lookup"><span data-stu-id="da4a6-104">In a derived class, every constructor must call a base class constructor (`MyBase.New`).</span></span> <span data-ttu-id="da4a6-105">Jeśli klasa bazowa ma konstruktora bez parametrów, które są dostępne dla klas pochodnych, `MyBase.New` może być wywoływana automatycznie.</span><span class="sxs-lookup"><span data-stu-id="da4a6-105">If the base class has a constructor with no parameters that is accessible to derived classes, `MyBase.New` can be called automatically.</span></span> <span data-ttu-id="da4a6-106">Jeśli nie, Konstruktor klasy bazowej musi być wywołany z parametrami i nie można wykonać tej operacji automatycznie.</span><span class="sxs-lookup"><span data-stu-id="da4a6-106">If not, a base class constructor must be called with parameters, and this cannot be done automatically.</span></span> <span data-ttu-id="da4a6-107">W takim przypadku pierwsza instrukcja każdego pochodnego konstruktora klasy musi wywołać sparametryzowany Konstruktor w klasie bazowej lub wywołać innego konstruktora w klasie pochodnej, która tworzy wywołanie konstruktora klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="da4a6-107">In this case, the first statement of every derived class constructor must call a parameterized constructor on the base class, or call another constructor in the derived class that makes a base class constructor call.</span></span>  
  
 <span data-ttu-id="da4a6-108">**Identyfikator błędu:** BC30148</span><span class="sxs-lookup"><span data-stu-id="da4a6-108">**Error ID:** BC30148</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="da4a6-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="da4a6-109">To correct this error</span></span>  
  
- <span data-ttu-id="da4a6-110">Wywołanie `MyBase.New` podawania wymaganych parametrów lub wywołanie konstruktora równorzędnego, który wykonuje takie wywołanie.</span><span class="sxs-lookup"><span data-stu-id="da4a6-110">Either call `MyBase.New` supplying the required parameters, or call a peer constructor that makes such a call.</span></span>  
  
     <span data-ttu-id="da4a6-111">Na przykład jeśli klasa bazowa ma Konstruktor, który jest zadeklarowany jako `Public Sub New(ByVal index as Integer)` , pierwsza instrukcja w konstruktorze klasy pochodnej może być `MyBase.New(100)` .</span><span class="sxs-lookup"><span data-stu-id="da4a6-111">For example, if the base class has a constructor that’s declared as `Public Sub New(ByVal index as Integer)`, the first statement in the derived class constructor might be `MyBase.New(100)`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da4a6-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="da4a6-112">See also</span></span>

- [<span data-ttu-id="da4a6-113">Podstawowe informacje o dziedziczeniu</span><span class="sxs-lookup"><span data-stu-id="da4a6-113">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
