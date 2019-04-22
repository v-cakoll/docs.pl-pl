---
title: Typy wartości i odwołań
ms.date: 07/20/2015
helpviewer_keywords:
- reference data types [Visual Basic]
- reference types [Visual Basic]
- value types [Visual Basic]
- value data types [Visual Basic]
- types [Visual Basic]
- data types [Visual Basic], value types
- data types [Visual Basic], reference types
ms.assetid: fc82ce15-5a40-4c5c-a1e1-a556830e7391
ms.openlocfilehash: 4e0831a045da5eb5798d10aeb977981ecae20040
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58819541"
---
# <a name="value-types-and-reference-types"></a><span data-ttu-id="23bf8-102">Typy wartości i odwołań</span><span class="sxs-lookup"><span data-stu-id="23bf8-102">Value Types and Reference Types</span></span>
<span data-ttu-id="23bf8-103">W języku Visual Basic typy danych są implementowane w na podstawie ich klasyfikacji.</span><span class="sxs-lookup"><span data-stu-id="23bf8-103">In Visual Basic, data types are implemented based on their classification.</span></span> <span data-ttu-id="23bf8-104">Typy danych Visual Basic mogą być klasyfikowane według tego, czy zmienna określonego typu przechowuje własnych danych lub wskaźnik do danych.</span><span class="sxs-lookup"><span data-stu-id="23bf8-104">The Visual Basic data types can be classified according to whether a variable of a particular type stores its own data or a pointer to the data.</span></span> <span data-ttu-id="23bf8-105">Jeśli przechowuje swoje własne dane *typu wartości*; Jeśli przechowuje wskaźnik do danych w pamięci jest *odwołania do typu*.</span><span class="sxs-lookup"><span data-stu-id="23bf8-105">If it stores its own data it is a *value type*; if it holds a pointer to data elsewhere in memory it is a *reference type*.</span></span>  
  
## <a name="value-types"></a><span data-ttu-id="23bf8-106">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="23bf8-106">Value Types</span></span>  
 <span data-ttu-id="23bf8-107">Typ danych jest *typu wartości* Jeśli przechowuje dane w obrębie własnej alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="23bf8-107">A data type is a *value type* if it holds the data within its own memory allocation.</span></span> <span data-ttu-id="23bf8-108">Typy wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="23bf8-108">Value types include the following:</span></span>  
  
-   <span data-ttu-id="23bf8-109">Wszystkie typy danych numerycznych</span><span class="sxs-lookup"><span data-stu-id="23bf8-109">All numeric data types</span></span>  
  
-   <span data-ttu-id="23bf8-110">`Boolean`, `Char`, i `Date`</span><span class="sxs-lookup"><span data-stu-id="23bf8-110">`Boolean`, `Char`, and `Date`</span></span>  
  
-   <span data-ttu-id="23bf8-111">Wszystkie struktury, nawet jeśli ich elementy członkowskie są typami odwołań</span><span class="sxs-lookup"><span data-stu-id="23bf8-111">All structures, even if their members are reference types</span></span>  
  
-   <span data-ttu-id="23bf8-112">Wyliczenia, ponieważ jego typ podstawowy jest zawsze `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, lub `ULong`</span><span class="sxs-lookup"><span data-stu-id="23bf8-112">Enumerations, since their underlying type is always `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, or `ULong`</span></span>  
  
 <span data-ttu-id="23bf8-113">Co struktura jest typem wartości, nawet wtedy, gdy zawiera on elementy członkowskie typu odwołania.</span><span class="sxs-lookup"><span data-stu-id="23bf8-113">Every structure is a value type, even if it contains reference type members.</span></span> <span data-ttu-id="23bf8-114">Z tego powodu wartość typy takie jak `Char` i `Integer` są implementowane przez struktury .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="23bf8-114">For this reason, value types such as `Char` and `Integer` are implemented by .NET Framework structures.</span></span>  
  
 <span data-ttu-id="23bf8-115">Typ wartości można zadeklarować za pomocą zastrzeżonego słowa kluczowego, na przykład `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="23bf8-115">You can declare a value type by using the reserved keyword, for example, `Decimal`.</span></span> <span data-ttu-id="23bf8-116">Można również użyć `New` — słowo kluczowe można zainicjować typu wartości.</span><span class="sxs-lookup"><span data-stu-id="23bf8-116">You can also use the `New` keyword to initialize a value type.</span></span> <span data-ttu-id="23bf8-117">Jest to szczególnie przydatne, jeśli typ ma konstruktora przyjmującego parametry.</span><span class="sxs-lookup"><span data-stu-id="23bf8-117">This is especially useful if the type has a constructor that takes parameters.</span></span> <span data-ttu-id="23bf8-118">Na przykład <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> konstruktora, który tworzy nową `Decimal` wartości z części podane.</span><span class="sxs-lookup"><span data-stu-id="23bf8-118">An example of this is the <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> constructor, which builds a new `Decimal` value from the supplied parts.</span></span>  
  
## <a name="reference-types"></a><span data-ttu-id="23bf8-119">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="23bf8-119">Reference Types</span></span>  
 <span data-ttu-id="23bf8-120">A *odwołania do typu* zawiera wskaźnik do innej lokalizacji w pamięci, która przechowuje dane.</span><span class="sxs-lookup"><span data-stu-id="23bf8-120">A *reference type* contains a pointer to another memory location that holds the data.</span></span> <span data-ttu-id="23bf8-121">Typy odwołań są następujące:</span><span class="sxs-lookup"><span data-stu-id="23bf8-121">Reference types include the following:</span></span>  
  
-   `String`  
  
-   <span data-ttu-id="23bf8-122">Wszystkie tablice, nawet jeśli ich elementy są typami wartości</span><span class="sxs-lookup"><span data-stu-id="23bf8-122">All arrays, even if their elements are value types</span></span>  
  
-   <span data-ttu-id="23bf8-123">Klasa typów, takich jak <xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="23bf8-123">Class types, such as <xref:System.Windows.Forms.Form></span></span>  
  
-   <span data-ttu-id="23bf8-124">Delegaty</span><span class="sxs-lookup"><span data-stu-id="23bf8-124">Delegates</span></span>  
  
 <span data-ttu-id="23bf8-125">Klasa jest *odwołania do typu*.</span><span class="sxs-lookup"><span data-stu-id="23bf8-125">A class is a *reference type*.</span></span> <span data-ttu-id="23bf8-126">Z tego powodu typy odwołań takich jak `Object` i `String` są obsługiwane przez [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] klasy.</span><span class="sxs-lookup"><span data-stu-id="23bf8-126">For this reason, reference types such as `Object` and `String` are supported by [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] classes.</span></span> <span data-ttu-id="23bf8-127">Należy pamiętać, że każda tablica typu odwołania, nawet jeśli jego członkowie są typami wartości.</span><span class="sxs-lookup"><span data-stu-id="23bf8-127">Note that every array is a reference type, even if its members are value types.</span></span>  
  
 <span data-ttu-id="23bf8-128">Ponieważ każdy typ odniesienia reprezentuje podstawowej klasy .NET Framework, należy użyć [operatora New](../../../../visual-basic/language-reference/operators/new-operator.md) — słowo kluczowe, podczas jego inicjowania.</span><span class="sxs-lookup"><span data-stu-id="23bf8-128">Since every reference type represents an underlying .NET Framework class, you must use the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword when you initialize it.</span></span> <span data-ttu-id="23bf8-129">Poniższa instrukcja inicjuje tablicę.</span><span class="sxs-lookup"><span data-stu-id="23bf8-129">The following statement initializes an array.</span></span>  
  
```  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a><span data-ttu-id="23bf8-130">Elementy, które nie są typami</span><span class="sxs-lookup"><span data-stu-id="23bf8-130">Elements That Are Not Types</span></span>  
 <span data-ttu-id="23bf8-131">Następujące elementy programowania nie kwalifikują się jako typów, ponieważ nie można określić dowolny z nich jako element zadeklarowany typ danych:</span><span class="sxs-lookup"><span data-stu-id="23bf8-131">The following programming elements do not qualify as types, because you cannot specify any of them as a data type for a declared element:</span></span>  
  
-   <span data-ttu-id="23bf8-132">Namespaces</span><span class="sxs-lookup"><span data-stu-id="23bf8-132">Namespaces</span></span>  
  
-   <span data-ttu-id="23bf8-133">Moduły</span><span class="sxs-lookup"><span data-stu-id="23bf8-133">Modules</span></span>  
  
-   <span data-ttu-id="23bf8-134">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="23bf8-134">Events</span></span>  
  
-   <span data-ttu-id="23bf8-135">Właściwości i procedury</span><span class="sxs-lookup"><span data-stu-id="23bf8-135">Properties and procedures</span></span>  
  
-   <span data-ttu-id="23bf8-136">Zmienne, stałe i pola</span><span class="sxs-lookup"><span data-stu-id="23bf8-136">Variables, constants, and fields</span></span>  
  
## <a name="working-with-the-object-data-type"></a><span data-ttu-id="23bf8-137">Praca z typem danych obiektu</span><span class="sxs-lookup"><span data-stu-id="23bf8-137">Working with the Object Data Type</span></span>  
 <span data-ttu-id="23bf8-138">Można przypisać do zmiennej typu odwołania lub typu wartościowego `Object` typu danych.</span><span class="sxs-lookup"><span data-stu-id="23bf8-138">You can assign either a reference type or a value type to a variable of the `Object` data type.</span></span> <span data-ttu-id="23bf8-139">`Object` Zawsze zmienna przechowuje wskaźnik do danych, nigdy nie dane.</span><span class="sxs-lookup"><span data-stu-id="23bf8-139">An `Object` variable always holds a pointer to the data, never the data itself.</span></span> <span data-ttu-id="23bf8-140">Jednak jeśli przypisujesz typ wartości do `Object` zmiennej działa tak, jakby posiada własnych danych.</span><span class="sxs-lookup"><span data-stu-id="23bf8-140">However, if you assign a value type to an `Object` variable, it behaves as if it holds its own data.</span></span> <span data-ttu-id="23bf8-141">Aby uzyskać więcej informacji, zobacz [Object — typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="23bf8-141">For more information, see [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="23bf8-142">Można dowiedzieć się, czy `Object` zmiennej działa jako typu odwołania lub typu wartościowego przez przekazanie jej do <xref:Microsoft.VisualBasic.Information.IsReference%2A> method in Class metoda <xref:Microsoft.VisualBasic.Information> klasy <xref:Microsoft.VisualBasic?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="23bf8-142">You can find out whether an `Object` variable is acting as a reference type or a value type by passing it to the <xref:Microsoft.VisualBasic.Information.IsReference%2A> method in the <xref:Microsoft.VisualBasic.Information> class of the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="23bf8-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> Zwraca `True` Jeśli zawartość `Object` zmienna reprezentuje typ odwołania.</span><span class="sxs-lookup"><span data-stu-id="23bf8-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> returns `True` if the content of the `Object` variable represents a reference type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23bf8-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="23bf8-144">See also</span></span>

- [<span data-ttu-id="23bf8-145">Typy wartości dopuszczających wartości null</span><span class="sxs-lookup"><span data-stu-id="23bf8-145">Nullable Value Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="23bf8-146">Konwersje typów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="23bf8-146">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="23bf8-147">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="23bf8-147">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="23bf8-148">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="23bf8-148">Efficient Use of Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="23bf8-149">Object, typ danych</span><span class="sxs-lookup"><span data-stu-id="23bf8-149">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="23bf8-150">Typy danych</span><span class="sxs-lookup"><span data-stu-id="23bf8-150">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
