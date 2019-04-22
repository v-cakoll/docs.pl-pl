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
ms.openlocfilehash: 630b0c48def77449f426b287a26f95af7cfb930e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58837735"
---
# <a name="new-operator-visual-basic"></a><span data-ttu-id="8ef2b-102">New — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8ef2b-102">New Operator (Visual Basic)</span></span>
<span data-ttu-id="8ef2b-103">Wprowadza `New` klauzulę, aby utworzyć nowe wystąpienie obiektu określa ograniczenie konstruktora dla parametru typu lub identyfikuje `Sub` procedury jak konstruktora klasy.</span><span class="sxs-lookup"><span data-stu-id="8ef2b-103">Introduces a `New` clause to create a new object instance, specifies a constructor constraint on a type parameter, or identifies a `Sub` procedure as a class constructor.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ef2b-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8ef2b-104">Remarks</span></span>  
 <span data-ttu-id="8ef2b-105">W deklaracji lub instrukcji przypisania `New` klauzula musi określać zdefiniowana klasa, z którego można utworzyć wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="8ef2b-105">In a declaration or assignment statement, a `New` clause must specify a defined class from which the instance can be created.</span></span> <span data-ttu-id="8ef2b-106">Oznacza to, że klasa musi ujawniać jeden lub więcej konstruktorów, które mogą uzyskiwać dostęp do kodu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="8ef2b-106">This means that the class must expose one or more constructors that the calling code can access.</span></span>  
  
 <span data-ttu-id="8ef2b-107">Możesz użyć `New` klauzuli w instrukcji deklaracji lub instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="8ef2b-107">You can use a `New` clause in a declaration statement or an assignment statement.</span></span> <span data-ttu-id="8ef2b-108">Po uruchomieniu instrukcja wywołuje odpowiedniego konstruktora określonej klasy, przekazując dowolne argumenty, które zostały wprowadzone.</span><span class="sxs-lookup"><span data-stu-id="8ef2b-108">When the statement runs, it calls the appropriate constructor of the specified class, passing any arguments you have supplied.</span></span> <span data-ttu-id="8ef2b-109">Poniższy przykład przedstawia to przez utworzenie wystąpienia `Customer` klasy, która ma dwa konstruktory: jedną, która nie przyjmuje żadnych parametrów, a ta, która przyjmuje jako parametr ciągu.</span><span class="sxs-lookup"><span data-stu-id="8ef2b-109">The following example demonstrates this by creating instances of a `Customer` class that has two constructors, one that takes no parameters and one that takes a string parameter.</span></span>  
  
 [!code-vb[VbVbalrKeywords#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#11)]  
  
 <span data-ttu-id="8ef2b-110">Ponieważ tablice są klasami, `New` można utworzyć nowego wystąpienia tablicy, jak pokazano w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="8ef2b-110">Since arrays are classes, `New` can create a new array instance, as shown in the following examples.</span></span>  
  
 [!code-vb[VbVbalrKeywords#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#12)]  
  
 <span data-ttu-id="8ef2b-111">Środowisko uruchomieniowe języka wspólnego (CLR) zgłasza <xref:System.OutOfMemoryException> błąd, jeśli ma za mało pamięci do utworzenia nowego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="8ef2b-111">The common language runtime (CLR) throws an <xref:System.OutOfMemoryException> error if there is insufficient memory to create the new instance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ef2b-112">`New` Słowo kluczowe jest również używane w liście parametrów typu do określenia, czy podany typ należy ujawnić dostępny konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="8ef2b-112">The `New` keyword is also used in type parameter lists to specify that the supplied type must expose an accessible parameterless constructor.</span></span> <span data-ttu-id="8ef2b-113">Aby uzyskać więcej informacji na temat parametrów typu i ograniczeń, zobacz [lista typów](../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="8ef2b-113">For more information about type parameters and constraints, see [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
 <span data-ttu-id="8ef2b-114">Aby utworzyć procedurę konstruktora dla klasy, ustaw nazwę `Sub` procedury, aby `New` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="8ef2b-114">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="8ef2b-115">Aby uzyskać więcej informacji, zobacz [okres istnienia obiektów: Jak obiekty są tworzone i niszczone](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="8ef2b-115">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>  
  
 <span data-ttu-id="8ef2b-116">Słowa kluczowego `New` można używać w następujących kontekstach:</span><span class="sxs-lookup"><span data-stu-id="8ef2b-116">The `New` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="8ef2b-117">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="8ef2b-117">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="8ef2b-118">z</span><span class="sxs-lookup"><span data-stu-id="8ef2b-118">Of</span></span>](../../../visual-basic/language-reference/statements/of-clause.md)  
  
 [<span data-ttu-id="8ef2b-119">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="8ef2b-119">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="8ef2b-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8ef2b-120">See also</span></span>

- <xref:System.OutOfMemoryException>
- [<span data-ttu-id="8ef2b-121">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="8ef2b-121">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="8ef2b-122">Lista typów</span><span class="sxs-lookup"><span data-stu-id="8ef2b-122">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
- [<span data-ttu-id="8ef2b-123">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8ef2b-123">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="8ef2b-124">Okres istnienia obiektów: Jak obiekty są tworzone i niszczone</span><span class="sxs-lookup"><span data-stu-id="8ef2b-124">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
