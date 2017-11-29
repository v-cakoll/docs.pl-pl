---
title: "New — Operator (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.new
- vb.NewConstraint
helpviewer_keywords:
- constraints, Visual Basic generic types
- generics [Visual Basic], constraints
- constraints, New keyword [Visual Basic]
- New constraint
- New keyword [Visual Basic]
ms.assetid: d7d566d7-fe0e-4336-91f7-641a542de4d0
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 74f0352379e861ad135ea23d31ea07d638f9e6c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="new-operator-visual-basic"></a><span data-ttu-id="3b622-102">New — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b622-102">New Operator (Visual Basic)</span></span>
<span data-ttu-id="3b622-103">Wprowadza `New` klauzuli do utworzenia nowego wystąpienia obiektu, określa ograniczenie konstruktora dla parametru typu lub identyfikuje `Sub` procedury jako konstruktora klasy.</span><span class="sxs-lookup"><span data-stu-id="3b622-103">Introduces a `New` clause to create a new object instance, specifies a constructor constraint on a type parameter, or identifies a `Sub` procedure as a class constructor.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b622-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3b622-104">Remarks</span></span>  
 <span data-ttu-id="3b622-105">W deklaracji lub instrukcji przypisania `New` klauzula musi określać zdefiniowanej klasy, z którego można utworzyć wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="3b622-105">In a declaration or assignment statement, a `New` clause must specify a defined class from which the instance can be created.</span></span> <span data-ttu-id="3b622-106">Oznacza to, że klasa musi ujawniać konstruktorów co najmniej jeden kod wywołujący może uzyskać dostęp.</span><span class="sxs-lookup"><span data-stu-id="3b622-106">This means that the class must expose one or more constructors that the calling code can access.</span></span>  
  
 <span data-ttu-id="3b622-107">Można użyć `New` klauzuli w instrukcji deklaracji lub instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="3b622-107">You can use a `New` clause in a declaration statement or an assignment statement.</span></span> <span data-ttu-id="3b622-108">Po uruchomieniu instrukcji, wymaga odpowiedniego konstruktora określonej klasy, przekazując żadnych argumentów, które podano.</span><span class="sxs-lookup"><span data-stu-id="3b622-108">When the statement runs, it calls the appropriate constructor of the specified class, passing any arguments you have supplied.</span></span> <span data-ttu-id="3b622-109">W poniższym przykładzie pokazano to przez utworzenie wystąpienia `Customer` klasy, która ma dwa konstruktory, który nie przyjmuje żadnych parametrów i jedną, która przyjmuje parametr typu string.</span><span class="sxs-lookup"><span data-stu-id="3b622-109">The following example demonstrates this by creating instances of a `Customer` class that has two constructors, one that takes no parameters and one that takes a string parameter.</span></span>  
  
 [!code-vb[VbVbalrKeywords#11](../../../visual-basic/language-reference/codesnippet/VisualBasic/new-operator_1.vb)]  
  
 <span data-ttu-id="3b622-110">Ponieważ tablic są klasy, `New` można utworzyć nowego wystąpienia tablicy, jak pokazano w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="3b622-110">Since arrays are classes, `New` can create a new array instance, as shown in the following examples.</span></span>  
  
 [!code-vb[VbVbalrKeywords#12](../../../visual-basic/language-reference/codesnippet/VisualBasic/new-operator_2.vb)]  
  
 <span data-ttu-id="3b622-111">Środowisko uruchomieniowe języka wspólnego (CLR) zgłasza <xref:System.OutOfMemoryException> błędu, jeśli jest za mało pamięci do utworzenia nowego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="3b622-111">The common language runtime (CLR) throws an <xref:System.OutOfMemoryException> error if there is insufficient memory to create the new instance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3b622-112">`New` — Słowo kluczowe umożliwia również w liście parametrów typu określ, czy dostarczony typ musi ujawniać dostępny konstruktor bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="3b622-112">The `New` keyword is also used in type parameter lists to specify that the supplied type must expose an accessible parameterless constructor.</span></span> <span data-ttu-id="3b622-113">Aby uzyskać więcej informacji na temat parametrów typu i ograniczeń, zobacz [lista typów](../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="3b622-113">For more information about type parameters and constraints, see [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
 <span data-ttu-id="3b622-114">Aby utworzyć procedury konstruktora dla klasy, ustaw nazwę `Sub` procedura `New` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="3b622-114">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="3b622-115">Aby uzyskać więcej informacji, zobacz [okres istnienia obiektów: sposób obiekty są utworzone i Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="3b622-115">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>  
  
 <span data-ttu-id="3b622-116">`New` — Słowo kluczowe może być używana w tych sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="3b622-116">The `New` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="3b622-117">Dim — instrukcja</span><span class="sxs-lookup"><span data-stu-id="3b622-117">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="3b622-118">Z</span><span class="sxs-lookup"><span data-stu-id="3b622-118">Of</span></span>](../../../visual-basic/language-reference/statements/of-clause.md)  
  
 [<span data-ttu-id="3b622-119">Sub — instrukcja</span><span class="sxs-lookup"><span data-stu-id="3b622-119">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="3b622-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3b622-120">See Also</span></span>  
 <xref:System.OutOfMemoryException>  
 [<span data-ttu-id="3b622-121">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="3b622-121">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="3b622-122">Lista typów</span><span class="sxs-lookup"><span data-stu-id="3b622-122">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)  
 [<span data-ttu-id="3b622-123">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3b622-123">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="3b622-124">Okres istnienia obiektów: Sposób obiekty są tworzone i niszczone</span><span class="sxs-lookup"><span data-stu-id="3b622-124">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
