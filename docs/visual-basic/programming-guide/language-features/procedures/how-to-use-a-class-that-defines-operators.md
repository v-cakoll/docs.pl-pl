---
title: 'Porady: używanie klasy definiującej operatory (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- operator procedures [Visual Basic], calling
- procedures [Visual Basic], operator
- procedures [Visual Basic], calling
- examples [Visual Basic], CType
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 7ccce94a-6ca0-47d1-9f3f-13385d34f5d5
ms.openlocfilehash: 7e1d5698c1e83f0adf1be67245e0726aecaabdac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a><span data-ttu-id="16f67-102">Porady: używanie klasy definiującej operatory (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="16f67-102">How to: Use a Class that Defines Operators (Visual Basic)</span></span>
<span data-ttu-id="16f67-103">Jeśli używasz klasy lub struktury, która definiuje własną operatory są dostępne te operatory języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="16f67-103">If you are using a class or structure that defines its own operators, you can access those operators from Visual Basic.</span></span>  
  
 <span data-ttu-id="16f67-104">Definiowanie operatora w klasie lub strukturze jest również nazywany *przeładowanie* operatora.</span><span class="sxs-lookup"><span data-stu-id="16f67-104">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16f67-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="16f67-105">Example</span></span>  
 <span data-ttu-id="16f67-106">Poniższy przykład uzyskuje dostęp do struktury SQL <xref:System.Data.SqlTypes.SqlString>, który definiuje operatory konwersji ([CType — funkcja](../../../../visual-basic/language-reference/functions/ctype-function.md)) w obu kierunkach między ciągu SQL i ciąg języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="16f67-106">The following example accesses the SQL structure <xref:System.Data.SqlTypes.SqlString>, which defines the conversion operators ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) in both directions between a SQL string and a Visual Basic string.</span></span> <span data-ttu-id="16f67-107">Użyj `CType(` *wyrażenia ciągu SQL*, `String)` do przekonwertowania ciągu SQL na ciąg języka Visual Basic i `CType(` *wyrażenia ciągu w języku Visual Basic*, <xref:System.Data.SqlTypes.SqlString> `)` przekonwertować w innym kierunku.</span><span class="sxs-lookup"><span data-stu-id="16f67-107">Use `CType(`*SQL string expression*, `String)` to convert a SQL string to a Visual Basic string, and `CType(`*Visual Basic string expression*, <xref:System.Data.SqlTypes.SqlString>`)` to convert in the other direction.</span></span>  
  
 [!code-vb[VbVbcnProcedures#30](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#31](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_2.vb)]  
  
 <span data-ttu-id="16f67-108"><xref:System.Data.SqlTypes.SqlString> Struktury definiuje operator konwersji ([CType — funkcja](../../../../visual-basic/language-reference/functions/ctype-function.md)) z `String` do <xref:System.Data.SqlTypes.SqlString> oraz z <xref:System.Data.SqlTypes.SqlString> do `String`.</span><span class="sxs-lookup"><span data-stu-id="16f67-108">The <xref:System.Data.SqlTypes.SqlString> structure defines a conversion operator ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) from `String` to <xref:System.Data.SqlTypes.SqlString> and another from <xref:System.Data.SqlTypes.SqlString> to `String`.</span></span> <span data-ttu-id="16f67-109">Instrukcja, która przypisuje `title` do `jobTitle` sprawia, że użycie operatora pierwszy i <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> drugi używa wywołania funkcji.</span><span class="sxs-lookup"><span data-stu-id="16f67-109">The statement that assigns `title` to `jobTitle` makes use of the first operator, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function call uses the second.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="16f67-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="16f67-110">Compiling the Code</span></span>  
 <span data-ttu-id="16f67-111">Upewnij się, że klasy lub struktury, którego używasz definiuje operator, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="16f67-111">Be sure the class or structure you are using defines the operator you want to use.</span></span> <span data-ttu-id="16f67-112">Zakłada się, że klasy lub struktury ma zdefiniowany co dostępne do przeciążania operatora.</span><span class="sxs-lookup"><span data-stu-id="16f67-112">Do not assume that the class or structure has defined every operator available for overloading.</span></span> <span data-ttu-id="16f67-113">Aby uzyskać listę dostępnych operatorów, zobacz [operator — instrukcja](../../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="16f67-113">For a list of available operators, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
 <span data-ttu-id="16f67-114">Dołączyć odpowiednie `Imports` instrukcji SQL ciągu na początku pliku źródłowego (w tym przypadku <xref:System.Data.SqlTypes>).</span><span class="sxs-lookup"><span data-stu-id="16f67-114">Include the appropriate `Imports` statement for the SQL string at the beginning of your source file (in this case <xref:System.Data.SqlTypes>).</span></span>  
  
 <span data-ttu-id="16f67-115">Projekt musi mieć odwołania do system.dane i zestawów System.XML.</span><span class="sxs-lookup"><span data-stu-id="16f67-115">Your project must have references to System.Data and System.XML.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16f67-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="16f67-116">See Also</span></span>  
 [<span data-ttu-id="16f67-117">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="16f67-117">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="16f67-118">Instrukcje: definiowanie operatora</span><span class="sxs-lookup"><span data-stu-id="16f67-118">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)  
 [<span data-ttu-id="16f67-119">Instrukcje: definiowanie operatora konwersji</span><span class="sxs-lookup"><span data-stu-id="16f67-119">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="16f67-120">Instrukcje: wywoływanie procedury operatora</span><span class="sxs-lookup"><span data-stu-id="16f67-120">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)  
 [<span data-ttu-id="16f67-121">Widening</span><span class="sxs-lookup"><span data-stu-id="16f67-121">Widening</span></span>](../../../../visual-basic/language-reference/modifiers/widening.md)  
 [<span data-ttu-id="16f67-122">Narrowing</span><span class="sxs-lookup"><span data-stu-id="16f67-122">Narrowing</span></span>](../../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [<span data-ttu-id="16f67-123">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="16f67-123">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="16f67-124">Instrukcje: deklarowanie struktury</span><span class="sxs-lookup"><span data-stu-id="16f67-124">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="16f67-125">Konwersje jawne i niejawne</span><span class="sxs-lookup"><span data-stu-id="16f67-125">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="16f67-126">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="16f67-126">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
