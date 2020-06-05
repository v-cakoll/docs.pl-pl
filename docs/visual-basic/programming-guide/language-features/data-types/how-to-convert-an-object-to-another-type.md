---
title: 'Instrukcje: Konwertowanie obiektu na inny typ'
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
ms.openlocfilehash: cdb78bc66867ce27076d7b7e42de6a2880cb3a8c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393964"
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a><span data-ttu-id="c9224-102">Porady: konwertowanie obiektu do innego typu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c9224-102">How to: Convert an Object to Another Type in Visual Basic</span></span>
<span data-ttu-id="c9224-103">Zmienną można przekonwertować `Object` na inny typ danych za pomocą słowa kluczowego konwersji, takiego jak [Funkcja CType](../../../language-reference/functions/ctype-function.md).</span><span class="sxs-lookup"><span data-stu-id="c9224-103">You convert an `Object` variable to another data type by using a conversion keyword such as [CType Function](../../../language-reference/functions/ctype-function.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9224-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="c9224-104">Example</span></span>  
 <span data-ttu-id="c9224-105">Poniższy przykład konwertuje `Object` zmienną na `Integer` i `String` .</span><span class="sxs-lookup"><span data-stu-id="c9224-105">The following example converts an `Object` variable to an `Integer` and a `String`.</span></span>  
  
```vb  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 <span data-ttu-id="c9224-106">Jeśli wiesz, że zawartość `Object` zmiennej jest określonego typu danych, lepiej jest skonwertować zmienną na ten typ danych.</span><span class="sxs-lookup"><span data-stu-id="c9224-106">If you know that the contents of an `Object` variable are of a particular data type, it is better to convert the variable to that data type.</span></span> <span data-ttu-id="c9224-107">Jeśli nadal używasz `Object` zmiennej, naliczane są *opakowanie* i *rozpakowywanie* (dla typu wartości) lub *późne wiązanie* (dla typu odwołania).</span><span class="sxs-lookup"><span data-stu-id="c9224-107">If you continue to use the `Object` variable, you incur either *boxing* and *unboxing* (for a value type) or *late binding* (for a reference type).</span></span> <span data-ttu-id="c9224-108">Wszystkie te operacje pobierają dodatkowy czas wykonywania i zwiększają wydajność.</span><span class="sxs-lookup"><span data-stu-id="c9224-108">These operations all take extra execution time and make your performance slower.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="c9224-109">Kompiluj kod</span><span class="sxs-lookup"><span data-stu-id="c9224-109">Compile the code</span></span>  
 <span data-ttu-id="c9224-110">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="c9224-110">This example requires:</span></span>  
  
- <span data-ttu-id="c9224-111">Odwołanie do <xref:System?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c9224-111">A reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9224-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c9224-112">See also</span></span>

- <xref:System.Object>
- [<span data-ttu-id="c9224-113">Konwersje plików w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c9224-113">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="c9224-114">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="c9224-114">Widening and Narrowing Conversions</span></span>](widening-and-narrowing-conversions.md)
- [<span data-ttu-id="c9224-115">Konwersje jawne i niejawne</span><span class="sxs-lookup"><span data-stu-id="c9224-115">Implicit and Explicit Conversions</span></span>](implicit-and-explicit-conversions.md)
- [<span data-ttu-id="c9224-116">Konwertowanie między ciągami a innymi typami danych</span><span class="sxs-lookup"><span data-stu-id="c9224-116">Conversions Between Strings and Other Types</span></span>](conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="c9224-117">Konwersje tablic</span><span class="sxs-lookup"><span data-stu-id="c9224-117">Array Conversions</span></span>](array-conversions.md)
- [<span data-ttu-id="c9224-118">Struktury</span><span class="sxs-lookup"><span data-stu-id="c9224-118">Structures</span></span>](structures.md)
- [<span data-ttu-id="c9224-119">Typy danych</span><span class="sxs-lookup"><span data-stu-id="c9224-119">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="c9224-120">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="c9224-120">Type Conversion Functions</span></span>](../../../language-reference/functions/type-conversion-functions.md)
