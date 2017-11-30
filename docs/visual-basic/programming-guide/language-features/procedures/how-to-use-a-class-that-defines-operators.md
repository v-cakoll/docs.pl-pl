---
title: "Porady: używanie klasy definiującej operatory (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 223b3fc84fe75d1d530cd182c9332e5c663aa519
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a><span data-ttu-id="3ff01-102">Porady: używanie klasy definiującej operatory (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ff01-102">How to: Use a Class that Defines Operators (Visual Basic)</span></span>
<span data-ttu-id="3ff01-103">Jeśli używasz klasy lub struktury, która definiuje operatory własną, możesz uzyskać dostęp tych operatorów z [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3ff01-103">If you are using a class or structure that defines its own operators, you can access those operators from [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
 <span data-ttu-id="3ff01-104">Definiowanie operatora w klasie lub strukturze jest również nazywany *przeładowanie* operatora.</span><span class="sxs-lookup"><span data-stu-id="3ff01-104">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ff01-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="3ff01-105">Example</span></span>  
 <span data-ttu-id="3ff01-106">Poniższy przykład uzyskuje dostęp do struktury SQL <xref:System.Data.SqlTypes.SqlString>, który definiuje operatory konwersji ([CType — funkcja](../../../../visual-basic/language-reference/functions/ctype-function.md)) w obu kierunkach między ciągu SQL i [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] ciągu.</span><span class="sxs-lookup"><span data-stu-id="3ff01-106">The following example accesses the SQL structure <xref:System.Data.SqlTypes.SqlString>, which defines the conversion operators ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) in both directions between a SQL string and a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] string.</span></span> <span data-ttu-id="3ff01-107">Użyj `CType(` *wyrażenia ciągu SQL*, `String)` do przekonwertowania ciągu SQL [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] ciągu i `CType(` *wyrażenia ciągu w języku Visual Basic*, <xref:System.Data.SqlTypes.SqlString> `)` przekonwertować w innym kierunku.</span><span class="sxs-lookup"><span data-stu-id="3ff01-107">Use `CType(`*SQL string expression*, `String)` to convert a SQL string to a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] string, and `CType(`*Visual Basic string expression*, <xref:System.Data.SqlTypes.SqlString>`)` to convert in the other direction.</span></span>  
  
 [!code-vb[VbVbcnProcedures#30](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#31](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_2.vb)]  
  
 <span data-ttu-id="3ff01-108"><xref:System.Data.SqlTypes.SqlString> Struktury definiuje operator konwersji ([CType — funkcja](../../../../visual-basic/language-reference/functions/ctype-function.md)) z `String` do <xref:System.Data.SqlTypes.SqlString> oraz z <xref:System.Data.SqlTypes.SqlString> do `String`.</span><span class="sxs-lookup"><span data-stu-id="3ff01-108">The <xref:System.Data.SqlTypes.SqlString> structure defines a conversion operator ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) from `String` to <xref:System.Data.SqlTypes.SqlString> and another from <xref:System.Data.SqlTypes.SqlString> to `String`.</span></span> <span data-ttu-id="3ff01-109">Instrukcja, która przypisuje `title` do `jobTitle` sprawia, że użycie operatora pierwszy i <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> drugi używa wywołania funkcji.</span><span class="sxs-lookup"><span data-stu-id="3ff01-109">The statement that assigns `title` to `jobTitle` makes use of the first operator, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function call uses the second.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3ff01-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="3ff01-110">Compiling the Code</span></span>  
 <span data-ttu-id="3ff01-111">Upewnij się, że klasy lub struktury, którego używasz definiuje operator, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="3ff01-111">Be sure the class or structure you are using defines the operator you want to use.</span></span> <span data-ttu-id="3ff01-112">Zakłada się, że klasy lub struktury ma zdefiniowany co dostępne do przeciążania operatora.</span><span class="sxs-lookup"><span data-stu-id="3ff01-112">Do not assume that the class or structure has defined every operator available for overloading.</span></span> <span data-ttu-id="3ff01-113">Aby uzyskać listę dostępnych operatorów, zobacz [operator — instrukcja](../../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3ff01-113">For a list of available operators, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
 <span data-ttu-id="3ff01-114">Dołączyć odpowiednie `Imports` instrukcji SQL ciągu na początku pliku źródłowego (w tym przypadku <xref:System.Data.SqlTypes>).</span><span class="sxs-lookup"><span data-stu-id="3ff01-114">Include the appropriate `Imports` statement for the SQL string at the beginning of your source file (in this case <xref:System.Data.SqlTypes>).</span></span>  
  
 <span data-ttu-id="3ff01-115">Projekt musi mieć odwołania do system.dane i zestawów System.XML.</span><span class="sxs-lookup"><span data-stu-id="3ff01-115">Your project must have references to System.Data and System.XML.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ff01-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3ff01-116">See Also</span></span>  
 [<span data-ttu-id="3ff01-117">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="3ff01-117">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="3ff01-118">Porady: Definiowanie operatora</span><span class="sxs-lookup"><span data-stu-id="3ff01-118">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)  
 [<span data-ttu-id="3ff01-119">Porady: Definiowanie operatora konwersji</span><span class="sxs-lookup"><span data-stu-id="3ff01-119">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="3ff01-120">Porady: wywoływanie procedury operatora</span><span class="sxs-lookup"><span data-stu-id="3ff01-120">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)  
 [<span data-ttu-id="3ff01-121">Rozszerzanie</span><span class="sxs-lookup"><span data-stu-id="3ff01-121">Widening</span></span>](../../../../visual-basic/language-reference/modifiers/widening.md)  
 [<span data-ttu-id="3ff01-122">Zawężanie</span><span class="sxs-lookup"><span data-stu-id="3ff01-122">Narrowing</span></span>](../../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [<span data-ttu-id="3ff01-123">Structure — instrukcja</span><span class="sxs-lookup"><span data-stu-id="3ff01-123">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="3ff01-124">Porady: deklarowanie struktury</span><span class="sxs-lookup"><span data-stu-id="3ff01-124">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="3ff01-125">Konwersje jawne i niejawne</span><span class="sxs-lookup"><span data-stu-id="3ff01-125">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="3ff01-126">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="3ff01-126">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
