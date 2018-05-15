---
title: Konwersje tablic (Visual Basic)
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
ms.openlocfilehash: a179b7cf5b82132db88fb5412f0ca4be207f0987
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="array-conversions-visual-basic"></a><span data-ttu-id="35397-102">Konwersje tablic (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="35397-102">Array Conversions (Visual Basic)</span></span>
<span data-ttu-id="35397-103">Typem tablicy można przekonwertować na typ tablicy różnych pod warunkiem spełniać następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="35397-103">You can convert an array type to a different array type provided you meet the following conditions:</span></span>  
  
-   <span data-ttu-id="35397-104">**Ranga takie same.**</span><span class="sxs-lookup"><span data-stu-id="35397-104">**Equal Rank.**</span></span> <span data-ttu-id="35397-105">Rangi dwóch tablic muszą być takie same, oznacza to, musi mieć taką samą liczbę wymiarów.</span><span class="sxs-lookup"><span data-stu-id="35397-105">The ranks of the two arrays must be the same, that is, they must have the same number of dimensions.</span></span> <span data-ttu-id="35397-106">Jednak nie długości odpowiednich wymiarów muszą być takie same.</span><span class="sxs-lookup"><span data-stu-id="35397-106">However, the lengths of the respective dimensions do not need to be the same.</span></span>  
  
-   <span data-ttu-id="35397-107">**Typ danych elementu.**</span><span class="sxs-lookup"><span data-stu-id="35397-107">**Element Data Type.**</span></span> <span data-ttu-id="35397-108">Typy danych elementów zarówno tablic muszą być typy referencyjne.</span><span class="sxs-lookup"><span data-stu-id="35397-108">The data types of the elements of both arrays must be reference types.</span></span> <span data-ttu-id="35397-109">Nie można przekonwertować `Integer` tablicy do `Long` tablicy, a nawet z `Object` tablicy, ponieważ jest elementem typu co najmniej jedną wartość.</span><span class="sxs-lookup"><span data-stu-id="35397-109">You cannot convert an `Integer` array to a `Long` array, or even to an `Object` array, because at least one value type is involved.</span></span> <span data-ttu-id="35397-110">Aby uzyskać więcej informacji, zobacz [typów wartości i typy referencyjne](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="35397-110">For more information, see [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span></span>  
  
-   <span data-ttu-id="35397-111">**Możliwości konwersji.**</span><span class="sxs-lookup"><span data-stu-id="35397-111">**Convertibility.**</span></span> <span data-ttu-id="35397-112">Konwersja, rozszerzanie albo zawężanie, musi być możliwe między typami elementu dwóch tablic.</span><span class="sxs-lookup"><span data-stu-id="35397-112">A conversion, either widening or narrowing, must be possible between the element types of the two arrays.</span></span> <span data-ttu-id="35397-113">Przykładem, który zakończy się niepowodzeniem to wymaganie jest próba konwersji między `String` tablicy i Tablica klasę pochodną <xref:System.Attribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="35397-113">An example that fails this requirement is an attempted conversion between a `String` array and an array of a class derived from <xref:System.Attribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="35397-114">Te dwa typy mają one nic wspólnego, a nie dowolnego rodzaju istnieje konwersja między nimi.</span><span class="sxs-lookup"><span data-stu-id="35397-114">These two types have nothing in common, and no conversion of any kind exists between them.</span></span>  
  
 <span data-ttu-id="35397-115">Konwersja typu tablicy do innej rozszerzanie lub zawężanie w zależności od tego, czy rozszerzanie lub zawężanie konwersji odpowiednich elementów.</span><span class="sxs-lookup"><span data-stu-id="35397-115">A conversion of one array type to another is widening or narrowing depending on whether the conversion of the respective elements is widening or narrowing.</span></span> <span data-ttu-id="35397-116">Aby uzyskać więcej informacji, zobacz [rozszerzanie i zwężanie konwersji](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="35397-116">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>  
  
## <a name="conversion-to-an-object-array"></a><span data-ttu-id="35397-117">Konwersja na tablicę obiektów</span><span class="sxs-lookup"><span data-stu-id="35397-117">Conversion to an Object Array</span></span>  
 <span data-ttu-id="35397-118">Gdy zadeklarować `Object` tablica bez jego typem elementu inicjowania jest `Object` tak długo, jak pozostaje niezainicjowany.</span><span class="sxs-lookup"><span data-stu-id="35397-118">When you declare an `Object` array without initializing it, its element type is `Object` as long as it remains uninitialized.</span></span> <span data-ttu-id="35397-119">Po ustawieniu na tablicę określonej klasy przejmuje typ tej klasy.</span><span class="sxs-lookup"><span data-stu-id="35397-119">When you set it to an array of a specific class, it takes on the type of that class.</span></span> <span data-ttu-id="35397-120">Jednak jego typ podstawowy jest nadal `Object`, i później może go ustawić na innej tablicy klasy niepowiązanych.</span><span class="sxs-lookup"><span data-stu-id="35397-120">However, its underlying type is still `Object`, and you can subsequently set it to another array of an unrelated class.</span></span> <span data-ttu-id="35397-121">Ponieważ wszystkie klasy pochodzi od `Object`, możesz zmienić typ elementu tablicy w dowolnej klasy do innej klasy.</span><span class="sxs-lookup"><span data-stu-id="35397-121">Since all classes derive from `Object`, you can change the array's element type from any class to any other class.</span></span>  
  
 <span data-ttu-id="35397-122">W poniższym przykładzie, nie istnieje konwersja między typami `student` i `String`, ale jednocześnie pochodzi z `Object`, więc wszystkie przypisania są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="35397-122">In the following example, no conversion exists between types `student` and `String`, but both derive from `Object`, so all assignments are valid.</span></span>  
  
```  
' Assume student has already been defined as a class.  
Dim testArray() As Object  
' testArray is still an Object array at this point.  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
testArray = New student(3) {}  
' testArray is now of type student().  
testArray = names  
' testArray is now a String array.  
```  
  
### <a name="underlying-type-of-an-array"></a><span data-ttu-id="35397-123">Typ podstawowy elementu tablicy</span><span class="sxs-lookup"><span data-stu-id="35397-123">Underlying Type of an Array</span></span>  
 <span data-ttu-id="35397-124">Jeśli pierwotnie zadeklarować tablicy o określonej klasy, jego typ podstawowy elementu jest tej klasy.</span><span class="sxs-lookup"><span data-stu-id="35397-124">If you originally declare an array with a specific class, its underlying element type is that class.</span></span> <span data-ttu-id="35397-125">Jeśli zostanie następnie ustawiona na tablicę innej klasy, musi być konwersji między dwiema klasami.</span><span class="sxs-lookup"><span data-stu-id="35397-125">If you subsequently set it to an array of another class, there must be a conversion between the two classes.</span></span>  
  
 <span data-ttu-id="35397-126">W poniższym przykładzie `students` jest `student` tablicy.</span><span class="sxs-lookup"><span data-stu-id="35397-126">In the following example, `students` is a `student` array.</span></span> <span data-ttu-id="35397-127">Ponieważ nie istnieje konwersja między `String` i `student`, ostatniej instrukcji nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="35397-127">Since no conversion exists between `String` and `student`, the last statement fails.</span></span>  
  
```  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## <a name="see-also"></a><span data-ttu-id="35397-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="35397-128">See Also</span></span>  
 [<span data-ttu-id="35397-129">Typy danych</span><span class="sxs-lookup"><span data-stu-id="35397-129">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="35397-130">Konwersje typów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="35397-130">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="35397-131">Konwersje jawne i niejawne</span><span class="sxs-lookup"><span data-stu-id="35397-131">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="35397-132">Konwertowanie między ciągami a innymi typami danych</span><span class="sxs-lookup"><span data-stu-id="35397-132">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [<span data-ttu-id="35397-133">Porady: konwertowanie obiektu do innego typu w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="35397-133">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [<span data-ttu-id="35397-134">Typy danych</span><span class="sxs-lookup"><span data-stu-id="35397-134">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="35397-135">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="35397-135">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="35397-136">Tablice</span><span class="sxs-lookup"><span data-stu-id="35397-136">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
