---
title: 'Porady: konwertowanie obiektu do innego typu w Visual Basic'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 053c93e7cf842138f5b9299cd2fcfa56342dd40b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a><span data-ttu-id="c502b-102">Porady: konwertowanie obiektu do innego typu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c502b-102">How to: Convert an Object to Another Type in Visual Basic</span></span>
<span data-ttu-id="c502b-103">Możesz przekonwertować `Object` zmiennej na inny typ danych przy użyciu słowa kluczowego konwersji, takich jak [CType — funkcja](../../../../visual-basic/language-reference/functions/ctype-function.md).</span><span class="sxs-lookup"><span data-stu-id="c502b-103">You convert an `Object` variable to another data type by using a conversion keyword such as [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c502b-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="c502b-104">Example</span></span>  
 <span data-ttu-id="c502b-105">Poniższy przykład konwertuje `Object` zmienną `Integer` i `String`.</span><span class="sxs-lookup"><span data-stu-id="c502b-105">The following example converts an `Object` variable to an `Integer` and a `String`.</span></span>  
  
```  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 <span data-ttu-id="c502b-106">Jeśli wiesz, że zawartość `Object` są zmiennej typu danych, warto przekonwertować zmiennej typu danych.</span><span class="sxs-lookup"><span data-stu-id="c502b-106">If you know that the contents of an `Object` variable are of a particular data type, it is better to convert the variable to that data type.</span></span> <span data-ttu-id="c502b-107">Jeśli będziesz nadal używać `Object` zmiennej, ponosisz albo *boxing* i *rozpakowującej* (dla typu wartości) lub *późne wiązanie* (dla typu odwołania).</span><span class="sxs-lookup"><span data-stu-id="c502b-107">If you continue to use the `Object` variable, you incur either *boxing* and *unboxing* (for a value type) or *late binding* (for a reference type).</span></span> <span data-ttu-id="c502b-108">Te operacje wszystkie zająć dodatkowy czas wykonywania i upewnij wydajność wolniejszej.</span><span class="sxs-lookup"><span data-stu-id="c502b-108">These operations all take extra execution time and make your performance slower.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c502b-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="c502b-109">Compiling the Code</span></span>  
 <span data-ttu-id="c502b-110">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="c502b-110">This example requires:</span></span>  
  
-   <span data-ttu-id="c502b-111">Odwołanie do <xref:System?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c502b-111">A reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c502b-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c502b-112">See Also</span></span>  
 <xref:System.Object>  
 [<span data-ttu-id="c502b-113">Konwersje typów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c502b-113">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="c502b-114">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="c502b-114">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="c502b-115">Konwersje jawne i niejawne</span><span class="sxs-lookup"><span data-stu-id="c502b-115">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="c502b-116">Konwertowanie pomiędzy ciągami a innymi typami</span><span class="sxs-lookup"><span data-stu-id="c502b-116">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [<span data-ttu-id="c502b-117">Konwersje tablic</span><span class="sxs-lookup"><span data-stu-id="c502b-117">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 [<span data-ttu-id="c502b-118">Struktury</span><span class="sxs-lookup"><span data-stu-id="c502b-118">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="c502b-119">Typy danych</span><span class="sxs-lookup"><span data-stu-id="c502b-119">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="c502b-120">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="c502b-120">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
