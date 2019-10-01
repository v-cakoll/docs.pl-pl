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
ms.openlocfilehash: a2a5ab99ff68e6dce783a2fd986ee6e8c15ae858
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701175"
---
# <a name="cannot-refer-to-an-instance-member-of-a-class-from-within-a-shared-method-or-shared-member-initializer-without-an-explicit-instance-of-the-class"></a><span data-ttu-id="28d97-102">Do składowej wystąpienia klasy nie można odwołać się z obrębu udostępnionej metody lub udostępnionego inicjatora składowej bez jawnego wystąpienia klasy</span><span class="sxs-lookup"><span data-stu-id="28d97-102">Cannot refer to an instance member of a class from within a shared method or shared member initializer without an explicit instance of the class</span></span>
<span data-ttu-id="28d97-103">Podjęto próbę odwołania się do nieudostępnionego elementu członkowskiego klasy z procedury wspólnej.</span><span class="sxs-lookup"><span data-stu-id="28d97-103">You have tried to refer to a non-shared member of a class from within a shared procedure.</span></span> <span data-ttu-id="28d97-104">Poniższy przykład demonstruje takie sytuacje.</span><span class="sxs-lookup"><span data-stu-id="28d97-104">The following example demonstrates such a situation.</span></span>  
  
```vb  
Class sample  
    Public x as Integer  
    Public Shared Sub setX()  
        x = 10  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="28d97-105">W poprzednim przykładzie instrukcja przypisania `x = 10` generuje ten komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="28d97-105">In the preceding example, the assignment statement `x = 10` generates this error message.</span></span> <span data-ttu-id="28d97-106">Wynika to z faktu, że wspólna procedura próbuje uzyskać dostęp do zmiennej wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="28d97-106">This is because a shared procedure is attempting to access an instance variable.</span></span>  
  
 <span data-ttu-id="28d97-107">Zmienna `x` jest członkiem wystąpienia, ponieważ nie jest zadeklarowana jako [udostępniona](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="28d97-107">The variable `x` is an instance member because it is not declared as [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span> <span data-ttu-id="28d97-108">Każde wystąpienie klasy `sample` zawiera własną indywidualną zmienną `x`.</span><span class="sxs-lookup"><span data-stu-id="28d97-108">Each instance of class `sample` contains its own individual variable `x`.</span></span> <span data-ttu-id="28d97-109">Gdy jedno wystąpienie ustawia lub zmienia wartość `x`, nie ma wpływu na wartość `x` w żadnym innym wystąpieniu.</span><span class="sxs-lookup"><span data-stu-id="28d97-109">When one instance sets or changes the value of `x`, it does not affect the value of `x` in any other instance.</span></span>  
  
 <span data-ttu-id="28d97-110">Jednak procedura `setX` jest `Shared` między wszystkimi wystąpieniami klasy `sample`.</span><span class="sxs-lookup"><span data-stu-id="28d97-110">However, the procedure `setX` is `Shared` among all instances of class `sample`.</span></span> <span data-ttu-id="28d97-111">Oznacza to, że nie jest on skojarzony z jednym wystąpieniem klasy, ale raczej działa niezależnie od poszczególnych wystąpień.</span><span class="sxs-lookup"><span data-stu-id="28d97-111">This means it is not associated with any one instance of the class, but rather operates independently of individual instances.</span></span> <span data-ttu-id="28d97-112">Ponieważ nie ma połączenia z określonym wystąpieniem, `setX` nie może uzyskać dostępu do zmiennej wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="28d97-112">Because it has no connection with a particular instance, `setX` cannot access an instance variable.</span></span> <span data-ttu-id="28d97-113">Musi działać tylko w przypadku zmiennych `Shared`.</span><span class="sxs-lookup"><span data-stu-id="28d97-113">It must operate only on `Shared` variables.</span></span> <span data-ttu-id="28d97-114">Gdy `setX` ustawia lub zmienia wartość zmiennej udostępnionej, Nowa wartość jest dostępna dla wszystkich wystąpień klasy.</span><span class="sxs-lookup"><span data-stu-id="28d97-114">When `setX` sets or changes the value of a shared variable, that new value is available to all instances of the class.</span></span>  
  
 <span data-ttu-id="28d97-115">**Identyfikator błędu:** BC30369</span><span class="sxs-lookup"><span data-stu-id="28d97-115">**Error ID:** BC30369</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="28d97-116">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="28d97-116">To correct this error</span></span>  
  
1. <span data-ttu-id="28d97-117">Zdecyduj, czy element członkowski ma być współużytkowany między wszystkimi wystąpieniami klasy, czy dla każdego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="28d97-117">Decide whether you want the member to be shared among all instances of the class, or kept individual for each instance.</span></span>  
  
2. <span data-ttu-id="28d97-118">Jeśli chcesz, aby jedna kopia elementu członkowskiego była współdzielona między wszystkimi wystąpieniami, Dodaj słowo kluczowe `Shared` do deklaracji elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="28d97-118">If you want a single copy of the member to be shared among all instances, add the `Shared` keyword to the member declaration.</span></span> <span data-ttu-id="28d97-119">Zachowaj słowo kluczowe `Shared` w deklaracji procedury.</span><span class="sxs-lookup"><span data-stu-id="28d97-119">Retain the `Shared` keyword in the procedure declaration.</span></span>  
  
3. <span data-ttu-id="28d97-120">Jeśli każde wystąpienie ma mieć własną indywidualną kopię elementu członkowskiego, nie należy określać `Shared` dla deklaracji elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="28d97-120">If you want each instance to have its own individual copy of the member, do not specify `Shared` for the member declaration.</span></span> <span data-ttu-id="28d97-121">Usuń słowo kluczowe `Shared` z deklaracji procedury.</span><span class="sxs-lookup"><span data-stu-id="28d97-121">Remove the `Shared` keyword from the procedure declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28d97-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="28d97-122">See also</span></span>

- [<span data-ttu-id="28d97-123">Shared</span><span class="sxs-lookup"><span data-stu-id="28d97-123">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
