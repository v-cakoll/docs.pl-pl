---
title: 'Instrukcje: konwertowanie obiektu na inny typ'
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
ms.openlocfilehash: 6d16e0eafc3fa9233037abe0c92dcb1945ca8da9
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75341585"
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a><span data-ttu-id="bdcda-102">Porady: konwertowanie obiektu do innego typu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bdcda-102">How to: Convert an Object to Another Type in Visual Basic</span></span>
<span data-ttu-id="bdcda-103">Zmienna `Object` jest konwertowana na inny typ danych za pomocą słowa kluczowego konwersji, takiego jak [Funkcja CType](../../../../visual-basic/language-reference/functions/ctype-function.md).</span><span class="sxs-lookup"><span data-stu-id="bdcda-103">You convert an `Object` variable to another data type by using a conversion keyword such as [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bdcda-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="bdcda-104">Example</span></span>  
 <span data-ttu-id="bdcda-105">Poniższy przykład konwertuje zmienną `Object` na `Integer` i `String`.</span><span class="sxs-lookup"><span data-stu-id="bdcda-105">The following example converts an `Object` variable to an `Integer` and a `String`.</span></span>  
  
```vb  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 <span data-ttu-id="bdcda-106">Jeśli wiesz, że zawartość zmiennej `Object` jest określonego typu danych, lepiej jest skonwertować zmienną na ten typ danych.</span><span class="sxs-lookup"><span data-stu-id="bdcda-106">If you know that the contents of an `Object` variable are of a particular data type, it is better to convert the variable to that data type.</span></span> <span data-ttu-id="bdcda-107">Jeśli nadal używasz zmiennej `Object`, naliczane są *opakowanie* i *rozpakowywanie* (dla typu wartości) lub *późne wiązanie* (dla typu odwołania).</span><span class="sxs-lookup"><span data-stu-id="bdcda-107">If you continue to use the `Object` variable, you incur either *boxing* and *unboxing* (for a value type) or *late binding* (for a reference type).</span></span> <span data-ttu-id="bdcda-108">Wszystkie te operacje pobierają dodatkowy czas wykonywania i zwiększają wydajność.</span><span class="sxs-lookup"><span data-stu-id="bdcda-108">These operations all take extra execution time and make your performance slower.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="bdcda-109">Skompilować kod</span><span class="sxs-lookup"><span data-stu-id="bdcda-109">Compile the code</span></span>  
 <span data-ttu-id="bdcda-110">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="bdcda-110">This example requires:</span></span>  
  
- <span data-ttu-id="bdcda-111">Odwołanie do przestrzeni nazw <xref:System?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bdcda-111">A reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdcda-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bdcda-112">See also</span></span>

- <xref:System.Object>
- [<span data-ttu-id="bdcda-113">Konwersje typów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bdcda-113">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="bdcda-114">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="bdcda-114">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="bdcda-115">Konwersje jawne i niejawne</span><span class="sxs-lookup"><span data-stu-id="bdcda-115">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="bdcda-116">Konwertowanie między ciągami a innymi typami danych</span><span class="sxs-lookup"><span data-stu-id="bdcda-116">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="bdcda-117">Konwersje tablic</span><span class="sxs-lookup"><span data-stu-id="bdcda-117">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
- [<span data-ttu-id="bdcda-118">Struktury</span><span class="sxs-lookup"><span data-stu-id="bdcda-118">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="bdcda-119">Typy danych</span><span class="sxs-lookup"><span data-stu-id="bdcda-119">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="bdcda-120">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="bdcda-120">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
