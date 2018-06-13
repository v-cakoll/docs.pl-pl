---
title: Lista atrybutów (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- attribute list
- attributes [Visual Basic], applying
ms.assetid: 5880073a-68a4-4b6b-8a07-ace32959a4e2
ms.openlocfilehash: 35d031722a5eddd6adce5e32df62b86c500d305b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604077"
---
# <a name="attribute-list-visual-basic"></a><span data-ttu-id="6dfae-102">Lista atrybutów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6dfae-102">Attribute List (Visual Basic)</span></span>
<span data-ttu-id="6dfae-103">Określa atrybuty, które ma zostać zastosowany do zadeklarowany element.</span><span class="sxs-lookup"><span data-stu-id="6dfae-103">Specifies the attributes to be applied to a declared programming element.</span></span> <span data-ttu-id="6dfae-104">Wiele atrybutów są rozdzielane przecinkami.</span><span class="sxs-lookup"><span data-stu-id="6dfae-104">Multiple attributes are separated by commas.</span></span> <span data-ttu-id="6dfae-105">Poniżej przedstawiono składnię jeden atrybut.</span><span class="sxs-lookup"><span data-stu-id="6dfae-105">Following is the syntax for one attribute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6dfae-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="6dfae-106">Syntax</span></span>  
  
```  
[ attributemodifier ] attributename [ ( attributearguments | attributeinitializer ) ]  
```  
  
## <a name="parts"></a><span data-ttu-id="6dfae-107">Części</span><span class="sxs-lookup"><span data-stu-id="6dfae-107">Parts</span></span>  
 `attributemodifier`  
 <span data-ttu-id="6dfae-108">Wymagany dla atrybutów zastosowanych na początku pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="6dfae-108">Required for attributes applied at the beginning of a source file.</span></span> <span data-ttu-id="6dfae-109">Może być [zestawu](../../../visual-basic/language-reference/modifiers/assembly.md) lub [modułu](../../../visual-basic/language-reference/modifiers/module-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="6dfae-109">Can be [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md) or [Module](../../../visual-basic/language-reference/modifiers/module-keyword.md).</span></span>  
  
 `attributename`  
 <span data-ttu-id="6dfae-110">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="6dfae-110">Required.</span></span> <span data-ttu-id="6dfae-111">Nazwa atrybutu.</span><span class="sxs-lookup"><span data-stu-id="6dfae-111">Name of the attribute.</span></span>  
  
 `attributearguments`  
 <span data-ttu-id="6dfae-112">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="6dfae-112">Optional.</span></span> <span data-ttu-id="6dfae-113">Lista argumentów pozycyjnych dla tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="6dfae-113">List of positional arguments for this attribute.</span></span> <span data-ttu-id="6dfae-114">Używanie wielu argumentów są oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="6dfae-114">Multiple arguments are separated by commas.</span></span>  
  
 `attributeinitializer`  
 <span data-ttu-id="6dfae-115">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="6dfae-115">Optional.</span></span> <span data-ttu-id="6dfae-116">Listy inicjatorów zmienna lub właściwość dla tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="6dfae-116">List of variable or property initializers for this attribute.</span></span> <span data-ttu-id="6dfae-117">Wiele inicjatory są oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="6dfae-117">Multiple initializers are separated by commas.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6dfae-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6dfae-118">Remarks</span></span>  
 <span data-ttu-id="6dfae-119">Co najmniej jeden atrybut można stosować do niemal dowolnego elementu programistycznego (typy, procedur, właściwości i tak dalej).</span><span class="sxs-lookup"><span data-stu-id="6dfae-119">You can apply one or more attributes to nearly any programming element (types, procedures, properties, and so forth).</span></span> <span data-ttu-id="6dfae-120">Atrybuty są wyświetlane w metadanych zestawu i mogą pomóc adnotacji kodu lub określić sposób użycia konkretnego elementu programistycznego.</span><span class="sxs-lookup"><span data-stu-id="6dfae-120">Attributes appear in your assembly's metadata, and they can help you annotate your code or specify how to use a particular programming element.</span></span> <span data-ttu-id="6dfae-121">Można zastosować atrybutów zdefiniowanych przez Visual Basic i .NET Framework, a można definiować własne atrybuty.</span><span class="sxs-lookup"><span data-stu-id="6dfae-121">You can apply attributes defined by Visual Basic and the .NET Framework, and you can define your own attributes.</span></span>  

 <span data-ttu-id="6dfae-122">Aby uzyskać więcej informacji o tym, kiedy należy używać atrybutów, zobacz [Omówienie atrybutów](../../../visual-basic/programming-guide/concepts/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="6dfae-122">For more information on when to use attributes, see [Attributes overview](../../../visual-basic/programming-guide/concepts/attributes/index.md).</span></span> <span data-ttu-id="6dfae-123">Aby uzyskać informacje o nazwach atrybutów, zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="6dfae-123">For information on attribute names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="6dfae-124">Reguły</span><span class="sxs-lookup"><span data-stu-id="6dfae-124">Rules</span></span>  
  
-   <span data-ttu-id="6dfae-125">**Umieszczanie.**</span><span class="sxs-lookup"><span data-stu-id="6dfae-125">**Placement.**</span></span> <span data-ttu-id="6dfae-126">Atrybuty można zastosować do najbardziej zadeklarowanych elementów programistycznych.</span><span class="sxs-lookup"><span data-stu-id="6dfae-126">You can apply attributes to most declared programming elements.</span></span> <span data-ttu-id="6dfae-127">Aby zastosować jeden lub więcej atrybutów, umieść *bloku attribute* na początku deklaracji elementu.</span><span class="sxs-lookup"><span data-stu-id="6dfae-127">To apply one or more attributes, you place an *attribute block* at the beginning of the element declaration.</span></span> <span data-ttu-id="6dfae-128">Każdy wpis na liście atrybutów Określa atrybut, który chcesz zastosować i modyfikator i argumenty używanego dla tego wywołania atrybutu.</span><span class="sxs-lookup"><span data-stu-id="6dfae-128">Each entry in the attribute list specifies an attribute you wish to apply, and the modifier and arguments you are using for this invocation of the attribute.</span></span>  
  
-   <span data-ttu-id="6dfae-129">**Nawiasy.**</span><span class="sxs-lookup"><span data-stu-id="6dfae-129">**Angle Brackets.**</span></span> <span data-ttu-id="6dfae-130">Jeśli podasz lista atrybutów, należy ująć go w nawiasy ("`<`"i"`>`").</span><span class="sxs-lookup"><span data-stu-id="6dfae-130">If you supply an attribute list, you must enclose it in angle brackets ("`<`" and "`>`").</span></span>  
  
-   <span data-ttu-id="6dfae-131">**Część deklaracji.**</span><span class="sxs-lookup"><span data-stu-id="6dfae-131">**Part of the Declaration.**</span></span> <span data-ttu-id="6dfae-132">Atrybut musi być w deklaracji elementu oddzielną instrukcję.</span><span class="sxs-lookup"><span data-stu-id="6dfae-132">The attribute must be part of the element declaration, not a separate statement.</span></span> <span data-ttu-id="6dfae-133">Można użyć sekwencji kontynuacji wiersza (" `_`") do rozszerzenia instrukcji deklaracji na wiele wierszy kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="6dfae-133">You can use the line-continuation sequence (" `_`") to extend the declaration statement onto multiple source-code lines.</span></span>  
  
-   <span data-ttu-id="6dfae-134">**Modyfikatory.**</span><span class="sxs-lookup"><span data-stu-id="6dfae-134">**Modifiers.**</span></span> <span data-ttu-id="6dfae-135">Modyfikator atrybutu (`Assembly` lub `Module`) jest wymagany na każdy atrybut zastosowany do elementu programistycznego na początku pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="6dfae-135">An attribute modifier (`Assembly` or `Module`) is required on every attribute applied to a programming element at the beginning of a source file.</span></span> <span data-ttu-id="6dfae-136">Atrybut modyfikatorów nie są dozwolone na atrybuty stosowane do elementów, które nie są na początku pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="6dfae-136">Attribute modifiers are not allowed on attributes applied to elements that are not at the beginning of a source file.</span></span>  
  
-   <span data-ttu-id="6dfae-137">**Argumenty.**</span><span class="sxs-lookup"><span data-stu-id="6dfae-137">**Arguments.**</span></span> <span data-ttu-id="6dfae-138">Wszystkie argumenty pozycyjne atrybutu musi poprzedzać wszystkie inicjatory zmienna lub właściwość.</span><span class="sxs-lookup"><span data-stu-id="6dfae-138">All positional arguments for an attribute must precede any variable or property initializers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6dfae-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="6dfae-139">Example</span></span>  
 <span data-ttu-id="6dfae-140">Następujący przykład dotyczy <xref:System.Runtime.InteropServices.DllImportAttribute> atrybutu szkielet definicji `Function` procedury.</span><span class="sxs-lookup"><span data-stu-id="6dfae-140">The following example applies the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute to a skeleton definition of a `Function` procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#1](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/attribute-list_1.vb)]  
  
 <span data-ttu-id="6dfae-141"><xref:System.Runtime.InteropServices.DllImportAttribute> Wskazuje, że procedura oparte na atrybutach reprezentuje punkt wejścia w niezarządzanych biblioteki dołączanej (dynamicznie DLL).</span><span class="sxs-lookup"><span data-stu-id="6dfae-141"><xref:System.Runtime.InteropServices.DllImportAttribute> indicates that the attributed procedure represents an entry point in an unmanaged dynamic-link library (DLL).</span></span> <span data-ttu-id="6dfae-142">Ten atrybut zawiera nazwy biblioteki DLL jako argument pozycyjny oraz inne informacje jako inicjatory zmiennej.</span><span class="sxs-lookup"><span data-stu-id="6dfae-142">The attribute supplies the DLL name as a positional argument and the other information as variable initializers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dfae-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6dfae-143">See Also</span></span>  
 [<span data-ttu-id="6dfae-144">Assembly</span><span class="sxs-lookup"><span data-stu-id="6dfae-144">Assembly</span></span>](../../../visual-basic/language-reference/modifiers/assembly.md)  
 [<span data-ttu-id="6dfae-145">Moduł \<— słowo kluczowe ></span><span class="sxs-lookup"><span data-stu-id="6dfae-145">Module \<keyword></span></span>](../../../visual-basic/language-reference/modifiers/module-keyword.md)  
 [<span data-ttu-id="6dfae-146">Atrybuty — omówienie</span><span class="sxs-lookup"><span data-stu-id="6dfae-146">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)  
 [<span data-ttu-id="6dfae-147">Instrukcje: przerywanie i łączenie instrukcji w kodzie</span><span class="sxs-lookup"><span data-stu-id="6dfae-147">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
