---
title: "Do składowej wystąpienia klasy nie można odwołać się z obrębu udostępnionej metody lub udostępnionego inicjatora składowej bez jawnego wystąpienia klasy"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30369
- bc30369
helpviewer_keywords:
- Shared
- BC30369
ms.assetid: 39d9466b-c1f3-4406-91a5-3d6c52d23a3d
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6a15d36c0b3a4d6b1657d583de0dc61621da960d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="cannot-refer-to-an-instance-member-of-a-class-from-within-a-shared-method-or-shared-member-initializer-without-an-explicit-instance-of-the-class"></a><span data-ttu-id="cc74f-102">Do składowej wystąpienia klasy nie można odwołać się z obrębu udostępnionej metody lub udostępnionego inicjatora składowej bez jawnego wystąpienia klasy</span><span class="sxs-lookup"><span data-stu-id="cc74f-102">Cannot refer to an instance member of a class from within a shared method or shared member initializer without an explicit instance of the class</span></span>
<span data-ttu-id="cc74f-103">Próbowano odwołać się do nieudostępnionego członka klasy z wnętrza współdzielonej procedury.</span><span class="sxs-lookup"><span data-stu-id="cc74f-103">You have tried to refer to a non-shared member of a class from within a shared procedure.</span></span> <span data-ttu-id="cc74f-104">W poniższym przykładzie pokazano takiej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="cc74f-104">The following example demonstrates such a situation.</span></span>  
  
```  
Class sample  
    Public x as Integer  
    Public Shared Sub setX()  
        x = 10  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="cc74f-105">W powyższym przykładzie w instrukcji przypisania `x = 10` generuje ten komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="cc74f-105">In the preceding example, the assignment statement `x = 10` generates this error message.</span></span> <span data-ttu-id="cc74f-106">Jest to spowodowane współdzielonej procedury próbuje uzyskać dostęp do zmiennej wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="cc74f-106">This is because a shared procedure is attempting to access an instance variable.</span></span>  
  
 <span data-ttu-id="cc74f-107">Zmienna `x` jest elementem członkowskim wystąpienia, ponieważ nie jest zadeklarowany jako [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="cc74f-107">The variable `x` is an instance member because it is not declared as [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span> <span data-ttu-id="cc74f-108">Każde wystąpienie klasy `sample` zawiera poszczególnych zmienna `x`.</span><span class="sxs-lookup"><span data-stu-id="cc74f-108">Each instance of class `sample` contains its own individual variable `x`.</span></span> <span data-ttu-id="cc74f-109">Jeśli jedno wystąpienie Ustawia lub zmienia wartość `x`, nie ma wpływu na wartość `x` w innym wystąpieniu.</span><span class="sxs-lookup"><span data-stu-id="cc74f-109">When one instance sets or changes the value of `x`, it does not affect the value of `x` in any other instance.</span></span>  
  
 <span data-ttu-id="cc74f-110">Jednak procedura `setX` jest `Shared` wśród wszystkich wystąpień klasy `sample`.</span><span class="sxs-lookup"><span data-stu-id="cc74f-110">However, the procedure `setX` is `Shared` among all instances of class `sample`.</span></span> <span data-ttu-id="cc74f-111">Oznacza to, nie jest skojarzony z dowolnego jednego wystąpienia klasy, ale raczej działa niezależnie od poszczególnych wystąpień.</span><span class="sxs-lookup"><span data-stu-id="cc74f-111">This means it is not associated with any one instance of the class, but rather operates independently of individual instances.</span></span> <span data-ttu-id="cc74f-112">Ponieważ nie jest on żadne połączenie z określonym wystąpieniem `setX` nie może uzyskać dostępu do zmiennej wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="cc74f-112">Because it has no connection with a particular instance, `setX` cannot access an instance variable.</span></span> <span data-ttu-id="cc74f-113">Musi działać tylko na `Shared` zmiennych.</span><span class="sxs-lookup"><span data-stu-id="cc74f-113">It must operate only on `Shared` variables.</span></span> <span data-ttu-id="cc74f-114">Gdy `setX` Ustawia lub zmienia wartość zmiennej udostępnionego, że nowa wartość jest dostępna dla wszystkich wystąpień klasy.</span><span class="sxs-lookup"><span data-stu-id="cc74f-114">When `setX` sets or changes the value of a shared variable, that new value is available to all instances of the class.</span></span>  
  
 <span data-ttu-id="cc74f-115">**Identyfikator błędu:** BC30369</span><span class="sxs-lookup"><span data-stu-id="cc74f-115">**Error ID:** BC30369</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cc74f-116">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="cc74f-116">To correct this error</span></span>  
  
1.  <span data-ttu-id="cc74f-117">Zdecyduj, czy ma element członkowski współdzielona przez wszystkie wystąpienia klasy lub przechowywane poszczególnych dla każdego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="cc74f-117">Decide whether you want the member to be shared among all instances of the class, or kept individual for each instance.</span></span>  
  
2.  <span data-ttu-id="cc74f-118">Pojedynczej kopii elementu członkowskiego do współdzielona przez wszystkie wystąpienia, należy dodać `Shared` — słowo kluczowe do deklaracji elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="cc74f-118">If you want a single copy of the member to be shared among all instances, add the `Shared` keyword to the member declaration.</span></span> <span data-ttu-id="cc74f-119">Zachowaj `Shared` — słowo kluczowe w deklaracji procedury.</span><span class="sxs-lookup"><span data-stu-id="cc74f-119">Retain the `Shared` keyword in the procedure declaration.</span></span>  
  
3.  <span data-ttu-id="cc74f-120">Jeśli chcesz, aby każde wystąpienie ma własną pojedynczych kopii elementu członkowskiego, nie należy określać `Shared` dla deklaracji elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="cc74f-120">If you want each instance to have its own individual copy of the member, do not specify `Shared` for the member declaration.</span></span> <span data-ttu-id="cc74f-121">Usuń `Shared` — słowo kluczowe z deklaracji procedury.</span><span class="sxs-lookup"><span data-stu-id="cc74f-121">Remove the `Shared` keyword from the procedure declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc74f-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cc74f-122">See Also</span></span>  
 [<span data-ttu-id="cc74f-123">Udostępnione</span><span class="sxs-lookup"><span data-stu-id="cc74f-123">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
