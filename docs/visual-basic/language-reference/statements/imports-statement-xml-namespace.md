---
title: Imports, instrukcja - Namespace XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ImportsXmlns
helpviewer_keywords:
- XML namespace [Visual Basic], importing
- imports [Visual Basic]
- Imports statement [Visual Basic]
- namespaces [Visual Basic], importing
ms.assetid: 1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4
ms.openlocfilehash: 1100afd89b27e789c0db713291ed3656092fb0c7
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43802395"
---
# <a name="imports-statement-xml-namespace"></a><span data-ttu-id="14a28-102">Imports — Instrukcja (przestrzeń nazw XML)</span><span class="sxs-lookup"><span data-stu-id="14a28-102">Imports Statement (XML Namespace)</span></span>
<span data-ttu-id="14a28-103">Importuje prefiksy przestrzeni nazw XML do użycia w literałach XML i właściwości osi XML.</span><span class="sxs-lookup"><span data-stu-id="14a28-103">Imports XML namespace prefixes for use in XML literals and XML axis properties.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14a28-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="14a28-104">Syntax</span></span>  
  
```  
Imports <xmlns:xmlNamespacePrefix = "xmlNamespaceName">  
```  
  
## <a name="parts"></a><span data-ttu-id="14a28-105">Części</span><span class="sxs-lookup"><span data-stu-id="14a28-105">Parts</span></span>  
 `xmlNamespacePrefix`  
 <span data-ttu-id="14a28-106">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="14a28-106">Optional.</span></span> <span data-ttu-id="14a28-107">Ciąg, który XML elementy i atrybuty mogą odwoływać się do `xmlNamespaceName`.</span><span class="sxs-lookup"><span data-stu-id="14a28-107">The string by which XML elements and attributes can refer to `xmlNamespaceName`.</span></span> <span data-ttu-id="14a28-108">Jeśli nie `xmlNamespacePrefix` jest podany, importowanych przestrzeni nazw XML jest domyślny obszar nazw XML.</span><span class="sxs-lookup"><span data-stu-id="14a28-108">If no `xmlNamespacePrefix` is supplied, the imported XML namespace is the default XML namespace.</span></span> <span data-ttu-id="14a28-109">Musi być prawidłowym identyfikatorem XML.</span><span class="sxs-lookup"><span data-stu-id="14a28-109">Must be a valid XML identifier.</span></span> <span data-ttu-id="14a28-110">Aby uzyskać więcej informacji, zobacz [nazwy z zadeklarowane elementy i atrybuty XML](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="14a28-110">For more information, see [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>  
  
 `xmlNamespaceName`  
 <span data-ttu-id="14a28-111">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="14a28-111">Required.</span></span> <span data-ttu-id="14a28-112">Ciąg identyfikujący importowanych przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="14a28-112">The string identifying the XML namespace being imported.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="14a28-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="14a28-113">Remarks</span></span>  
 <span data-ttu-id="14a28-114">Możesz użyć `Imports` instrukcji, aby zdefiniować globalnej przestrzeni nazw XML, korzystających z literały XML i właściwości osi XML lub przekazywane jako parametry do `GetXmlNamespace` operatora.</span><span class="sxs-lookup"><span data-stu-id="14a28-114">You can use the `Imports` statement to define global XML namespaces that you can use with XML literals and XML axis properties, or as parameters passed to the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="14a28-115">(Aby uzyskać informacje o używaniu `Imports` instrukcję, aby zaimportować alias, który może służyć użycia nazwy typów w kodzie, zobacz [Importy — instrukcja (.NET Namespace i Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).) Składnia deklaracji przestrzeni nazw XML przy użyciu `Imports` instrukcja jest taka sama jak składnią używaną w formacie XML.</span><span class="sxs-lookup"><span data-stu-id="14a28-115">(For information about using the `Imports` statement to import an alias that can be used where type names are used in your code, see [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).) The syntax for declaring an XML namespace by using the `Imports` statement is identical to the syntax used in XML.</span></span> <span data-ttu-id="14a28-116">W związku z tym, możesz skopiować deklarację przestrzeni nazw z pliku XML i korzystać z niej w `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="14a28-116">Therefore, you can copy a namespace declaration from an XML file and use it in an `Imports` statement.</span></span>  
  
 <span data-ttu-id="14a28-117">Prefiksy przestrzeni nazw XML są przydatne, jeśli chcesz regularnie tworzyć elementy XML, które pochodzą z tej samej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="14a28-117">XML namespace prefixes are useful when you want to repeatedly create XML elements that are from the same namespace.</span></span> <span data-ttu-id="14a28-118">Prefiks przestrzeni nazw XML zadeklarowane za pomocą `Imports` instrukcja jest globalne w tym sensie, że jest ona dostępna dla całego kodu w pliku.</span><span class="sxs-lookup"><span data-stu-id="14a28-118">The XML namespace prefix declared with the `Imports` statement is global in the sense that it is available to all code in the file.</span></span> <span data-ttu-id="14a28-119">Można użyć go po utworzeniu literały — element XML i jeśli uzyskujesz dostęp do właściwości osi XML.</span><span class="sxs-lookup"><span data-stu-id="14a28-119">You can use it when you create XML element literals and when you access XML axis properties.</span></span> <span data-ttu-id="14a28-120">Aby uzyskać więcej informacji, zobacz [literał elementu XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) i [właściwości osi XML](../../../visual-basic/language-reference/xml-axis/index.md).</span><span class="sxs-lookup"><span data-stu-id="14a28-120">For more information, see [XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) and [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/index.md).</span></span>  
  
 <span data-ttu-id="14a28-121">Jeśli zdefiniujesz globalnej przestrzeni nazw XML bez prefiksu przestrzeni nazw (na przykład `Imports <xmlns="http://SomeNameSpace>"`), przestrzeń nazw jest traktowane jako domyślny obszar nazw XML.</span><span class="sxs-lookup"><span data-stu-id="14a28-121">If you define a global XML namespace without a namespace prefix (for example, `Imports <xmlns="http://SomeNameSpace>"`), that namespace is considered the default XML namespace.</span></span> <span data-ttu-id="14a28-122">Domyślny obszar nazw XML jest używany dla literałów — element XML i właściwości osi atrybutu XML, które nie są określone jawnie przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="14a28-122">The default XML namespace is used for any XML element literals or XML attribute axis properties that do not explicitly specify a namespace.</span></span> <span data-ttu-id="14a28-123">Domyślny obszar nazw jest również używana, gdy określonego obszaru nazw jest pusta przestrzeń nazw (czyli `xmlns=""`).</span><span class="sxs-lookup"><span data-stu-id="14a28-123">The default namespace is also used if the specified namespace is the empty namespace (that is, `xmlns=""`).</span></span> <span data-ttu-id="14a28-124">Domyślny obszar nazw XML nie ma zastosowania do atrybutów XML w literałach XML lub do właściwości osi atrybutu XML, które nie mają przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="14a28-124">The default XML namespace does not apply to XML attributes in XML literals or to XML attribute axis properties that do not have a namespace.</span></span>  
  
 <span data-ttu-id="14a28-125">Obszary nazw XML, które są zdefiniowane w pliku XML literału, są one nazywane *lokalne obszary nazw XML*, pierwszeństwo przestrzeni nazw XML, które są zdefiniowane przez `Imports` instrukcję jako globalne.</span><span class="sxs-lookup"><span data-stu-id="14a28-125">XML namespaces that are defined in an XML literal, which are called *local XML namespaces*, take precedence over XML namespaces that are defined by the `Imports` statement as global.</span></span> <span data-ttu-id="14a28-126">Przestrzenie nazw XML, które są definiowane przez `Imports` instrukcji mają pierwszeństwo przed przestrzeni nazw XML zaimportowane dla projektów języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="14a28-126">XML namespaces that are defined by the `Imports` statement take precedence over XML namespaces imported for a Visual Basic project.</span></span> <span data-ttu-id="14a28-127">Jeśli literał XML definiuje obszar nazw XML, że lokalną przestrzeń nazw nie ma zastosowania do wyrażenia osadzone.</span><span class="sxs-lookup"><span data-stu-id="14a28-127">If an XML literal defines an XML namespace, that local namespace does not apply to embedded expressions.</span></span>  
  
 <span data-ttu-id="14a28-128">Globalnej przestrzeni nazw XML, wykonaj te same reguły zakresu i definicji jako przestrzeni nazw .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="14a28-128">Global XML namespaces follow the same scoping and definition rules as .NET Framework namespaces.</span></span> <span data-ttu-id="14a28-129">W rezultacie mogą obejmować `Imports` instrukcji, aby zdefiniować globalnej przestrzeni nazw XML dowolnym miejscu importujesz przestrzeń nazw .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="14a28-129">As a result, you can include an `Imports` statement to define a global XML namespace anywhere you can import a .NET Framework namespace.</span></span> <span data-ttu-id="14a28-130">Obejmuje to zarówno pliki kodu, jak i na poziomie projektu importowanych przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="14a28-130">This includes both code files and project-level imported namespaces.</span></span> <span data-ttu-id="14a28-131">Aby uzyskać informacji na temat importowanych przestrzeni nazw na poziomie projektu, zobacz [strona odwołań, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="14a28-131">For information about project-level imported namespaces, see [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="14a28-132">Każdy plik źródłowy może zawierać dowolną liczbę `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="14a28-132">Each source file can contain any number of `Imports` statements.</span></span> <span data-ttu-id="14a28-133">Te należy wykonać, opcja deklaracji, takich jak `Option Strict` instrukcji, dlatego musi poprzedzać deklaracji elementu programowania, takich jak `Module` lub `Class` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="14a28-133">These must follow option declarations, such as the `Option Strict` statement, and they must precede programming element declarations, such as `Module` or `Class` statements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14a28-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="14a28-134">Example</span></span>  
 <span data-ttu-id="14a28-135">Następujący przykład importuje, domyślnej przestrzeni nazw XML i zidentyfikowanego za prefiks przestrzeni nazw XML `ns`.</span><span class="sxs-lookup"><span data-stu-id="14a28-135">The following example imports a default XML namespace and an XML namespace identified with the prefix `ns`.</span></span> <span data-ttu-id="14a28-136">Następnie tworzy ona literałach XML, które używają obu tych przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="14a28-136">It then creates XML literals that use both namespaces.</span></span>  
  
 [!code-vb[VbXMLSamples#45](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_1.vb)]  
  
 <span data-ttu-id="14a28-137">Ten kod wyświetla następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="14a28-137">This code displays the following text:</span></span>  
  
```xml  
<ns:outer xmlns="http://DefaultNamespace"   
          xmlns:ns="http://NewNamespace">  
  <ns:innerElement></ns:innerElement>  
  <siblingElement></siblingElement>  
  <innerElement />  
</ns:outer>  
```  
  
## <a name="example"></a><span data-ttu-id="14a28-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="14a28-138">Example</span></span>  
 <span data-ttu-id="14a28-139">Następujący przykład importuje prefiks przestrzeni nazw XML `ns`.</span><span class="sxs-lookup"><span data-stu-id="14a28-139">The following example imports the XML namespace prefix `ns`.</span></span> <span data-ttu-id="14a28-140">Następnie tworzy literał XML używa prefiksu przestrzeni nazw, która wyświetla formularz końcowego elementu.</span><span class="sxs-lookup"><span data-stu-id="14a28-140">It then creates an XML literal that uses the namespace prefix and displays the element's final form.</span></span>  
  
 [!code-vb[VbXMLSamples#22](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_2.vb)]  
  
 <span data-ttu-id="14a28-141">Ten kod wyświetla następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="14a28-141">This code displays the following text:</span></span>  
  
```xml  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 <span data-ttu-id="14a28-142">Zwróć uwagę, kompilator przekonwertować prefiks przestrzeni nazw XML z globalnego prefiksu, do definicji lokalnego prefiks.</span><span class="sxs-lookup"><span data-stu-id="14a28-142">Notice that the compiler converted the XML namespace prefix from a global prefix to a local prefix definition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14a28-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="14a28-143">Example</span></span>  
 <span data-ttu-id="14a28-144">Następujący przykład importuje prefiks przestrzeni nazw XML `ns`.</span><span class="sxs-lookup"><span data-stu-id="14a28-144">The following example imports the XML namespace prefix `ns`.</span></span> <span data-ttu-id="14a28-145">Następnie używa prefiksu przestrzeni nazw tworzenie literałów XML i dostępem pierwszy węzeł podrzędny o nazwie kwalifikowanej `ns:name`.</span><span class="sxs-lookup"><span data-stu-id="14a28-145">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span></span>  
  
 [!code-vb[VbXMLSamples#19](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_3.vb)]  
  
 <span data-ttu-id="14a28-146">Ten kod wyświetla następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="14a28-146">This code displays the following text:</span></span>  
  
 `Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="14a28-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="14a28-147">See Also</span></span>  
 [<span data-ttu-id="14a28-148">Literał elementu XML</span><span class="sxs-lookup"><span data-stu-id="14a28-148">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [<span data-ttu-id="14a28-149">Właściwości osi XML</span><span class="sxs-lookup"><span data-stu-id="14a28-149">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)  
 [<span data-ttu-id="14a28-150">Nazwy deklarowanych elementów i atrybutów XML</span><span class="sxs-lookup"><span data-stu-id="14a28-150">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)  
 [<span data-ttu-id="14a28-151">GetXmlNamespace, operator</span><span class="sxs-lookup"><span data-stu-id="14a28-151">GetXmlNamespace Operator</span></span>](../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)
