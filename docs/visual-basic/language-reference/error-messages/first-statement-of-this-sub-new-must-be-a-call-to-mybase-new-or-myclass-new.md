---
title: "Pierwsza instrukcja tego &#39; Sub nowy &#39; musi być wywołanie &#39; MyBase.New &#39; i &#39; MyClass.New &#39; (Brak dostępnych konstruktora bez parametrów)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30148
- vbc30148
helpviewer_keywords: BC30148
ms.assetid: 4426e8fc-cb39-4eb8-ba95-503cd32fcc89
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1065643e1f6c868092fbad839af0dbbd33afaf01
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="first-statement-of-this-39sub-new39-must-be-a-call-to-39mybasenew39-or-39myclassnew39-no-accessible-constructor-without-parameters"></a><span data-ttu-id="4c106-102">Pierwsza instrukcja tego &#39; Sub nowy &#39; musi być wywołanie &#39; MyBase.New &#39; i &#39; MyClass.New &#39; (Brak dostępnych konstruktora bez parametrów)</span><span class="sxs-lookup"><span data-stu-id="4c106-102">First statement of this &#39;Sub New&#39; must be a call to &#39;MyBase.New&#39; or &#39;MyClass.New&#39; (No Accessible Constructor Without Parameters)</span></span>
<span data-ttu-id="4c106-103">Pierwsza instrukcja tego elementu "Sub New" musi być wywołanie "MyBase.New" lub "MyClass.New", ponieważ klasa podstawowa\<nazwę bazową > "z"\<derivedname > "nie ma dostępnego elementu"Sub New", który można wywołać bez argumentów.</span><span class="sxs-lookup"><span data-stu-id="4c106-103">First statement of this 'Sub New' must be a call to 'MyBase.New' or 'MyClass.New' because base class '\<basename>' of '\<derivedname>' does not have an accessible 'Sub New' that can be called with no arguments.</span></span>  
  
 <span data-ttu-id="4c106-104">W klasie pochodnej, co konstruktor musi wywoływać konstruktora klasy podstawowej (`MyBase.New`).</span><span class="sxs-lookup"><span data-stu-id="4c106-104">In a derived class, every constructor must call a base class constructor (`MyBase.New`).</span></span> <span data-ttu-id="4c106-105">Jeśli klasa podstawowa ma konstruktora bez parametrów, który jest dostępny dla klas pochodnych `MyBase.New` wywoływana automatycznie.</span><span class="sxs-lookup"><span data-stu-id="4c106-105">If the base class has a constructor with no parameters that is accessible to derived classes, `MyBase.New` can be called automatically.</span></span> <span data-ttu-id="4c106-106">Jeśli nie, konstruktora klasy podstawowej musi zostać wywołana z parametrami, a nie jest to możliwe automatycznie.</span><span class="sxs-lookup"><span data-stu-id="4c106-106">If not, a base class constructor must be called with parameters, and this cannot be done automatically.</span></span> <span data-ttu-id="4c106-107">W takim przypadku pierwsza instrukcja każdej konstruktora klasy pochodnej musi wywołać sparametryzowane konstruktora dla klasy podstawowej, lub zadzwoń innego konstruktora w klasie pochodnej, która sprawia, że wywołanie konstruktora klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="4c106-107">In this case, the first statement of every derived class constructor must call a parameterized constructor on the base class, or call another constructor in the derived class that makes a base class constructor call.</span></span>  
  
 <span data-ttu-id="4c106-108">**Identyfikator błędu:** BC30148</span><span class="sxs-lookup"><span data-stu-id="4c106-108">**Error ID:** BC30148</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4c106-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="4c106-109">To correct this error</span></span>  
  
-   <span data-ttu-id="4c106-110">Albo wywołanie `MyBase.New` dostarczanie wymagane parametry lub wywołać konstruktora elementu równorzędnego, który nawiązuje takie połączenie.</span><span class="sxs-lookup"><span data-stu-id="4c106-110">Either call `MyBase.New` supplying the required parameters, or call a peer constructor that makes such a call.</span></span>  
  
     <span data-ttu-id="4c106-111">Na przykład, jeśli klasa podstawowa ma konstruktora, który jest zadeklarowany jako `Public Sub New(ByVal index as Integer)`, pierwsza instrukcja w pochodnej konstruktora klasy może być `MyBase.New(100)`.</span><span class="sxs-lookup"><span data-stu-id="4c106-111">For example, if the base class has a constructor that’s declared as `Public Sub New(ByVal index as Integer)`, the first statement in the derived class constructor might be `MyBase.New(100)`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c106-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4c106-112">See Also</span></span>  
 [<span data-ttu-id="4c106-113">Podstawowe informacje o dziedziczeniu</span><span class="sxs-lookup"><span data-stu-id="4c106-113">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
