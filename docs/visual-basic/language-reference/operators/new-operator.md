---
title: New — Operator (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: dda23ef3ff49bd32474f39f5ae1807e57bdc2a62
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980467"
---
# <a name="new-operator-visual-basic"></a><span data-ttu-id="21a92-102">New — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21a92-102">New Operator (Visual Basic)</span></span>
<span data-ttu-id="21a92-103">Wprowadza `New` klauzulę, aby utworzyć nowe wystąpienie obiektu określa ograniczenie konstruktora dla parametru typu lub identyfikuje `Sub` procedury jak konstruktora klasy.</span><span class="sxs-lookup"><span data-stu-id="21a92-103">Introduces a `New` clause to create a new object instance, specifies a constructor constraint on a type parameter, or identifies a `Sub` procedure as a class constructor.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21a92-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="21a92-104">Remarks</span></span>  
 <span data-ttu-id="21a92-105">W deklaracji lub instrukcji przypisania `New` klauzula musi określać zdefiniowana klasa, z którego można utworzyć wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="21a92-105">In a declaration or assignment statement, a `New` clause must specify a defined class from which the instance can be created.</span></span> <span data-ttu-id="21a92-106">Oznacza to, że klasa musi ujawniać jeden lub więcej konstruktorów, które mogą uzyskiwać dostęp do kodu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="21a92-106">This means that the class must expose one or more constructors that the calling code can access.</span></span>  
  
 <span data-ttu-id="21a92-107">Możesz użyć `New` klauzuli w instrukcji deklaracji lub instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="21a92-107">You can use a `New` clause in a declaration statement or an assignment statement.</span></span> <span data-ttu-id="21a92-108">Po uruchomieniu instrukcja wywołuje odpowiedniego konstruktora określonej klasy, przekazując dowolne argumenty, które zostały wprowadzone.</span><span class="sxs-lookup"><span data-stu-id="21a92-108">When the statement runs, it calls the appropriate constructor of the specified class, passing any arguments you have supplied.</span></span> <span data-ttu-id="21a92-109">Poniższy przykład przedstawia to przez utworzenie wystąpienia `Customer` klasy, która ma dwa konstruktory: jedną, która nie przyjmuje żadnych parametrów, a ta, która przyjmuje jako parametr ciągu.</span><span class="sxs-lookup"><span data-stu-id="21a92-109">The following example demonstrates this by creating instances of a `Customer` class that has two constructors, one that takes no parameters and one that takes a string parameter.</span></span>  
  
 [!code-vb[VbVbalrKeywords#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#11)]  
  
 <span data-ttu-id="21a92-110">Ponieważ tablice są klasami, `New` można utworzyć nowego wystąpienia tablicy, jak pokazano w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="21a92-110">Since arrays are classes, `New` can create a new array instance, as shown in the following examples.</span></span>  
  
 [!code-vb[VbVbalrKeywords#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#12)]  
  
 <span data-ttu-id="21a92-111">Środowisko uruchomieniowe języka wspólnego (CLR) zgłasza <xref:System.OutOfMemoryException> błąd, jeśli ma za mało pamięci do utworzenia nowego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="21a92-111">The common language runtime (CLR) throws an <xref:System.OutOfMemoryException> error if there is insufficient memory to create the new instance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="21a92-112">`New` Słowo kluczowe jest również używane w liście parametrów typu do określenia, czy podany typ należy ujawnić dostępny konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="21a92-112">The `New` keyword is also used in type parameter lists to specify that the supplied type must expose an accessible parameterless constructor.</span></span> <span data-ttu-id="21a92-113">Aby uzyskać więcej informacji na temat parametrów typu i ograniczeń, zobacz [lista typów](../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="21a92-113">For more information about type parameters and constraints, see [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
 <span data-ttu-id="21a92-114">Aby utworzyć procedurę konstruktora dla klasy, ustaw nazwę `Sub` procedury, aby `New` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="21a92-114">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="21a92-115">Aby uzyskać więcej informacji, zobacz [okres istnienia obiektów: Jak obiekty są tworzone i niszczone](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="21a92-115">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>  
  
 <span data-ttu-id="21a92-116">Słowa kluczowego `New` można używać w następujących kontekstach:</span><span class="sxs-lookup"><span data-stu-id="21a92-116">The `New` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="21a92-117">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="21a92-117">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="21a92-118">z</span><span class="sxs-lookup"><span data-stu-id="21a92-118">Of</span></span>](../../../visual-basic/language-reference/statements/of-clause.md)  
  
 [<span data-ttu-id="21a92-119">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="21a92-119">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="21a92-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="21a92-120">See also</span></span>
- <xref:System.OutOfMemoryException>
- [<span data-ttu-id="21a92-121">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="21a92-121">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="21a92-122">Lista typów</span><span class="sxs-lookup"><span data-stu-id="21a92-122">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
- [<span data-ttu-id="21a92-123">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="21a92-123">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="21a92-124">Okres istnienia obiektów: Jak obiekty są tworzone i niszczone</span><span class="sxs-lookup"><span data-stu-id="21a92-124">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
