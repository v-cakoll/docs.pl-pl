---
title: "Złożone typy danych (Visual Basic)"
ms.custom: 
ms.date: 04/25/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e9adb407757dbee2f7ac5a94118623a62212faec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="composite-data-types-visual-basic"></a><span data-ttu-id="5b55a-102">Złożone typy danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5b55a-102">Composite Data Types (Visual Basic)</span></span>
<span data-ttu-id="5b55a-103">Oprócz podstawowe typy danych [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] dostaw, można również grupować elementy różnych typów, aby utworzyć *złożone typy danych* takich jak klasy, tablic i struktury.</span><span class="sxs-lookup"><span data-stu-id="5b55a-103">In addition to the elementary data types [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] supplies, you can also assemble items of different types to create *composite data types* such as structures, arrays, and classes.</span></span> <span data-ttu-id="5b55a-104">Złożone typy danych można tworzyć z typów podstawowych i innych typów złożonych.</span><span class="sxs-lookup"><span data-stu-id="5b55a-104">You can build composite data types from elementary types and from other composite types.</span></span> <span data-ttu-id="5b55a-105">Na przykład można zdefiniować tablicę elementów struktury lub struktura z tablicy elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="5b55a-105">For example, you can define an array of structure elements, or a structure with array members.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="5b55a-106">Typy danych</span><span class="sxs-lookup"><span data-stu-id="5b55a-106">Data Types</span></span>  
 <span data-ttu-id="5b55a-107">Typ złożony jest inny niż typ danych dowolnego z jego składników.</span><span class="sxs-lookup"><span data-stu-id="5b55a-107">A composite type is different from the data type of any of its components.</span></span> <span data-ttu-id="5b55a-108">Na przykład tablicę `Integer` nie ma elementów `Integer` typu danych.</span><span class="sxs-lookup"><span data-stu-id="5b55a-108">For example, an array of `Integer` elements is not of the `Integer` data type.</span></span>  
  
 <span data-ttu-id="5b55a-109">Typ tablicy danych zwykle odpowiada za pomocą typu elementu, nawiasy i przecinkami w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="5b55a-109">An array data type is normally represented using the element type, parentheses, and commas as necessary.</span></span> <span data-ttu-id="5b55a-110">Na przykład tablicą jednowymiarową z `String` elementów jest reprezentowany jako `String()`i jest tablicą dwuwymiarową z `Boolean` elementów jest reprezentowany jako `Boolean(,)`.</span><span class="sxs-lookup"><span data-stu-id="5b55a-110">For example, a one-dimensional array of `String` elements is represented as `String()`, and a two-dimensional array of `Boolean` elements is represented as `Boolean(,)`.</span></span>  
  
## <a name="structure-types"></a><span data-ttu-id="5b55a-111">Typy struktur</span><span class="sxs-lookup"><span data-stu-id="5b55a-111">Structure Types</span></span>  
 <span data-ttu-id="5b55a-112">Nie ma typu danych jednego obejmujące wszystkie struktury.</span><span class="sxs-lookup"><span data-stu-id="5b55a-112">There is no single data type comprising all structures.</span></span> <span data-ttu-id="5b55a-113">Zamiast tego każdej definicji struktury reprezentuje typ unikatowy danych, nawet jeśli dwie struktury zdefiniować identyczne elementy w tej samej kolejności.</span><span class="sxs-lookup"><span data-stu-id="5b55a-113">Instead, each definition of a structure represents a unique data type, even if two structures define identical elements in the same order.</span></span> <span data-ttu-id="5b55a-114">Jednak, w przypadku utworzenia dwóch lub więcej wystąpień tej samej struktury [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] traktuje je tego samego typu danych.</span><span class="sxs-lookup"><span data-stu-id="5b55a-114">However, if you create two or more instances of the same structure, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] considers them to be of the same data type.</span></span>  
  
## <a name="tuples"></a><span data-ttu-id="5b55a-115">Krotki</span><span class="sxs-lookup"><span data-stu-id="5b55a-115">Tuples</span></span>

<span data-ttu-id="5b55a-116">Krotka jest strukturą lekkie, która zawiera dwa lub więcej pól, których typy są wstępnie zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="5b55a-116">A tuple is a lightweight structure that contains two or more fields whose types are predefined.</span></span> <span data-ttu-id="5b55a-117">Spójne kolekcje są obsługiwane w programie Visual Basic 2017 r.</span><span class="sxs-lookup"><span data-stu-id="5b55a-117">Tuples are supported starting with Visual Basic 2017.</span></span> <span data-ttu-id="5b55a-118">Spójne kolekcje są najczęściej używane do zwrócenia wiele wartości z wywołania metody pojedynczego bez konieczności przekazywać argumentów przez odwołanie lub pakowania zwrócony pól w bardziej ciężki klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="5b55a-118">Tuples are most commonly used to return multiple values from a single method call without having to pass arguments by reference or packaging the returned fields in a more heavy-weight class or structure.</span></span> <span data-ttu-id="5b55a-119">Zobacz [krotek](tuples.md) tematu, aby uzyskać więcej informacji na temat spójnych kolekcji.</span><span class="sxs-lookup"><span data-stu-id="5b55a-119">See the [Tuples](tuples.md) topic for more information on tuples.</span></span>

## <a name="array-types"></a><span data-ttu-id="5b55a-120">Typy tablic</span><span class="sxs-lookup"><span data-stu-id="5b55a-120">Array Types</span></span>  
 <span data-ttu-id="5b55a-121">Nie ma typu danych jednego obejmujące wszystkie tablice.</span><span class="sxs-lookup"><span data-stu-id="5b55a-121">There is no single data type comprising all arrays.</span></span> <span data-ttu-id="5b55a-122">Typ danych konkretnego wystąpienia tablicy jest określany przez następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="5b55a-122">The data type of a particular instance of an array is determined by the following:</span></span>  
  
-   <span data-ttu-id="5b55a-123">Fakt trwa tablicy</span><span class="sxs-lookup"><span data-stu-id="5b55a-123">The fact of being an array</span></span>  
  
-   <span data-ttu-id="5b55a-124">Rangą tablicy (liczba wymiarów)</span><span class="sxs-lookup"><span data-stu-id="5b55a-124">The rank (number of dimensions) of the array</span></span>  
  
-   <span data-ttu-id="5b55a-125">Typ elementu tablicy</span><span class="sxs-lookup"><span data-stu-id="5b55a-125">The element type of the array</span></span>  
  
 <span data-ttu-id="5b55a-126">W szczególności długość danego wymiaru nie jest częścią typ danych wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="5b55a-126">In particular, the length of a given dimension is not part of the instance's data type.</span></span> <span data-ttu-id="5b55a-127">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="5b55a-127">The following example illustrates this.</span></span>  
  
```  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 <span data-ttu-id="5b55a-128">W powyższym przykładzie tablicy zmienne `arrayA` i `arrayB` są uważane za tego samego typu danych — `Byte()` — nawet jeśli są one inicjowane różne długości.</span><span class="sxs-lookup"><span data-stu-id="5b55a-128">In the preceding example, array variables `arrayA` and `arrayB` are considered to be of the same data type — `Byte()` — even though they are initialized to different lengths.</span></span> <span data-ttu-id="5b55a-129">Zmienne `arrayB` i `arrayC` nie są tego samego typu, ponieważ ich typy elementów są różne.</span><span class="sxs-lookup"><span data-stu-id="5b55a-129">Variables `arrayB` and `arrayC` are not of the same type because their element types are different.</span></span> <span data-ttu-id="5b55a-130">Zmienne `arrayC` i `arrayD` nie są tego samego typu, ponieważ różnią się ich rangi.</span><span class="sxs-lookup"><span data-stu-id="5b55a-130">Variables `arrayC` and `arrayD` are not of the same type because their ranks are different.</span></span> <span data-ttu-id="5b55a-131">Zmienne `arrayD` i `arrayE` mają ten sam typ — `Short(,)` — ponieważ ich rangi i typy elementu są takie same, nawet jeśli `arrayD` nie została jeszcze zainicjowana.</span><span class="sxs-lookup"><span data-stu-id="5b55a-131">Variables `arrayD` and `arrayE` have the same type — `Short(,)` — because their ranks and element types are the same, even though `arrayD` is not yet initialized.</span></span>  
  
 <span data-ttu-id="5b55a-132">Aby uzyskać więcej informacji na tablice, zobacz [tablice](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="5b55a-132">For more information on arrays, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="class-types"></a><span data-ttu-id="5b55a-133">Typy klas</span><span class="sxs-lookup"><span data-stu-id="5b55a-133">Class Types</span></span>  
 <span data-ttu-id="5b55a-134">Nie ma typu danych jednego zawierający wszystkie klasy.</span><span class="sxs-lookup"><span data-stu-id="5b55a-134">There is no single data type comprising all classes.</span></span> <span data-ttu-id="5b55a-135">Mimo że jednej klasy mogą dziedziczyć z innej klasy, każdy jest typem danych.</span><span class="sxs-lookup"><span data-stu-id="5b55a-135">Although one class can inherit from another class, each is a separate data type.</span></span> <span data-ttu-id="5b55a-136">Wiele wystąpień tej samej klasy są tego samego typu danych.</span><span class="sxs-lookup"><span data-stu-id="5b55a-136">Multiple instances of the same class are of the same data type.</span></span> <span data-ttu-id="5b55a-137">Po przypisaniu co zmienna wystąpienia klasy do innego, nie tylko mają ten sam typ danych, wskazywać tego samego wystąpienia klasy w pamięci.</span><span class="sxs-lookup"><span data-stu-id="5b55a-137">If you assign one class instance variable to another, not only do they have the same data type, they point to the same class instance in memory.</span></span>  
  
 <span data-ttu-id="5b55a-138">Aby uzyskać więcej informacji na temat klas, zobacz [obiekty i klasy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span><span class="sxs-lookup"><span data-stu-id="5b55a-138">For more information on classes, see [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b55a-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5b55a-139">See Also</span></span>  
 [<span data-ttu-id="5b55a-140">Typy danych</span><span class="sxs-lookup"><span data-stu-id="5b55a-140">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="5b55a-141">Podstawowe typy danych</span><span class="sxs-lookup"><span data-stu-id="5b55a-141">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [<span data-ttu-id="5b55a-142">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5b55a-142">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="5b55a-143">Typy wartości i typy referencyjne</span><span class="sxs-lookup"><span data-stu-id="5b55a-143">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="5b55a-144">Konwersje typów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5b55a-144">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="5b55a-145">Struktury</span><span class="sxs-lookup"><span data-stu-id="5b55a-145">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="5b55a-146">Rozwiązywanie problemów z typów danych</span><span class="sxs-lookup"><span data-stu-id="5b55a-146">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="5b55a-147">Porady: utrzymywanie więcej niż jedną wartość w zmiennej</span><span class="sxs-lookup"><span data-stu-id="5b55a-147">How to: Hold More Than One Value in a Variable</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)
