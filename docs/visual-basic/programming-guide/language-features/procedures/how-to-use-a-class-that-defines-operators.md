---
title: 'Instrukcje: Używanie klasy definiującej operatory (Visual Basic)'
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
ms.openlocfilehash: bd512adf2f06ed0fbd3d36ed3175a0928bf1c57c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58829411"
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a><span data-ttu-id="f7424-102">Instrukcje: Używanie klasy definiującej operatory (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f7424-102">How to: Use a Class that Defines Operators (Visual Basic)</span></span>
<span data-ttu-id="f7424-103">Jeśli używasz klasy lub struktury, która definiuje swój własny operatory są dostępne te operatory języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f7424-103">If you are using a class or structure that defines its own operators, you can access those operators from Visual Basic.</span></span>  
  
 <span data-ttu-id="f7424-104">Definiowanie operatora dla klasy lub struktury jest również nazywany *przeciążenie* operatora.</span><span class="sxs-lookup"><span data-stu-id="f7424-104">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7424-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="f7424-105">Example</span></span>  
 <span data-ttu-id="f7424-106">Poniższy przykład uzyskuje dostęp do struktury SQL <xref:System.Data.SqlTypes.SqlString>, która definiuje operatory konwersji ([funkcja CType](../../../../visual-basic/language-reference/functions/ctype-function.md)) w obu kierunkach między ciąg SQL i ciąg języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f7424-106">The following example accesses the SQL structure <xref:System.Data.SqlTypes.SqlString>, which defines the conversion operators ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) in both directions between a SQL string and a Visual Basic string.</span></span> <span data-ttu-id="f7424-107">Użyj `CType(` *wyrażenia ciągu SQL*, `String)` do przekonwertowania ciągu SQL na ciąg języka Visual Basic i `CType(` *wyrażenia ciągu w języku Visual Basic*, <xref:System.Data.SqlTypes.SqlString> `)` do przekonwertowania w drugą stronę.</span><span class="sxs-lookup"><span data-stu-id="f7424-107">Use `CType(`*SQL string expression*, `String)` to convert a SQL string to a Visual Basic string, and `CType(`*Visual Basic string expression*, <xref:System.Data.SqlTypes.SqlString>`)` to convert in the other direction.</span></span>  
  
 [!code-vb[VbVbcnProcedures#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#30)]  
  
 [!code-vb[VbVbcnProcedures#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#31)]  
  
 <span data-ttu-id="f7424-108"><xref:System.Data.SqlTypes.SqlString> Struktury definiuje operator konwersji ([funkcja CType](../../../../visual-basic/language-reference/functions/ctype-function.md)) z `String` do <xref:System.Data.SqlTypes.SqlString> , a drugi z <xref:System.Data.SqlTypes.SqlString> do `String`.</span><span class="sxs-lookup"><span data-stu-id="f7424-108">The <xref:System.Data.SqlTypes.SqlString> structure defines a conversion operator ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) from `String` to <xref:System.Data.SqlTypes.SqlString> and another from <xref:System.Data.SqlTypes.SqlString> to `String`.</span></span> <span data-ttu-id="f7424-109">Instrukcja, która przypisuje `title` do `jobTitle` sprawia, że użycie pierwszy operator i <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> wywołanie funkcji używa drugiego.</span><span class="sxs-lookup"><span data-stu-id="f7424-109">The statement that assigns `title` to `jobTitle` makes use of the first operator, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function call uses the second.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f7424-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="f7424-110">Compiling the Code</span></span>  
 <span data-ttu-id="f7424-111">Upewnij się, że klasy lub struktury, którego używasz, określa operator, który chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="f7424-111">Be sure the class or structure you are using defines the operator you want to use.</span></span> <span data-ttu-id="f7424-112">Nie należy zakładać, że klasa lub struktura został zdefiniowany co dostępne dla przeciążania operatora.</span><span class="sxs-lookup"><span data-stu-id="f7424-112">Do not assume that the class or structure has defined every operator available for overloading.</span></span> <span data-ttu-id="f7424-113">Aby uzyskać listę dostępnych operatorów, zobacz [operator — instrukcja](../../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f7424-113">For a list of available operators, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
 <span data-ttu-id="f7424-114">Dołączyć odpowiednie `Imports` poufności informacji dla ciągu SQL na początku pliku źródłowego (w tym przypadku <xref:System.Data.SqlTypes>).</span><span class="sxs-lookup"><span data-stu-id="f7424-114">Include the appropriate `Imports` statement for the SQL string at the beginning of your source file (in this case <xref:System.Data.SqlTypes>).</span></span>  
  
 <span data-ttu-id="f7424-115">Projekt musi mieć odwołania do dane systemowe i System.XML.</span><span class="sxs-lookup"><span data-stu-id="f7424-115">Your project must have references to System.Data and System.XML.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7424-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f7424-116">See also</span></span>

- [<span data-ttu-id="f7424-117">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="f7424-117">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="f7424-118">Instrukcje: Definiowanie operatora</span><span class="sxs-lookup"><span data-stu-id="f7424-118">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="f7424-119">Instrukcje: Definiowanie operatora konwersji</span><span class="sxs-lookup"><span data-stu-id="f7424-119">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="f7424-120">Instrukcje: Wywoływanie procedury operatora</span><span class="sxs-lookup"><span data-stu-id="f7424-120">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="f7424-121">Widening</span><span class="sxs-lookup"><span data-stu-id="f7424-121">Widening</span></span>](../../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="f7424-122">Narrowing</span><span class="sxs-lookup"><span data-stu-id="f7424-122">Narrowing</span></span>](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="f7424-123">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="f7424-123">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="f7424-124">Instrukcje: deklarowanie struktury</span><span class="sxs-lookup"><span data-stu-id="f7424-124">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="f7424-125">Konwersje jawne i niejawne</span><span class="sxs-lookup"><span data-stu-id="f7424-125">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="f7424-126">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="f7424-126">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
