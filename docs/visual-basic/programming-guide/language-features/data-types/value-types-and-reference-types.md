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
ms.openlocfilehash: f25caec43b7118b7b64db1b14516b0c5ea80f4f6
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504878"
---
# <a name="value-types-and-reference-types"></a><span data-ttu-id="c0d0b-102">Typy wartości i odwołań</span><span class="sxs-lookup"><span data-stu-id="c0d0b-102">Value Types and Reference Types</span></span>
<span data-ttu-id="c0d0b-103">Istnieją dwa rodzaje typów w języku Visual Basic: typy referencyjne i typy wartości.</span><span class="sxs-lookup"><span data-stu-id="c0d0b-103">There are two kinds of types in Visual Basic: reference types and value types.</span></span> <span data-ttu-id="c0d0b-104">W zmiennych typu referencyjnego są przechowywane odwołania do ich danych (obiekty), a zmienne typu wartości zawierają bezpośrednio swoje dane.</span><span class="sxs-lookup"><span data-stu-id="c0d0b-104">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="c0d0b-105">W przypadku typów referencyjnych dwie zmienne mogą odwoływać się do jednego obiektu, a więc operacje wykonane na jednej zmiennych mogą mieć wpływ na obiekt, do którego odwołuje się druga zmienna.</span><span class="sxs-lookup"><span data-stu-id="c0d0b-105">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="c0d0b-106">Z typami wartości każda zmienna ma własną kopię danych i nie jest możliwe dla operacji na jednej zmiennej miały wpływ na inne (z wyjątkiem w przypadku właściwości [ByRef modyfikator parametrów](../../../language-reference/modifiers/byref.md)).</span><span class="sxs-lookup"><span data-stu-id="c0d0b-106">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of the [ByRef modifier on parameters](../../../language-reference/modifiers/byref.md)).</span></span>
  
## <a name="value-types"></a><span data-ttu-id="c0d0b-107">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="c0d0b-107">Value Types</span></span>  
 <span data-ttu-id="c0d0b-108">Typ danych jest *typu wartości* Jeśli przechowuje dane w obrębie własnej alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="c0d0b-108">A data type is a *value type* if it holds the data within its own memory allocation.</span></span> <span data-ttu-id="c0d0b-109">Typy wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="c0d0b-109">Value types include the following:</span></span>  
  
- <span data-ttu-id="c0d0b-110">Wszystkie typy danych numerycznych</span><span class="sxs-lookup"><span data-stu-id="c0d0b-110">All numeric data types</span></span>  
  
- <span data-ttu-id="c0d0b-111">`Boolean`, `Char`, i `Date`</span><span class="sxs-lookup"><span data-stu-id="c0d0b-111">`Boolean`, `Char`, and `Date`</span></span>  
  
- <span data-ttu-id="c0d0b-112">Wszystkie struktury, nawet jeśli ich elementy członkowskie są typami odwołań</span><span class="sxs-lookup"><span data-stu-id="c0d0b-112">All structures, even if their members are reference types</span></span>  
  
- <span data-ttu-id="c0d0b-113">Wyliczenia, ponieważ jego typ podstawowy jest zawsze `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, lub `ULong`</span><span class="sxs-lookup"><span data-stu-id="c0d0b-113">Enumerations, since their underlying type is always `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, or `ULong`</span></span>  
  
 <span data-ttu-id="c0d0b-114">Co struktura jest typem wartości, nawet wtedy, gdy zawiera on elementy członkowskie typu odwołania.</span><span class="sxs-lookup"><span data-stu-id="c0d0b-114">Every structure is a value type, even if it contains reference type members.</span></span> <span data-ttu-id="c0d0b-115">Z tego powodu wartość typy takie jak `Char` i `Integer` są implementowane przez struktury .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c0d0b-115">For this reason, value types such as `Char` and `Integer` are implemented by .NET Framework structures.</span></span>  
  
 <span data-ttu-id="c0d0b-116">Typ wartości można zadeklarować za pomocą zastrzeżonego słowa kluczowego, na przykład `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="c0d0b-116">You can declare a value type by using the reserved keyword, for example, `Decimal`.</span></span> <span data-ttu-id="c0d0b-117">Można również użyć `New` — słowo kluczowe można zainicjować typu wartości.</span><span class="sxs-lookup"><span data-stu-id="c0d0b-117">You can also use the `New` keyword to initialize a value type.</span></span> <span data-ttu-id="c0d0b-118">Jest to szczególnie przydatne, jeśli typ ma konstruktora przyjmującego parametry.</span><span class="sxs-lookup"><span data-stu-id="c0d0b-118">This is especially useful if the type has a constructor that takes parameters.</span></span> <span data-ttu-id="c0d0b-119">Na przykład <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> konstruktora, który tworzy nową `Decimal` wartości z części podane.</span><span class="sxs-lookup"><span data-stu-id="c0d0b-119">An example of this is the <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> constructor, which builds a new `Decimal` value from the supplied parts.</span></span>  
  
## <a name="reference-types"></a><span data-ttu-id="c0d0b-120">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="c0d0b-120">Reference Types</span></span>  
 <span data-ttu-id="c0d0b-121">A *odwołania do typu* przechowuje odwołania do jego danych.</span><span class="sxs-lookup"><span data-stu-id="c0d0b-121">A *reference type* stores a reference to its data.</span></span> <span data-ttu-id="c0d0b-122">Typy odwołań są następujące:</span><span class="sxs-lookup"><span data-stu-id="c0d0b-122">Reference types include the following:</span></span>  
  
- `String`  
  
- <span data-ttu-id="c0d0b-123">Wszystkie tablice, nawet jeśli ich elementy są typami wartości</span><span class="sxs-lookup"><span data-stu-id="c0d0b-123">All arrays, even if their elements are value types</span></span>  
  
- <span data-ttu-id="c0d0b-124">Klasa typów, takich jak <xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="c0d0b-124">Class types, such as <xref:System.Windows.Forms.Form></span></span>  
  
- <span data-ttu-id="c0d0b-125">Delegaty</span><span class="sxs-lookup"><span data-stu-id="c0d0b-125">Delegates</span></span>  
  
 <span data-ttu-id="c0d0b-126">Klasa jest *odwołania do typu*.</span><span class="sxs-lookup"><span data-stu-id="c0d0b-126">A class is a *reference type*.</span></span> <span data-ttu-id="c0d0b-127">Należy pamiętać, że każda tablica typu odwołania, nawet jeśli jego członkowie są typami wartości.</span><span class="sxs-lookup"><span data-stu-id="c0d0b-127">Note that every array is a reference type, even if its members are value types.</span></span>  
  
 <span data-ttu-id="c0d0b-128">Ponieważ każdy typ odniesienia reprezentuje podstawowej klasy .NET Framework, należy użyć [operatora New](../../../../visual-basic/language-reference/operators/new-operator.md) — słowo kluczowe, podczas jego inicjowania.</span><span class="sxs-lookup"><span data-stu-id="c0d0b-128">Since every reference type represents an underlying .NET Framework class, you must use the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword when you initialize it.</span></span> <span data-ttu-id="c0d0b-129">Poniższa instrukcja inicjuje tablicę.</span><span class="sxs-lookup"><span data-stu-id="c0d0b-129">The following statement initializes an array.</span></span>  
  
```  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a><span data-ttu-id="c0d0b-130">Elementy, które nie są typami</span><span class="sxs-lookup"><span data-stu-id="c0d0b-130">Elements That Are Not Types</span></span>  
 <span data-ttu-id="c0d0b-131">Następujące elementy programowania nie kwalifikują się jako typów, ponieważ nie można określić dowolny z nich jako element zadeklarowany typ danych:</span><span class="sxs-lookup"><span data-stu-id="c0d0b-131">The following programming elements do not qualify as types, because you cannot specify any of them as a data type for a declared element:</span></span>  
  
- <span data-ttu-id="c0d0b-132">Namespaces</span><span class="sxs-lookup"><span data-stu-id="c0d0b-132">Namespaces</span></span>  
  
- <span data-ttu-id="c0d0b-133">Moduły</span><span class="sxs-lookup"><span data-stu-id="c0d0b-133">Modules</span></span>  
  
- <span data-ttu-id="c0d0b-134">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="c0d0b-134">Events</span></span>  
  
- <span data-ttu-id="c0d0b-135">Właściwości i procedury</span><span class="sxs-lookup"><span data-stu-id="c0d0b-135">Properties and procedures</span></span>  
  
- <span data-ttu-id="c0d0b-136">Zmienne, stałe i pola</span><span class="sxs-lookup"><span data-stu-id="c0d0b-136">Variables, constants, and fields</span></span>  
  
## <a name="working-with-the-object-data-type"></a><span data-ttu-id="c0d0b-137">Praca z typem danych obiektu</span><span class="sxs-lookup"><span data-stu-id="c0d0b-137">Working with the Object Data Type</span></span>  
 <span data-ttu-id="c0d0b-138">Można przypisać do zmiennej typu odwołania lub typu wartościowego `Object` typu danych.</span><span class="sxs-lookup"><span data-stu-id="c0d0b-138">You can assign either a reference type or a value type to a variable of the `Object` data type.</span></span> <span data-ttu-id="c0d0b-139">`Object` Zmiennej zawsze zawiera odwołanie do danych, nigdy nie dane.</span><span class="sxs-lookup"><span data-stu-id="c0d0b-139">An `Object` variable always holds a reference to the data, never the data itself.</span></span> <span data-ttu-id="c0d0b-140">Jednak jeśli przypisujesz typ wartości do `Object` zmiennej działa tak, jakby posiada własnych danych.</span><span class="sxs-lookup"><span data-stu-id="c0d0b-140">However, if you assign a value type to an `Object` variable, it behaves as if it holds its own data.</span></span> <span data-ttu-id="c0d0b-141">Aby uzyskać więcej informacji, zobacz [Object — typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="c0d0b-141">For more information, see [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="c0d0b-142">Można dowiedzieć się, czy `Object` zmiennej działa jako typu odwołania lub typu wartościowego przez przekazanie jej do <xref:Microsoft.VisualBasic.Information.IsReference%2A> method in Class metoda <xref:Microsoft.VisualBasic.Information> klasy <xref:Microsoft.VisualBasic?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c0d0b-142">You can find out whether an `Object` variable is acting as a reference type or a value type by passing it to the <xref:Microsoft.VisualBasic.Information.IsReference%2A> method in the <xref:Microsoft.VisualBasic.Information> class of the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="c0d0b-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> Zwraca `True` Jeśli zawartość `Object` zmienna reprezentuje typ odwołania.</span><span class="sxs-lookup"><span data-stu-id="c0d0b-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> returns `True` if the content of the `Object` variable represents a reference type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0d0b-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c0d0b-144">See also</span></span>

- [<span data-ttu-id="c0d0b-145">Typy wartości dopuszczających wartości null</span><span class="sxs-lookup"><span data-stu-id="c0d0b-145">Nullable Value Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="c0d0b-146">Konwersje typów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c0d0b-146">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="c0d0b-147">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="c0d0b-147">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="c0d0b-148">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="c0d0b-148">Efficient Use of Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="c0d0b-149">Object, typ danych</span><span class="sxs-lookup"><span data-stu-id="c0d0b-149">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="c0d0b-150">Typy danych</span><span class="sxs-lookup"><span data-stu-id="c0d0b-150">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
