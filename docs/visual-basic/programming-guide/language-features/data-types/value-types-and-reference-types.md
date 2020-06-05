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
ms.openlocfilehash: 3a1de120f5f97ba93939f332f121d70cd3091216
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392977"
---
# <a name="value-types-and-reference-types"></a><span data-ttu-id="369ba-102">Typy wartości i odwołań</span><span class="sxs-lookup"><span data-stu-id="369ba-102">Value Types and Reference Types</span></span>
<span data-ttu-id="369ba-103">Istnieją dwa rodzaje typów w Visual Basic: typy referencyjne i typy wartości.</span><span class="sxs-lookup"><span data-stu-id="369ba-103">There are two kinds of types in Visual Basic: reference types and value types.</span></span> <span data-ttu-id="369ba-104">W zmiennych typu referencyjnego są przechowywane odwołania do ich danych (obiekty), a zmienne typu wartości zawierają bezpośrednio swoje dane.</span><span class="sxs-lookup"><span data-stu-id="369ba-104">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="369ba-105">W przypadku typów referencyjnych dwie zmienne mogą odwoływać się do jednego obiektu, a więc operacje wykonane na jednej zmiennych mogą mieć wpływ na obiekt, do którego odwołuje się druga zmienna.</span><span class="sxs-lookup"><span data-stu-id="369ba-105">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="369ba-106">W przypadku typów wartości Każda zmienna ma własną kopię danych i nie jest możliwe wykonywanie operacji na jednej zmiennej, która ma wpływ na drugą (z wyjątkiem przypadków [modyfikatora ByRef w przypadku parametrów](../../../language-reference/modifiers/byref.md)).</span><span class="sxs-lookup"><span data-stu-id="369ba-106">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of the [ByRef modifier on parameters](../../../language-reference/modifiers/byref.md)).</span></span>
  
## <a name="value-types"></a><span data-ttu-id="369ba-107">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="369ba-107">Value Types</span></span>  
 <span data-ttu-id="369ba-108">Typ danych jest *typem wartości* , jeśli przechowuje dane w ramach alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="369ba-108">A data type is a *value type* if it holds the data within its own memory allocation.</span></span> <span data-ttu-id="369ba-109">Dostępne są następujące typy wartości:</span><span class="sxs-lookup"><span data-stu-id="369ba-109">Value types include the following:</span></span>  
  
- <span data-ttu-id="369ba-110">Wszystkie typy danych liczbowych</span><span class="sxs-lookup"><span data-stu-id="369ba-110">All numeric data types</span></span>  
  
- <span data-ttu-id="369ba-111">`Boolean`, `Char` i`Date`</span><span class="sxs-lookup"><span data-stu-id="369ba-111">`Boolean`, `Char`, and `Date`</span></span>  
  
- <span data-ttu-id="369ba-112">Wszystkie struktury, nawet jeśli ich składowe są typami odwołań</span><span class="sxs-lookup"><span data-stu-id="369ba-112">All structures, even if their members are reference types</span></span>  
  
- <span data-ttu-id="369ba-113">Wyliczenia, ponieważ ich typ podstawowy ma zawsze,,,,,, `SByte` `Short` `Integer` `Long` `Byte` `UShort` `UInteger` , lub`ULong`</span><span class="sxs-lookup"><span data-stu-id="369ba-113">Enumerations, since their underlying type is always `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger`, or `ULong`</span></span>  
  
 <span data-ttu-id="369ba-114">Każda struktura jest typem wartości, nawet jeśli zawiera elementy członkowskie typu referencyjnego.</span><span class="sxs-lookup"><span data-stu-id="369ba-114">Every structure is a value type, even if it contains reference type members.</span></span> <span data-ttu-id="369ba-115">Z tego powodu typy wartości, takie jak `Char` i, `Integer` są implementowane przez struktury .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="369ba-115">For this reason, value types such as `Char` and `Integer` are implemented by .NET Framework structures.</span></span>  
  
 <span data-ttu-id="369ba-116">Typ wartości można zadeklarować przy użyciu zastrzeżonego słowa kluczowego, na przykład `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="369ba-116">You can declare a value type by using the reserved keyword, for example, `Decimal`.</span></span> <span data-ttu-id="369ba-117">Możesz również użyć `New` słowa kluczowego, aby zainicjować typ wartości.</span><span class="sxs-lookup"><span data-stu-id="369ba-117">You can also use the `New` keyword to initialize a value type.</span></span> <span data-ttu-id="369ba-118">Jest to szczególnie przydatne, jeśli typ ma konstruktora, który pobiera parametry.</span><span class="sxs-lookup"><span data-stu-id="369ba-118">This is especially useful if the type has a constructor that takes parameters.</span></span> <span data-ttu-id="369ba-119">Przykładem jest <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> Konstruktor, który kompiluje nową `Decimal` wartość z dostarczonych części.</span><span class="sxs-lookup"><span data-stu-id="369ba-119">An example of this is the <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> constructor, which builds a new `Decimal` value from the supplied parts.</span></span>  
  
## <a name="reference-types"></a><span data-ttu-id="369ba-120">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="369ba-120">Reference Types</span></span>  
 <span data-ttu-id="369ba-121">*Typ referencyjny* przechowuje odwołanie do swoich danych.</span><span class="sxs-lookup"><span data-stu-id="369ba-121">A *reference type* stores a reference to its data.</span></span> <span data-ttu-id="369ba-122">Typy odwołań obejmują następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="369ba-122">Reference types include the following:</span></span>  
  
- `String`  
  
- <span data-ttu-id="369ba-123">Wszystkie tablice, nawet jeśli ich elementy są typami wartości</span><span class="sxs-lookup"><span data-stu-id="369ba-123">All arrays, even if their elements are value types</span></span>  
  
- <span data-ttu-id="369ba-124">Typy klas, takie jak<xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="369ba-124">Class types, such as <xref:System.Windows.Forms.Form></span></span>  
  
- <span data-ttu-id="369ba-125">Delegaci</span><span class="sxs-lookup"><span data-stu-id="369ba-125">Delegates</span></span>  
  
 <span data-ttu-id="369ba-126">Klasa jest *typem referencyjnym*.</span><span class="sxs-lookup"><span data-stu-id="369ba-126">A class is a *reference type*.</span></span> <span data-ttu-id="369ba-127">Należy zauważyć, że każda tablica jest typem referencyjnym, nawet jeśli jego elementy członkowskie są typami wartości.</span><span class="sxs-lookup"><span data-stu-id="369ba-127">Note that every array is a reference type, even if its members are value types.</span></span>  
  
 <span data-ttu-id="369ba-128">Ponieważ każdy typ referencyjny reprezentuje bazową klasę .NET Framework, należy użyć słowa kluczowego [New](../../../language-reference/operators/new-operator.md) podczas inicjowania.</span><span class="sxs-lookup"><span data-stu-id="369ba-128">Since every reference type represents an underlying .NET Framework class, you must use the [New Operator](../../../language-reference/operators/new-operator.md) keyword when you initialize it.</span></span> <span data-ttu-id="369ba-129">Poniższa instrukcja Inicjuje tablicę.</span><span class="sxs-lookup"><span data-stu-id="369ba-129">The following statement initializes an array.</span></span>  
  
```vb  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a><span data-ttu-id="369ba-130">Elementy, które nie są typami</span><span class="sxs-lookup"><span data-stu-id="369ba-130">Elements That Are Not Types</span></span>  
 <span data-ttu-id="369ba-131">Następujące elementy programistyczne nie kwalifikują się jako typy, ponieważ nie można określić żadnego z nich jako typu danych dla zadeklarowanego elementu:</span><span class="sxs-lookup"><span data-stu-id="369ba-131">The following programming elements do not qualify as types, because you cannot specify any of them as a data type for a declared element:</span></span>  
  
- <span data-ttu-id="369ba-132">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="369ba-132">Namespaces</span></span>  
  
- <span data-ttu-id="369ba-133">Moduły</span><span class="sxs-lookup"><span data-stu-id="369ba-133">Modules</span></span>  
  
- <span data-ttu-id="369ba-134">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="369ba-134">Events</span></span>  
  
- <span data-ttu-id="369ba-135">Właściwości i procedury</span><span class="sxs-lookup"><span data-stu-id="369ba-135">Properties and procedures</span></span>  
  
- <span data-ttu-id="369ba-136">Zmienne, stałe i pola</span><span class="sxs-lookup"><span data-stu-id="369ba-136">Variables, constants, and fields</span></span>  
  
## <a name="working-with-the-object-data-type"></a><span data-ttu-id="369ba-137">Praca z typem danych obiektu</span><span class="sxs-lookup"><span data-stu-id="369ba-137">Working with the Object Data Type</span></span>  
 <span data-ttu-id="369ba-138">Do zmiennej typu danych można przypisać typ referencyjny lub typ wartości `Object` .</span><span class="sxs-lookup"><span data-stu-id="369ba-138">You can assign either a reference type or a value type to a variable of the `Object` data type.</span></span> <span data-ttu-id="369ba-139">`Object`Zmienna zawsze przechowuje odwołanie do danych, nigdy same same dane.</span><span class="sxs-lookup"><span data-stu-id="369ba-139">An `Object` variable always holds a reference to the data, never the data itself.</span></span> <span data-ttu-id="369ba-140">Jeśli jednak typ wartości zostanie przypisany do `Object` zmiennej, zachowuje się tak, jakby przechowywać własne dane.</span><span class="sxs-lookup"><span data-stu-id="369ba-140">However, if you assign a value type to an `Object` variable, it behaves as if it holds its own data.</span></span> <span data-ttu-id="369ba-141">Aby uzyskać więcej informacji, zobacz [Typ danych obiektu](../../../language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="369ba-141">For more information, see [Object Data Type](../../../language-reference/data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="369ba-142">Można dowiedzieć się, czy `Object` zmienna działa jako typ referencyjny, czy typ wartości poprzez przekazanie go do <xref:Microsoft.VisualBasic.Information.IsReference%2A> metody w <xref:Microsoft.VisualBasic.Information> klasie <xref:Microsoft.VisualBasic?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="369ba-142">You can find out whether an `Object` variable is acting as a reference type or a value type by passing it to the <xref:Microsoft.VisualBasic.Information.IsReference%2A> method in the <xref:Microsoft.VisualBasic.Information> class of the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="369ba-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType>zwraca `True` czy zawartość `Object` zmiennej reprezentuje typ referencyjny.</span><span class="sxs-lookup"><span data-stu-id="369ba-143"><xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=nameWithType> returns `True` if the content of the `Object` variable represents a reference type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="369ba-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="369ba-144">See also</span></span>

- [<span data-ttu-id="369ba-145">Typy wartości null</span><span class="sxs-lookup"><span data-stu-id="369ba-145">Nullable Value Types</span></span>](nullable-value-types.md)
- [<span data-ttu-id="369ba-146">Konwersje plików w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="369ba-146">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="369ba-147">Structure — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="369ba-147">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
- [<span data-ttu-id="369ba-148">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="369ba-148">Efficient Use of Data Types</span></span>](efficient-use-of-data-types.md)
- [<span data-ttu-id="369ba-149">Object — typ danych</span><span class="sxs-lookup"><span data-stu-id="369ba-149">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="369ba-150">Typy danych</span><span class="sxs-lookup"><span data-stu-id="369ba-150">Data Types</span></span>](index.md)
