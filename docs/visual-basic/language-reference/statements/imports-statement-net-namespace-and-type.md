---
title: Imports — instrukcja — .NET Namespace i Type (Visual Basic)
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
ms.openlocfilehash: 93b299ffd8d2be1b1fabfd752e75d18ef87714b2
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974383"
---
# <a name="imports-statement-net-namespace-and-type"></a><span data-ttu-id="ee2d1-102">Imports — Instrukcja (.NET Namespace i Type)</span><span class="sxs-lookup"><span data-stu-id="ee2d1-102">Imports Statement (.NET Namespace and Type)</span></span>
<span data-ttu-id="ee2d1-103">Pozwala wpisać nazwy przywoływanie bez kwalifikacji przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ee2d1-103">Enables type names to be referenced without namespace qualification.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee2d1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ee2d1-104">Syntax</span></span>  
  
```  
Imports [ aliasname = ] namespace  
-or-  
Imports [ aliasname = ] namespace.element  
```  
  
## <a name="parts"></a><span data-ttu-id="ee2d1-105">Części</span><span class="sxs-lookup"><span data-stu-id="ee2d1-105">Parts</span></span>  
  
|<span data-ttu-id="ee2d1-106">Termin</span><span class="sxs-lookup"><span data-stu-id="ee2d1-106">Term</span></span>|<span data-ttu-id="ee2d1-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="ee2d1-107">Definition</span></span>|  
|---|---|  
|`aliasname`|<span data-ttu-id="ee2d1-108">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="ee2d1-108">Optional.</span></span> <span data-ttu-id="ee2d1-109">*Zaimportować alias* lub za pomocą którego kod może odnosić się do nazwy `namespace` zamiast ciągu pełnej kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="ee2d1-109">An *import alias* or name by which code can refer to `namespace` instead of the full qualification string.</span></span> <span data-ttu-id="ee2d1-110">Zobacz [Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="ee2d1-110">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
|`namespace`|<span data-ttu-id="ee2d1-111">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="ee2d1-111">Required.</span></span> <span data-ttu-id="ee2d1-112">W pełni kwalifikowana nazwa importowanych przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ee2d1-112">The fully qualified name of the namespace being imported.</span></span> <span data-ttu-id="ee2d1-113">Może być ciągiem przestrzenie nazw zagnieżdżona na dowolnym poziomie.</span><span class="sxs-lookup"><span data-stu-id="ee2d1-113">Can be a string of namespaces nested to any level.</span></span>|  
|`element`|<span data-ttu-id="ee2d1-114">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="ee2d1-114">Optional.</span></span> <span data-ttu-id="ee2d1-115">Nazwa elementu programistycznego zadeklarowanych w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ee2d1-115">The name of a programming element declared in the namespace.</span></span> <span data-ttu-id="ee2d1-116">Może być dowolny element kontenera.</span><span class="sxs-lookup"><span data-stu-id="ee2d1-116">Can be any container element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee2d1-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ee2d1-117">Remarks</span></span>  
 <span data-ttu-id="ee2d1-118">`Imports` Instrukcji umożliwia typy, które są zawarte w danej przestrzeni nazw, aby odwoływać się bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="ee2d1-118">The `Imports`  statement enables types that are contained in a given namespace to be referenced directly.</span></span>  
  
 <span data-ttu-id="ee2d1-119">Możesz podać nazwę jednej przestrzeni nazw lub ciąg zagnieżdżone przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="ee2d1-119">You can supply a single namespace name or a string of nested namespaces.</span></span> <span data-ttu-id="ee2d1-120">Każdy zagnieżdżone przestrzenie nazw są oddzielone od dalej wyższym poziomie przestrzeni nazw kropkę (`.`), tak jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ee2d1-120">Each nested namespace is separated from the next higher level namespace by a period (`.`), as the following example illustrates.</span></span>  
  
 `Imports System.Collections.Generic`  
  
 <span data-ttu-id="ee2d1-121">Każdy plik źródłowy może zawierać dowolną liczbę `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ee2d1-121">Each source file can contain any number of `Imports` statements.</span></span> <span data-ttu-id="ee2d1-122">Te muszą być zgodne wszystkie deklaracje opcji, takich jak `Option Strict` instrukcji, dlatego musi poprzedzać żadnych deklaracji elementu programowania, takich jak `Module` lub `Class` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ee2d1-122">These must follow any option declarations, such as the `Option Strict` statement, and they must precede any programming element declarations, such as `Module` or `Class` statements.</span></span>  
  
 <span data-ttu-id="ee2d1-123">Możesz użyć `Imports` tylko na poziomie pliku.</span><span class="sxs-lookup"><span data-stu-id="ee2d1-123">You can use `Imports` only at file level.</span></span> <span data-ttu-id="ee2d1-124">Oznacza to, kontekst deklaracji importowanie musi być plikiem źródłowym, a nie może być przestrzeni nazw, klasy, struktury, moduł, interfejsu, procedurę lub blok.</span><span class="sxs-lookup"><span data-stu-id="ee2d1-124">This means the declaration context for importation must be a source file, and cannot be a namespace, class, structure, module, interface, procedure, or block.</span></span>  
  
 <span data-ttu-id="ee2d1-125">Należy pamiętać, że `Imports` instrukcji nie udostępnia elementy z innych projektów i zestawów do projektu.</span><span class="sxs-lookup"><span data-stu-id="ee2d1-125">Note that the `Imports` statement does not make elements from other projects and assemblies available to your project.</span></span> <span data-ttu-id="ee2d1-126">Importowanie nie odbywa się odwołanie do ustawienia.</span><span class="sxs-lookup"><span data-stu-id="ee2d1-126">Importing does not take the place of setting a reference.</span></span> <span data-ttu-id="ee2d1-127">Powoduje tylko usunięcie potrzeby kwalifikowania nazwy, które są już dostępne do projektu.</span><span class="sxs-lookup"><span data-stu-id="ee2d1-127">It only removes the need to qualify names that are already available to your project.</span></span> <span data-ttu-id="ee2d1-128">Aby uzyskać więcej informacji, zobacz "Importowanie zawierający elementy" w [odwołania do elementów zadeklarowany](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="ee2d1-128">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ee2d1-129">Można zdefiniować niejawne `Imports` instrukcji za pomocą [strona odwołań, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="ee2d1-129">You can define implicit `Imports` statements by using the [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span> <span data-ttu-id="ee2d1-130">Aby uzyskać więcej informacji, zobacz [jak: Dodawanie lub usuwanie importowanych przestrzeni nazw (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="ee2d1-130">For more information, see [How to: Add or Remove Imported Namespaces (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span></span>  
  
## <a name="import-aliases"></a><span data-ttu-id="ee2d1-131">Importowanie aliasów</span><span class="sxs-lookup"><span data-stu-id="ee2d1-131">Import Aliases</span></span>  
 <span data-ttu-id="ee2d1-132">*Zaimportować alias* definiuje aliasu dla typu lub przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ee2d1-132">An *import alias* defines the alias for a namespace or type.</span></span> <span data-ttu-id="ee2d1-133">Importowanie aliasów są przydatne, gdy należy użyć elementów o takiej samej nazwie, które są zadeklarowane w jeden lub kilka przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ee2d1-133">Import aliases are useful when you need to use items with the same name that are declared in one or more namespaces.</span></span> <span data-ttu-id="ee2d1-134">Aby uzyskać więcej informacji i obejrzeć przykład, zobacz "Kwalifikowanie elementu Name" w [odwołania do elementów zadeklarowany](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="ee2d1-134">For more information and an example, see "Qualifying an Element Name" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
 <span data-ttu-id="ee2d1-135">Nie należy zadeklarować członka na poziomie modułu z taką samą nazwę jak `aliasname`.</span><span class="sxs-lookup"><span data-stu-id="ee2d1-135">You should not declare a member at module level with the same name as `aliasname`.</span></span> <span data-ttu-id="ee2d1-136">Jeśli to zrobisz, kompilator języka Visual Basic używa `aliasname` wyłącznie do zadeklarowanej składowej, a nie znajduje się już rozpoznaje je jako aliasu importu.</span><span class="sxs-lookup"><span data-stu-id="ee2d1-136">If you do, the Visual Basic compiler uses `aliasname` only for the declared member and no longer recognizes it as an import alias.</span></span>  
  
 <span data-ttu-id="ee2d1-137">Mimo że składnia używane do deklarowania aliasu importu Krewny, który jest używany do importowania prefiks przestrzeni nazw XML, wyniki są różne.</span><span class="sxs-lookup"><span data-stu-id="ee2d1-137">Although the syntax used for declaring an import alias is like that used for importing an XML namespace prefix, the results are different.</span></span> <span data-ttu-id="ee2d1-138">Import alias może służyć jako wyrażenia w swoim kodzie, prefiks przestrzeni nazw XML należy stosować tylko w literałach XML i właściwości osi XML jako prefiks dla elementu kwalifikowaną lub nazwa atrybutu.</span><span class="sxs-lookup"><span data-stu-id="ee2d1-138">An import alias can be used as an expression in your code, whereas an XML namespace prefix can be used only in XML literals or XML axis properties as the prefix for a qualified element or attribute name.</span></span>  
  
### <a name="element-names"></a><span data-ttu-id="ee2d1-139">Nazwy elementów</span><span class="sxs-lookup"><span data-stu-id="ee2d1-139">Element Names</span></span>  
 <span data-ttu-id="ee2d1-140">Jeśli podasz `element`, musi reprezentować *element kontenera*, czyli programowania element, który może zawierać innych elementów.</span><span class="sxs-lookup"><span data-stu-id="ee2d1-140">If you supply `element`, it must represent a *container element*, that is, a programming element that can contain other elements.</span></span> <span data-ttu-id="ee2d1-141">Elementy kontenera zawierają klasy, struktury, moduły, interfejsy i wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="ee2d1-141">Container elements include classes, structures, modules, interfaces, and enumerations.</span></span>  
  
 <span data-ttu-id="ee2d1-142">Zakres elementy udostępnione przez `Imports` instrukcja jest zależna od tego, czy należy określić `element`.</span><span class="sxs-lookup"><span data-stu-id="ee2d1-142">The scope of the elements made available by an `Imports` statement depends on whether you specify `element`.</span></span> <span data-ttu-id="ee2d1-143">Jeśli określisz tylko `namespace`, wszystkie jednoznacznie o nazwie członków tego obszaru nazw, a członkowie kontenerów elementów w obrębie tej przestrzeni nazw, są dostępne bez kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="ee2d1-143">If you specify only `namespace`, all uniquely named members of that namespace, and members of container elements within that namespace, are available without qualification.</span></span> <span data-ttu-id="ee2d1-144">Jeśli określisz zarówno `namespace` i `element`tylko elementy członkowskie tego elementu są dostępne bez kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="ee2d1-144">If you specify both `namespace` and `element`, only the members of that element are available without qualification.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee2d1-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="ee2d1-145">Example</span></span>  
 <span data-ttu-id="ee2d1-146">Poniższy przykład zwraca wszystkie foldery w katalogu C:\ przy użyciu <xref:System.IO.DirectoryInfo> klasy.</span><span class="sxs-lookup"><span data-stu-id="ee2d1-146">The following example returns all the folders in the C:\ directory by using the <xref:System.IO.DirectoryInfo> class.</span></span>  
  
 <span data-ttu-id="ee2d1-147">Nie ma kodu `Imports` instrukcji w górnej części pliku.</span><span class="sxs-lookup"><span data-stu-id="ee2d1-147">The code has no `Imports` statements at the top of the file.</span></span> <span data-ttu-id="ee2d1-148">W związku z tym `DirectoryInfo`, <xref:System.Text.StringBuilder>, i <xref:Microsoft.VisualBasic.ControlChars.CrLf> odwołania są w pełni kwalifikowaną z przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ee2d1-148">Therefore, the `DirectoryInfo`, <xref:System.Text.StringBuilder>, and <xref:Microsoft.VisualBasic.ControlChars.CrLf> references are all fully qualified with the namespaces.</span></span>  
  
 [!code-vb[VbVbalrStatements#152](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#152)]  
  
## <a name="example"></a><span data-ttu-id="ee2d1-149">Przykład</span><span class="sxs-lookup"><span data-stu-id="ee2d1-149">Example</span></span>  
 <span data-ttu-id="ee2d1-150">Poniższy przykład zawiera `Imports` instrukcji dla przywoływane obszary nazw.</span><span class="sxs-lookup"><span data-stu-id="ee2d1-150">The following example includes `Imports` statements for the referenced namespaces.</span></span> <span data-ttu-id="ee2d1-151">W związku z tym typy ma być w pełni kwalifikowana przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="ee2d1-151">Therefore, the types do not have to be fully qualified with the namespaces.</span></span>  
  
 [!code-vb[VbVbalrStatements#153](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#153)]  
  
 [!code-vb[VbVbalrStatements#154](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#154)]  
  
## <a name="example"></a><span data-ttu-id="ee2d1-152">Przykład</span><span class="sxs-lookup"><span data-stu-id="ee2d1-152">Example</span></span>  
 <span data-ttu-id="ee2d1-153">Poniższy przykład zawiera `Imports` instrukcji, które Tworzenie aliasów przywoływane obszary nazw.</span><span class="sxs-lookup"><span data-stu-id="ee2d1-153">The following example includes `Imports` statements that create aliases for the referenced namespaces.</span></span> <span data-ttu-id="ee2d1-154">Typy są kwalifikowany za pomocą aliasów.</span><span class="sxs-lookup"><span data-stu-id="ee2d1-154">The types are qualified with the aliases.</span></span>  
  
 [!code-vb[VbVbalrStatements#155](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#155)]  
  
 [!code-vb[VbVbalrStatements#156](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#156)]  
  
## <a name="example"></a><span data-ttu-id="ee2d1-155">Przykład</span><span class="sxs-lookup"><span data-stu-id="ee2d1-155">Example</span></span>  
 <span data-ttu-id="ee2d1-156">Poniższy przykład zawiera `Imports` instrukcji, które Tworzenie aliasów dla typów odwołania.</span><span class="sxs-lookup"><span data-stu-id="ee2d1-156">The following example includes `Imports` statements that create aliases for the referenced types.</span></span> <span data-ttu-id="ee2d1-157">Aliasy są używane do określania typów.</span><span class="sxs-lookup"><span data-stu-id="ee2d1-157">Aliases are used to specify the types.</span></span>  
  
 [!code-vb[VbVbalrStatements#157](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#157)]  
  
 [!code-vb[VbVbalrStatements#158](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#158)]  
  
## <a name="see-also"></a><span data-ttu-id="ee2d1-158">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ee2d1-158">See also</span></span>
- [<span data-ttu-id="ee2d1-159">Namespace, instrukcja</span><span class="sxs-lookup"><span data-stu-id="ee2d1-159">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [<span data-ttu-id="ee2d1-160">Przestrzenie nazw w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ee2d1-160">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="ee2d1-161">Referencje i instrukcja Imports</span><span class="sxs-lookup"><span data-stu-id="ee2d1-161">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [<span data-ttu-id="ee2d1-162">Imports, instrukcja (przestrzeń nazw XML)</span><span class="sxs-lookup"><span data-stu-id="ee2d1-162">Imports Statement (XML Namespace)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
- [<span data-ttu-id="ee2d1-163">Odwołania do elementów zadeklarowanych</span><span class="sxs-lookup"><span data-stu-id="ee2d1-163">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
