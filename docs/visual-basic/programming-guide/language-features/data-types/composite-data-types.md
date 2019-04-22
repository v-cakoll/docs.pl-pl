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
ms.openlocfilehash: ea719b60a6bcd40494666d4923fad296a8ddae70
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58833818"
---
# <a name="composite-data-types-visual-basic"></a><span data-ttu-id="14318-102">Złożone typy danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="14318-102">Composite Data Types (Visual Basic)</span></span>
<span data-ttu-id="14318-103">Oprócz danych podstawowych typów języka Visual Basic dostaw, również można grupować elementy o różnych typach, aby utworzyć *złożone typy danych* takich jak klasy, tablic i struktur.</span><span class="sxs-lookup"><span data-stu-id="14318-103">In addition to the elementary data types Visual Basic supplies, you can also assemble items of different types to create *composite data types* such as structures, arrays, and classes.</span></span> <span data-ttu-id="14318-104">Możesz tworzyć złożone typy danych, z typów podstawowych i z innych typów złożonych.</span><span class="sxs-lookup"><span data-stu-id="14318-104">You can build composite data types from elementary types and from other composite types.</span></span> <span data-ttu-id="14318-105">Na przykład można zdefiniować tablicę elementy struktury lub struktury z tablicy elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="14318-105">For example, you can define an array of structure elements, or a structure with array members.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="14318-106">Typy danych</span><span class="sxs-lookup"><span data-stu-id="14318-106">Data Types</span></span>  
 <span data-ttu-id="14318-107">Typ złożony różni się od typu danych żadnej z jej składników.</span><span class="sxs-lookup"><span data-stu-id="14318-107">A composite type is different from the data type of any of its components.</span></span> <span data-ttu-id="14318-108">Na przykład tablica `Integer` nie ma elementów `Integer` typu danych.</span><span class="sxs-lookup"><span data-stu-id="14318-108">For example, an array of `Integer` elements is not of the `Integer` data type.</span></span>  
  
 <span data-ttu-id="14318-109">Typ danych tablicy jest zwykle reprezentowany za pomocą typu elementu, nawiasy i przecinki, zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="14318-109">An array data type is normally represented using the element type, parentheses, and commas as necessary.</span></span> <span data-ttu-id="14318-110">Na przykład Jednowymiarowa tablica `String` elementy są reprezentowane jako `String()`i dwuwymiarową tablicę `Boolean` elementy są reprezentowane jako `Boolean(,)`.</span><span class="sxs-lookup"><span data-stu-id="14318-110">For example, a one-dimensional array of `String` elements is represented as `String()`, and a two-dimensional array of `Boolean` elements is represented as `Boolean(,)`.</span></span>  
  
## <a name="structure-types"></a><span data-ttu-id="14318-111">Typy struktur</span><span class="sxs-lookup"><span data-stu-id="14318-111">Structure Types</span></span>  
 <span data-ttu-id="14318-112">Nie ma żadnych single — typ danych obejmujące wszystkie struktury.</span><span class="sxs-lookup"><span data-stu-id="14318-112">There is no single data type comprising all structures.</span></span> <span data-ttu-id="14318-113">Zamiast tego każda definicja struktury reprezentuje typ unikatowe dane, nawet wtedy, gdy dwie struktury zdefiniować identyczne elementy w tej samej kolejności.</span><span class="sxs-lookup"><span data-stu-id="14318-113">Instead, each definition of a structure represents a unique data type, even if two structures define identical elements in the same order.</span></span> <span data-ttu-id="14318-114">Jednak jeśli tworzysz tę samą strukturę co najmniej dwóch wystąpień, Visual Basic traktuje je tego samego typu danych.</span><span class="sxs-lookup"><span data-stu-id="14318-114">However, if you create two or more instances of the same structure, Visual Basic considers them to be of the same data type.</span></span>  
  
## <a name="tuples"></a><span data-ttu-id="14318-115">Krotki</span><span class="sxs-lookup"><span data-stu-id="14318-115">Tuples</span></span>

<span data-ttu-id="14318-116">Spójna Kolekcja to lekki strukturę, która zawiera dwa lub więcej pól, których typy są wstępnie zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="14318-116">A tuple is a lightweight structure that contains two or more fields whose types are predefined.</span></span> <span data-ttu-id="14318-117">Spójne kolekcje są obsługiwane, począwszy od programu Visual Basic w 2017 r.</span><span class="sxs-lookup"><span data-stu-id="14318-117">Tuples are supported starting with Visual Basic 2017.</span></span> <span data-ttu-id="14318-118">Kolekcje są najczęściej używane zwracanie wielu wartości w pojedynczym wywołaniu metody bez konieczności przekazywać argumentów przez odwołanie lub spakowanie zwracanego pola w bardziej ciężki klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="14318-118">Tuples are most commonly used to return multiple values from a single method call without having to pass arguments by reference or packaging the returned fields in a more heavy-weight class or structure.</span></span> <span data-ttu-id="14318-119">Zobacz [krotek](tuples.md) tematu, aby uzyskać więcej informacji na temat krotek.</span><span class="sxs-lookup"><span data-stu-id="14318-119">See the [Tuples](tuples.md) topic for more information on tuples.</span></span>

## <a name="array-types"></a><span data-ttu-id="14318-120">Typy tablic</span><span class="sxs-lookup"><span data-stu-id="14318-120">Array Types</span></span>  
 <span data-ttu-id="14318-121">Nie ma żadnych single — typ danych wchodzących w skład wszystkich tablic.</span><span class="sxs-lookup"><span data-stu-id="14318-121">There is no single data type comprising all arrays.</span></span> <span data-ttu-id="14318-122">Typ danych konkretnego wystąpienia tablicy jest określana przez następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="14318-122">The data type of a particular instance of an array is determined by the following:</span></span>  
  
-   <span data-ttu-id="14318-123">Fakt jest tablicą</span><span class="sxs-lookup"><span data-stu-id="14318-123">The fact of being an array</span></span>  
  
-   <span data-ttu-id="14318-124">Ranga tablicy (liczba wymiarów)</span><span class="sxs-lookup"><span data-stu-id="14318-124">The rank (number of dimensions) of the array</span></span>  
  
-   <span data-ttu-id="14318-125">Typ elementu tablicy</span><span class="sxs-lookup"><span data-stu-id="14318-125">The element type of the array</span></span>  
  
 <span data-ttu-id="14318-126">W szczególności długość danego wymiaru nie jest częścią typu danych wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="14318-126">In particular, the length of a given dimension is not part of the instance's data type.</span></span> <span data-ttu-id="14318-127">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="14318-127">The following example illustrates this.</span></span>  
  
```  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 <span data-ttu-id="14318-128">W poprzednim przykładzie, tablica zmienne `arrayA` i `arrayB` są traktowane jako typu danych — `Byte()` — nawet jeśli są one inicjowane na różne długości.</span><span class="sxs-lookup"><span data-stu-id="14318-128">In the preceding example, array variables `arrayA` and `arrayB` are considered to be of the same data type — `Byte()` — even though they are initialized to different lengths.</span></span> <span data-ttu-id="14318-129">Zmienne `arrayB` i `arrayC` nie są tego samego typu, ponieważ ich typy elementów są różne.</span><span class="sxs-lookup"><span data-stu-id="14318-129">Variables `arrayB` and `arrayC` are not of the same type because their element types are different.</span></span> <span data-ttu-id="14318-130">Zmienne `arrayC` i `arrayD` nie są tego samego typu, ponieważ różnią się ich rangę.</span><span class="sxs-lookup"><span data-stu-id="14318-130">Variables `arrayC` and `arrayD` are not of the same type because their ranks are different.</span></span> <span data-ttu-id="14318-131">Zmienne `arrayD` i `arrayE` mieć taki sam typ — `Short(,)` — ponieważ ich rangę i typów elementów są takie same, nawet jeśli `arrayD` nie została jeszcze zainicjowana.</span><span class="sxs-lookup"><span data-stu-id="14318-131">Variables `arrayD` and `arrayE` have the same type — `Short(,)` — because their ranks and element types are the same, even though `arrayD` is not yet initialized.</span></span>  
  
 <span data-ttu-id="14318-132">Aby uzyskać więcej informacji na temat tablic, zobacz [tablic](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="14318-132">For more information on arrays, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="class-types"></a><span data-ttu-id="14318-133">Typy klas</span><span class="sxs-lookup"><span data-stu-id="14318-133">Class Types</span></span>  
 <span data-ttu-id="14318-134">Nie ma żadnych single — typ danych wchodzących w skład wszystkich klas.</span><span class="sxs-lookup"><span data-stu-id="14318-134">There is no single data type comprising all classes.</span></span> <span data-ttu-id="14318-135">Mimo że jednej klasy mogą dziedziczyć z innej klasy, każdy jest typem osobne dane.</span><span class="sxs-lookup"><span data-stu-id="14318-135">Although one class can inherit from another class, each is a separate data type.</span></span> <span data-ttu-id="14318-136">Wiele wystąpień tej samej klasy są tego samego typu danych.</span><span class="sxs-lookup"><span data-stu-id="14318-136">Multiple instances of the same class are of the same data type.</span></span> <span data-ttu-id="14318-137">Jeśli przypiszesz jednej zmiennej wystąpienia klasy do innego nie tylko mają ten sam typ danych, wskazują na tym samym wystąpieniu klasy w pamięci.</span><span class="sxs-lookup"><span data-stu-id="14318-137">If you assign one class instance variable to another, not only do they have the same data type, they point to the same class instance in memory.</span></span>  
  
 <span data-ttu-id="14318-138">Aby uzyskać więcej informacji na temat klas, zobacz [obiekty i klasy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span><span class="sxs-lookup"><span data-stu-id="14318-138">For more information on classes, see [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14318-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="14318-139">See also</span></span>

- [<span data-ttu-id="14318-140">Typy danych</span><span class="sxs-lookup"><span data-stu-id="14318-140">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="14318-141">Typy danych podstawowych</span><span class="sxs-lookup"><span data-stu-id="14318-141">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="14318-142">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="14318-142">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="14318-143">Typy wartości i odwołań</span><span class="sxs-lookup"><span data-stu-id="14318-143">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="14318-144">Konwersje typów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="14318-144">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="14318-145">Struktury</span><span class="sxs-lookup"><span data-stu-id="14318-145">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="14318-146">Rozwiązywanie problemów związanych z typami danych</span><span class="sxs-lookup"><span data-stu-id="14318-146">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="14318-147">Instrukcje: utrzymywanie więcej niż jednej wartości w zmiennej</span><span class="sxs-lookup"><span data-stu-id="14318-147">How to: Hold More Than One Value in a Variable</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)
