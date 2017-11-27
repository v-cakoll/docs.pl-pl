---
title: "Implements — Instrukcja"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Implements
- Implements
helpviewer_keywords:
- Implements statement [Visual Basic], syntax
- Implements statement [Visual Basic]
- interface implementation [Visual Basic], Implements statement
ms.assetid: 1fafb83f-f55a-4215-8ea9-681e8622613d
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1103305ffbf5425d9a6a6a09695437968642710d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="implements-statement"></a><span data-ttu-id="c427a-102">Implements — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="c427a-102">Implements Statement</span></span>
<span data-ttu-id="c427a-103">Określa jeden lub więcej interfejsów lub członków interfejsu, które muszą zostać zaimplementowane w klasie lub definicji struktury, w której znajduje się.</span><span class="sxs-lookup"><span data-stu-id="c427a-103">Specifies one or more interfaces, or interface members, that must be implemented in the class or structure definition in which it appears.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c427a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c427a-104">Syntax</span></span>  
  
```  
Implements interfacename [, ...]  
-or-  
Implements interfacename.interfacemember [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="c427a-105">Części</span><span class="sxs-lookup"><span data-stu-id="c427a-105">Parts</span></span>  
 `interfacename`  
 <span data-ttu-id="c427a-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="c427a-106">Required.</span></span> <span data-ttu-id="c427a-107">Interfejs, którego właściwości, procedur i zdarzenia są wdrażane przez odpowiednie elementy członkowskie w klasie lub strukturze.</span><span class="sxs-lookup"><span data-stu-id="c427a-107">An interface whose properties, procedures, and events are to be implemented by corresponding members in the class or structure.</span></span>  
  
 `interfacemember`  
 <span data-ttu-id="c427a-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="c427a-108">Required.</span></span> <span data-ttu-id="c427a-109">Element członkowski interfejsu, który zostanie wdrożony.</span><span class="sxs-lookup"><span data-stu-id="c427a-109">The member of an interface that is being implemented.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c427a-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c427a-110">Remarks</span></span>  
 <span data-ttu-id="c427a-111">Interfejs jest kolekcją prototypów reprezentujący członków (właściwości, procedur i zdarzeń) hermetyzuje interfejsu.</span><span class="sxs-lookup"><span data-stu-id="c427a-111">An interface is a collection of prototypes representing the members (properties, procedures, and events) the interface encapsulates.</span></span> <span data-ttu-id="c427a-112">Interfejsy zawierać tylko deklaracje elementów członkowskich; klasy i struktury implementuje tych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="c427a-112">Interfaces contain only the declarations for members; classes and structures implement these members.</span></span> <span data-ttu-id="c427a-113">Aby uzyskać więcej informacji, zobacz [interfejsów](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="c427a-113">For more information, see [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span></span>  
  
 <span data-ttu-id="c427a-114">`Implements` Instrukcji musi występować zaraz po `Class` lub `Structure` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="c427a-114">The `Implements` statement must immediately follow the `Class` or `Structure` statement.</span></span>  
  
 <span data-ttu-id="c427a-115">Po zaimplementowaniu interfejsu należy zaimplementować wszystkich elementów członkowskich zadeklarowanych w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="c427a-115">When you implement an interface, you must implement all the members declared in the interface.</span></span> <span data-ttu-id="c427a-116">Pominięcie dowolnego elementu członkowskiego jest uważany za błąd składni.</span><span class="sxs-lookup"><span data-stu-id="c427a-116">Omitting any member is considered to be a syntax error.</span></span> <span data-ttu-id="c427a-117">Aby zaimplementować poszczególnych elementów członkowskich, należy określić [implementuje](../../../visual-basic/language-reference/statements/implements-clause.md) — słowo kluczowe (które są oddzielne od `Implements` instrukcji) po deklaruje element członkowski klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="c427a-117">To implement an individual member, you specify the [Implements](../../../visual-basic/language-reference/statements/implements-clause.md) keyword (which is separate from the `Implements` statement) when you declare the member in the class or structure.</span></span> <span data-ttu-id="c427a-118">Aby uzyskać więcej informacji, zobacz [interfejsów](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="c427a-118">For more information, see [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md).</span></span>  
  
 <span data-ttu-id="c427a-119">Można użyć klasy [prywatnej](../../../visual-basic/language-reference/modifiers/private.md) implementacje właściwości i procedury, ale elementy te są dostępne tylko rzutowanie zadeklarowany wystąpienia klasy implementującej do zmiennej typu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="c427a-119">Classes can use [Private](../../../visual-basic/language-reference/modifiers/private.md) implementations of properties and procedures, but these members are accessible only by casting an instance of the implementing class into a variable declared to be of the type of the interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c427a-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="c427a-120">Example</span></span>  
 <span data-ttu-id="c427a-121">Poniższy przykład przedstawia użycie `Implements` instrukcji można implementować członków interfejsu.</span><span class="sxs-lookup"><span data-stu-id="c427a-121">The following example shows how to use the `Implements` statement to implement members of an interface.</span></span> <span data-ttu-id="c427a-122">Definiuje interfejs o nazwie `ICustomerInfo` zdarzenia, właściwości i procedury.</span><span class="sxs-lookup"><span data-stu-id="c427a-122">It defines an interface named `ICustomerInfo` with an event, a property, and a procedure.</span></span> <span data-ttu-id="c427a-123">Klasa `customerInfo` implementuje wszystkich elementów członkowskich zdefiniowanych w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="c427a-123">The class `customerInfo` implements all the members defined in the interface.</span></span>  
  
 [!code-vb[VbVbalrStatements#33](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/implements-statement_1.vb)]  
  
 <span data-ttu-id="c427a-124">Należy pamiętać, że klasa `customerInfo` używa `Implements` instrukcji w wierszu kodu oddzielne źródło, aby wskazać, że klasa implementuje wszyscy członkowie `ICustomerInfo` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="c427a-124">Note that the class `customerInfo` uses the `Implements` statement on a separate source code line to indicate that the class implements all the members of the `ICustomerInfo` interface.</span></span> <span data-ttu-id="c427a-125">Następnie używa każdy element członkowski w klasie `Implements` słowa kluczowego jako części swojej deklaracji elementu członkowskiego, aby wskazać, że implementuje ten element członkowski interfejsu.</span><span class="sxs-lookup"><span data-stu-id="c427a-125">Then each member in the class uses the `Implements` keyword as part of its member declaration to indicate that it implements that interface member.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c427a-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="c427a-126">Example</span></span>  
 <span data-ttu-id="c427a-127">Poniższe dwie procedury pokazują, jak można za pomocą interfejsu zaimplementowana w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c427a-127">The following two procedures show how you could use the interface implemented in the preceding example.</span></span> <span data-ttu-id="c427a-128">Próba wykonania tych procedur projektu i dodawać wywołania `testImplements` procedury.</span><span class="sxs-lookup"><span data-stu-id="c427a-128">To test the implementation, add these procedures to your project and call the `testImplements` procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#34](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/implements-statement_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="c427a-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c427a-129">See Also</span></span>  
 [<span data-ttu-id="c427a-130">Implementuje</span><span class="sxs-lookup"><span data-stu-id="c427a-130">Implements</span></span>](../../../visual-basic/language-reference/statements/implements-clause.md)  
 [<span data-ttu-id="c427a-131">Interface — instrukcja</span><span class="sxs-lookup"><span data-stu-id="c427a-131">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [<span data-ttu-id="c427a-132">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="c427a-132">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
