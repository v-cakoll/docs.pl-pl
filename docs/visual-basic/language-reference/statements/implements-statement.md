---
title: Implements — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Implements
- Implements
helpviewer_keywords:
- Implements statement [Visual Basic], syntax
- Implements statement [Visual Basic]
- interface implementation [Visual Basic], Implements statement
ms.assetid: 1fafb83f-f55a-4215-8ea9-681e8622613d
ms.openlocfilehash: 865e99aa0e27591d10fde1465047a2e6bf183bbf
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581791"
---
# <a name="implements-statement"></a><span data-ttu-id="3dd1a-102">Implements — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="3dd1a-102">Implements Statement</span></span>
<span data-ttu-id="3dd1a-103">Określa jeden lub więcej interfejsów lub składowych interfejsu, które muszą zostać zaimplementowane w definicji klasy lub struktury, w której występuje.</span><span class="sxs-lookup"><span data-stu-id="3dd1a-103">Specifies one or more interfaces, or interface members, that must be implemented in the class or structure definition in which it appears.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dd1a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3dd1a-104">Syntax</span></span>  
  
```vb  
Implements interfacename [, ...]  
' -or-  
Implements interfacename.interfacemember [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="3dd1a-105">Części</span><span class="sxs-lookup"><span data-stu-id="3dd1a-105">Parts</span></span>  
 `interfacename`  
 <span data-ttu-id="3dd1a-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="3dd1a-106">Required.</span></span> <span data-ttu-id="3dd1a-107">Interfejs, którego właściwości, procedury i zdarzenia mają być implementowane przez odpowiadające im elementy członkowskie klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="3dd1a-107">An interface whose properties, procedures, and events are to be implemented by corresponding members in the class or structure.</span></span>  
  
 `interfacemember`  
 <span data-ttu-id="3dd1a-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="3dd1a-108">Required.</span></span> <span data-ttu-id="3dd1a-109">Element członkowski interfejsu, który jest implementowany.</span><span class="sxs-lookup"><span data-stu-id="3dd1a-109">The member of an interface that is being implemented.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3dd1a-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3dd1a-110">Remarks</span></span>  
 <span data-ttu-id="3dd1a-111">Interfejs jest kolekcją prototypów reprezentujących elementy członkowskie (właściwości, procedury i zdarzenia), które są hermetyzowane w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="3dd1a-111">An interface is a collection of prototypes representing the members (properties, procedures, and events) the interface encapsulates.</span></span> <span data-ttu-id="3dd1a-112">Interfejsy zawierają tylko deklaracje elementów członkowskich; klasy i struktury implementują te składowe.</span><span class="sxs-lookup"><span data-stu-id="3dd1a-112">Interfaces contain only the declarations for members; classes and structures implement these members.</span></span> <span data-ttu-id="3dd1a-113">Aby uzyskać więcej informacji, zobacz [interfejsy](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="3dd1a-113">For more information, see [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span></span>  
  
 <span data-ttu-id="3dd1a-114">Instrukcja `Implements` musi być od razu zgodna z instrukcją `Class` lub `Structure`.</span><span class="sxs-lookup"><span data-stu-id="3dd1a-114">The `Implements` statement must immediately follow the `Class` or `Structure` statement.</span></span>  
  
 <span data-ttu-id="3dd1a-115">Podczas implementowania interfejsu, należy zaimplementować wszystkie elementy członkowskie zadeklarowane w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="3dd1a-115">When you implement an interface, you must implement all the members declared in the interface.</span></span> <span data-ttu-id="3dd1a-116">Pominięcie żadnego elementu członkowskiego jest uznawane za błąd składniowy.</span><span class="sxs-lookup"><span data-stu-id="3dd1a-116">Omitting any member is considered to be a syntax error.</span></span> <span data-ttu-id="3dd1a-117">Aby zaimplementować pojedynczy element członkowski, należy określić słowo kluczowe [Implements](../../../visual-basic/language-reference/statements/implements-clause.md) (które jest oddzielone od instrukcji `Implements`) podczas deklarowania elementu członkowskiego w klasie lub strukturze.</span><span class="sxs-lookup"><span data-stu-id="3dd1a-117">To implement an individual member, you specify the [Implements](../../../visual-basic/language-reference/statements/implements-clause.md) keyword (which is separate from the `Implements` statement) when you declare the member in the class or structure.</span></span> <span data-ttu-id="3dd1a-118">Aby uzyskać więcej informacji, zobacz [interfejsy](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="3dd1a-118">For more information, see [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span></span>  
  
 <span data-ttu-id="3dd1a-119">Klasy mogą używać [prywatnych](../../../visual-basic/language-reference/modifiers/private.md) implementacji właściwości i procedur, ale te elementy członkowskie są dostępne tylko przez rzutowanie wystąpienia klasy implementującej na zmienną zadeklarowaną jako typ interfejsu.</span><span class="sxs-lookup"><span data-stu-id="3dd1a-119">Classes can use [Private](../../../visual-basic/language-reference/modifiers/private.md) implementations of properties and procedures, but these members are accessible only by casting an instance of the implementing class into a variable declared to be of the type of the interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3dd1a-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="3dd1a-120">Example</span></span>  
 <span data-ttu-id="3dd1a-121">Poniższy przykład pokazuje, jak używać instrukcji `Implements` do implementowania elementów członkowskich interfejsu.</span><span class="sxs-lookup"><span data-stu-id="3dd1a-121">The following example shows how to use the `Implements` statement to implement members of an interface.</span></span> <span data-ttu-id="3dd1a-122">Definiuje interfejs o nazwie `ICustomerInfo` ze zdarzeniem, właściwością i procedurą.</span><span class="sxs-lookup"><span data-stu-id="3dd1a-122">It defines an interface named `ICustomerInfo` with an event, a property, and a procedure.</span></span> <span data-ttu-id="3dd1a-123">Klasa `customerInfo` implementuje wszystkie elementy członkowskie zdefiniowane w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="3dd1a-123">The class `customerInfo` implements all the members defined in the interface.</span></span>  
  
 [!code-vb[VbVbalrStatements#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#33)]  
  
 <span data-ttu-id="3dd1a-124">Należy zauważyć, że Klasa `customerInfo` używa instrukcji `Implements` w oddzielnym wierszu kodu źródłowego, aby wskazać, że klasa implementuje wszystkie elementy członkowskie interfejsu `ICustomerInfo`.</span><span class="sxs-lookup"><span data-stu-id="3dd1a-124">Note that the class `customerInfo` uses the `Implements` statement on a separate source code line to indicate that the class implements all the members of the `ICustomerInfo` interface.</span></span> <span data-ttu-id="3dd1a-125">Następnie każdy element członkowski w klasie używa słowa kluczowego `Implements` jako części deklaracji elementu członkowskiego, aby wskazać, że implementuje ten element członkowski interfejsu.</span><span class="sxs-lookup"><span data-stu-id="3dd1a-125">Then each member in the class uses the `Implements` keyword as part of its member declaration to indicate that it implements that interface member.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3dd1a-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="3dd1a-126">Example</span></span>  
 <span data-ttu-id="3dd1a-127">W poniższych dwóch procedurach pokazano, jak można użyć interfejsu zaimplementowanego w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="3dd1a-127">The following two procedures show how you could use the interface implemented in the preceding example.</span></span> <span data-ttu-id="3dd1a-128">Aby przetestować implementację, należy dodać te procedury do projektu i wywołać procedurę `testImplements`.</span><span class="sxs-lookup"><span data-stu-id="3dd1a-128">To test the implementation, add these procedures to your project and call the `testImplements` procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#34)]  
  
## <a name="see-also"></a><span data-ttu-id="3dd1a-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3dd1a-129">See also</span></span>

- [<span data-ttu-id="3dd1a-130">Wprowadza</span><span class="sxs-lookup"><span data-stu-id="3dd1a-130">Implements</span></span>](../../../visual-basic/language-reference/statements/implements-clause.md)
- [<span data-ttu-id="3dd1a-131">Interface, instrukcja</span><span class="sxs-lookup"><span data-stu-id="3dd1a-131">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="3dd1a-132">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="3dd1a-132">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
