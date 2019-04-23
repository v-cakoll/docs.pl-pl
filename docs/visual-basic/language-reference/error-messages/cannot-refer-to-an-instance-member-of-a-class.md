---
title: Do składowej wystąpienia klasy nie można odwołać się z obrębu udostępnionej metody lub udostępnionego inicjatora składowej bez jawnego wystąpienia klasy
ms.date: 07/20/2015
f1_keywords:
- vbc30369
- bc30369
helpviewer_keywords:
- Shared
- BC30369
ms.assetid: 39d9466b-c1f3-4406-91a5-3d6c52d23a3d
ms.openlocfilehash: aad068b5857eb956ded63fa2a57cb163d3cf5c58
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59322696"
---
# <a name="cannot-refer-to-an-instance-member-of-a-class-from-within-a-shared-method-or-shared-member-initializer-without-an-explicit-instance-of-the-class"></a><span data-ttu-id="e84e7-102">Do składowej wystąpienia klasy nie można odwołać się z obrębu udostępnionej metody lub udostępnionego inicjatora składowej bez jawnego wystąpienia klasy</span><span class="sxs-lookup"><span data-stu-id="e84e7-102">Cannot refer to an instance member of a class from within a shared method or shared member initializer without an explicit instance of the class</span></span>
<span data-ttu-id="e84e7-103">Wykonano do odwoływania się do elementu członkowskiego klasy z w ramach procedury udostępnianej nieudostępnione.</span><span class="sxs-lookup"><span data-stu-id="e84e7-103">You have tried to refer to a non-shared member of a class from within a shared procedure.</span></span> <span data-ttu-id="e84e7-104">W poniższym przykładzie pokazano takiej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="e84e7-104">The following example demonstrates such a situation.</span></span>  
  
```  
Class sample  
    Public x as Integer  
    Public Shared Sub setX()  
        x = 10  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="e84e7-105">W powyższym przykładzie instrukcja przypisania `x = 10` generuje ten komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="e84e7-105">In the preceding example, the assignment statement `x = 10` generates this error message.</span></span> <span data-ttu-id="e84e7-106">Jest to spowodowane procedury udostępnianej próbuje uzyskać dostęp do zmiennej wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e84e7-106">This is because a shared procedure is attempting to access an instance variable.</span></span>  
  
 <span data-ttu-id="e84e7-107">Zmienna `x` jest członkiem wystąpienia, ponieważ nie jest zadeklarowany jako [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="e84e7-107">The variable `x` is an instance member because it is not declared as [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span> <span data-ttu-id="e84e7-108">Każde wystąpienie klasy `sample` zawiera poszczególne zmienna `x`.</span><span class="sxs-lookup"><span data-stu-id="e84e7-108">Each instance of class `sample` contains its own individual variable `x`.</span></span> <span data-ttu-id="e84e7-109">Jeśli jedno wystąpienie, ustawia lub zmienia wartość `x`, nie ma wpływu na wartość `x` w innym wystąpieniu.</span><span class="sxs-lookup"><span data-stu-id="e84e7-109">When one instance sets or changes the value of `x`, it does not affect the value of `x` in any other instance.</span></span>  
  
 <span data-ttu-id="e84e7-110">Jednak procedura `setX` jest `Shared` wśród wszystkich wystąpień klasy `sample`.</span><span class="sxs-lookup"><span data-stu-id="e84e7-110">However, the procedure `setX` is `Shared` among all instances of class `sample`.</span></span> <span data-ttu-id="e84e7-111">Oznacza to, nie jest skojarzony z dowolnego jedno wystąpienie tej klasy, ale raczej działa niezależnie od poszczególnych wystąpień.</span><span class="sxs-lookup"><span data-stu-id="e84e7-111">This means it is not associated with any one instance of the class, but rather operates independently of individual instances.</span></span> <span data-ttu-id="e84e7-112">Ponieważ ma ona nie połączenia z konkretnego wystąpienia `setX` nie może uzyskać dostępu do zmiennej wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e84e7-112">Because it has no connection with a particular instance, `setX` cannot access an instance variable.</span></span> <span data-ttu-id="e84e7-113">Musi działać tylko na `Shared` zmiennych.</span><span class="sxs-lookup"><span data-stu-id="e84e7-113">It must operate only on `Shared` variables.</span></span> <span data-ttu-id="e84e7-114">Gdy `setX` Ustawia lub zmienia wartość zmiennej udostępnionego, nowa wartość jest dostępna dla wszystkich wystąpień klasy.</span><span class="sxs-lookup"><span data-stu-id="e84e7-114">When `setX` sets or changes the value of a shared variable, that new value is available to all instances of the class.</span></span>  
  
 <span data-ttu-id="e84e7-115">**Identyfikator błędu:** BC30369</span><span class="sxs-lookup"><span data-stu-id="e84e7-115">**Error ID:** BC30369</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e84e7-116">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="e84e7-116">To correct this error</span></span>  
  
1. <span data-ttu-id="e84e7-117">Zdecyduj, czy chcesz, aby element członkowski współużytkowane przez wszystkie wystąpienia klasy lub przechowywać poszczególne dla każdego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e84e7-117">Decide whether you want the member to be shared among all instances of the class, or kept individual for each instance.</span></span>  
  
2. <span data-ttu-id="e84e7-118">Pojedyncza kopia elementu członkowskiego do współdzielenia pośród wszystkich wystąpień, dodać `Shared` — słowo kluczowe do deklaracji elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="e84e7-118">If you want a single copy of the member to be shared among all instances, add the `Shared` keyword to the member declaration.</span></span> <span data-ttu-id="e84e7-119">Zachowaj `Shared` słowa kluczowego w zgłoszeniu procedury.</span><span class="sxs-lookup"><span data-stu-id="e84e7-119">Retain the `Shared` keyword in the procedure declaration.</span></span>  
  
3. <span data-ttu-id="e84e7-120">Jeśli chcesz, aby każde wystąpienie ma swój własny pojedyncza kopia elementu członkowskiego, nie należy określać `Shared` deklaracji elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="e84e7-120">If you want each instance to have its own individual copy of the member, do not specify `Shared` for the member declaration.</span></span> <span data-ttu-id="e84e7-121">Usuń `Shared` słowo kluczowe z deklaracja procedury.</span><span class="sxs-lookup"><span data-stu-id="e84e7-121">Remove the `Shared` keyword from the procedure declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e84e7-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e84e7-122">See also</span></span>

- [<span data-ttu-id="e84e7-123">Shared</span><span class="sxs-lookup"><span data-stu-id="e84e7-123">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
