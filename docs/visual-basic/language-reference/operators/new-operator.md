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
ms.openlocfilehash: 36cf71529b1f81c27881638d788117222c37171d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955881"
---
# <a name="new-operator-visual-basic"></a><span data-ttu-id="580dd-102">New — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="580dd-102">New Operator (Visual Basic)</span></span>
<span data-ttu-id="580dd-103">Wprowadza klauzulę do utworzenia nowego wystąpienia obiektu, określa ograniczenie konstruktora dla parametru typu lub `Sub` identyfikuje procedurę jako konstruktora klasy. `New`</span><span class="sxs-lookup"><span data-stu-id="580dd-103">Introduces a `New` clause to create a new object instance, specifies a constructor constraint on a type parameter, or identifies a `Sub` procedure as a class constructor.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="580dd-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="580dd-104">Remarks</span></span>  
 <span data-ttu-id="580dd-105">W deklaracji lub przypisaniu `New` klauzula musi określać zdefiniowaną klasę, z której można utworzyć wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="580dd-105">In a declaration or assignment statement, a `New` clause must specify a defined class from which the instance can be created.</span></span> <span data-ttu-id="580dd-106">Oznacza to, że klasa musi uwidaczniać jeden lub więcej konstruktorów, do których kod wywołujący może uzyskać dostęp.</span><span class="sxs-lookup"><span data-stu-id="580dd-106">This means that the class must expose one or more constructors that the calling code can access.</span></span>  
  
 <span data-ttu-id="580dd-107">Można użyć `New` klauzuli w instrukcji deklaracji lub instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="580dd-107">You can use a `New` clause in a declaration statement or an assignment statement.</span></span> <span data-ttu-id="580dd-108">Po uruchomieniu instrukcji wywołuje odpowiedni Konstruktor określonej klasy, przekazując wszystkie podane argumenty.</span><span class="sxs-lookup"><span data-stu-id="580dd-108">When the statement runs, it calls the appropriate constructor of the specified class, passing any arguments you have supplied.</span></span> <span data-ttu-id="580dd-109">Poniższy przykład ilustruje to przez utworzenie wystąpień `Customer` klasy, która ma dwa konstruktory, jeden, który nie przyjmuje parametrów i jeden, który pobiera parametr ciągu.</span><span class="sxs-lookup"><span data-stu-id="580dd-109">The following example demonstrates this by creating instances of a `Customer` class that has two constructors, one that takes no parameters and one that takes a string parameter.</span></span>  
  
 [!code-vb[VbVbalrKeywords#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#11)]  
  
 <span data-ttu-id="580dd-110">Ponieważ tablice są klasami `New` , można utworzyć nowe wystąpienie tablicy, jak pokazano w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="580dd-110">Since arrays are classes, `New` can create a new array instance, as shown in the following examples.</span></span>  
  
 [!code-vb[VbVbalrKeywords#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#12)]  
  
 <span data-ttu-id="580dd-111">Środowisko uruchomieniowe języka wspólnego (CLR) zgłasza <xref:System.OutOfMemoryException> błąd, jeśli nie ma wystarczającej ilości pamięci do utworzenia nowego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="580dd-111">The common language runtime (CLR) throws an <xref:System.OutOfMemoryException> error if there is insufficient memory to create the new instance.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="580dd-112">`New` Słowo kluczowe jest również używane na listach parametrów typu, aby określić, że dostarczony typ musi uwidaczniać dostępny Konstruktor bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="580dd-112">The `New` keyword is also used in type parameter lists to specify that the supplied type must expose an accessible parameterless constructor.</span></span> <span data-ttu-id="580dd-113">Aby uzyskać więcej informacji o parametrach typu i ograniczeniach, zobacz [list typów](../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="580dd-113">For more information about type parameters and constraints, see [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
 <span data-ttu-id="580dd-114">Aby utworzyć procedurę konstruktora dla klasy, należy ustawić nazwę `Sub` procedury `New` dla słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="580dd-114">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="580dd-115">Aby uzyskać więcej informacji, [Zobacz okres istnienia obiektu: Jak obiekty są tworzone i niszczone](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="580dd-115">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>  
  
 <span data-ttu-id="580dd-116">Słowa kluczowego `New` można używać w następujących kontekstach:</span><span class="sxs-lookup"><span data-stu-id="580dd-116">The `New` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="580dd-117">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="580dd-117">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="580dd-118">Z</span><span class="sxs-lookup"><span data-stu-id="580dd-118">Of</span></span>](../../../visual-basic/language-reference/statements/of-clause.md)  
  
 [<span data-ttu-id="580dd-119">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="580dd-119">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="580dd-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="580dd-120">See also</span></span>

- <xref:System.OutOfMemoryException>
- [<span data-ttu-id="580dd-121">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="580dd-121">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="580dd-122">Lista typów</span><span class="sxs-lookup"><span data-stu-id="580dd-122">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
- [<span data-ttu-id="580dd-123">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="580dd-123">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="580dd-124">Okres istnienia obiektu: Jak obiekty są tworzone i niszczone</span><span class="sxs-lookup"><span data-stu-id="580dd-124">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
