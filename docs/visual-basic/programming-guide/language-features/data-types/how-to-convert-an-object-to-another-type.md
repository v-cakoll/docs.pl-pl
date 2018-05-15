---
title: 'Porady: konwertowanie obiektu do innego typu w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
ms.openlocfilehash: 367991e4bbca710df54edf73179f855ff79bb56e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a><span data-ttu-id="103b3-102">Porady: konwertowanie obiektu do innego typu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="103b3-102">How to: Convert an Object to Another Type in Visual Basic</span></span>
<span data-ttu-id="103b3-103">Możesz przekonwertować `Object` zmiennej na inny typ danych przy użyciu słowa kluczowego konwersji, takich jak [CType — funkcja](../../../../visual-basic/language-reference/functions/ctype-function.md).</span><span class="sxs-lookup"><span data-stu-id="103b3-103">You convert an `Object` variable to another data type by using a conversion keyword such as [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="103b3-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="103b3-104">Example</span></span>  
 <span data-ttu-id="103b3-105">Poniższy przykład konwertuje `Object` zmienną `Integer` i `String`.</span><span class="sxs-lookup"><span data-stu-id="103b3-105">The following example converts an `Object` variable to an `Integer` and a `String`.</span></span>  
  
```  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 <span data-ttu-id="103b3-106">Jeśli wiesz, że zawartość `Object` są zmiennej typu danych, warto przekonwertować zmiennej typu danych.</span><span class="sxs-lookup"><span data-stu-id="103b3-106">If you know that the contents of an `Object` variable are of a particular data type, it is better to convert the variable to that data type.</span></span> <span data-ttu-id="103b3-107">Jeśli będziesz nadal używać `Object` zmiennej, ponosisz albo *boxing* i *rozpakowującej* (dla typu wartości) lub *późne wiązanie* (dla typu odwołania).</span><span class="sxs-lookup"><span data-stu-id="103b3-107">If you continue to use the `Object` variable, you incur either *boxing* and *unboxing* (for a value type) or *late binding* (for a reference type).</span></span> <span data-ttu-id="103b3-108">Te operacje wszystkie zająć dodatkowy czas wykonywania i upewnij wydajność wolniejszej.</span><span class="sxs-lookup"><span data-stu-id="103b3-108">These operations all take extra execution time and make your performance slower.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="103b3-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="103b3-109">Compiling the Code</span></span>  
 <span data-ttu-id="103b3-110">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="103b3-110">This example requires:</span></span>  
  
-   <span data-ttu-id="103b3-111">Odwołanie do <xref:System?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="103b3-111">A reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="103b3-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="103b3-112">See Also</span></span>  
 <xref:System.Object>  
 [<span data-ttu-id="103b3-113">Konwersje typów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="103b3-113">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="103b3-114">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="103b3-114">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="103b3-115">Konwersje jawne i niejawne</span><span class="sxs-lookup"><span data-stu-id="103b3-115">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="103b3-116">Konwertowanie między ciągami a innymi typami danych</span><span class="sxs-lookup"><span data-stu-id="103b3-116">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [<span data-ttu-id="103b3-117">Konwersje tablic</span><span class="sxs-lookup"><span data-stu-id="103b3-117">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 [<span data-ttu-id="103b3-118">Struktury</span><span class="sxs-lookup"><span data-stu-id="103b3-118">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="103b3-119">Typy danych</span><span class="sxs-lookup"><span data-stu-id="103b3-119">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="103b3-120">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="103b3-120">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
