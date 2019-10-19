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
ms.openlocfilehash: 466bb5386235917705344d35c5141c8bf779218d
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582646"
---
# <a name="value-types-and-reference-types"></a><span data-ttu-id="95e71-102">Typy wartości i odwołań</span><span class="sxs-lookup"><span data-stu-id="95e71-102">Value Types and Reference Types</span></span>
<span data-ttu-id="95e71-103">Istnieją dwa rodzaje typów w Visual Basic: typy referencyjne i typy wartości.</span><span class="sxs-lookup"><span data-stu-id="95e71-103">There are two kinds of types in Visual Basic: reference types and value types.</span></span> <span data-ttu-id="95e71-104">W zmiennych typu referencyjnego są przechowywane odwołania do ich danych (obiekty), a zmienne typu wartości zawierają bezpośrednio swoje dane.</span><span class="sxs-lookup"><span data-stu-id="95e71-104">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="95e71-105">W przypadku typów referencyjnych dwie zmienne mogą odwoływać się do jednego obiektu, a więc operacje wykonane na jednej zmiennych mogą mieć wpływ na obiekt, do którego odwołuje się druga zmienna.</span><span class="sxs-lookup"><span data-stu-id="95e71-105">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="95e71-106">W przypadku typów wartości Każda zmienna ma własną kopię danych i nie jest możliwe wykonywanie operacji na jednej zmiennej, która ma wpływ na drugą (z wyjątkiem przypadków [modyfikatora ByRef w przypadku parametrów](../../../language-reference/modifiers/byref.md)).</span><span class="sxs-lookup"><span data-stu-id="95e71-106">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of the [ByRef modifier on parameters](../../../language-reference/modifiers/byref.md)).</span></span>
  
## <a name="value-types"></a><span data-ttu-id="95e71-107">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="95e71-107">Value Types</span></span>  
 <span data-ttu-id="95e71-108">Typ danych jest *typem wartości* , jeśli przechowuje dane w ramach alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="95e71-108">A data type is a *value type* if it holds the data within its own memory allocation.</span></span> <span data-ttu-id="95e71-109">Dostępne są następujące typy wartości:</span><span class="sxs-lookup"><span data-stu-id="95e71-109">Value types include the following:</span></span>  
  
- <span data-ttu-id="95e71-110">Wszystkie typy danych liczbowych</span><span class="sxs-lookup"><span data-stu-id="95e71-110">All numeric data types</span></span>  
  
- <span data-ttu-id="95e71-111">`Boolean`, `Char` i `Date`</span><span class="sxs-lookup"><span data-stu-id="95e71-111">`Boolean`, `Char`, and `Date`</span></span>  
  
- <span data-ttu-id="95e71-112">Wszystkie struktury, nawet jeśli ich składowe są typami odwołań</span><span class="sxs-lookup"><span data-stu-id="95e71-112">All structures, even if their members are reference types</span></span>  
  
- <span data-ttu-id="95e71-113">Wyliczenia, ponieważ ich typ podstawowy jest zawsze `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger` lub `ULong`</span><span class="sxs-lookup"><span data-stu-id="95e71-113">Enumerations, since their underlying type is always `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, or `ULong`</span></span>  
  
 <span data-ttu-id="95e71-114">Każda struktura jest typem wartości, nawet jeśli zawiera elementy członkowskie typu referencyjnego.</span><span class="sxs-lookup"><span data-stu-id="95e71-114">Every structure is a value type, even if it contains reference type members.</span></span> <span data-ttu-id="95e71-115">Z tego powodu typy wartości, takie jak `Char` i `Integer`, są implementowane przez .NET Framework struktur.</span><span class="sxs-lookup"><span data-stu-id="95e71-115">For this reason, value types such as `Char` and `Integer` are implemented by .NET Framework structures.</span></span>  
  
 <span data-ttu-id="95e71-116">Typ wartości można zadeklarować przy użyciu zastrzeżonego słowa kluczowego, na przykład `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="95e71-116">You can declare a value type by using the reserved keyword, for example, `Decimal`.</span></span> <span data-ttu-id="95e71-117">Możesz również użyć słowa kluczowego `New`, aby zainicjować typ wartości.</span><span class="sxs-lookup"><span data-stu-id="95e71-117">You can also use the `New` keyword to initialize a value type.</span></span> <span data-ttu-id="95e71-118">Jest to szczególnie przydatne, jeśli typ ma konstruktora, który pobiera parametry.</span><span class="sxs-lookup"><span data-stu-id="95e71-118">This is especially useful if the type has a constructor that takes parameters.</span></span> <span data-ttu-id="95e71-119">Przykładem jest Konstruktor <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29>, który kompiluje nową wartość `Decimal` z dostarczonych części.</span><span class="sxs-lookup"><span data-stu-id="95e71-119">An example of this is the <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> constructor, which builds a new `Decimal` value from the supplied parts.</span></span>  
  
## <a name="reference-types"></a><span data-ttu-id="95e71-120">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="95e71-120">Reference Types</span></span>  
 <span data-ttu-id="95e71-121">*Typ referencyjny* przechowuje odwołanie do swoich danych.</span><span class="sxs-lookup"><span data-stu-id="95e71-121">A *reference type* stores a reference to its data.</span></span> <span data-ttu-id="95e71-122">Typy odwołań obejmują następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="95e71-122">Reference types include the following:</span></span>  
  
- `String`  
  
- <span data-ttu-id="95e71-123">Wszystkie tablice, nawet jeśli ich elementy są typami wartości</span><span class="sxs-lookup"><span data-stu-id="95e71-123">All arrays, even if their elements are value types</span></span>  
  
- <span data-ttu-id="95e71-124">Typy klas, takie jak <xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="95e71-124">Class types, such as <xref:System.Windows.Forms.Form></span></span>  
  
- <span data-ttu-id="95e71-125">Delegaty</span><span class="sxs-lookup"><span data-stu-id="95e71-125">Delegates</span></span>  
  
 <span data-ttu-id="95e71-126">Klasa jest *typem referencyjnym*.</span><span class="sxs-lookup"><span data-stu-id="95e71-126">A class is a *reference type*.</span></span> <span data-ttu-id="95e71-127">Należy zauważyć, że każda tablica jest typem referencyjnym, nawet jeśli jego elementy członkowskie są typami wartości.</span><span class="sxs-lookup"><span data-stu-id="95e71-127">Note that every array is a reference type, even if its members are value types.</span></span>  
  
 <span data-ttu-id="95e71-128">Ponieważ każdy typ referencyjny reprezentuje bazową klasę .NET Framework, należy użyć słowa kluczowego [New](../../../../visual-basic/language-reference/operators/new-operator.md) podczas inicjowania.</span><span class="sxs-lookup"><span data-stu-id="95e71-128">Since every reference type represents an underlying .NET Framework class, you must use the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword when you initialize it.</span></span> <span data-ttu-id="95e71-129">Poniższa instrukcja Inicjuje tablicę.</span><span class="sxs-lookup"><span data-stu-id="95e71-129">The following statement initializes an array.</span></span>  
  
```vb  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a><span data-ttu-id="95e71-130">Elementy, które nie są typami</span><span class="sxs-lookup"><span data-stu-id="95e71-130">Elements That Are Not Types</span></span>  
 <span data-ttu-id="95e71-131">Następujące elementy programistyczne nie kwalifikują się jako typy, ponieważ nie można określić żadnego z nich jako typu danych dla zadeklarowanego elementu:</span><span class="sxs-lookup"><span data-stu-id="95e71-131">The following programming elements do not qualify as types, because you cannot specify any of them as a data type for a declared element:</span></span>  
  
- <span data-ttu-id="95e71-132">Namespaces</span><span class="sxs-lookup"><span data-stu-id="95e71-132">Namespaces</span></span>  
  
- <span data-ttu-id="95e71-133">Moduły</span><span class="sxs-lookup"><span data-stu-id="95e71-133">Modules</span></span>  
  
- <span data-ttu-id="95e71-134">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="95e71-134">Events</span></span>  
  
- <span data-ttu-id="95e71-135">Właściwości i procedury</span><span class="sxs-lookup"><span data-stu-id="95e71-135">Properties and procedures</span></span>  
  
- <span data-ttu-id="95e71-136">Zmienne, stałe i pola</span><span class="sxs-lookup"><span data-stu-id="95e71-136">Variables, constants, and fields</span></span>  
  
## <a name="working-with-the-object-data-type"></a><span data-ttu-id="95e71-137">Praca z typem danych obiektu</span><span class="sxs-lookup"><span data-stu-id="95e71-137">Working with the Object Data Type</span></span>  
 <span data-ttu-id="95e71-138">Do zmiennej typu danych `Object` można przypisać typ referencyjny lub typ wartości.</span><span class="sxs-lookup"><span data-stu-id="95e71-138">You can assign either a reference type or a value type to a variable of the `Object` data type.</span></span> <span data-ttu-id="95e71-139">Zmienna `Object` zawsze przechowuje odwołanie do danych, nigdy nie same same dane.</span><span class="sxs-lookup"><span data-stu-id="95e71-139">An `Object` variable always holds a reference to the data, never the data itself.</span></span> <span data-ttu-id="95e71-140">Jeśli jednak przypiszesz typ wartości do zmiennej `Object`, zachowuje się tak, jakby przechowywać własne dane.</span><span class="sxs-lookup"><span data-stu-id="95e71-140">However, if you assign a value type to an `Object` variable, it behaves as if it holds its own data.</span></span> <span data-ttu-id="95e71-141">Aby uzyskać więcej informacji, zobacz [Typ danych obiektu](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="95e71-141">For more information, see [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="95e71-142">Można dowiedzieć się, czy zmienna `Object` działa jako typ referencyjny czy typ wartości poprzez przekazanie go do metody <xref:Microsoft.VisualBasic.Information.IsReference%2A> w klasie <xref:Microsoft.VisualBasic.Information> <xref:Microsoft.VisualBasic?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="95e71-142">You can find out whether an `Object` variable is acting as a reference type or a value type by passing it to the <xref:Microsoft.VisualBasic.Information.IsReference%2A> method in the <xref:Microsoft.VisualBasic.Information> class of the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="95e71-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> zwraca `True`, jeśli zawartość zmiennej `Object` reprezentuje typ referencyjny.</span><span class="sxs-lookup"><span data-stu-id="95e71-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> returns `True` if the content of the `Object` variable represents a reference type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95e71-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="95e71-144">See also</span></span>

- [<span data-ttu-id="95e71-145">Typy wartości dopuszczających wartości null</span><span class="sxs-lookup"><span data-stu-id="95e71-145">Nullable Value Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="95e71-146">Konwersje typów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="95e71-146">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="95e71-147">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="95e71-147">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="95e71-148">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="95e71-148">Efficient Use of Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="95e71-149">Object, typ danych</span><span class="sxs-lookup"><span data-stu-id="95e71-149">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="95e71-150">Typy danych</span><span class="sxs-lookup"><span data-stu-id="95e71-150">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
