---
title: Implements — instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Implements
- Implements
helpviewer_keywords:
- Implements statement [Visual Basic], syntax
- Implements statement [Visual Basic]
- interface implementation [Visual Basic], Implements statement
ms.assetid: 1fafb83f-f55a-4215-8ea9-681e8622613d
ms.openlocfilehash: cdcbe20157b9647040e3610d0632bd8e3fb9df65
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54681069"
---
# <a name="implements-statement"></a><span data-ttu-id="1d582-102">Implements — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="1d582-102">Implements Statement</span></span>
<span data-ttu-id="1d582-103">Określa jedną lub więcej interfejsów lub składowych interfejsu, które muszą zostać zaimplementowane w klasie lub definicji struktury, w której występuje.</span><span class="sxs-lookup"><span data-stu-id="1d582-103">Specifies one or more interfaces, or interface members, that must be implemented in the class or structure definition in which it appears.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d582-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1d582-104">Syntax</span></span>  
  
```  
Implements interfacename [, ...]  
-or-  
Implements interfacename.interfacemember [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="1d582-105">Części</span><span class="sxs-lookup"><span data-stu-id="1d582-105">Parts</span></span>  
 `interfacename`  
 <span data-ttu-id="1d582-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="1d582-106">Required.</span></span> <span data-ttu-id="1d582-107">Interfejs, którego właściwości, procedur i zdarzeń mają być wykonywane przez odpowiednie elementy członkowskie w klasie lub strukturze.</span><span class="sxs-lookup"><span data-stu-id="1d582-107">An interface whose properties, procedures, and events are to be implemented by corresponding members in the class or structure.</span></span>  
  
 `interfacemember`  
 <span data-ttu-id="1d582-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="1d582-108">Required.</span></span> <span data-ttu-id="1d582-109">Element członkowski interfejs, który zostanie wdrożony.</span><span class="sxs-lookup"><span data-stu-id="1d582-109">The member of an interface that is being implemented.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d582-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1d582-110">Remarks</span></span>  
 <span data-ttu-id="1d582-111">Interfejs jest kolekcją prototypów reprezentujących elementy członkowskie (właściwości, procedur i zdarzeń) hermetyzuje interfejs.</span><span class="sxs-lookup"><span data-stu-id="1d582-111">An interface is a collection of prototypes representing the members (properties, procedures, and events) the interface encapsulates.</span></span> <span data-ttu-id="1d582-112">Interfejsy zawierać deklaracje dla elementów członkowskich; klasy i struktury zaimplementować te składowe.</span><span class="sxs-lookup"><span data-stu-id="1d582-112">Interfaces contain only the declarations for members; classes and structures implement these members.</span></span> <span data-ttu-id="1d582-113">Więcej informacji znajdziesz w artykule [Interfejsy](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="1d582-113">For more information, see [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span></span>  
  
 <span data-ttu-id="1d582-114">`Implements` Natychmiast wykonaj instrukcję `Class` lub `Structure` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="1d582-114">The `Implements` statement must immediately follow the `Class` or `Structure` statement.</span></span>  
  
 <span data-ttu-id="1d582-115">Podczas implementowania interfejsu musi implementować wszystkich elementów członkowskich zadeklarowanych w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="1d582-115">When you implement an interface, you must implement all the members declared in the interface.</span></span> <span data-ttu-id="1d582-116">Pominięcie dowolnego elementu członkowskiego jest uważany za błąd składni.</span><span class="sxs-lookup"><span data-stu-id="1d582-116">Omitting any member is considered to be a syntax error.</span></span> <span data-ttu-id="1d582-117">Aby zaimplementować poszczególnych elementów członkowskich, należy określić [implementuje](../../../visual-basic/language-reference/statements/implements-clause.md) — słowo kluczowe (który jest oddzielony od `Implements` instrukcji) kiedy Deklarujesz element członkowski w klasie lub strukturze.</span><span class="sxs-lookup"><span data-stu-id="1d582-117">To implement an individual member, you specify the [Implements](../../../visual-basic/language-reference/statements/implements-clause.md) keyword (which is separate from the `Implements` statement) when you declare the member in the class or structure.</span></span> <span data-ttu-id="1d582-118">Więcej informacji znajdziesz w artykule [Interfejsy](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="1d582-118">For more information, see [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span></span>  
  
 <span data-ttu-id="1d582-119">Można użyć klasy [prywatnej](../../../visual-basic/language-reference/modifiers/private.md) implementacji właściwości i procedury, ale te składowe są dostępne tylko rzutowania wystąpienia klasy implementującej do zmiennej zadeklarowany typ interfejsu.</span><span class="sxs-lookup"><span data-stu-id="1d582-119">Classes can use [Private](../../../visual-basic/language-reference/modifiers/private.md) implementations of properties and procedures, but these members are accessible only by casting an instance of the implementing class into a variable declared to be of the type of the interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d582-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="1d582-120">Example</span></span>  
 <span data-ttu-id="1d582-121">Poniższy przykład pokazuje, jak używać `Implements` instrukcję, aby implementować członków interfejsu.</span><span class="sxs-lookup"><span data-stu-id="1d582-121">The following example shows how to use the `Implements` statement to implement members of an interface.</span></span> <span data-ttu-id="1d582-122">Definiuje interfejs o nazwie `ICustomerInfo` zdarzenie, właściwości i procedury.</span><span class="sxs-lookup"><span data-stu-id="1d582-122">It defines an interface named `ICustomerInfo` with an event, a property, and a procedure.</span></span> <span data-ttu-id="1d582-123">Klasa `customerInfo` implementuje wszystkie elementy członkowskie zdefiniowane w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="1d582-123">The class `customerInfo` implements all the members defined in the interface.</span></span>  
  
 [!code-vb[VbVbalrStatements#33](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/implements-statement_1.vb)]  
  
 <span data-ttu-id="1d582-124">Należy pamiętać, że klasa `customerInfo` używa `Implements` instrukcji na oddzielne źródło wiersza kodu, aby wskazać, że klasa implementuje wszystkie elementy członkowskie `ICustomerInfo` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="1d582-124">Note that the class `customerInfo` uses the `Implements` statement on a separate source code line to indicate that the class implements all the members of the `ICustomerInfo` interface.</span></span> <span data-ttu-id="1d582-125">Następnie używa każdego elementu członkowskiego w klasie `Implements` słowa kluczowego jako części swojej deklaracji elementu członkowskiego, aby wskazać implementuje tej składowej interfejsu.</span><span class="sxs-lookup"><span data-stu-id="1d582-125">Then each member in the class uses the `Implements` keyword as part of its member declaration to indicate that it implements that interface member.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d582-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="1d582-126">Example</span></span>  
 <span data-ttu-id="1d582-127">Poniższe dwie procedury pokazują, jak można użyć interfejsu implementowany w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1d582-127">The following two procedures show how you could use the interface implemented in the preceding example.</span></span> <span data-ttu-id="1d582-128">Aby przetestować wdrożenia, należy dodać te procedury do projektu i wywołania `testImplements` procedury.</span><span class="sxs-lookup"><span data-stu-id="1d582-128">To test the implementation, add these procedures to your project and call the `testImplements` procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#34](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/implements-statement_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="1d582-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1d582-129">See also</span></span>
- [<span data-ttu-id="1d582-130">Implements</span><span class="sxs-lookup"><span data-stu-id="1d582-130">Implements</span></span>](../../../visual-basic/language-reference/statements/implements-clause.md)
- [<span data-ttu-id="1d582-131">Instrukcja Interface</span><span class="sxs-lookup"><span data-stu-id="1d582-131">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="1d582-132">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="1d582-132">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
