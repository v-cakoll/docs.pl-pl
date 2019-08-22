---
title: Użycie domyślnego wystąpienia klasy w konstruktorze klas może prowadzić do nieskończonego wywołania cyklicznego
ms.date: 07/20/2015
ms.assetid: 9645b47f-7de5-46d0-bb45-d5fdaa8aaa2a
ms.openlocfilehash: cec3d3d462822ca571cab59a2e4d7e730d2aec46
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664366"
---
# <a name="use-of-default-instance-of-a-class-in-the-class-constructor-could-lead-to-infinite-recursive-call"></a><span data-ttu-id="d5026-102">Użycie domyślnego wystąpienia klasy w konstruktorze klas może prowadzić do nieskończonego wywołania cyklicznego</span><span class="sxs-lookup"><span data-stu-id="d5026-102">Use of Default Instance of a class in the class constructor could lead to infinite recursive call</span></span>
<span data-ttu-id="d5026-103">W konstruktorze klasy użyto domyślnego wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="d5026-103">A default instance of a class has been used in the constructor of the class.</span></span> <span data-ttu-id="d5026-104">Może to prowadzić do nieskończonego wywołania cyklicznego, nazywanego również pętlą nieskończoną.</span><span class="sxs-lookup"><span data-stu-id="d5026-104">This can lead to an infinite recursive call, also known as an infinite loop.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d5026-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="d5026-105">To correct this error</span></span>  
  
- <span data-ttu-id="d5026-106">Usuń wystąpienie domyślne z konstruktora klasy.</span><span class="sxs-lookup"><span data-stu-id="d5026-106">Remove the default instance from the class constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5026-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d5026-107">See also</span></span>

- [<span data-ttu-id="d5026-108">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="d5026-108">Constructors</span></span>](../programming-guide/concepts/object-oriented-programming.md#constructors)
