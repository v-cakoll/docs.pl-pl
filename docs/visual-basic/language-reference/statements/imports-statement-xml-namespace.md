---
title: Imports — przestrzeń nazw XML
ms.date: 07/20/2015
f1_keywords:
- vb.ImportsXmlns
helpviewer_keywords:
- XML namespace [Visual Basic], importing
- imports [Visual Basic]
- Imports statement [Visual Basic]
- namespaces [Visual Basic], importing
ms.assetid: 1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4
ms.openlocfilehash: a3184d68b0e4cdff5d4296a5a638e22b4e83bcde
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404540"
---
# <a name="imports-statement-xml-namespace"></a><span data-ttu-id="804e0-102">Imports — Instrukcja (przestrzeń nazw XML)</span><span class="sxs-lookup"><span data-stu-id="804e0-102">Imports Statement (XML Namespace)</span></span>

<span data-ttu-id="804e0-103">Importuje prefiksy przestrzeni nazw XML do użycia w literałach XML i właściwościach osi XML.</span><span class="sxs-lookup"><span data-stu-id="804e0-103">Imports XML namespace prefixes for use in XML literals and XML axis properties.</span></span>

## <a name="syntax"></a><span data-ttu-id="804e0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="804e0-104">Syntax</span></span>

```vb
Imports <xmlns:xmlNamespacePrefix = "xmlNamespaceName">
```

## <a name="parts"></a><span data-ttu-id="804e0-105">Części</span><span class="sxs-lookup"><span data-stu-id="804e0-105">Parts</span></span>

`xmlNamespacePrefix`  
<span data-ttu-id="804e0-106">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="804e0-106">Optional.</span></span> <span data-ttu-id="804e0-107">Ciąg, do którego mogą się odwoływać elementy i atrybuty XML `xmlNamespaceName` .</span><span class="sxs-lookup"><span data-stu-id="804e0-107">The string by which XML elements and attributes can refer to `xmlNamespaceName`.</span></span> <span data-ttu-id="804e0-108">Jeśli nie `xmlNamespacePrefix` jest podany, importowana przestrzeń nazw XML jest domyślną przestrzenią nazw XML.</span><span class="sxs-lookup"><span data-stu-id="804e0-108">If no `xmlNamespacePrefix` is supplied, the imported XML namespace is the default XML namespace.</span></span> <span data-ttu-id="804e0-109">Musi być prawidłowym identyfikatorem XML.</span><span class="sxs-lookup"><span data-stu-id="804e0-109">Must be a valid XML identifier.</span></span> <span data-ttu-id="804e0-110">Aby uzyskać więcej informacji, zobacz [nazwy zadeklarowanych elementów i atrybutów XML](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="804e0-110">For more information, see [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>

`xmlNamespaceName`  
<span data-ttu-id="804e0-111">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="804e0-111">Required.</span></span> <span data-ttu-id="804e0-112">Ciąg identyfikujący importowaną przestrzeń nazw XML.</span><span class="sxs-lookup"><span data-stu-id="804e0-112">The string identifying the XML namespace being imported.</span></span>

## <a name="remarks"></a><span data-ttu-id="804e0-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="804e0-113">Remarks</span></span>

<span data-ttu-id="804e0-114">Możesz użyć instrukcji, `Imports` Aby zdefiniować globalne przestrzenie nazw XML, których można używać z literałami XML i właściwościami osi XML, lub jako parametry przesłane do `GetXmlNamespace` operatora.</span><span class="sxs-lookup"><span data-stu-id="804e0-114">You can use the `Imports` statement to define global XML namespaces that you can use with XML literals and XML axis properties, or as parameters passed to the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="804e0-115">(Aby uzyskać informacje o używaniu `Imports` instrukcji do importowania aliasu, którego można użyć w przypadku używania nazw typów w kodzie, zobacz [Imports (przestrzeń nazw i typ platformy .NET)](imports-statement-net-namespace-and-type.md). Składnia do deklarowania przestrzeni nazw XML przy użyciu `Imports` instrukcji jest taka sama jak składnia użyta w kodzie XML.</span><span class="sxs-lookup"><span data-stu-id="804e0-115">(For information about using the `Imports` statement to import an alias that can be used where type names are used in your code, see [Imports Statement (.NET Namespace and Type)](imports-statement-net-namespace-and-type.md).) The syntax for declaring an XML namespace by using the `Imports` statement is identical to the syntax used in XML.</span></span> <span data-ttu-id="804e0-116">W związku z tym można skopiować deklarację przestrzeni nazw z pliku XML i użyć jej w `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="804e0-116">Therefore, you can copy a namespace declaration from an XML file and use it in an `Imports` statement.</span></span>

<span data-ttu-id="804e0-117">Prefiksy przestrzeni nazw XML są przydatne, gdy chcesz wielokrotnie tworzyć elementy XML, które są z tego samego obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="804e0-117">XML namespace prefixes are useful when you want to repeatedly create XML elements that are from the same namespace.</span></span> <span data-ttu-id="804e0-118">Prefiks przestrzeni nazw XML zadeklarowany za pomocą `Imports` instrukcji jest globalnie w sensie, że jest dostępny dla całego kodu w pliku.</span><span class="sxs-lookup"><span data-stu-id="804e0-118">The XML namespace prefix declared with the `Imports` statement is global in the sense that it is available to all code in the file.</span></span> <span data-ttu-id="804e0-119">Można jej użyć podczas tworzenia literałów elementu XML i uzyskiwania dostępu do właściwości osi XML.</span><span class="sxs-lookup"><span data-stu-id="804e0-119">You can use it when you create XML element literals and when you access XML axis properties.</span></span> <span data-ttu-id="804e0-120">Aby uzyskać więcej informacji, zobacz [literał elementu XML](../xml-literals/xml-element-literal.md) i [Właściwości osi XML](../xml-axis/index.md).</span><span class="sxs-lookup"><span data-stu-id="804e0-120">For more information, see [XML Element Literal](../xml-literals/xml-element-literal.md) and [XML Axis Properties](../xml-axis/index.md).</span></span>

<span data-ttu-id="804e0-121">Jeśli zdefiniujesz globalną przestrzeń nazw XML bez prefiksu przestrzeni nazw (na przykład `Imports <xmlns="http://SomeNameSpace>"` ), ta przestrzeń nazw jest traktowana jako domyślna przestrzeń nazw XML.</span><span class="sxs-lookup"><span data-stu-id="804e0-121">If you define a global XML namespace without a namespace prefix (for example, `Imports <xmlns="http://SomeNameSpace>"`), that namespace is considered the default XML namespace.</span></span> <span data-ttu-id="804e0-122">Domyślna przestrzeń nazw XML jest używana dla wszystkich literałów elementu XML lub właściwości osi XML, które nie określają jawnie przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="804e0-122">The default XML namespace is used for any XML element literals or XML attribute axis properties that do not explicitly specify a namespace.</span></span> <span data-ttu-id="804e0-123">Domyślna przestrzeń nazw jest również używana, jeśli określona przestrzeń nazw jest pustą przestrzenią nazw (czyli `xmlns=""` ).</span><span class="sxs-lookup"><span data-stu-id="804e0-123">The default namespace is also used if the specified namespace is the empty namespace (that is, `xmlns=""`).</span></span> <span data-ttu-id="804e0-124">Domyślna przestrzeń nazw XML nie ma zastosowania do atrybutów XML w literałach XML ani do właściwości osi atrybutu XML, które nie mają przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="804e0-124">The default XML namespace does not apply to XML attributes in XML literals or to XML attribute axis properties that do not have a namespace.</span></span>

<span data-ttu-id="804e0-125">Przestrzenie nazw XML, które są zdefiniowane w literale XML, które są nazywane *lokalnymi przestrzeniami nazw XML*, mają pierwszeństwo przed przestrzeniami nazw XML, które są zdefiniowane przez `Imports` instrukcję jako globalną.</span><span class="sxs-lookup"><span data-stu-id="804e0-125">XML namespaces that are defined in an XML literal, which are called *local XML namespaces*, take precedence over XML namespaces that are defined by the `Imports` statement as global.</span></span> <span data-ttu-id="804e0-126">Przestrzenie nazw XML, które są zdefiniowane przez `Imports` instrukcję, mają pierwszeństwo przed przestrzeniami nazw XML importowanymi dla projektu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="804e0-126">XML namespaces that are defined by the `Imports` statement take precedence over XML namespaces imported for a Visual Basic project.</span></span> <span data-ttu-id="804e0-127">Jeśli literał XML definiuje przestrzeń nazw XML, ta lokalna przestrzeń nazw nie ma zastosowania do wyrażeń osadzonych.</span><span class="sxs-lookup"><span data-stu-id="804e0-127">If an XML literal defines an XML namespace, that local namespace does not apply to embedded expressions.</span></span>

<span data-ttu-id="804e0-128">Globalne przestrzenie nazw XML są zgodne z tymi samymi regułami określania zakresu i definicji co .NET Framework przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="804e0-128">Global XML namespaces follow the same scoping and definition rules as .NET Framework namespaces.</span></span> <span data-ttu-id="804e0-129">W związku z tym można dołączyć `Imports` instrukcję definiowania globalnej przestrzeni nazw XML w dowolnym miejscu, w którym można zaimportować .NET Framework przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="804e0-129">As a result, you can include an `Imports` statement to define a global XML namespace anywhere you can import a .NET Framework namespace.</span></span> <span data-ttu-id="804e0-130">Dotyczy to zarówno plików kodu, jak i importowanych przestrzeni nazw na poziomie projektu.</span><span class="sxs-lookup"><span data-stu-id="804e0-130">This includes both code files and project-level imported namespaces.</span></span> <span data-ttu-id="804e0-131">Aby uzyskać informacje na temat importowanych przestrzeni nazw na poziomie projektu, zobacz [Strona odwołań, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="804e0-131">For information about project-level imported namespaces, see [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span>

<span data-ttu-id="804e0-132">Każdy plik źródłowy może zawierać dowolną liczbę `Imports` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="804e0-132">Each source file can contain any number of `Imports` statements.</span></span> <span data-ttu-id="804e0-133">Muszą one być zgodne z deklaracjami opcji, takimi jak `Option Strict` instrukcja, i muszą poprzedzać deklaracje elementów programistycznych, takich jak `Module` lub `Class` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="804e0-133">These must follow option declarations, such as the `Option Strict` statement, and they must precede programming element declarations, such as `Module` or `Class` statements.</span></span>

## <a name="example"></a><span data-ttu-id="804e0-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="804e0-134">Example</span></span>

<span data-ttu-id="804e0-135">Poniższy przykład importuje domyślną przestrzeń nazw XML i przestrzeń nazw XML zidentyfikowaną z prefiksem `ns` .</span><span class="sxs-lookup"><span data-stu-id="804e0-135">The following example imports a default XML namespace and an XML namespace identified with the prefix `ns`.</span></span> <span data-ttu-id="804e0-136">Następnie tworzy literały XML używające obu przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="804e0-136">It then creates XML literals that use both namespaces.</span></span>

[!code-vb[VbXMLSamples#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/Module1.vb#45)]

<span data-ttu-id="804e0-137">Ten kod wyświetla następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="804e0-137">This code displays the following text:</span></span>

```xml
<ns:outer xmlns="http://DefaultNamespace"
          xmlns:ns="http://NewNamespace">
  <ns:innerElement></ns:innerElement>
  <siblingElement></siblingElement>
  <innerElement />
</ns:outer>
```

## <a name="example"></a><span data-ttu-id="804e0-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="804e0-138">Example</span></span>

<span data-ttu-id="804e0-139">Poniższy przykład importuje prefiks przestrzeni nazw XML `ns` .</span><span class="sxs-lookup"><span data-stu-id="804e0-139">The following example imports the XML namespace prefix `ns`.</span></span> <span data-ttu-id="804e0-140">Następnie tworzy literał XML, który używa prefiksu przestrzeni nazw i wyświetla ostateczną postać elementu.</span><span class="sxs-lookup"><span data-stu-id="804e0-140">It then creates an XML literal that uses the namespace prefix and displays the element's final form.</span></span>

[!code-vb[VbXMLSamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples10.vb#22)]

<span data-ttu-id="804e0-141">Ten kod wyświetla następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="804e0-141">This code displays the following text:</span></span>

```xml
<ns:outer xmlns:ns="http://SomeNamespace">
  <ns:middle xmlns:ns="http://NewNamespace">
    <ns:inner1 />
    <inner2 xmlns="http://SomeNamespace" />
  </ns:middle>
</ns:outer>
```

<span data-ttu-id="804e0-142">Zwróć uwagę, że kompilator przekonwertował prefiks przestrzeni nazw XML z globalnego prefiksu na definicję prefiksu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="804e0-142">Notice that the compiler converted the XML namespace prefix from a global prefix to a local prefix definition.</span></span>

## <a name="example"></a><span data-ttu-id="804e0-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="804e0-143">Example</span></span>

<span data-ttu-id="804e0-144">Poniższy przykład importuje prefiks przestrzeni nazw XML `ns` .</span><span class="sxs-lookup"><span data-stu-id="804e0-144">The following example imports the XML namespace prefix `ns`.</span></span> <span data-ttu-id="804e0-145">Następnie używa prefiksu przestrzeni nazw w celu utworzenia literału XML i uzyskania dostępu do pierwszego węzła podrzędnego przy użyciu kwalifikowanej nazwy `ns:name` .</span><span class="sxs-lookup"><span data-stu-id="804e0-145">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span></span>

[!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]

<span data-ttu-id="804e0-146">Ten kod wyświetla następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="804e0-146">This code displays the following text:</span></span>

`Patrick Hines`

## <a name="see-also"></a><span data-ttu-id="804e0-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="804e0-147">See also</span></span>

- [<span data-ttu-id="804e0-148">Literał elementu XML</span><span class="sxs-lookup"><span data-stu-id="804e0-148">XML Element Literal</span></span>](../xml-literals/xml-element-literal.md)
- [<span data-ttu-id="804e0-149">Właściwości osi XML</span><span class="sxs-lookup"><span data-stu-id="804e0-149">XML Axis Properties</span></span>](../xml-axis/index.md)
- [<span data-ttu-id="804e0-150">Nazwy deklarowanych elementów XML oraz atrybuty</span><span class="sxs-lookup"><span data-stu-id="804e0-150">Names of Declared XML Elements and Attributes</span></span>](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [<span data-ttu-id="804e0-151">GetXmlNamespace, operator</span><span class="sxs-lookup"><span data-stu-id="804e0-151">GetXmlNamespace Operator</span></span>](../operators/getxmlnamespace-operator.md)
