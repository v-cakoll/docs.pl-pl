---
title: Konstruktor „<name>” nie może wywołać sam siebie
ms.date: 07/20/2015
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords:
- BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
ms.openlocfilehash: 6abb6dde624e129b52fefecf8c51e6cde2567ae1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409806"
---
# <a name="constructor-name-cannot-call-itself"></a><span data-ttu-id="f4e46-102">Konstruktor „\<name>” nie może wywołać sam siebie</span><span class="sxs-lookup"><span data-stu-id="f4e46-102">Constructor '\<name>' cannot call itself</span></span>
<span data-ttu-id="f4e46-103">`Sub New`Procedura w klasie lub strukturze wywołuje sam siebie.</span><span class="sxs-lookup"><span data-stu-id="f4e46-103">A `Sub New` procedure in a class or structure calls itself.</span></span>  
  
 <span data-ttu-id="f4e46-104">Celem konstruktora jest zainicjowanie wystąpienia klasy lub struktury, gdy jest ona najpierw tworzona.</span><span class="sxs-lookup"><span data-stu-id="f4e46-104">The purpose of a constructor is to initialize an instance of a class or structure when it is first created.</span></span> <span data-ttu-id="f4e46-105">Klasa lub struktura może mieć kilka konstruktorów, pod warunkiem, że wszystkie mają różne listy parametrów.</span><span class="sxs-lookup"><span data-stu-id="f4e46-105">A class or structure can have several constructors, provided they all have different parameter lists.</span></span> <span data-ttu-id="f4e46-106">Konstruktor jest uprawniony do wywołania innego konstruktora, aby wykonywał jego funkcję oprócz własnych.</span><span class="sxs-lookup"><span data-stu-id="f4e46-106">A constructor is permitted to call another constructor to perform its functionality in addition to its own.</span></span> <span data-ttu-id="f4e46-107">Jednak nie ma to znaczenia dla konstruktora, który wywołuje siebie, i w rzeczywistości spowoduje nieskończoną rekursję, jeśli jest to dozwolone.</span><span class="sxs-lookup"><span data-stu-id="f4e46-107">But it is meaningless for a constructor to call itself, and in fact it would result in infinite recursion if permitted.</span></span>  
  
 <span data-ttu-id="f4e46-108">**Identyfikator błędu:** BC30298</span><span class="sxs-lookup"><span data-stu-id="f4e46-108">**Error ID:** BC30298</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f4e46-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="f4e46-109">To correct this error</span></span>  
  
1. <span data-ttu-id="f4e46-110">Sprawdź listę parametrów wywoływanego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="f4e46-110">Check the parameter list of the constructor being called.</span></span> <span data-ttu-id="f4e46-111">Powinien być różny od konstruktora wywołującego wywołanie.</span><span class="sxs-lookup"><span data-stu-id="f4e46-111">It should be different from that of the constructor making the call.</span></span>  
  
2. <span data-ttu-id="f4e46-112">Jeśli nie zamierzasz wywołać innego konstruktora, Usuń `Sub New` wywołanie całkowicie.</span><span class="sxs-lookup"><span data-stu-id="f4e46-112">If you do not intend to call a different constructor, remove the `Sub New` call entirely.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4e46-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f4e46-113">See also</span></span>

- [<span data-ttu-id="f4e46-114">Okres istnienia obiektów: w jaki sposób obiekty są tworzone i niszczone</span><span class="sxs-lookup"><span data-stu-id="f4e46-114">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
