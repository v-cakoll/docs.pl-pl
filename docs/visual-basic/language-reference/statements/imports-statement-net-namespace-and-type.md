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
ms.openlocfilehash: 62b208d4795d0370cb6eace7f45ef42551e6960f
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581778"
---
# <a name="imports-statement-net-namespace-and-type"></a><span data-ttu-id="721a7-102">Imports — Instrukcja (.NET Namespace i Type)</span><span class="sxs-lookup"><span data-stu-id="721a7-102">Imports Statement (.NET Namespace and Type)</span></span>
<span data-ttu-id="721a7-103">Umożliwia odwoływanie się do nazw typów bez kwalifikacji przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="721a7-103">Enables type names to be referenced without namespace qualification.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="721a7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="721a7-104">Syntax</span></span>  
  
```vb  
Imports [ aliasname = ] namespace  
' -or-  
Imports [ aliasname = ] namespace.element  
```  
  
## <a name="parts"></a><span data-ttu-id="721a7-105">Części</span><span class="sxs-lookup"><span data-stu-id="721a7-105">Parts</span></span>  
  
|<span data-ttu-id="721a7-106">Termin</span><span class="sxs-lookup"><span data-stu-id="721a7-106">Term</span></span>|<span data-ttu-id="721a7-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="721a7-107">Definition</span></span>|  
|---|---|  
|`aliasname`|<span data-ttu-id="721a7-108">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="721a7-108">Optional.</span></span> <span data-ttu-id="721a7-109">*Alias importu* lub nazwa, za pomocą którego kod może odwoływać się do `namespace` zamiast pełnego ciągu kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="721a7-109">An *import alias* or name by which code can refer to `namespace` instead of the full qualification string.</span></span> <span data-ttu-id="721a7-110">Zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="721a7-110">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
|`namespace`|<span data-ttu-id="721a7-111">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="721a7-111">Required.</span></span> <span data-ttu-id="721a7-112">W pełni kwalifikowana nazwa importowanej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="721a7-112">The fully qualified name of the namespace being imported.</span></span> <span data-ttu-id="721a7-113">Może być ciągiem przestrzeni nazw zagnieżdżonych na dowolnym poziomie.</span><span class="sxs-lookup"><span data-stu-id="721a7-113">Can be a string of namespaces nested to any level.</span></span>|  
|`element`|<span data-ttu-id="721a7-114">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="721a7-114">Optional.</span></span> <span data-ttu-id="721a7-115">Nazwa elementu programowania zadeklarowanego w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="721a7-115">The name of a programming element declared in the namespace.</span></span> <span data-ttu-id="721a7-116">Może być dowolnym elementem kontenera.</span><span class="sxs-lookup"><span data-stu-id="721a7-116">Can be any container element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="721a7-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="721a7-117">Remarks</span></span>  
 <span data-ttu-id="721a7-118">Instrukcja `Imports` umożliwia bezpośrednie wywoływanie typów zawartych w danej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="721a7-118">The `Imports`  statement enables types that are contained in a given namespace to be referenced directly.</span></span>  
  
 <span data-ttu-id="721a7-119">Można podać nazwę pojedynczej przestrzeni nazw lub ciąg zagnieżdżonych przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="721a7-119">You can supply a single namespace name or a string of nested namespaces.</span></span> <span data-ttu-id="721a7-120">Każda zagnieżdżona przestrzeń nazw jest oddzielona od kolejnej przestrzeni nazw wyższego poziomu przez okres (`.`), jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="721a7-120">Each nested namespace is separated from the next higher level namespace by a period (`.`), as the following example illustrates.</span></span>  
  
 `Imports System.Collections.Generic`  
  
 <span data-ttu-id="721a7-121">Każdy plik źródłowy może zawierać dowolną liczbę instrukcji `Imports`.</span><span class="sxs-lookup"><span data-stu-id="721a7-121">Each source file can contain any number of `Imports` statements.</span></span> <span data-ttu-id="721a7-122">Muszą one być zgodne z dowolnymi deklaracjami opcji, takimi jak instrukcja `Option Strict`, i muszą poprzedzać deklaracje elementów programistycznych, takie jak `Module` lub `Class` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="721a7-122">These must follow any option declarations, such as the `Option Strict` statement, and they must precede any programming element declarations, such as `Module` or `Class` statements.</span></span>  
  
 <span data-ttu-id="721a7-123">@No__t_0 można użyć tylko na poziomie pliku.</span><span class="sxs-lookup"><span data-stu-id="721a7-123">You can use `Imports` only at file level.</span></span> <span data-ttu-id="721a7-124">Oznacza to, że kontekst deklaracji dla importu musi być plikiem źródłowym i nie może być przestrzenią nazw, klasą, strukturą, modułem, interfejsem, procedurą lub blokiem.</span><span class="sxs-lookup"><span data-stu-id="721a7-124">This means the declaration context for importation must be a source file, and cannot be a namespace, class, structure, module, interface, procedure, or block.</span></span>  
  
 <span data-ttu-id="721a7-125">Należy zauważyć, że instrukcja `Imports` nie sprawia, że elementy z innych projektów i zestawów są dostępne dla projektu.</span><span class="sxs-lookup"><span data-stu-id="721a7-125">Note that the `Imports` statement does not make elements from other projects and assemblies available to your project.</span></span> <span data-ttu-id="721a7-126">Importowanie nie ma miejsca na ustawienie odwołania.</span><span class="sxs-lookup"><span data-stu-id="721a7-126">Importing does not take the place of setting a reference.</span></span> <span data-ttu-id="721a7-127">Tylko eliminuje konieczność kwalifikowania nazw, które są już dostępne dla projektu.</span><span class="sxs-lookup"><span data-stu-id="721a7-127">It only removes the need to qualify names that are already available to your project.</span></span> <span data-ttu-id="721a7-128">Aby uzyskać więcej informacji, zobacz "Importowanie zawierających elementy" w [odniesieniu do zadeklarowanych elementów](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="721a7-128">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="721a7-129">Niejawne instrukcje `Imports` można definiować przy użyciu [strony odwołania, projektanta projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="721a7-129">You can define implicit `Imports` statements by using the [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span> <span data-ttu-id="721a7-130">Aby uzyskać więcej informacji, zobacz [jak: Dodawanie lub usuwanie importowanych przestrzeni nazw (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="721a7-130">For more information, see [How to: Add or Remove Imported Namespaces (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span></span>  
  
## <a name="import-aliases"></a><span data-ttu-id="721a7-131">Zaimportuj aliasy</span><span class="sxs-lookup"><span data-stu-id="721a7-131">Import Aliases</span></span>  
 <span data-ttu-id="721a7-132">*Alias importu* definiuje alias dla przestrzeni nazw lub typu.</span><span class="sxs-lookup"><span data-stu-id="721a7-132">An *import alias* defines the alias for a namespace or type.</span></span> <span data-ttu-id="721a7-133">Aliasy importu są przydatne, gdy trzeba użyć elementów o tej samej nazwie, które są zadeklarowane w co najmniej jednym obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="721a7-133">Import aliases are useful when you need to use items with the same name that are declared in one or more namespaces.</span></span> <span data-ttu-id="721a7-134">Aby uzyskać więcej informacji i zapoznać się z przykładem, zobacz "Kwalifikowanie nazwy elementu" w [odwołaniach do zadeklarowanych elementów](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="721a7-134">For more information and an example, see "Qualifying an Element Name" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
 <span data-ttu-id="721a7-135">Nie należy deklarować elementu członkowskiego na poziomie modułu o takiej samej nazwie jak `aliasname`.</span><span class="sxs-lookup"><span data-stu-id="721a7-135">You should not declare a member at module level with the same name as `aliasname`.</span></span> <span data-ttu-id="721a7-136">W takim przypadku kompilator Visual Basic używa `aliasname` tylko dla zadeklarowanego elementu członkowskiego i nie rozpoznaje go jako aliasu importu.</span><span class="sxs-lookup"><span data-stu-id="721a7-136">If you do, the Visual Basic compiler uses `aliasname` only for the declared member and no longer recognizes it as an import alias.</span></span>  
  
 <span data-ttu-id="721a7-137">Mimo że składnia używana do deklarowania aliasu importu jest taka sama jak ta, która jest używana do importowania prefiksu przestrzeni nazw XML, wyniki są różne.</span><span class="sxs-lookup"><span data-stu-id="721a7-137">Although the syntax used for declaring an import alias is like that used for importing an XML namespace prefix, the results are different.</span></span> <span data-ttu-id="721a7-138">Alias importu może służyć jako wyrażenie w kodzie, natomiast prefiks przestrzeni nazw XML może być używany tylko w literałach XML lub właściwościach osi XML jako prefiks dla kwalifikowanego elementu lub nazwy atrybutu.</span><span class="sxs-lookup"><span data-stu-id="721a7-138">An import alias can be used as an expression in your code, whereas an XML namespace prefix can be used only in XML literals or XML axis properties as the prefix for a qualified element or attribute name.</span></span>  
  
### <a name="element-names"></a><span data-ttu-id="721a7-139">Nazwy elementów</span><span class="sxs-lookup"><span data-stu-id="721a7-139">Element Names</span></span>  
 <span data-ttu-id="721a7-140">Jeśli podasz `element`, musi on reprezentować *element kontenera*, czyli element programistyczny, który może zawierać inne elementy.</span><span class="sxs-lookup"><span data-stu-id="721a7-140">If you supply `element`, it must represent a *container element*, that is, a programming element that can contain other elements.</span></span> <span data-ttu-id="721a7-141">Elementy kontenera obejmują klasy, struktury, moduły, interfejsy i wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="721a7-141">Container elements include classes, structures, modules, interfaces, and enumerations.</span></span>  
  
 <span data-ttu-id="721a7-142">Zakres elementów udostępnianych przez instrukcję `Imports` zależy od tego, czy określono `element`.</span><span class="sxs-lookup"><span data-stu-id="721a7-142">The scope of the elements made available by an `Imports` statement depends on whether you specify `element`.</span></span> <span data-ttu-id="721a7-143">Jeśli określisz tylko `namespace`, wszystkie jednoznacznie nazwane elementy członkowskie tej przestrzeni nazw oraz członkowie elementów kontenera w tej przestrzeni nazw są dostępne bez kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="721a7-143">If you specify only `namespace`, all uniquely named members of that namespace, and members of container elements within that namespace, are available without qualification.</span></span> <span data-ttu-id="721a7-144">Jeśli określisz zarówno `namespace` i `element`, tylko elementy członkowskie tego elementu są dostępne bez kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="721a7-144">If you specify both `namespace` and `element`, only the members of that element are available without qualification.</span></span>  
  
## <a name="example"></a><span data-ttu-id="721a7-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="721a7-145">Example</span></span>  
 <span data-ttu-id="721a7-146">Poniższy przykład zwraca wszystkie foldery w C:\ Katalog przy użyciu klasy <xref:System.IO.DirectoryInfo>.</span><span class="sxs-lookup"><span data-stu-id="721a7-146">The following example returns all the folders in the C:\ directory by using the <xref:System.IO.DirectoryInfo> class.</span></span>  
  
 <span data-ttu-id="721a7-147">Kod nie zawiera instrukcji `Imports` w górnej części pliku.</span><span class="sxs-lookup"><span data-stu-id="721a7-147">The code has no `Imports` statements at the top of the file.</span></span> <span data-ttu-id="721a7-148">W związku z tym odwołania `DirectoryInfo`, <xref:System.Text.StringBuilder> i <xref:Microsoft.VisualBasic.ControlChars.CrLf> są całkowicie kwalifikowane do przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="721a7-148">Therefore, the `DirectoryInfo`, <xref:System.Text.StringBuilder>, and <xref:Microsoft.VisualBasic.ControlChars.CrLf> references are all fully qualified with the namespaces.</span></span>  
  
 [!code-vb[VbVbalrStatements#152](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#152)]  
  
## <a name="example"></a><span data-ttu-id="721a7-149">Przykład</span><span class="sxs-lookup"><span data-stu-id="721a7-149">Example</span></span>  
 <span data-ttu-id="721a7-150">Poniższy przykład zawiera instrukcje `Imports` dla przestrzeni nazw, do których się odwołuje.</span><span class="sxs-lookup"><span data-stu-id="721a7-150">The following example includes `Imports` statements for the referenced namespaces.</span></span> <span data-ttu-id="721a7-151">W związku z tym typy nie muszą być w pełni kwalifikowane z przestrzeniami nazw.</span><span class="sxs-lookup"><span data-stu-id="721a7-151">Therefore, the types do not have to be fully qualified with the namespaces.</span></span>  
  
 [!code-vb[VbVbalrStatements#153](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#153)]  
  
 [!code-vb[VbVbalrStatements#154](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#154)]  
  
## <a name="example"></a><span data-ttu-id="721a7-152">Przykład</span><span class="sxs-lookup"><span data-stu-id="721a7-152">Example</span></span>  
 <span data-ttu-id="721a7-153">Poniższy przykład zawiera instrukcje `Imports`, które tworzą aliasy dla przywoływanych przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="721a7-153">The following example includes `Imports` statements that create aliases for the referenced namespaces.</span></span> <span data-ttu-id="721a7-154">Typy są kwalifikowane przy użyciu aliasów.</span><span class="sxs-lookup"><span data-stu-id="721a7-154">The types are qualified with the aliases.</span></span>  
  
 [!code-vb[VbVbalrStatements#155](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#155)]  
  
 [!code-vb[VbVbalrStatements#156](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#156)]  
  
## <a name="example"></a><span data-ttu-id="721a7-155">Przykład</span><span class="sxs-lookup"><span data-stu-id="721a7-155">Example</span></span>  
 <span data-ttu-id="721a7-156">Poniższy przykład zawiera instrukcje `Imports`, które tworzą aliasy dla typów, do których istnieją odwołania.</span><span class="sxs-lookup"><span data-stu-id="721a7-156">The following example includes `Imports` statements that create aliases for the referenced types.</span></span> <span data-ttu-id="721a7-157">Aliasy są używane do określania typów.</span><span class="sxs-lookup"><span data-stu-id="721a7-157">Aliases are used to specify the types.</span></span>  
  
 [!code-vb[VbVbalrStatements#157](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#157)]  
  
 [!code-vb[VbVbalrStatements#158](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#158)]  
  
## <a name="see-also"></a><span data-ttu-id="721a7-158">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="721a7-158">See also</span></span>

- [<span data-ttu-id="721a7-159">Namespace, instrukcja</span><span class="sxs-lookup"><span data-stu-id="721a7-159">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [<span data-ttu-id="721a7-160">Przestrzenie nazw w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="721a7-160">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="721a7-161">Referencje i instrukcja Imports</span><span class="sxs-lookup"><span data-stu-id="721a7-161">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [<span data-ttu-id="721a7-162">Imports, instrukcja (przestrzeń nazw XML)</span><span class="sxs-lookup"><span data-stu-id="721a7-162">Imports Statement (XML Namespace)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
- [<span data-ttu-id="721a7-163">Odwołania do elementów zadeklarowanych</span><span class="sxs-lookup"><span data-stu-id="721a7-163">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
