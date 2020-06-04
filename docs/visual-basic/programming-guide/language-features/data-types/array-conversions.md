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
ms.openlocfilehash: 1d20b01200d3f967e3355dc6e9651291003d140e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402008"
---
# <a name="array-conversions-visual-basic"></a><span data-ttu-id="c6b62-102">Konwersje tablic (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6b62-102">Array Conversions (Visual Basic)</span></span>
<span data-ttu-id="c6b62-103">Typ tablicy można skonwertować na inny typ tablicy, pod warunkiem, że są spełnione następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="c6b62-103">You can convert an array type to a different array type provided you meet the following conditions:</span></span>  
  
- <span data-ttu-id="c6b62-104">**Równa ranga.**</span><span class="sxs-lookup"><span data-stu-id="c6b62-104">**Equal Rank.**</span></span> <span data-ttu-id="c6b62-105">Range dwóch tablic muszą być takie same, co oznacza, że muszą mieć taką samą liczbę wymiarów.</span><span class="sxs-lookup"><span data-stu-id="c6b62-105">The ranks of the two arrays must be the same, that is, they must have the same number of dimensions.</span></span> <span data-ttu-id="c6b62-106">Jednak długości odpowiednich wymiarów nie muszą być takie same.</span><span class="sxs-lookup"><span data-stu-id="c6b62-106">However, the lengths of the respective dimensions do not need to be the same.</span></span>  
  
- <span data-ttu-id="c6b62-107">**Typ danych elementu.**</span><span class="sxs-lookup"><span data-stu-id="c6b62-107">**Element Data Type.**</span></span> <span data-ttu-id="c6b62-108">Typy danych elementów obu tablic muszą być typami referencyjnymi.</span><span class="sxs-lookup"><span data-stu-id="c6b62-108">The data types of the elements of both arrays must be reference types.</span></span> <span data-ttu-id="c6b62-109">Nie można przekonwertować `Integer` tablicy na `Long` tablicę, a nawet do `Object` tablicy, ponieważ występuje co najmniej jeden typ wartości.</span><span class="sxs-lookup"><span data-stu-id="c6b62-109">You cannot convert an `Integer` array to a `Long` array, or even to an `Object` array, because at least one value type is involved.</span></span> <span data-ttu-id="c6b62-110">Aby uzyskać więcej informacji, zobacz [typy wartości i typy odwołań](value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="c6b62-110">For more information, see [Value Types and Reference Types](value-types-and-reference-types.md).</span></span>  
  
- <span data-ttu-id="c6b62-111">**Convertibility.**</span><span class="sxs-lookup"><span data-stu-id="c6b62-111">**Convertibility.**</span></span> <span data-ttu-id="c6b62-112">Konwersja, rozszerzająca lub zawężania, musi być możliwa między typami elementów dwóch tablic.</span><span class="sxs-lookup"><span data-stu-id="c6b62-112">A conversion, either widening or narrowing, must be possible between the element types of the two arrays.</span></span> <span data-ttu-id="c6b62-113">Przykładem, że niepowodzenie tego wymagania jest próba konwersji między `String` tablicą a tablicą klasy pochodnej <xref:System.Attribute?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="c6b62-113">An example that fails this requirement is an attempted conversion between a `String` array and an array of a class derived from <xref:System.Attribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c6b62-114">Te dwa typy nie mają wspólnych wartości i nie istnieje konwersja żadnego rodzaju między nimi.</span><span class="sxs-lookup"><span data-stu-id="c6b62-114">These two types have nothing in common, and no conversion of any kind exists between them.</span></span>  
  
 <span data-ttu-id="c6b62-115">Konwersja jednego typu tablicy na inny jest poszerzana lub zawężana w zależności od tego, czy konwersja odpowiednich elementów jest poszerzana czy zawężana.</span><span class="sxs-lookup"><span data-stu-id="c6b62-115">A conversion of one array type to another is widening or narrowing depending on whether the conversion of the respective elements is widening or narrowing.</span></span> <span data-ttu-id="c6b62-116">Aby uzyskać więcej informacji, zobacz [rozszerzanie i zwężanie konwersji](widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="c6b62-116">For more information, see [Widening and Narrowing Conversions](widening-and-narrowing-conversions.md).</span></span>  
  
## <a name="conversion-to-an-object-array"></a><span data-ttu-id="c6b62-117">Konwersja na tablicę obiektów</span><span class="sxs-lookup"><span data-stu-id="c6b62-117">Conversion to an Object Array</span></span>  
 <span data-ttu-id="c6b62-118">Po zadeklarowaniu `Object` tablicy bez jej inicjalizacji jej typ elementu jest `Object` tak długo, jak pozostaje niezainicjowany.</span><span class="sxs-lookup"><span data-stu-id="c6b62-118">When you declare an `Object` array without initializing it, its element type is `Object` as long as it remains uninitialized.</span></span> <span data-ttu-id="c6b62-119">Gdy ustawiasz ją na tablicę określonej klasy, przyjmuje ona typ tej klasy.</span><span class="sxs-lookup"><span data-stu-id="c6b62-119">When you set it to an array of a specific class, it takes on the type of that class.</span></span> <span data-ttu-id="c6b62-120">Jednak jego typ podstawowy jest nadal `Object` , a następnie można ustawić go na inną tablicę niepowiązanej klasy.</span><span class="sxs-lookup"><span data-stu-id="c6b62-120">However, its underlying type is still `Object`, and you can subsequently set it to another array of an unrelated class.</span></span> <span data-ttu-id="c6b62-121">Ponieważ wszystkie klasy pochodzą z `Object` , można zmienić typ elementu tablicy z dowolnej klasy na dowolną inną klasę.</span><span class="sxs-lookup"><span data-stu-id="c6b62-121">Since all classes derive from `Object`, you can change the array's element type from any class to any other class.</span></span>  
  
 <span data-ttu-id="c6b62-122">W poniższym przykładzie nie istnieje żadna konwersja między typami `student` i `String` , ale obie wartości pochodzą od `Object` , więc wszystkie przypisania są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="c6b62-122">In the following example, no conversion exists between types `student` and `String`, but both derive from `Object`, so all assignments are valid.</span></span>  
  
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
  
### <a name="underlying-type-of-an-array"></a><span data-ttu-id="c6b62-123">Typ podstawowy tablicy</span><span class="sxs-lookup"><span data-stu-id="c6b62-123">Underlying Type of an Array</span></span>  
 <span data-ttu-id="c6b62-124">Jeśli pierwotnie deklarujesz tablicę z określoną klasą, jej typem elementu podstawowego jest Klasa.</span><span class="sxs-lookup"><span data-stu-id="c6b62-124">If you originally declare an array with a specific class, its underlying element type is that class.</span></span> <span data-ttu-id="c6b62-125">Jeśli następnie ustawisz ją na tablicę innej klasy, musi istnieć konwersja między tymi dwiema klasami.</span><span class="sxs-lookup"><span data-stu-id="c6b62-125">If you subsequently set it to an array of another class, there must be a conversion between the two classes.</span></span>  
  
 <span data-ttu-id="c6b62-126">W poniższym przykładzie `students` jest `student` tablicą.</span><span class="sxs-lookup"><span data-stu-id="c6b62-126">In the following example, `students` is a `student` array.</span></span> <span data-ttu-id="c6b62-127">Ponieważ nie istnieje konwersja między `String` i `student` , Ostatnia instrukcja kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="c6b62-127">Since no conversion exists between `String` and `student`, the last statement fails.</span></span>  
  
```vb  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## <a name="see-also"></a><span data-ttu-id="c6b62-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c6b62-128">See also</span></span>

- [<span data-ttu-id="c6b62-129">Typy danych</span><span class="sxs-lookup"><span data-stu-id="c6b62-129">Data Types</span></span>](index.md)
- [<span data-ttu-id="c6b62-130">Konwersje plików w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c6b62-130">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="c6b62-131">Konwersje jawne i niejawne</span><span class="sxs-lookup"><span data-stu-id="c6b62-131">Implicit and Explicit Conversions</span></span>](implicit-and-explicit-conversions.md)
- [<span data-ttu-id="c6b62-132">Konwertowanie między ciągami a innymi typami danych</span><span class="sxs-lookup"><span data-stu-id="c6b62-132">Conversions Between Strings and Other Types</span></span>](conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="c6b62-133">Porady: konwertowanie obiektu do innego typu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c6b62-133">How to: Convert an Object to Another Type in Visual Basic</span></span>](how-to-convert-an-object-to-another-type.md)
- [<span data-ttu-id="c6b62-134">Typy danych</span><span class="sxs-lookup"><span data-stu-id="c6b62-134">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="c6b62-135">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="c6b62-135">Type Conversion Functions</span></span>](../../../language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="c6b62-136">Tablice</span><span class="sxs-lookup"><span data-stu-id="c6b62-136">Arrays</span></span>](../arrays/index.md)
