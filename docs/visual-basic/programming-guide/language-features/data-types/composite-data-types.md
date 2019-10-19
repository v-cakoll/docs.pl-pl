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
ms.openlocfilehash: 768559c7a6caf064f7529786675e51ce19667d6b
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581716"
---
# <a name="composite-data-types-visual-basic"></a><span data-ttu-id="205c1-102">Złożone typy danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="205c1-102">Composite Data Types (Visual Basic)</span></span>
<span data-ttu-id="205c1-103">Oprócz podstawowych typów danych Visual Basic dostaw, można także złożyć elementy różnych typów w celu utworzenia *złożonych typów danych* , takich jak struktury, tablice i klasy.</span><span class="sxs-lookup"><span data-stu-id="205c1-103">In addition to the elementary data types Visual Basic supplies, you can also assemble items of different types to create *composite data types* such as structures, arrays, and classes.</span></span> <span data-ttu-id="205c1-104">Można tworzyć złożone typy danych z typów podstawowych i z innych typów złożonych.</span><span class="sxs-lookup"><span data-stu-id="205c1-104">You can build composite data types from elementary types and from other composite types.</span></span> <span data-ttu-id="205c1-105">Na przykład można zdefiniować tablicę elementów struktury lub strukturę z elementami członkowskimi tablicy.</span><span class="sxs-lookup"><span data-stu-id="205c1-105">For example, you can define an array of structure elements, or a structure with array members.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="205c1-106">Typy danych</span><span class="sxs-lookup"><span data-stu-id="205c1-106">Data Types</span></span>  
 <span data-ttu-id="205c1-107">Typ złożony różni się od typu danych któregokolwiek z jego składników.</span><span class="sxs-lookup"><span data-stu-id="205c1-107">A composite type is different from the data type of any of its components.</span></span> <span data-ttu-id="205c1-108">Na przykład tablica elementów `Integer` nie jest typu danych `Integer`.</span><span class="sxs-lookup"><span data-stu-id="205c1-108">For example, an array of `Integer` elements is not of the `Integer` data type.</span></span>  
  
 <span data-ttu-id="205c1-109">Typ danych tablicy jest zwykle reprezentowany przy użyciu typu elementu, nawiasów i przecinków w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="205c1-109">An array data type is normally represented using the element type, parentheses, and commas as necessary.</span></span> <span data-ttu-id="205c1-110">Na przykład Jednowymiarowa tablica elementów `String` jest reprezentowana jako `String()`, a Dwuwymiarowa tablica elementów `Boolean` jest reprezentowana jako `Boolean(,)`.</span><span class="sxs-lookup"><span data-stu-id="205c1-110">For example, a one-dimensional array of `String` elements is represented as `String()`, and a two-dimensional array of `Boolean` elements is represented as `Boolean(,)`.</span></span>  
  
## <a name="structure-types"></a><span data-ttu-id="205c1-111">Typy struktur</span><span class="sxs-lookup"><span data-stu-id="205c1-111">Structure Types</span></span>  
 <span data-ttu-id="205c1-112">Nie istnieje pojedynczy typ danych obejmujący wszystkie struktury.</span><span class="sxs-lookup"><span data-stu-id="205c1-112">There is no single data type comprising all structures.</span></span> <span data-ttu-id="205c1-113">Zamiast tego każda definicja struktury reprezentuje unikatowy typ danych, nawet jeśli dwie struktury definiują identyczne elementy w tej samej kolejności.</span><span class="sxs-lookup"><span data-stu-id="205c1-113">Instead, each definition of a structure represents a unique data type, even if two structures define identical elements in the same order.</span></span> <span data-ttu-id="205c1-114">Jeśli jednak tworzysz dwa lub więcej wystąpień tej samej struktury, Visual Basic uznaje ich za tego samego typu danych.</span><span class="sxs-lookup"><span data-stu-id="205c1-114">However, if you create two or more instances of the same structure, Visual Basic considers them to be of the same data type.</span></span>  
  
## <a name="tuples"></a><span data-ttu-id="205c1-115">Krotki</span><span class="sxs-lookup"><span data-stu-id="205c1-115">Tuples</span></span>

<span data-ttu-id="205c1-116">Krotka jest strukturą uproszczoną, która zawiera co najmniej dwa pola, których typy są wstępnie zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="205c1-116">A tuple is a lightweight structure that contains two or more fields whose types are predefined.</span></span> <span data-ttu-id="205c1-117">Krotki są obsługiwane począwszy od Visual Basic 2017.</span><span class="sxs-lookup"><span data-stu-id="205c1-117">Tuples are supported starting with Visual Basic 2017.</span></span> <span data-ttu-id="205c1-118">Krotki są najczęściej używane do zwracania wielu wartości z pojedynczej metody wywołania bez konieczności przekazywania argumentów przez odwołanie lub pakowanie zwracanych pól w bardziej ciężkich klasach lub strukturach.</span><span class="sxs-lookup"><span data-stu-id="205c1-118">Tuples are most commonly used to return multiple values from a single method call without having to pass arguments by reference or packaging the returned fields in a more heavy-weight class or structure.</span></span> <span data-ttu-id="205c1-119">Aby uzyskać więcej informacji na temat krotek, zobacz temat [krotki](tuples.md) .</span><span class="sxs-lookup"><span data-stu-id="205c1-119">See the [Tuples](tuples.md) topic for more information on tuples.</span></span>

## <a name="array-types"></a><span data-ttu-id="205c1-120">Typy tablic</span><span class="sxs-lookup"><span data-stu-id="205c1-120">Array Types</span></span>  
 <span data-ttu-id="205c1-121">Nie istnieje pojedynczy typ danych składający się ze wszystkich tablic.</span><span class="sxs-lookup"><span data-stu-id="205c1-121">There is no single data type comprising all arrays.</span></span> <span data-ttu-id="205c1-122">Typ danych określonego wystąpienia tablicy jest określany na podstawie następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="205c1-122">The data type of a particular instance of an array is determined by the following:</span></span>  
  
- <span data-ttu-id="205c1-123">Fakt, że jest tablicą</span><span class="sxs-lookup"><span data-stu-id="205c1-123">The fact of being an array</span></span>  
  
- <span data-ttu-id="205c1-124">Ranga (liczba wymiarów) tablicy</span><span class="sxs-lookup"><span data-stu-id="205c1-124">The rank (number of dimensions) of the array</span></span>  
  
- <span data-ttu-id="205c1-125">Typ elementu tablicy</span><span class="sxs-lookup"><span data-stu-id="205c1-125">The element type of the array</span></span>  
  
 <span data-ttu-id="205c1-126">W szczególności długość danego wymiaru nie jest częścią typu danych wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="205c1-126">In particular, the length of a given dimension is not part of the instance's data type.</span></span> <span data-ttu-id="205c1-127">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="205c1-127">The following example illustrates this.</span></span>  
  
```vb  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 <span data-ttu-id="205c1-128">W poprzednim przykładzie Zmienne tablicowe `arrayA` i `arrayB` są uważane za takie same typy danych — `Byte()` — nawet jeśli są zainicjowane do różnych długości.</span><span class="sxs-lookup"><span data-stu-id="205c1-128">In the preceding example, array variables `arrayA` and `arrayB` are considered to be of the same data type — `Byte()` — even though they are initialized to different lengths.</span></span> <span data-ttu-id="205c1-129">Zmienne `arrayB` i `arrayC` nie są tego samego typu, ponieważ ich typy elementów są różne.</span><span class="sxs-lookup"><span data-stu-id="205c1-129">Variables `arrayB` and `arrayC` are not of the same type because their element types are different.</span></span> <span data-ttu-id="205c1-130">Zmienne `arrayC` i `arrayD` nie są tego samego typu, ponieważ ich Range różnią się od siebie.</span><span class="sxs-lookup"><span data-stu-id="205c1-130">Variables `arrayC` and `arrayD` are not of the same type because their ranks are different.</span></span> <span data-ttu-id="205c1-131">Zmienne `arrayD` i `arrayE` mają ten sam typ — `Short(,)` — ponieważ ich Range i typy elementów są takie same, nawet jeśli `arrayD` nie została jeszcze zainicjowana.</span><span class="sxs-lookup"><span data-stu-id="205c1-131">Variables `arrayD` and `arrayE` have the same type — `Short(,)` — because their ranks and element types are the same, even though `arrayD` is not yet initialized.</span></span>  
  
 <span data-ttu-id="205c1-132">Aby uzyskać więcej informacji na temat tablic, zobacz [tablice](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="205c1-132">For more information on arrays, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="class-types"></a><span data-ttu-id="205c1-133">Typy klas</span><span class="sxs-lookup"><span data-stu-id="205c1-133">Class Types</span></span>  
 <span data-ttu-id="205c1-134">Nie istnieje pojedynczy typ danych składający się ze wszystkich klas.</span><span class="sxs-lookup"><span data-stu-id="205c1-134">There is no single data type comprising all classes.</span></span> <span data-ttu-id="205c1-135">Chociaż jedna klasa może dziedziczyć z innej klasy, każda z nich jest osobnym typem danych.</span><span class="sxs-lookup"><span data-stu-id="205c1-135">Although one class can inherit from another class, each is a separate data type.</span></span> <span data-ttu-id="205c1-136">Wiele wystąpień tej samej klasy ma ten sam typ danych.</span><span class="sxs-lookup"><span data-stu-id="205c1-136">Multiple instances of the same class are of the same data type.</span></span> <span data-ttu-id="205c1-137">W przypadku przypisania jednej zmiennej wystąpienia klasy do innej nie tylko mają one ten sam typ danych, wskazują na to samo wystąpienie klasy w pamięci.</span><span class="sxs-lookup"><span data-stu-id="205c1-137">If you assign one class instance variable to another, not only do they have the same data type, they point to the same class instance in memory.</span></span>  
  
 <span data-ttu-id="205c1-138">Aby uzyskać więcej informacji na temat klas, zobacz [obiekty i klasy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span><span class="sxs-lookup"><span data-stu-id="205c1-138">For more information on classes, see [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="205c1-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="205c1-139">See also</span></span>

- [<span data-ttu-id="205c1-140">Typy danych</span><span class="sxs-lookup"><span data-stu-id="205c1-140">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="205c1-141">Typy danych podstawowych</span><span class="sxs-lookup"><span data-stu-id="205c1-141">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="205c1-142">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="205c1-142">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="205c1-143">Typy wartości i odwołań</span><span class="sxs-lookup"><span data-stu-id="205c1-143">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="205c1-144">Konwersje typów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="205c1-144">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="205c1-145">Struktury</span><span class="sxs-lookup"><span data-stu-id="205c1-145">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="205c1-146">Rozwiązywanie problemów związanych z typami danych</span><span class="sxs-lookup"><span data-stu-id="205c1-146">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="205c1-147">Instrukcje: utrzymywanie więcej niż jednej wartości w zmiennej</span><span class="sxs-lookup"><span data-stu-id="205c1-147">How to: Hold More Than One Value in a Variable</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)
