---
title: Imports — Instrukcja (.NET Namespace i Type)
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
ms.openlocfilehash: ef569b0ed6428d24d019e00c500e4d4b91c83d49
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604487"
---
# <a name="imports-statement-net-namespace-and-type"></a><span data-ttu-id="6ac01-102">Imports — Instrukcja (.NET Namespace i Type)</span><span class="sxs-lookup"><span data-stu-id="6ac01-102">Imports Statement (.NET Namespace and Type)</span></span>
<span data-ttu-id="6ac01-103">Umożliwia wpisz nazwy przywoływanie bez kwalifikacji przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="6ac01-103">Enables type names to be referenced without namespace qualification.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ac01-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6ac01-104">Syntax</span></span>  
  
```  
Imports [ aliasname = ] namespace  
-or-  
Imports [ aliasname = ] namespace.element  
```  
  
## <a name="parts"></a><span data-ttu-id="6ac01-105">Części</span><span class="sxs-lookup"><span data-stu-id="6ac01-105">Parts</span></span>  
  
|<span data-ttu-id="6ac01-106">Termin</span><span class="sxs-lookup"><span data-stu-id="6ac01-106">Term</span></span>|<span data-ttu-id="6ac01-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="6ac01-107">Definition</span></span>|  
|---|---|  
|`aliasname`|<span data-ttu-id="6ac01-108">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="6ac01-108">Optional.</span></span> <span data-ttu-id="6ac01-109">*Zaimportować alias* lub za pomocą którego kod może odwoływać się do nazwy `namespace` zamiast ciągu pełnej kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="6ac01-109">An *import alias* or name by which code can refer to `namespace` instead of the full qualification string.</span></span> <span data-ttu-id="6ac01-110">Zobacz temat[Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="6ac01-110">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
|`namespace`|<span data-ttu-id="6ac01-111">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="6ac01-111">Required.</span></span> <span data-ttu-id="6ac01-112">Pełna nazwa importowanych przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="6ac01-112">The fully qualified name of the namespace being imported.</span></span> <span data-ttu-id="6ac01-113">Może być ciągiem przestrzeni nazw zagnieżdżone na dowolnym poziomie.</span><span class="sxs-lookup"><span data-stu-id="6ac01-113">Can be a string of namespaces nested to any level.</span></span>|  
|`element`|<span data-ttu-id="6ac01-114">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="6ac01-114">Optional.</span></span> <span data-ttu-id="6ac01-115">Nazwa elementu programowania zadeklarowana w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="6ac01-115">The name of a programming element declared in the namespace.</span></span> <span data-ttu-id="6ac01-116">Może być dowolnym elemencie kontenera.</span><span class="sxs-lookup"><span data-stu-id="6ac01-116">Can be any container element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ac01-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6ac01-117">Remarks</span></span>  
 <span data-ttu-id="6ac01-118">`Imports` Instrukcji umożliwia typy, które są zawarte w danej przestrzeni nazw, aby odwoływać się bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="6ac01-118">The `Imports`  statement enables types that are contained in a given namespace to be referenced directly.</span></span>  
  
 <span data-ttu-id="6ac01-119">Można podać nazwę jednej przestrzeni nazw lub ciąg zagnieżdżonych obszarów nazw.</span><span class="sxs-lookup"><span data-stu-id="6ac01-119">You can supply a single namespace name or a string of nested namespaces.</span></span> <span data-ttu-id="6ac01-120">Każdej zagnieżdżonej przestrzeni nazw jest oddzielona z następnym wyższym poziomu przestrzeni nazw kropką (`.`), jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="6ac01-120">Each nested namespace is separated from the next higher level namespace by a period (`.`), as the following example illustrates.</span></span>  
  
 `Imports System.Collections.Generic`  
  
 <span data-ttu-id="6ac01-121">Każdy plik źródłowy może zawierać dowolną liczbę `Imports` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="6ac01-121">Each source file can contain any number of `Imports` statements.</span></span> <span data-ttu-id="6ac01-122">Te należy wykonać wszelkimi deklaracjami opcji, takich jak `Option Strict` instrukcji i ich musi występować przed wszelkimi deklaracjami elementu programowania, takich jak `Module` lub `Class` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="6ac01-122">These must follow any option declarations, such as the `Option Strict` statement, and they must precede any programming element declarations, such as `Module` or `Class` statements.</span></span>  
  
 <span data-ttu-id="6ac01-123">Można użyć `Imports` tylko na poziomie pliku.</span><span class="sxs-lookup"><span data-stu-id="6ac01-123">You can use `Imports` only at file level.</span></span> <span data-ttu-id="6ac01-124">Oznacza to, w kontekście deklaracji Import musi być plikiem źródłowym i nie może być w przestrzeni nazw, klasy, struktury, modułu, interfejsu, procedurę lub blok.</span><span class="sxs-lookup"><span data-stu-id="6ac01-124">This means the declaration context for importation must be a source file, and cannot be a namespace, class, structure, module, interface, procedure, or block.</span></span>  
  
 <span data-ttu-id="6ac01-125">Należy pamiętać, że `Imports` instrukcji nie udostępnia elementy z innych projektów i zespołów projektu.</span><span class="sxs-lookup"><span data-stu-id="6ac01-125">Note that the `Imports` statement does not make elements from other projects and assemblies available to your project.</span></span> <span data-ttu-id="6ac01-126">Importowanie nie odbywa się odwołanie do ustawienia.</span><span class="sxs-lookup"><span data-stu-id="6ac01-126">Importing does not take the place of setting a reference.</span></span> <span data-ttu-id="6ac01-127">Tylko eliminuje konieczność na kwalifikować się nazw, które są już dostępne do projektu.</span><span class="sxs-lookup"><span data-stu-id="6ac01-127">It only removes the need to qualify names that are already available to your project.</span></span> <span data-ttu-id="6ac01-128">Aby uzyskać więcej informacji, zobacz "Importowanie zawierających elementy" w [odwołania do elementów zadeklarowany](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="6ac01-128">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6ac01-129">Można zdefiniować niejawne `Imports` instrukcji za pomocą [strona odwołań, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="6ac01-129">You can define implicit `Imports` statements by using the [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span> <span data-ttu-id="6ac01-130">Aby uzyskać więcej informacji, zobacz [porady: Dodawanie lub usuwanie zaimportowane przestrzenie nazw (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="6ac01-130">For more information, see [How to: Add or Remove Imported Namespaces (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span></span>  
  
## <a name="import-aliases"></a><span data-ttu-id="6ac01-131">Importowanie aliasów</span><span class="sxs-lookup"><span data-stu-id="6ac01-131">Import Aliases</span></span>  
 <span data-ttu-id="6ac01-132">*Zaimportować alias* definiuje alias przestrzeni nazw lub typu.</span><span class="sxs-lookup"><span data-stu-id="6ac01-132">An *import alias* defines the alias for a namespace or type.</span></span> <span data-ttu-id="6ac01-133">Importowanie aliasów są przydatne, gdy musisz użyć elementów o takiej samej nazwie, które są zadeklarowane w jedną lub kilka przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="6ac01-133">Import aliases are useful when you need to use items with the same name that are declared in one or more namespaces.</span></span> <span data-ttu-id="6ac01-134">Więcej informacji oraz przykładem, zobacz "Kwalifikowanie nazwy elementu" w [odwołania do elementów zadeklarowany](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="6ac01-134">For more information and an example, see "Qualifying an Element Name" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
 <span data-ttu-id="6ac01-135">Nie należy deklarować Członkowskich na poziomie modułu z taką samą nazwę jak `aliasname`.</span><span class="sxs-lookup"><span data-stu-id="6ac01-135">You should not declare a member at module level with the same name as `aliasname`.</span></span> <span data-ttu-id="6ac01-136">Jeśli to zrobisz, kompilator Visual Basic używa `aliasname` tylko w przypadku zadeklarowanego elementu członkowskiego i nie rozpoznaje ją jako aliasu importu.</span><span class="sxs-lookup"><span data-stu-id="6ac01-136">If you do, the Visual Basic compiler uses `aliasname` only for the declared member and no longer recognizes it as an import alias.</span></span>  
  
 <span data-ttu-id="6ac01-137">Mimo że składnia używana do deklarowania aliasu importu tak jak jest używany do importowania prefiks przestrzeni nazw XML, wyniki są różne.</span><span class="sxs-lookup"><span data-stu-id="6ac01-137">Although the syntax used for declaring an import alias is like that used for importing an XML namespace prefix, the results are different.</span></span> <span data-ttu-id="6ac01-138">Aliasu importu można używać jako wyrażenia w kodzie, prefiks przestrzeni nazw XML można stosować tylko w literałach XML i właściwości osi XML jako prefiks kwalifikowaną elementu lub nazwa atrybutu.</span><span class="sxs-lookup"><span data-stu-id="6ac01-138">An import alias can be used as an expression in your code, whereas an XML namespace prefix can be used only in XML literals or XML axis properties as the prefix for a qualified element or attribute name.</span></span>  
  
### <a name="element-names"></a><span data-ttu-id="6ac01-139">Nazwy elementów</span><span class="sxs-lookup"><span data-stu-id="6ac01-139">Element Names</span></span>  
 <span data-ttu-id="6ac01-140">Jeśli podasz `element`, musi reprezentować *element kontenera*, czyli programowania element, który może zawierać inne elementy.</span><span class="sxs-lookup"><span data-stu-id="6ac01-140">If you supply `element`, it must represent a *container element*, that is, a programming element that can contain other elements.</span></span> <span data-ttu-id="6ac01-141">Elementy kontenera obejmują klasy, struktury, modułów, interfejsów i wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="6ac01-141">Container elements include classes, structures, modules, interfaces, and enumerations.</span></span>  
  
 <span data-ttu-id="6ac01-142">Zakres elementów udostępnione przez `Imports` instrukcji zależy od tego, czy wybrano `element`.</span><span class="sxs-lookup"><span data-stu-id="6ac01-142">The scope of the elements made available by an `Imports` statement depends on whether you specify `element`.</span></span> <span data-ttu-id="6ac01-143">Jeśli określisz tylko `namespace`, wszystkie jednoznacznie o nazwie członkami tej przestrzeni nazw i elementów członkowskich elementów kontenera w tej przestrzeni nazw, są dostępne bez kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="6ac01-143">If you specify only `namespace`, all uniquely named members of that namespace, and members of container elements within that namespace, are available without qualification.</span></span> <span data-ttu-id="6ac01-144">Jeśli możesz określić ich obu `namespace` i `element`tylko elementy członkowskie tego elementu są dostępne bez kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="6ac01-144">If you specify both `namespace` and `element`, only the members of that element are available without qualification.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ac01-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="6ac01-145">Example</span></span>  
 <span data-ttu-id="6ac01-146">Poniższy przykład zwraca wszystkie foldery w katalogu C:\ przy użyciu <xref:System.IO.DirectoryInfo> klasy.</span><span class="sxs-lookup"><span data-stu-id="6ac01-146">The following example returns all the folders in the C:\ directory by using the <xref:System.IO.DirectoryInfo> class.</span></span>  
  
 <span data-ttu-id="6ac01-147">Nie ma kodu `Imports` instrukcje w górnej części pliku.</span><span class="sxs-lookup"><span data-stu-id="6ac01-147">The code has no `Imports` statements at the top of the file.</span></span> <span data-ttu-id="6ac01-148">W związku z tym `DirectoryInfo`, <xref:System.Text.StringBuilder>, i <xref:Microsoft.VisualBasic.ControlChars.CrLf> odwołania są w pełni kwalifikowanej z przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="6ac01-148">Therefore, the `DirectoryInfo`, <xref:System.Text.StringBuilder>, and <xref:Microsoft.VisualBasic.ControlChars.CrLf> references are all fully qualified with the namespaces.</span></span>  
  
 [!code-vb[VbVbalrStatements#152](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="6ac01-149">Przykład</span><span class="sxs-lookup"><span data-stu-id="6ac01-149">Example</span></span>  
 <span data-ttu-id="6ac01-150">Poniższy przykład zawiera `Imports` instrukcji, do którego istnieje odwołanie przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="6ac01-150">The following example includes `Imports` statements for the referenced namespaces.</span></span> <span data-ttu-id="6ac01-151">W związku z tym typów ma być w pełni kwalifikowana z przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="6ac01-151">Therefore, the types do not have to be fully qualified with the namespaces.</span></span>  
  
 [!code-vb[VbVbalrStatements#153](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_2.vb)]  
  
 [!code-vb[VbVbalrStatements#154](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="6ac01-152">Przykład</span><span class="sxs-lookup"><span data-stu-id="6ac01-152">Example</span></span>  
 <span data-ttu-id="6ac01-153">Poniższy przykład zawiera `Imports` instrukcji, które Tworzenie aliasów przywoływanego przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="6ac01-153">The following example includes `Imports` statements that create aliases for the referenced namespaces.</span></span> <span data-ttu-id="6ac01-154">Typy są poprzedzone aliasów.</span><span class="sxs-lookup"><span data-stu-id="6ac01-154">The types are qualified with the aliases.</span></span>  
  
 [!code-vb[VbVbalrStatements#155](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_4.vb)]  
  
 [!code-vb[VbVbalrStatements#156](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_5.vb)]  
  
## <a name="example"></a><span data-ttu-id="6ac01-155">Przykład</span><span class="sxs-lookup"><span data-stu-id="6ac01-155">Example</span></span>  
 <span data-ttu-id="6ac01-156">Poniższy przykład zawiera `Imports` instrukcji, które Tworzenie aliasów dla wskazanych typów.</span><span class="sxs-lookup"><span data-stu-id="6ac01-156">The following example includes `Imports` statements that create aliases for the referenced types.</span></span> <span data-ttu-id="6ac01-157">Aliasy służą do określania typów.</span><span class="sxs-lookup"><span data-stu-id="6ac01-157">Aliases are used to specify the types.</span></span>  
  
 [!code-vb[VbVbalrStatements#157](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_6.vb)]  
  
 [!code-vb[VbVbalrStatements#158](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_7.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="6ac01-158">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6ac01-158">See Also</span></span>  
 [<span data-ttu-id="6ac01-159">Namespace, instrukcja</span><span class="sxs-lookup"><span data-stu-id="6ac01-159">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [<span data-ttu-id="6ac01-160">Przestrzenie nazw w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6ac01-160">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [<span data-ttu-id="6ac01-161">Referencje i instrukcja Imports</span><span class="sxs-lookup"><span data-stu-id="6ac01-161">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [<span data-ttu-id="6ac01-162">Imports, instrukcja (przestrzeń nazw XML)</span><span class="sxs-lookup"><span data-stu-id="6ac01-162">Imports Statement (XML Namespace)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)  
 [<span data-ttu-id="6ac01-163">Odwołania do elementów zadeklarowanych</span><span class="sxs-lookup"><span data-stu-id="6ac01-163">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
