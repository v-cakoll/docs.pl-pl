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
ms.openlocfilehash: c0870f4b056658a22928769c369024cdda24f354
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/23/2019
ms.locfileid: "72799038"
---
# <a name="new-operator-visual-basic"></a><span data-ttu-id="1ddea-102">New — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ddea-102">New Operator (Visual Basic)</span></span>

<span data-ttu-id="1ddea-103">Wprowadza klauzulę `New`, aby utworzyć nowe wystąpienie obiektu, określa ograniczenie konstruktora dla parametru typu lub identyfikuje procedurę `Sub` jako konstruktora klasy.</span><span class="sxs-lookup"><span data-stu-id="1ddea-103">Introduces a `New` clause to create a new object instance, specifies a constructor constraint on a type parameter, or identifies a `Sub` procedure as a class constructor.</span></span>

## <a name="remarks"></a><span data-ttu-id="1ddea-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1ddea-104">Remarks</span></span>

<span data-ttu-id="1ddea-105">W deklaracji lub przypisaniu klauzula `New` musi określać zdefiniowaną klasę, z której można utworzyć wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="1ddea-105">In a declaration or assignment statement, a `New` clause must specify a defined class from which the instance can be created.</span></span> <span data-ttu-id="1ddea-106">Oznacza to, że klasa musi uwidaczniać jeden lub więcej konstruktorów, do których kod wywołujący może uzyskać dostęp.</span><span class="sxs-lookup"><span data-stu-id="1ddea-106">This means that the class must expose one or more constructors that the calling code can access.</span></span>

<span data-ttu-id="1ddea-107">Można użyć klauzuli `New` w instrukcji deklaracji lub instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="1ddea-107">You can use a `New` clause in a declaration statement or an assignment statement.</span></span> <span data-ttu-id="1ddea-108">Po uruchomieniu instrukcji wywołuje odpowiedni Konstruktor określonej klasy, przekazując wszystkie podane argumenty.</span><span class="sxs-lookup"><span data-stu-id="1ddea-108">When the statement runs, it calls the appropriate constructor of the specified class, passing any arguments you have supplied.</span></span> <span data-ttu-id="1ddea-109">Poniższy przykład ilustruje to przez utworzenie wystąpień klasy `Customer`, która ma dwa konstruktory, jeden, który nie przyjmuje parametrów i jeden z nich przyjmuje parametr String:</span><span class="sxs-lookup"><span data-stu-id="1ddea-109">The following example demonstrates this by creating instances of a `Customer` class that has two constructors, one that takes no parameters and one that takes a string parameter:</span></span>

[!code-vb[VbVbalrKeywords#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#11)]

<span data-ttu-id="1ddea-110">Ponieważ tablice są klasami, `New` może utworzyć nowe wystąpienie tablicy, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="1ddea-110">Since arrays are classes, `New` can create a new array instance, as shown in the following example:</span></span>

[!code-vb[VbVbalrKeywords#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#12)]

<span data-ttu-id="1ddea-111">Środowisko uruchomieniowe języka wspólnego (CLR) zgłasza błąd <xref:System.OutOfMemoryException>, jeśli nie ma wystarczającej ilości pamięci do utworzenia nowego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="1ddea-111">The common language runtime (CLR) throws an <xref:System.OutOfMemoryException> error if there is insufficient memory to create the new instance.</span></span>

> [!NOTE]
> <span data-ttu-id="1ddea-112">Słowo kluczowe `New` jest również używane na listach parametrów typu, aby określić, że dostarczony typ musi uwidaczniać dostępny Konstruktor bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="1ddea-112">The `New` keyword is also used in type parameter lists to specify that the supplied type must expose an accessible parameterless constructor.</span></span> <span data-ttu-id="1ddea-113">Aby uzyskać więcej informacji o parametrach typu i ograniczeniach, zobacz [list typów](../statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="1ddea-113">For more information about type parameters and constraints, see [Type List](../statements/type-list.md).</span></span>

<span data-ttu-id="1ddea-114">Aby utworzyć procedurę konstruktora dla klasy, należy ustawić nazwę procedury `Sub` na słowo kluczowe `New`.</span><span class="sxs-lookup"><span data-stu-id="1ddea-114">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="1ddea-115">Aby uzyskać więcej informacji, zobacz [okres istnienia obiektu: sposób tworzenia i zniszczenia obiektów](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="1ddea-115">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>

<span data-ttu-id="1ddea-116">Słowa kluczowego `New` można użyć w tych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="1ddea-116">The `New` keyword can be used in these contexts:</span></span>

- [<span data-ttu-id="1ddea-117">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1ddea-117">Dim Statement</span></span>](../statements/dim-statement.md)
- [<span data-ttu-id="1ddea-118">Z</span><span class="sxs-lookup"><span data-stu-id="1ddea-118">Of</span></span>](../statements/of-clause.md)
- [<span data-ttu-id="1ddea-119">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1ddea-119">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="1ddea-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1ddea-120">See also</span></span>

- <xref:System.OutOfMemoryException>
- [<span data-ttu-id="1ddea-121">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="1ddea-121">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="1ddea-122">Lista typów</span><span class="sxs-lookup"><span data-stu-id="1ddea-122">Type List</span></span>](../statements/type-list.md)
- [<span data-ttu-id="1ddea-123">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1ddea-123">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="1ddea-124">Okres istnienia obiektów: w jaki sposób obiekty są tworzone i niszczone</span><span class="sxs-lookup"><span data-stu-id="1ddea-124">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
