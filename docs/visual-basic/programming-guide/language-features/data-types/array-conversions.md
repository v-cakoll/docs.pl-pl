---
title: Konwersje tablic
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], converting type
- type conversion [Visual Basic], arrays
- conversions [Visual Basic], type
- arrays [Visual Basic], data types
- conversions [Visual Basic], data type
- object arrays [Visual Basic], converting type
- data type conversion [Visual Basic], array conversions
- conversions [Visual Basic], array types
- object arrays
ms.assetid: fceff7d2-a1b7-44c7-b9aa-8bd831d8a444
ms.openlocfilehash: 622ebe8a77f2dfbeb35e0408be48622d93d409c6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345859"
---
# <a name="array-conversions-visual-basic"></a><span data-ttu-id="9530f-102">Konwersje tablic (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9530f-102">Array Conversions (Visual Basic)</span></span>
<span data-ttu-id="9530f-103">You can convert an array type to a different array type provided you meet the following conditions:</span><span class="sxs-lookup"><span data-stu-id="9530f-103">You can convert an array type to a different array type provided you meet the following conditions:</span></span>  
  
- <span data-ttu-id="9530f-104">**Equal Rank.**</span><span class="sxs-lookup"><span data-stu-id="9530f-104">**Equal Rank.**</span></span> <span data-ttu-id="9530f-105">The ranks of the two arrays must be the same, that is, they must have the same number of dimensions.</span><span class="sxs-lookup"><span data-stu-id="9530f-105">The ranks of the two arrays must be the same, that is, they must have the same number of dimensions.</span></span> <span data-ttu-id="9530f-106">However, the lengths of the respective dimensions do not need to be the same.</span><span class="sxs-lookup"><span data-stu-id="9530f-106">However, the lengths of the respective dimensions do not need to be the same.</span></span>  
  
- <span data-ttu-id="9530f-107">**Element Data Type.**</span><span class="sxs-lookup"><span data-stu-id="9530f-107">**Element Data Type.**</span></span> <span data-ttu-id="9530f-108">The data types of the elements of both arrays must be reference types.</span><span class="sxs-lookup"><span data-stu-id="9530f-108">The data types of the elements of both arrays must be reference types.</span></span> <span data-ttu-id="9530f-109">You cannot convert an `Integer` array to a `Long` array, or even to an `Object` array, because at least one value type is involved.</span><span class="sxs-lookup"><span data-stu-id="9530f-109">You cannot convert an `Integer` array to a `Long` array, or even to an `Object` array, because at least one value type is involved.</span></span> <span data-ttu-id="9530f-110">For more information, see [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="9530f-110">For more information, see [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span></span>  
  
- <span data-ttu-id="9530f-111">**Convertibility.**</span><span class="sxs-lookup"><span data-stu-id="9530f-111">**Convertibility.**</span></span> <span data-ttu-id="9530f-112">A conversion, either widening or narrowing, must be possible between the element types of the two arrays.</span><span class="sxs-lookup"><span data-stu-id="9530f-112">A conversion, either widening or narrowing, must be possible between the element types of the two arrays.</span></span> <span data-ttu-id="9530f-113">An example that fails this requirement is an attempted conversion between a `String` array and an array of a class derived from <xref:System.Attribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9530f-113">An example that fails this requirement is an attempted conversion between a `String` array and an array of a class derived from <xref:System.Attribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9530f-114">These two types have nothing in common, and no conversion of any kind exists between them.</span><span class="sxs-lookup"><span data-stu-id="9530f-114">These two types have nothing in common, and no conversion of any kind exists between them.</span></span>  
  
 <span data-ttu-id="9530f-115">A conversion of one array type to another is widening or narrowing depending on whether the conversion of the respective elements is widening or narrowing.</span><span class="sxs-lookup"><span data-stu-id="9530f-115">A conversion of one array type to another is widening or narrowing depending on whether the conversion of the respective elements is widening or narrowing.</span></span> <span data-ttu-id="9530f-116">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="9530f-116">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>  
  
## <a name="conversion-to-an-object-array"></a><span data-ttu-id="9530f-117">Conversion to an Object Array</span><span class="sxs-lookup"><span data-stu-id="9530f-117">Conversion to an Object Array</span></span>  
 <span data-ttu-id="9530f-118">When you declare an `Object` array without initializing it, its element type is `Object` as long as it remains uninitialized.</span><span class="sxs-lookup"><span data-stu-id="9530f-118">When you declare an `Object` array without initializing it, its element type is `Object` as long as it remains uninitialized.</span></span> <span data-ttu-id="9530f-119">When you set it to an array of a specific class, it takes on the type of that class.</span><span class="sxs-lookup"><span data-stu-id="9530f-119">When you set it to an array of a specific class, it takes on the type of that class.</span></span> <span data-ttu-id="9530f-120">However, its underlying type is still `Object`, and you can subsequently set it to another array of an unrelated class.</span><span class="sxs-lookup"><span data-stu-id="9530f-120">However, its underlying type is still `Object`, and you can subsequently set it to another array of an unrelated class.</span></span> <span data-ttu-id="9530f-121">Since all classes derive from `Object`, you can change the array's element type from any class to any other class.</span><span class="sxs-lookup"><span data-stu-id="9530f-121">Since all classes derive from `Object`, you can change the array's element type from any class to any other class.</span></span>  
  
 <span data-ttu-id="9530f-122">In the following example, no conversion exists between types `student` and `String`, but both derive from `Object`, so all assignments are valid.</span><span class="sxs-lookup"><span data-stu-id="9530f-122">In the following example, no conversion exists between types `student` and `String`, but both derive from `Object`, so all assignments are valid.</span></span>  
  
```vb  
' Assume student has already been defined as a class.  
Dim testArray() As Object  
' testArray is still an Object array at this point.  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
testArray = New student(3) {}  
' testArray is now of type student().  
testArray = names  
' testArray is now a String array.  
```  
  
### <a name="underlying-type-of-an-array"></a><span data-ttu-id="9530f-123">Underlying Type of an Array</span><span class="sxs-lookup"><span data-stu-id="9530f-123">Underlying Type of an Array</span></span>  
 <span data-ttu-id="9530f-124">If you originally declare an array with a specific class, its underlying element type is that class.</span><span class="sxs-lookup"><span data-stu-id="9530f-124">If you originally declare an array with a specific class, its underlying element type is that class.</span></span> <span data-ttu-id="9530f-125">If you subsequently set it to an array of another class, there must be a conversion between the two classes.</span><span class="sxs-lookup"><span data-stu-id="9530f-125">If you subsequently set it to an array of another class, there must be a conversion between the two classes.</span></span>  
  
 <span data-ttu-id="9530f-126">In the following example, `students` is a `student` array.</span><span class="sxs-lookup"><span data-stu-id="9530f-126">In the following example, `students` is a `student` array.</span></span> <span data-ttu-id="9530f-127">Since no conversion exists between `String` and `student`, the last statement fails.</span><span class="sxs-lookup"><span data-stu-id="9530f-127">Since no conversion exists between `String` and `student`, the last statement fails.</span></span>  
  
```vb  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## <a name="see-also"></a><span data-ttu-id="9530f-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9530f-128">See also</span></span>

- [<span data-ttu-id="9530f-129">Typy danych</span><span class="sxs-lookup"><span data-stu-id="9530f-129">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="9530f-130">Type Conversions in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9530f-130">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="9530f-131">Konwersje jawne i niejawne</span><span class="sxs-lookup"><span data-stu-id="9530f-131">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="9530f-132">Konwertowanie między ciągami a innymi typami danych</span><span class="sxs-lookup"><span data-stu-id="9530f-132">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="9530f-133">How to: Convert an Object to Another Type in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9530f-133">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [<span data-ttu-id="9530f-134">Typy danych</span><span class="sxs-lookup"><span data-stu-id="9530f-134">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="9530f-135">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="9530f-135">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="9530f-136">Tablice</span><span class="sxs-lookup"><span data-stu-id="9530f-136">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
