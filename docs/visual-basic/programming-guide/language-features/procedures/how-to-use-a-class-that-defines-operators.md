---
title: 'Porady: używanie klasy definiującej operatory'
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
ms.openlocfilehash: 455c839702b90738ec5aea37c1b09d72eba42ff4
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347891"
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a><span data-ttu-id="2668e-102">Porady: używanie klasy definiującej operatory (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2668e-102">How to: Use a Class that Defines Operators (Visual Basic)</span></span>
<span data-ttu-id="2668e-103">Jeśli używasz klasy lub struktury, która definiuje własne operatory, możesz uzyskać dostęp do tych operatorów z Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2668e-103">If you are using a class or structure that defines its own operators, you can access those operators from Visual Basic.</span></span>  
  
 <span data-ttu-id="2668e-104">Definiowanie operatora w klasie lub strukturze jest również nazywane *przeciążeniem* operatora.</span><span class="sxs-lookup"><span data-stu-id="2668e-104">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2668e-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="2668e-105">Example</span></span>  
 <span data-ttu-id="2668e-106">Poniższy przykład uzyskuje dostęp do struktury SQL <xref:System.Data.SqlTypes.SqlString>, która definiuje operatory konwersji ([Funkcja CType](../../../../visual-basic/language-reference/functions/ctype-function.md)) w obu kierunkach między ciągiem SQL i ciągiem Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2668e-106">The following example accesses the SQL structure <xref:System.Data.SqlTypes.SqlString>, which defines the conversion operators ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) in both directions between a SQL string and a Visual Basic string.</span></span> <span data-ttu-id="2668e-107">Użyj `CType(`*wyrażenia ciągu SQL*, `String)` do przekonwertowania ciągu SQL na ciąg Visual Basic i `CType(`*Visual Basic wyrażenie ciągu*, <xref:System.Data.SqlTypes.SqlString>`)` do konwersji w innym kierunku.</span><span class="sxs-lookup"><span data-stu-id="2668e-107">Use `CType(`*SQL string expression*, `String)` to convert a SQL string to a Visual Basic string, and `CType(`*Visual Basic string expression*, <xref:System.Data.SqlTypes.SqlString>`)` to convert in the other direction.</span></span>  
  
 [!code-vb[VbVbcnProcedures#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#30)]  
  
 [!code-vb[VbVbcnProcedures#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#31)]  
  
 <span data-ttu-id="2668e-108">Struktura <xref:System.Data.SqlTypes.SqlString> definiuje operator konwersji ([Funkcja CType](../../../../visual-basic/language-reference/functions/ctype-function.md)) z `String` do <xref:System.Data.SqlTypes.SqlString> i innej od <xref:System.Data.SqlTypes.SqlString> do `String`.</span><span class="sxs-lookup"><span data-stu-id="2668e-108">The <xref:System.Data.SqlTypes.SqlString> structure defines a conversion operator ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) from `String` to <xref:System.Data.SqlTypes.SqlString> and another from <xref:System.Data.SqlTypes.SqlString> to `String`.</span></span> <span data-ttu-id="2668e-109">Instrukcja, która przypisuje `title` do `jobTitle` używa pierwszego operatora, a wywołanie funkcji <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> używa drugiego.</span><span class="sxs-lookup"><span data-stu-id="2668e-109">The statement that assigns `title` to `jobTitle` makes use of the first operator, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function call uses the second.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="2668e-110">Skompilować kod</span><span class="sxs-lookup"><span data-stu-id="2668e-110">Compile the code</span></span>  
 <span data-ttu-id="2668e-111">Upewnij się, że używana Klasa lub struktura definiuje operatora, którego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="2668e-111">Be sure the class or structure you are using defines the operator you want to use.</span></span> <span data-ttu-id="2668e-112">Nie należy zakładać, że Klasa lub struktura zdefiniowano każdy operator dostępny do przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="2668e-112">Do not assume that the class or structure has defined every operator available for overloading.</span></span> <span data-ttu-id="2668e-113">Aby uzyskać listę dostępnych operatorów, zobacz [instrukcja operatora](../../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2668e-113">For a list of available operators, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
 <span data-ttu-id="2668e-114">Uwzględnij odpowiednią instrukcję `Imports` dla ciągu SQL na początku pliku źródłowego (w tym przypadku <xref:System.Data.SqlTypes>).</span><span class="sxs-lookup"><span data-stu-id="2668e-114">Include the appropriate `Imports` statement for the SQL string at the beginning of your source file (in this case <xref:System.Data.SqlTypes>).</span></span>  
  
 <span data-ttu-id="2668e-115">Projekt musi mieć odwołania do System. Data i system. XML.</span><span class="sxs-lookup"><span data-stu-id="2668e-115">Your project must have references to System.Data and System.XML.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2668e-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2668e-116">See also</span></span>

- [<span data-ttu-id="2668e-117">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="2668e-117">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="2668e-118">Instrukcje: definiowanie operatora</span><span class="sxs-lookup"><span data-stu-id="2668e-118">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="2668e-119">Instrukcje: definiowanie operatora konwersji</span><span class="sxs-lookup"><span data-stu-id="2668e-119">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="2668e-120">Instrukcje: wywoływanie procedury operatora</span><span class="sxs-lookup"><span data-stu-id="2668e-120">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="2668e-121">Widening</span><span class="sxs-lookup"><span data-stu-id="2668e-121">Widening</span></span>](../../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="2668e-122">Narrowing</span><span class="sxs-lookup"><span data-stu-id="2668e-122">Narrowing</span></span>](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="2668e-123">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2668e-123">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="2668e-124">Instrukcje: deklarowanie struktury</span><span class="sxs-lookup"><span data-stu-id="2668e-124">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="2668e-125">Konwersje jawne i niejawne</span><span class="sxs-lookup"><span data-stu-id="2668e-125">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="2668e-126">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="2668e-126">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
