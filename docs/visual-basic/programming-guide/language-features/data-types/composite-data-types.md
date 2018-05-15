---
title: Złożone typy danych (Visual Basic)
ms.date: 04/25/2017
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types [Visual Basic]
- composite data types [Visual Basic]
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures [Visual Basic], composite data types
- classes [Visual Basic], composite types
- types [Visual Basic], composite
ms.assetid: 62970f2e-52c0-4369-8963-613820f1f434
ms.openlocfilehash: 73867a5881db7c94d258e8716c4ff4c5b1119e71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="composite-data-types-visual-basic"></a><span data-ttu-id="825fa-102">Złożone typy danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="825fa-102">Composite Data Types (Visual Basic)</span></span>
<span data-ttu-id="825fa-103">Oprócz dostaw Visual Basic typy podstawowe dane, można złożyć elementów różnego typu, aby utworzyć *złożone typy danych* takich jak klasy, tablic i struktury.</span><span class="sxs-lookup"><span data-stu-id="825fa-103">In addition to the elementary data types Visual Basic supplies, you can also assemble items of different types to create *composite data types* such as structures, arrays, and classes.</span></span> <span data-ttu-id="825fa-104">Złożone typy danych można tworzyć z typów podstawowych i innych typów złożonych.</span><span class="sxs-lookup"><span data-stu-id="825fa-104">You can build composite data types from elementary types and from other composite types.</span></span> <span data-ttu-id="825fa-105">Na przykład można zdefiniować tablicę elementów struktury lub struktura z tablicy elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="825fa-105">For example, you can define an array of structure elements, or a structure with array members.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="825fa-106">Typy danych</span><span class="sxs-lookup"><span data-stu-id="825fa-106">Data Types</span></span>  
 <span data-ttu-id="825fa-107">Typ złożony jest inny niż typ danych dowolnego z jego składników.</span><span class="sxs-lookup"><span data-stu-id="825fa-107">A composite type is different from the data type of any of its components.</span></span> <span data-ttu-id="825fa-108">Na przykład tablicę `Integer` nie ma elementów `Integer` typu danych.</span><span class="sxs-lookup"><span data-stu-id="825fa-108">For example, an array of `Integer` elements is not of the `Integer` data type.</span></span>  
  
 <span data-ttu-id="825fa-109">Typ tablicy danych zwykle odpowiada za pomocą typu elementu, nawiasy i przecinkami w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="825fa-109">An array data type is normally represented using the element type, parentheses, and commas as necessary.</span></span> <span data-ttu-id="825fa-110">Na przykład tablicą jednowymiarową z `String` elementów jest reprezentowany jako `String()`i jest tablicą dwuwymiarową z `Boolean` elementów jest reprezentowany jako `Boolean(,)`.</span><span class="sxs-lookup"><span data-stu-id="825fa-110">For example, a one-dimensional array of `String` elements is represented as `String()`, and a two-dimensional array of `Boolean` elements is represented as `Boolean(,)`.</span></span>  
  
## <a name="structure-types"></a><span data-ttu-id="825fa-111">Typy struktur</span><span class="sxs-lookup"><span data-stu-id="825fa-111">Structure Types</span></span>  
 <span data-ttu-id="825fa-112">Nie ma typu danych jednego obejmujące wszystkie struktury.</span><span class="sxs-lookup"><span data-stu-id="825fa-112">There is no single data type comprising all structures.</span></span> <span data-ttu-id="825fa-113">Zamiast tego każdej definicji struktury reprezentuje typ unikatowy danych, nawet jeśli dwie struktury zdefiniować identyczne elementy w tej samej kolejności.</span><span class="sxs-lookup"><span data-stu-id="825fa-113">Instead, each definition of a structure represents a unique data type, even if two structures define identical elements in the same order.</span></span> <span data-ttu-id="825fa-114">Jednak po utworzeniu co najmniej dwa wystąpienia tej samej struktury języka Visual Basic traktuje je tego samego typu danych.</span><span class="sxs-lookup"><span data-stu-id="825fa-114">However, if you create two or more instances of the same structure, Visual Basic considers them to be of the same data type.</span></span>  
  
## <a name="tuples"></a><span data-ttu-id="825fa-115">Krotki</span><span class="sxs-lookup"><span data-stu-id="825fa-115">Tuples</span></span>

<span data-ttu-id="825fa-116">Krotka jest strukturą lekkie, która zawiera dwa lub więcej pól, których typy są wstępnie zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="825fa-116">A tuple is a lightweight structure that contains two or more fields whose types are predefined.</span></span> <span data-ttu-id="825fa-117">Spójne kolekcje są obsługiwane w programie Visual Basic 2017 r.</span><span class="sxs-lookup"><span data-stu-id="825fa-117">Tuples are supported starting with Visual Basic 2017.</span></span> <span data-ttu-id="825fa-118">Spójne kolekcje są najczęściej używane do zwrócenia wiele wartości z wywołania metody pojedynczego bez konieczności przekazywać argumentów przez odwołanie lub pakowania zwrócony pól w bardziej ciężki klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="825fa-118">Tuples are most commonly used to return multiple values from a single method call without having to pass arguments by reference or packaging the returned fields in a more heavy-weight class or structure.</span></span> <span data-ttu-id="825fa-119">Zobacz [krotek](tuples.md) tematu, aby uzyskać więcej informacji na temat spójnych kolekcji.</span><span class="sxs-lookup"><span data-stu-id="825fa-119">See the [Tuples](tuples.md) topic for more information on tuples.</span></span>

## <a name="array-types"></a><span data-ttu-id="825fa-120">Typy tablic</span><span class="sxs-lookup"><span data-stu-id="825fa-120">Array Types</span></span>  
 <span data-ttu-id="825fa-121">Nie ma typu danych jednego obejmujące wszystkie tablice.</span><span class="sxs-lookup"><span data-stu-id="825fa-121">There is no single data type comprising all arrays.</span></span> <span data-ttu-id="825fa-122">Typ danych konkretnego wystąpienia tablicy jest określany przez następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="825fa-122">The data type of a particular instance of an array is determined by the following:</span></span>  
  
-   <span data-ttu-id="825fa-123">Fakt trwa tablicy</span><span class="sxs-lookup"><span data-stu-id="825fa-123">The fact of being an array</span></span>  
  
-   <span data-ttu-id="825fa-124">Rangą tablicy (liczba wymiarów)</span><span class="sxs-lookup"><span data-stu-id="825fa-124">The rank (number of dimensions) of the array</span></span>  
  
-   <span data-ttu-id="825fa-125">Typ elementu tablicy</span><span class="sxs-lookup"><span data-stu-id="825fa-125">The element type of the array</span></span>  
  
 <span data-ttu-id="825fa-126">W szczególności długość danego wymiaru nie jest częścią typ danych wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="825fa-126">In particular, the length of a given dimension is not part of the instance's data type.</span></span> <span data-ttu-id="825fa-127">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="825fa-127">The following example illustrates this.</span></span>  
  
```  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 <span data-ttu-id="825fa-128">W powyższym przykładzie tablicy zmienne `arrayA` i `arrayB` są uważane za tego samego typu danych — `Byte()` — nawet jeśli są one inicjowane różne długości.</span><span class="sxs-lookup"><span data-stu-id="825fa-128">In the preceding example, array variables `arrayA` and `arrayB` are considered to be of the same data type — `Byte()` — even though they are initialized to different lengths.</span></span> <span data-ttu-id="825fa-129">Zmienne `arrayB` i `arrayC` nie są tego samego typu, ponieważ ich typy elementów są różne.</span><span class="sxs-lookup"><span data-stu-id="825fa-129">Variables `arrayB` and `arrayC` are not of the same type because their element types are different.</span></span> <span data-ttu-id="825fa-130">Zmienne `arrayC` i `arrayD` nie są tego samego typu, ponieważ różnią się ich rangi.</span><span class="sxs-lookup"><span data-stu-id="825fa-130">Variables `arrayC` and `arrayD` are not of the same type because their ranks are different.</span></span> <span data-ttu-id="825fa-131">Zmienne `arrayD` i `arrayE` mają ten sam typ — `Short(,)` — ponieważ ich rangi i typy elementu są takie same, nawet jeśli `arrayD` nie została jeszcze zainicjowana.</span><span class="sxs-lookup"><span data-stu-id="825fa-131">Variables `arrayD` and `arrayE` have the same type — `Short(,)` — because their ranks and element types are the same, even though `arrayD` is not yet initialized.</span></span>  
  
 <span data-ttu-id="825fa-132">Aby uzyskać więcej informacji na tablice, zobacz [tablice](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="825fa-132">For more information on arrays, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="class-types"></a><span data-ttu-id="825fa-133">Typy klas</span><span class="sxs-lookup"><span data-stu-id="825fa-133">Class Types</span></span>  
 <span data-ttu-id="825fa-134">Nie ma typu danych jednego zawierający wszystkie klasy.</span><span class="sxs-lookup"><span data-stu-id="825fa-134">There is no single data type comprising all classes.</span></span> <span data-ttu-id="825fa-135">Mimo że jednej klasy mogą dziedziczyć z innej klasy, każdy jest typem danych.</span><span class="sxs-lookup"><span data-stu-id="825fa-135">Although one class can inherit from another class, each is a separate data type.</span></span> <span data-ttu-id="825fa-136">Wiele wystąpień tej samej klasy są tego samego typu danych.</span><span class="sxs-lookup"><span data-stu-id="825fa-136">Multiple instances of the same class are of the same data type.</span></span> <span data-ttu-id="825fa-137">Po przypisaniu co zmienna wystąpienia klasy do innego, nie tylko mają ten sam typ danych, wskazywać tego samego wystąpienia klasy w pamięci.</span><span class="sxs-lookup"><span data-stu-id="825fa-137">If you assign one class instance variable to another, not only do they have the same data type, they point to the same class instance in memory.</span></span>  
  
 <span data-ttu-id="825fa-138">Aby uzyskać więcej informacji na temat klas, zobacz [obiekty i klasy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span><span class="sxs-lookup"><span data-stu-id="825fa-138">For more information on classes, see [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="825fa-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="825fa-139">See Also</span></span>  
 [<span data-ttu-id="825fa-140">Typy danych</span><span class="sxs-lookup"><span data-stu-id="825fa-140">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="825fa-141">Typy danych podstawowych</span><span class="sxs-lookup"><span data-stu-id="825fa-141">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [<span data-ttu-id="825fa-142">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="825fa-142">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="825fa-143">Typy wartości i odwołań</span><span class="sxs-lookup"><span data-stu-id="825fa-143">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="825fa-144">Konwersje typów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="825fa-144">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="825fa-145">Struktury</span><span class="sxs-lookup"><span data-stu-id="825fa-145">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="825fa-146">Rozwiązywanie problemów związanych z typami danych</span><span class="sxs-lookup"><span data-stu-id="825fa-146">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="825fa-147">Instrukcje: utrzymywanie więcej niż jednej wartości w zmiennej</span><span class="sxs-lookup"><span data-stu-id="825fa-147">How to: Hold More Than One Value in a Variable</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)
