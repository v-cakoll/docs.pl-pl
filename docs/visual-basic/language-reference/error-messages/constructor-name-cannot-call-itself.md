---
title: Konstruktor &#39; &lt;nazwa&gt; &#39; nie może wywołać się
ms.date: 07/20/2015
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords:
- BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
ms.openlocfilehash: 069de813a0426230e19cddf14c3b83d40a602a41
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="constructor-39ltnamegt39-cannot-call-itself"></a><span data-ttu-id="253d3-102">Konstruktor &#39; &lt;nazwa&gt; &#39; nie może wywołać się</span><span class="sxs-lookup"><span data-stu-id="253d3-102">Constructor &#39;&lt;name&gt;&#39; cannot call itself</span></span>
<span data-ttu-id="253d3-103">A `Sub New` procedury w klasie lub strukturze wywołuje sam siebie.</span><span class="sxs-lookup"><span data-stu-id="253d3-103">A `Sub New` procedure in a class or structure calls itself.</span></span>  
  
 <span data-ttu-id="253d3-104">Konstruktor ma na celu zainicjować wystąpienia klasy lub struktury przy pierwszym.</span><span class="sxs-lookup"><span data-stu-id="253d3-104">The purpose of a constructor is to initialize an instance of a class or structure when it is first created.</span></span> <span data-ttu-id="253d3-105">Klasy lub struktury może mieć kilka konstruktorów, pod warunkiem wszystkie mają listy różnych parametrów.</span><span class="sxs-lookup"><span data-stu-id="253d3-105">A class or structure can have several constructors, provided they all have different parameter lists.</span></span> <span data-ttu-id="253d3-106">Konstruktor służyć do wywoływania innego konstruktora do wykonania jego funkcje oprócz własnego.</span><span class="sxs-lookup"><span data-stu-id="253d3-106">A constructor is permitted to call another constructor to perform its functionality in addition to its own.</span></span> <span data-ttu-id="253d3-107">Ale go nie ma znaczenia dla konstruktora wywołać się, a w rzeczywistości skutkowałoby to nieskończoną rekursję Jeśli dozwolone.</span><span class="sxs-lookup"><span data-stu-id="253d3-107">But it is meaningless for a constructor to call itself, and in fact it would result in infinite recursion if permitted.</span></span>  
  
 <span data-ttu-id="253d3-108">**Identyfikator błędu:** BC30298</span><span class="sxs-lookup"><span data-stu-id="253d3-108">**Error ID:** BC30298</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="253d3-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="253d3-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="253d3-110">Zapoznaj się z listą parametrów wywoływana z konstruktora.</span><span class="sxs-lookup"><span data-stu-id="253d3-110">Check the parameter list of the constructor being called.</span></span> <span data-ttu-id="253d3-111">Należy go innym niż wywołania konstruktora.</span><span class="sxs-lookup"><span data-stu-id="253d3-111">It should be different from that of the constructor making the call.</span></span>  
  
2.  <span data-ttu-id="253d3-112">Jeśli nie zamierzasz wywołać innego konstruktora, Usuń `Sub New` wywołać całkowicie.</span><span class="sxs-lookup"><span data-stu-id="253d3-112">If you do not intend to call a different constructor, remove the `Sub New` call entirely.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="253d3-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="253d3-113">See Also</span></span>  
 [<span data-ttu-id="253d3-114">Okres istnienia obiektów: w jaki sposób obiekty są tworzone i niszczone</span><span class="sxs-lookup"><span data-stu-id="253d3-114">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
