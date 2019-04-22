---
title: 'Instrukcje: Konwertowanie obiektu na inny typ w języku Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
ms.openlocfilehash: 1e515c0f4ce8e787754c61a9b53d247fa93c49f2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58814383"
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a><span data-ttu-id="7c878-102">Instrukcje: Konwertowanie obiektu na inny typ w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7c878-102">How to: Convert an Object to Another Type in Visual Basic</span></span>
<span data-ttu-id="7c878-103">Możesz przekonwertować `Object` zmiennej na inny typ danych przy użyciu słowa kluczowego konwersji, takich jak [funkcja CType](../../../../visual-basic/language-reference/functions/ctype-function.md).</span><span class="sxs-lookup"><span data-stu-id="7c878-103">You convert an `Object` variable to another data type by using a conversion keyword such as [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c878-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="7c878-104">Example</span></span>  
 <span data-ttu-id="7c878-105">Poniższy przykład konwertuje `Object` zmienną `Integer` i `String`.</span><span class="sxs-lookup"><span data-stu-id="7c878-105">The following example converts an `Object` variable to an `Integer` and a `String`.</span></span>  
  
```  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 <span data-ttu-id="7c878-106">Jeśli wiesz, że zawartość `Object` zmiennych są typu danych, zaleca się przekonwertować zmiennej tego typu danych.</span><span class="sxs-lookup"><span data-stu-id="7c878-106">If you know that the contents of an `Object` variable are of a particular data type, it is better to convert the variable to that data type.</span></span> <span data-ttu-id="7c878-107">Jeśli będziesz nadal używać `Object` zmiennej, wiąże się z jednej *pakowania* i *Rozpakowywanie* (w przypadku typu wartości) lub *późnym wiązaniu* (dla typu odwołania).</span><span class="sxs-lookup"><span data-stu-id="7c878-107">If you continue to use the `Object` variable, you incur either *boxing* and *unboxing* (for a value type) or *late binding* (for a reference type).</span></span> <span data-ttu-id="7c878-108">Te operacje wszystkie zająć dodatkowy czas wykonywania i wprowadź wydajność wolniej.</span><span class="sxs-lookup"><span data-stu-id="7c878-108">These operations all take extra execution time and make your performance slower.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7c878-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="7c878-109">Compiling the Code</span></span>  
 <span data-ttu-id="7c878-110">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="7c878-110">This example requires:</span></span>  
  
-   <span data-ttu-id="7c878-111">Odwołanie do <xref:System?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="7c878-111">A reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c878-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7c878-112">See also</span></span>

- <xref:System.Object>
- [<span data-ttu-id="7c878-113">Konwersje typów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7c878-113">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="7c878-114">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="7c878-114">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="7c878-115">Konwersje jawne i niejawne</span><span class="sxs-lookup"><span data-stu-id="7c878-115">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="7c878-116">Konwertowanie między ciągami a innymi typami danych</span><span class="sxs-lookup"><span data-stu-id="7c878-116">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="7c878-117">Konwersje tablic</span><span class="sxs-lookup"><span data-stu-id="7c878-117">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
- [<span data-ttu-id="7c878-118">Struktury</span><span class="sxs-lookup"><span data-stu-id="7c878-118">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="7c878-119">Typy danych</span><span class="sxs-lookup"><span data-stu-id="7c878-119">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="7c878-120">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="7c878-120">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
