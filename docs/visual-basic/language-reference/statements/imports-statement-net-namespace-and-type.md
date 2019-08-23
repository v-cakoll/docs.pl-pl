---
title: Imports, instrukcja-przestrzeń nazw i typ .NET (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Imports
- imports
helpviewer_keywords:
- declared element names [Visual Basic], qualification
- imports [Visual Basic]
- Imports statement [Visual Basic]
- aliases [Visual Basic], Imports statement
- container elements [Visual Basic]
- namespaces [Visual Basic], importing
- Imports statement [Visual Basic], syntax
- import aliases [Visual Basic]
- aliases [Visual Basic], import
- declared elements [Visual Basic], container elements
ms.assetid: 7062f8aa-d890-4232-9eed-92836e13fb6e
ms.openlocfilehash: a0b7a6a5fd16dc0daa620e6b490ddfdeb0e7c80e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912388"
---
# <a name="imports-statement-net-namespace-and-type"></a><span data-ttu-id="bea81-102">Imports — Instrukcja (.NET Namespace i Type)</span><span class="sxs-lookup"><span data-stu-id="bea81-102">Imports Statement (.NET Namespace and Type)</span></span>
<span data-ttu-id="bea81-103">Umożliwia odwoływanie się do nazw typów bez kwalifikacji przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="bea81-103">Enables type names to be referenced without namespace qualification.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bea81-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bea81-104">Syntax</span></span>  
  
```  
Imports [ aliasname = ] namespace  
-or-  
Imports [ aliasname = ] namespace.element  
```  
  
## <a name="parts"></a><span data-ttu-id="bea81-105">Części</span><span class="sxs-lookup"><span data-stu-id="bea81-105">Parts</span></span>  
  
|<span data-ttu-id="bea81-106">Termin</span><span class="sxs-lookup"><span data-stu-id="bea81-106">Term</span></span>|<span data-ttu-id="bea81-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="bea81-107">Definition</span></span>|  
|---|---|  
|`aliasname`|<span data-ttu-id="bea81-108">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="bea81-108">Optional.</span></span> <span data-ttu-id="bea81-109">Alias lub nazwa *importu* , do `namespace` którego kod może odwoływać się zamiast pełnego ciągu kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="bea81-109">An *import alias* or name by which code can refer to `namespace` instead of the full qualification string.</span></span> <span data-ttu-id="bea81-110">Zobacz [Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="bea81-110">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
|`namespace`|<span data-ttu-id="bea81-111">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="bea81-111">Required.</span></span> <span data-ttu-id="bea81-112">W pełni kwalifikowana nazwa importowanej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="bea81-112">The fully qualified name of the namespace being imported.</span></span> <span data-ttu-id="bea81-113">Może być ciągiem przestrzeni nazw zagnieżdżonych na dowolnym poziomie.</span><span class="sxs-lookup"><span data-stu-id="bea81-113">Can be a string of namespaces nested to any level.</span></span>|  
|`element`|<span data-ttu-id="bea81-114">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="bea81-114">Optional.</span></span> <span data-ttu-id="bea81-115">Nazwa elementu programowania zadeklarowanego w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="bea81-115">The name of a programming element declared in the namespace.</span></span> <span data-ttu-id="bea81-116">Może być dowolnym elementem kontenera.</span><span class="sxs-lookup"><span data-stu-id="bea81-116">Can be any container element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bea81-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bea81-117">Remarks</span></span>  
 <span data-ttu-id="bea81-118">`Imports` Instrukcja włącza typy, które są zawarte w danej przestrzeni nazw, mają być bezpośrednio przywoływane.</span><span class="sxs-lookup"><span data-stu-id="bea81-118">The `Imports`  statement enables types that are contained in a given namespace to be referenced directly.</span></span>  
  
 <span data-ttu-id="bea81-119">Można podać nazwę pojedynczej przestrzeni nazw lub ciąg zagnieżdżonych przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="bea81-119">You can supply a single namespace name or a string of nested namespaces.</span></span> <span data-ttu-id="bea81-120">Każda zagnieżdżona przestrzeń nazw jest oddzielona od kolejnej przestrzeni nazw wyższego`.`poziomu o kropkę (), jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="bea81-120">Each nested namespace is separated from the next higher level namespace by a period (`.`), as the following example illustrates.</span></span>  
  
 `Imports System.Collections.Generic`  
  
 <span data-ttu-id="bea81-121">Każdy plik źródłowy może zawierać dowolną liczbę `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="bea81-121">Each source file can contain any number of `Imports` statements.</span></span> <span data-ttu-id="bea81-122">Muszą one być zgodne z dowolnymi deklaracjami `Option Strict` opcji, takimi jak instrukcja, i muszą poprzedzać deklaracje `Module` elementów `Class` programistycznych, takich jak lub instrukcji.</span><span class="sxs-lookup"><span data-stu-id="bea81-122">These must follow any option declarations, such as the `Option Strict` statement, and they must precede any programming element declarations, such as `Module` or `Class` statements.</span></span>  
  
 <span data-ttu-id="bea81-123">Można używać `Imports` tylko na poziomie pliku.</span><span class="sxs-lookup"><span data-stu-id="bea81-123">You can use `Imports` only at file level.</span></span> <span data-ttu-id="bea81-124">Oznacza to, że kontekst deklaracji dla importu musi być plikiem źródłowym i nie może być przestrzenią nazw, klasą, strukturą, modułem, interfejsem, procedurą lub blokiem.</span><span class="sxs-lookup"><span data-stu-id="bea81-124">This means the declaration context for importation must be a source file, and cannot be a namespace, class, structure, module, interface, procedure, or block.</span></span>  
  
 <span data-ttu-id="bea81-125">Należy zauważyć, `Imports` że instrukcja nie udostępnia elementów z innych projektów i zestawów dostępnych dla projektu.</span><span class="sxs-lookup"><span data-stu-id="bea81-125">Note that the `Imports` statement does not make elements from other projects and assemblies available to your project.</span></span> <span data-ttu-id="bea81-126">Importowanie nie ma miejsca na ustawienie odwołania.</span><span class="sxs-lookup"><span data-stu-id="bea81-126">Importing does not take the place of setting a reference.</span></span> <span data-ttu-id="bea81-127">Tylko eliminuje konieczność kwalifikowania nazw, które są już dostępne dla projektu.</span><span class="sxs-lookup"><span data-stu-id="bea81-127">It only removes the need to qualify names that are already available to your project.</span></span> <span data-ttu-id="bea81-128">Aby uzyskać więcej informacji, zobacz "Importowanie zawierających elementy" w odniesieniu [do zadeklarowanych elementów](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="bea81-128">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bea81-129">Niejawne `Imports` instrukcje można definiować przy użyciu [strony odwołania, projektanta projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="bea81-129">You can define implicit `Imports` statements by using the [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span> <span data-ttu-id="bea81-130">Aby uzyskać więcej informacji, zobacz [jak: Dodaj lub Usuń zaimportowane przestrzenie nazw](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic)(Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="bea81-130">For more information, see [How to: Add or Remove Imported Namespaces (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span></span>  
  
## <a name="import-aliases"></a><span data-ttu-id="bea81-131">Zaimportuj aliasy</span><span class="sxs-lookup"><span data-stu-id="bea81-131">Import Aliases</span></span>  
 <span data-ttu-id="bea81-132">*Alias importu* definiuje alias dla przestrzeni nazw lub typu.</span><span class="sxs-lookup"><span data-stu-id="bea81-132">An *import alias* defines the alias for a namespace or type.</span></span> <span data-ttu-id="bea81-133">Aliasy importu są przydatne, gdy trzeba użyć elementów o tej samej nazwie, które są zadeklarowane w co najmniej jednym obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="bea81-133">Import aliases are useful when you need to use items with the same name that are declared in one or more namespaces.</span></span> <span data-ttu-id="bea81-134">Aby uzyskać więcej informacji i zapoznać się z przykładem, zobacz "Kwalifikowanie nazwy elementu" w [odwołaniach do zadeklarowanych elementów](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="bea81-134">For more information and an example, see "Qualifying an Element Name" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
 <span data-ttu-id="bea81-135">Nie należy deklarować elementu członkowskiego na poziomie modułu o tej samej nazwie co `aliasname`.</span><span class="sxs-lookup"><span data-stu-id="bea81-135">You should not declare a member at module level with the same name as `aliasname`.</span></span> <span data-ttu-id="bea81-136">Jeśli to zrobisz, kompilator Visual Basic używa `aliasname` tylko dla zadeklarowanego elementu członkowskiego i nie rozpoznaje go już jako aliasu importu.</span><span class="sxs-lookup"><span data-stu-id="bea81-136">If you do, the Visual Basic compiler uses `aliasname` only for the declared member and no longer recognizes it as an import alias.</span></span>  
  
 <span data-ttu-id="bea81-137">Mimo że składnia używana do deklarowania aliasu importu jest taka sama jak ta, która jest używana do importowania prefiksu przestrzeni nazw XML, wyniki są różne.</span><span class="sxs-lookup"><span data-stu-id="bea81-137">Although the syntax used for declaring an import alias is like that used for importing an XML namespace prefix, the results are different.</span></span> <span data-ttu-id="bea81-138">Alias importu może służyć jako wyrażenie w kodzie, natomiast prefiks przestrzeni nazw XML może być używany tylko w literałach XML lub właściwościach osi XML jako prefiks dla kwalifikowanego elementu lub nazwy atrybutu.</span><span class="sxs-lookup"><span data-stu-id="bea81-138">An import alias can be used as an expression in your code, whereas an XML namespace prefix can be used only in XML literals or XML axis properties as the prefix for a qualified element or attribute name.</span></span>  
  
### <a name="element-names"></a><span data-ttu-id="bea81-139">Nazwy elementów</span><span class="sxs-lookup"><span data-stu-id="bea81-139">Element Names</span></span>  
 <span data-ttu-id="bea81-140">Jeśli dostarczasz `element`, musi reprezentować *element kontenera*, czyli element programistyczny, który może zawierać inne elementy.</span><span class="sxs-lookup"><span data-stu-id="bea81-140">If you supply `element`, it must represent a *container element*, that is, a programming element that can contain other elements.</span></span> <span data-ttu-id="bea81-141">Elementy kontenera obejmują klasy, struktury, moduły, interfejsy i wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="bea81-141">Container elements include classes, structures, modules, interfaces, and enumerations.</span></span>  
  
 <span data-ttu-id="bea81-142">Zakres elementów udostępnianych przez `Imports` instrukcję zależy od tego, czy określono. `element`</span><span class="sxs-lookup"><span data-stu-id="bea81-142">The scope of the elements made available by an `Imports` statement depends on whether you specify `element`.</span></span> <span data-ttu-id="bea81-143">Jeśli określisz tylko `namespace`, wszystkie jednoznacznie nazwane elementy członkowskie tej przestrzeni nazw i elementy członkowskie elementów kontenera w tej przestrzeni nazw są dostępne bez kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="bea81-143">If you specify only `namespace`, all uniquely named members of that namespace, and members of container elements within that namespace, are available without qualification.</span></span> <span data-ttu-id="bea81-144">W przypadku określenia obu `namespace` elementów `element`i, tylko elementy członkowskie tego elementu są dostępne bez kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="bea81-144">If you specify both `namespace` and `element`, only the members of that element are available without qualification.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bea81-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="bea81-145">Example</span></span>  
 <span data-ttu-id="bea81-146">Poniższy przykład zwraca wszystkie foldery w C:\ Katalog przy użyciu <xref:System.IO.DirectoryInfo> klasy.</span><span class="sxs-lookup"><span data-stu-id="bea81-146">The following example returns all the folders in the C:\ directory by using the <xref:System.IO.DirectoryInfo> class.</span></span>  
  
 <span data-ttu-id="bea81-147">Kod nie zawiera żadnych `Imports` instrukcji w górnej części pliku.</span><span class="sxs-lookup"><span data-stu-id="bea81-147">The code has no `Imports` statements at the top of the file.</span></span> <span data-ttu-id="bea81-148">W związku z tym,, <xref:Microsoft.VisualBasic.ControlChars.CrLf> i odwołania są całkowicie kwalifikowane do przestrzeni nazw. `DirectoryInfo` <xref:System.Text.StringBuilder></span><span class="sxs-lookup"><span data-stu-id="bea81-148">Therefore, the `DirectoryInfo`, <xref:System.Text.StringBuilder>, and <xref:Microsoft.VisualBasic.ControlChars.CrLf> references are all fully qualified with the namespaces.</span></span>  
  
 [!code-vb[VbVbalrStatements#152](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#152)]  
  
## <a name="example"></a><span data-ttu-id="bea81-149">Przykład</span><span class="sxs-lookup"><span data-stu-id="bea81-149">Example</span></span>  
 <span data-ttu-id="bea81-150">Poniższy przykład zawiera `Imports` instrukcje dla przestrzeni nazw, do których się odwołuje.</span><span class="sxs-lookup"><span data-stu-id="bea81-150">The following example includes `Imports` statements for the referenced namespaces.</span></span> <span data-ttu-id="bea81-151">W związku z tym typy nie muszą być w pełni kwalifikowane z przestrzeniami nazw.</span><span class="sxs-lookup"><span data-stu-id="bea81-151">Therefore, the types do not have to be fully qualified with the namespaces.</span></span>  
  
 [!code-vb[VbVbalrStatements#153](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#153)]  
  
 [!code-vb[VbVbalrStatements#154](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#154)]  
  
## <a name="example"></a><span data-ttu-id="bea81-152">Przykład</span><span class="sxs-lookup"><span data-stu-id="bea81-152">Example</span></span>  
 <span data-ttu-id="bea81-153">Poniższy przykład zawiera `Imports` instrukcje tworzące aliasy dla przestrzeni nazw, do których się odwołuje.</span><span class="sxs-lookup"><span data-stu-id="bea81-153">The following example includes `Imports` statements that create aliases for the referenced namespaces.</span></span> <span data-ttu-id="bea81-154">Typy są kwalifikowane przy użyciu aliasów.</span><span class="sxs-lookup"><span data-stu-id="bea81-154">The types are qualified with the aliases.</span></span>  
  
 [!code-vb[VbVbalrStatements#155](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#155)]  
  
 [!code-vb[VbVbalrStatements#156](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#156)]  
  
## <a name="example"></a><span data-ttu-id="bea81-155">Przykład</span><span class="sxs-lookup"><span data-stu-id="bea81-155">Example</span></span>  
 <span data-ttu-id="bea81-156">Poniższy przykład zawiera `Imports` instrukcje tworzące aliasy dla typów, do których istnieją odwołania.</span><span class="sxs-lookup"><span data-stu-id="bea81-156">The following example includes `Imports` statements that create aliases for the referenced types.</span></span> <span data-ttu-id="bea81-157">Aliasy są używane do określania typów.</span><span class="sxs-lookup"><span data-stu-id="bea81-157">Aliases are used to specify the types.</span></span>  
  
 [!code-vb[VbVbalrStatements#157](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#157)]  
  
 [!code-vb[VbVbalrStatements#158](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#158)]  
  
## <a name="see-also"></a><span data-ttu-id="bea81-158">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bea81-158">See also</span></span>

- [<span data-ttu-id="bea81-159">Namespace, instrukcja</span><span class="sxs-lookup"><span data-stu-id="bea81-159">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [<span data-ttu-id="bea81-160">Przestrzenie nazw w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bea81-160">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="bea81-161">Referencje i instrukcja Imports</span><span class="sxs-lookup"><span data-stu-id="bea81-161">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [<span data-ttu-id="bea81-162">Imports, instrukcja (przestrzeń nazw XML)</span><span class="sxs-lookup"><span data-stu-id="bea81-162">Imports Statement (XML Namespace)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
- [<span data-ttu-id="bea81-163">Odwołania do elementów zadeklarowanych</span><span class="sxs-lookup"><span data-stu-id="bea81-163">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
