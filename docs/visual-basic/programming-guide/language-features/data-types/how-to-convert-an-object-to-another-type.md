---
title: 'Porady: konwertowanie obiektu do innego typu w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
ms.openlocfilehash: 39083fc55d30e24c357ec162a15466f81655f4c8
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582328"
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a><span data-ttu-id="c9290-102">Porady: konwertowanie obiektu do innego typu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c9290-102">How to: Convert an Object to Another Type in Visual Basic</span></span>
<span data-ttu-id="c9290-103">Zmienna `Object` jest konwertowana na inny typ danych za pomocą słowa kluczowego konwersji, takiego jak [Funkcja CType](../../../../visual-basic/language-reference/functions/ctype-function.md).</span><span class="sxs-lookup"><span data-stu-id="c9290-103">You convert an `Object` variable to another data type by using a conversion keyword such as [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9290-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="c9290-104">Example</span></span>  
 <span data-ttu-id="c9290-105">Poniższy przykład konwertuje zmienną `Object` na `Integer` i `String`.</span><span class="sxs-lookup"><span data-stu-id="c9290-105">The following example converts an `Object` variable to an `Integer` and a `String`.</span></span>  
  
```vb  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 <span data-ttu-id="c9290-106">Jeśli wiesz, że zawartość zmiennej `Object` jest określonego typu danych, lepiej jest skonwertować zmienną na ten typ danych.</span><span class="sxs-lookup"><span data-stu-id="c9290-106">If you know that the contents of an `Object` variable are of a particular data type, it is better to convert the variable to that data type.</span></span> <span data-ttu-id="c9290-107">Jeśli nadal używasz zmiennej `Object`, naliczane są *opakowanie* i *rozpakowywanie* (dla typu wartości) lub *późne wiązanie* (dla typu odwołania).</span><span class="sxs-lookup"><span data-stu-id="c9290-107">If you continue to use the `Object` variable, you incur either *boxing* and *unboxing* (for a value type) or *late binding* (for a reference type).</span></span> <span data-ttu-id="c9290-108">Wszystkie te operacje pobierają dodatkowy czas wykonywania i zwiększają wydajność.</span><span class="sxs-lookup"><span data-stu-id="c9290-108">These operations all take extra execution time and make your performance slower.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c9290-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="c9290-109">Compiling the Code</span></span>  
 <span data-ttu-id="c9290-110">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="c9290-110">This example requires:</span></span>  
  
- <span data-ttu-id="c9290-111">Odwołanie do przestrzeni nazw <xref:System?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c9290-111">A reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9290-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c9290-112">See also</span></span>

- <xref:System.Object>
- [<span data-ttu-id="c9290-113">Konwersje typów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c9290-113">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="c9290-114">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="c9290-114">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="c9290-115">Konwersje jawne i niejawne</span><span class="sxs-lookup"><span data-stu-id="c9290-115">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="c9290-116">Konwertowanie między ciągami a innymi typami danych</span><span class="sxs-lookup"><span data-stu-id="c9290-116">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="c9290-117">Konwersje tablic</span><span class="sxs-lookup"><span data-stu-id="c9290-117">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
- [<span data-ttu-id="c9290-118">Struktury</span><span class="sxs-lookup"><span data-stu-id="c9290-118">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="c9290-119">Typy danych</span><span class="sxs-lookup"><span data-stu-id="c9290-119">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="c9290-120">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="c9290-120">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
