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
ms.openlocfilehash: 475f3f5357f7c989a30ca9e6c5d32b8cc989436f
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581861"
---
# <a name="array-conversions-visual-basic"></a><span data-ttu-id="aac32-102">Konwersje tablic (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aac32-102">Array Conversions (Visual Basic)</span></span>
<span data-ttu-id="aac32-103">Typ tablicy można skonwertować na inny typ tablicy, pod warunkiem, że są spełnione następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="aac32-103">You can convert an array type to a different array type provided you meet the following conditions:</span></span>  
  
- <span data-ttu-id="aac32-104">**Równa ranga.**</span><span class="sxs-lookup"><span data-stu-id="aac32-104">**Equal Rank.**</span></span> <span data-ttu-id="aac32-105">Range dwóch tablic muszą być takie same, co oznacza, że muszą mieć taką samą liczbę wymiarów.</span><span class="sxs-lookup"><span data-stu-id="aac32-105">The ranks of the two arrays must be the same, that is, they must have the same number of dimensions.</span></span> <span data-ttu-id="aac32-106">Jednak długości odpowiednich wymiarów nie muszą być takie same.</span><span class="sxs-lookup"><span data-stu-id="aac32-106">However, the lengths of the respective dimensions do not need to be the same.</span></span>  
  
- <span data-ttu-id="aac32-107">**Typ danych elementu.**</span><span class="sxs-lookup"><span data-stu-id="aac32-107">**Element Data Type.**</span></span> <span data-ttu-id="aac32-108">Typy danych elementów obu tablic muszą być typami referencyjnymi.</span><span class="sxs-lookup"><span data-stu-id="aac32-108">The data types of the elements of both arrays must be reference types.</span></span> <span data-ttu-id="aac32-109">Nie można przekonwertować tablicy `Integer` na tablicę `Long` lub nawet do tablicy `Object`, ponieważ jest uwzględniany co najmniej jeden typ wartości.</span><span class="sxs-lookup"><span data-stu-id="aac32-109">You cannot convert an `Integer` array to a `Long` array, or even to an `Object` array, because at least one value type is involved.</span></span> <span data-ttu-id="aac32-110">Aby uzyskać więcej informacji, zobacz [typy wartości i typy odwołań](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="aac32-110">For more information, see [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span></span>  
  
- <span data-ttu-id="aac32-111">**Convertibility.**</span><span class="sxs-lookup"><span data-stu-id="aac32-111">**Convertibility.**</span></span> <span data-ttu-id="aac32-112">Konwersja, rozszerzająca lub zawężania, musi być możliwa między typami elementów dwóch tablic.</span><span class="sxs-lookup"><span data-stu-id="aac32-112">A conversion, either widening or narrowing, must be possible between the element types of the two arrays.</span></span> <span data-ttu-id="aac32-113">Przykładem niepowodzenia tego wymagania jest próba konwersji między tablicą `String` i tablicą klasy pochodnej <xref:System.Attribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="aac32-113">An example that fails this requirement is an attempted conversion between a `String` array and an array of a class derived from <xref:System.Attribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="aac32-114">Te dwa typy nie mają wspólnych wartości i nie istnieje konwersja żadnego rodzaju między nimi.</span><span class="sxs-lookup"><span data-stu-id="aac32-114">These two types have nothing in common, and no conversion of any kind exists between them.</span></span>  
  
 <span data-ttu-id="aac32-115">Konwersja jednego typu tablicy na inny jest poszerzana lub zawężana w zależności od tego, czy konwersja odpowiednich elementów jest poszerzana czy zawężana.</span><span class="sxs-lookup"><span data-stu-id="aac32-115">A conversion of one array type to another is widening or narrowing depending on whether the conversion of the respective elements is widening or narrowing.</span></span> <span data-ttu-id="aac32-116">Aby uzyskać więcej informacji, zobacz [rozszerzanie i zwężanie konwersji](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="aac32-116">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>  
  
## <a name="conversion-to-an-object-array"></a><span data-ttu-id="aac32-117">Konwersja na tablicę obiektów</span><span class="sxs-lookup"><span data-stu-id="aac32-117">Conversion to an Object Array</span></span>  
 <span data-ttu-id="aac32-118">Gdy deklarujesz tablicę `Object` bez jej inicjalizacji, jej typ elementu jest `Object`, dopóki nie zostanie zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="aac32-118">When you declare an `Object` array without initializing it, its element type is `Object` as long as it remains uninitialized.</span></span> <span data-ttu-id="aac32-119">Gdy ustawiasz ją na tablicę określonej klasy, przyjmuje ona typ tej klasy.</span><span class="sxs-lookup"><span data-stu-id="aac32-119">When you set it to an array of a specific class, it takes on the type of that class.</span></span> <span data-ttu-id="aac32-120">Jednak jego typ podstawowy jest nadal `Object` i można następnie ustawić go na inną tablicę niepowiązanej klasy.</span><span class="sxs-lookup"><span data-stu-id="aac32-120">However, its underlying type is still `Object`, and you can subsequently set it to another array of an unrelated class.</span></span> <span data-ttu-id="aac32-121">Ponieważ wszystkie klasy pochodzą z `Object`, można zmienić typ elementu tablicy z dowolnej klasy na dowolną inną klasę.</span><span class="sxs-lookup"><span data-stu-id="aac32-121">Since all classes derive from `Object`, you can change the array's element type from any class to any other class.</span></span>  
  
 <span data-ttu-id="aac32-122">W poniższym przykładzie nie istnieje konwersja między typami `student` i `String`, ale oba pochodzą z `Object`, więc wszystkie przypisania są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="aac32-122">In the following example, no conversion exists between types `student` and `String`, but both derive from `Object`, so all assignments are valid.</span></span>  
  
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
  
### <a name="underlying-type-of-an-array"></a><span data-ttu-id="aac32-123">Typ podstawowy tablicy</span><span class="sxs-lookup"><span data-stu-id="aac32-123">Underlying Type of an Array</span></span>  
 <span data-ttu-id="aac32-124">Jeśli pierwotnie deklarujesz tablicę z określoną klasą, jej typem elementu podstawowego jest Klasa.</span><span class="sxs-lookup"><span data-stu-id="aac32-124">If you originally declare an array with a specific class, its underlying element type is that class.</span></span> <span data-ttu-id="aac32-125">Jeśli następnie ustawisz ją na tablicę innej klasy, musi istnieć konwersja między tymi dwiema klasami.</span><span class="sxs-lookup"><span data-stu-id="aac32-125">If you subsequently set it to an array of another class, there must be a conversion between the two classes.</span></span>  
  
 <span data-ttu-id="aac32-126">W poniższym przykładzie `students` jest tablicą `student`.</span><span class="sxs-lookup"><span data-stu-id="aac32-126">In the following example, `students` is a `student` array.</span></span> <span data-ttu-id="aac32-127">Ponieważ nie istnieje żadna konwersja między `String` i `student`, Ostatnia instrukcja kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="aac32-127">Since no conversion exists between `String` and `student`, the last statement fails.</span></span>  
  
```vb  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## <a name="see-also"></a><span data-ttu-id="aac32-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aac32-128">See also</span></span>

- [<span data-ttu-id="aac32-129">Typy danych</span><span class="sxs-lookup"><span data-stu-id="aac32-129">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="aac32-130">Konwersje typów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="aac32-130">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="aac32-131">Konwersje jawne i niejawne</span><span class="sxs-lookup"><span data-stu-id="aac32-131">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="aac32-132">Konwertowanie między ciągami a innymi typami danych</span><span class="sxs-lookup"><span data-stu-id="aac32-132">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="aac32-133">Instrukcje: konwertowanie obiektu na inny typ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="aac32-133">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [<span data-ttu-id="aac32-134">Typy danych</span><span class="sxs-lookup"><span data-stu-id="aac32-134">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="aac32-135">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="aac32-135">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="aac32-136">Tablice</span><span class="sxs-lookup"><span data-stu-id="aac32-136">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
