---
title: Konstruktor „<name>” nie może wywołać sam siebie
ms.date: 07/20/2015
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords:
- BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
ms.openlocfilehash: 8459ee7fec6d761161a721c88ccdc88e513fc95f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59324386"
---
# <a name="constructor-name-cannot-call-itself"></a><span data-ttu-id="2717a-102">Konstruktor "\<name >' nie może wywołać sam siebie</span><span class="sxs-lookup"><span data-stu-id="2717a-102">Constructor '\<name>' cannot call itself</span></span>
<span data-ttu-id="2717a-103">A `Sub New` procedury w klasie lub strukturze wywołuje sam siebie.</span><span class="sxs-lookup"><span data-stu-id="2717a-103">A `Sub New` procedure in a class or structure calls itself.</span></span>  
  
 <span data-ttu-id="2717a-104">Konstruktor ma na celu zainicjować wystąpienia klasy lub struktury, gdy po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="2717a-104">The purpose of a constructor is to initialize an instance of a class or structure when it is first created.</span></span> <span data-ttu-id="2717a-105">Klasa lub struktura może mieć kilka konstruktorów, pod warunkiem, wszystkie one mają listy różnych parametrów.</span><span class="sxs-lookup"><span data-stu-id="2717a-105">A class or structure can have several constructors, provided they all have different parameter lists.</span></span> <span data-ttu-id="2717a-106">Konstruktor jest dozwolony do wywoływania innego konstruktora, przeprowadzić jego funkcje oprócz swój własny.</span><span class="sxs-lookup"><span data-stu-id="2717a-106">A constructor is permitted to call another constructor to perform its functionality in addition to its own.</span></span> <span data-ttu-id="2717a-107">Ale jest całkowicie nieprzydatna dla konstruktora wywołać sam siebie, a w rzeczywistości spowoduje to nieskończoną rekursję Jeśli dozwolone.</span><span class="sxs-lookup"><span data-stu-id="2717a-107">But it is meaningless for a constructor to call itself, and in fact it would result in infinite recursion if permitted.</span></span>  
  
 <span data-ttu-id="2717a-108">**Identyfikator błędu:** BC30298</span><span class="sxs-lookup"><span data-stu-id="2717a-108">**Error ID:** BC30298</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2717a-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="2717a-109">To correct this error</span></span>  
  
1. <span data-ttu-id="2717a-110">Sprawdź listę parametrów konstruktora wywoływanego.</span><span class="sxs-lookup"><span data-stu-id="2717a-110">Check the parameter list of the constructor being called.</span></span> <span data-ttu-id="2717a-111">Należy go innym niż Konstruktor wykonuje wywołanie.</span><span class="sxs-lookup"><span data-stu-id="2717a-111">It should be different from that of the constructor making the call.</span></span>  
  
2. <span data-ttu-id="2717a-112">Jeśli nie zamierzasz wywołanie innego konstruktora, Usuń `Sub New` wywołań w całości.</span><span class="sxs-lookup"><span data-stu-id="2717a-112">If you do not intend to call a different constructor, remove the `Sub New` call entirely.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2717a-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2717a-113">See also</span></span>

- [<span data-ttu-id="2717a-114">Okres istnienia obiektu: w jaki sposób obiekty są tworzone i niszczone</span><span class="sxs-lookup"><span data-stu-id="2717a-114">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
