---
title: 'Instrukcje: Konwertowanie obiektu na inny typ w języku Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
ms.openlocfilehash: d80dc542f71aaf3eec6891006d77c5d39c985abf
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64600995"
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a><span data-ttu-id="85298-102">Instrukcje: Konwertowanie obiektu na inny typ w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="85298-102">How to: Convert an Object to Another Type in Visual Basic</span></span>
<span data-ttu-id="85298-103">Możesz przekonwertować `Object` zmiennej na inny typ danych przy użyciu słowa kluczowego konwersji, takich jak [funkcja CType](../../../../visual-basic/language-reference/functions/ctype-function.md).</span><span class="sxs-lookup"><span data-stu-id="85298-103">You convert an `Object` variable to another data type by using a conversion keyword such as [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="85298-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="85298-104">Example</span></span>  
 <span data-ttu-id="85298-105">Poniższy przykład konwertuje `Object` zmienną `Integer` i `String`.</span><span class="sxs-lookup"><span data-stu-id="85298-105">The following example converts an `Object` variable to an `Integer` and a `String`.</span></span>  
  
```  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 <span data-ttu-id="85298-106">Jeśli wiesz, że zawartość `Object` zmiennych są typu danych, zaleca się przekonwertować zmiennej tego typu danych.</span><span class="sxs-lookup"><span data-stu-id="85298-106">If you know that the contents of an `Object` variable are of a particular data type, it is better to convert the variable to that data type.</span></span> <span data-ttu-id="85298-107">Jeśli będziesz nadal używać `Object` zmiennej, wiąże się z jednej *pakowania* i *Rozpakowywanie* (w przypadku typu wartości) lub *późnym wiązaniu* (dla typu odwołania).</span><span class="sxs-lookup"><span data-stu-id="85298-107">If you continue to use the `Object` variable, you incur either *boxing* and *unboxing* (for a value type) or *late binding* (for a reference type).</span></span> <span data-ttu-id="85298-108">Te operacje wszystkie zająć dodatkowy czas wykonywania i wprowadź wydajność wolniej.</span><span class="sxs-lookup"><span data-stu-id="85298-108">These operations all take extra execution time and make your performance slower.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="85298-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="85298-109">Compiling the Code</span></span>  
 <span data-ttu-id="85298-110">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="85298-110">This example requires:</span></span>  
  
- <span data-ttu-id="85298-111">Odwołanie do <xref:System?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="85298-111">A reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85298-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="85298-112">See also</span></span>

- <xref:System.Object>
- [<span data-ttu-id="85298-113">Konwersje typów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="85298-113">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="85298-114">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="85298-114">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="85298-115">Konwersje jawne i niejawne</span><span class="sxs-lookup"><span data-stu-id="85298-115">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="85298-116">Konwertowanie między ciągami a innymi typami danych</span><span class="sxs-lookup"><span data-stu-id="85298-116">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="85298-117">Konwersje tablic</span><span class="sxs-lookup"><span data-stu-id="85298-117">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
- [<span data-ttu-id="85298-118">Struktury</span><span class="sxs-lookup"><span data-stu-id="85298-118">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="85298-119">Typy danych</span><span class="sxs-lookup"><span data-stu-id="85298-119">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="85298-120">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="85298-120">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
