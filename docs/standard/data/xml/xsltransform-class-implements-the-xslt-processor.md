---
title: Klasy XslTransform implementuje procesora XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 88373fe2-4a6b-44f9-8a62-8a3e348e3a46
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 81d0ce4f697935908b8ad7084560bd1adacbdf2d
ms.sourcegitcommit: daa8788af67ac2d1cecd24f9f3409babb2f978c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2018
ms.locfileid: "47863499"
---
# <a name="xsltransform-class-implements-the-xslt-processor"></a><span data-ttu-id="d9119-102">Klasy XslTransform implementuje procesora XSLT</span><span class="sxs-lookup"><span data-stu-id="d9119-102">XslTransform Class Implements the XSLT Processor</span></span>
> [!NOTE]
>  <span data-ttu-id="d9119-103"><xref:System.Xml.Xsl.XslTransform> Klasy jest przestarzała w [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d9119-103">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="d9119-104">Można przeprowadzić rozszerzalny język arkusza stylów dla przekształceń przekształcenia (XSLT) przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy.</span><span class="sxs-lookup"><span data-stu-id="d9119-104">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="d9119-105">Zobacz [używanie klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) i [Migrowanie z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="d9119-105">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="d9119-106"><xref:System.Xml.Xsl.XslTransform> Klasa jest procesora XSLT implementacji przekształcenia XSL (XSLT) w wersji 1.0 zalecenia.</span><span class="sxs-lookup"><span data-stu-id="d9119-106">The <xref:System.Xml.Xsl.XslTransform> class is an XSLT processor implementing the XSL Transformations (XSLT) Version 1.0 recommendation.</span></span> <span data-ttu-id="d9119-107"><xref:System.Xml.Xsl.XslTransform.Load%2A> Metoda lokalizuje i odczytuje arkusze stylów i <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda przekształca dokumentu danego źródła.</span><span class="sxs-lookup"><span data-stu-id="d9119-107">The <xref:System.Xml.Xsl.XslTransform.Load%2A> method locates and reads style sheets, and the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method transforms the given source document.</span></span> <span data-ttu-id="d9119-108">Dowolnego magazynu, który implementuje <xref:System.Xml.XPath.IXPathNavigable> interfejsu może być używany jako dokument źródłowy dla <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="d9119-108">Any store that implements the <xref:System.Xml.XPath.IXPathNavigable> interface can be used as the source document for the <xref:System.Xml.Xsl.XslTransform>.</span></span> <span data-ttu-id="d9119-109">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Implementuje obecnie <xref:System.Xml.XPath.IXPathNavigable> interfejsu na <xref:System.Xml.XmlDocument>, <xref:System.Xml.XmlDataDocument>i <xref:System.Xml.XPath.XPathDocument>, więc wszystkie te mogą być używane jako dokument źródła danych wejściowych do przekształcenia.</span><span class="sxs-lookup"><span data-stu-id="d9119-109">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] currently implements the <xref:System.Xml.XPath.IXPathNavigable> interface on the <xref:System.Xml.XmlDocument>, the <xref:System.Xml.XmlDataDocument>, and the <xref:System.Xml.XPath.XPathDocument>, so all of these can be used as the input source document to a transformation.</span></span>  
  
 <span data-ttu-id="d9119-110"><xref:System.Xml.Xsl.XslTransform> Obiektu [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] obsługuje tylko specyfikacji XSLT 1.0, zdefiniowana za pomocą następujących przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="d9119-110">The <xref:System.Xml.Xsl.XslTransform> object in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] only supports the XSLT 1.0 specification, defined with the following namespace:</span></span>  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">    
```  
  
 <span data-ttu-id="d9119-111">Arkusz stylów może być załadowany, za pomocą <xref:System.Xml.Xsl.XslTransform.Load%2A> metody, z jedną z następujących klas:</span><span class="sxs-lookup"><span data-stu-id="d9119-111">The style sheet can be loaded, using the <xref:System.Xml.Xsl.XslTransform.Load%2A> method, from one of the following classes:</span></span>  
  
-   <span data-ttu-id="d9119-112">Klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="d9119-112">XPathNavigator</span></span>  
  
-   <span data-ttu-id="d9119-113">Element XmlReader</span><span class="sxs-lookup"><span data-stu-id="d9119-113">XmlReader</span></span>  
  
-   <span data-ttu-id="d9119-114">Ciąg reprezentujący adres URL</span><span class="sxs-lookup"><span data-stu-id="d9119-114">A string representing a URL</span></span>  
  
 <span data-ttu-id="d9119-115">Istnieje inny <xref:System.Xml.Xsl.XslTransform.Load%2A> metody dla każdego z powyższych klas danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="d9119-115">There is a different <xref:System.Xml.Xsl.XslTransform.Load%2A> method for each of the above input classes.</span></span> <span data-ttu-id="d9119-116">Niektóre metody przyjmują w połączeniu z jednej z tych klas i <xref:System.Xml.XmlResolver> klasy jako argumenty.</span><span class="sxs-lookup"><span data-stu-id="d9119-116">Some methods take in a combination of one of these classes and the <xref:System.Xml.XmlResolver> class as arguments.</span></span> <span data-ttu-id="d9119-117"><xref:System.Xml.XmlResolver> Lokalizuje zasobów przywoływanych przez `<xsl:import>` lub `<xsl:include>` znalezione w arkuszu stylów.</span><span class="sxs-lookup"><span data-stu-id="d9119-117">The <xref:System.Xml.XmlResolver> locates resources referenced by `<xsl:import>` or `<xsl:include>` found in the style sheet.</span></span> <span data-ttu-id="d9119-118">Następujące metody przyjmują ciąg <xref:System.Xml.XmlReader>, lub <xref:System.Xml.XPath.XPathNavigator> jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="d9119-118">The following methods take a string, <xref:System.Xml.XmlReader>, or <xref:System.Xml.XPath.XPathNavigator> as input.</span></span>  
  
```vb  
Overloads Public Sub Load(String)  
```  
  
```csharp  
public void Load(string);  
```  
  
```vb  
Overloads Public Sub Load(String, XmlResolver)  
```  
  
```csharp  
public void Load(string, XmlResolver);  
```  
  
```vb  
Overloads Public Sub Load(XmlReader, XmlResolver, Evidence)  
```  
  
```csharp  
public void Load(XmlReader, XmlResolver, Evidence);  
```  
  
```vb  
Overloads Public Sub Load(XPathNavigator, XmlResolver, Evidence)  
```  
  
```csharp  
public void Load(XPathNavigator, XmlResolver, Evidence);  
```  
  
 <span data-ttu-id="d9119-119">Większość <xref:System.Xml.Xsl.XslTransform.Load%2A> metod przedstawionych powyżej take <xref:System.Xml.XmlResolver> jako parametr.</span><span class="sxs-lookup"><span data-stu-id="d9119-119">Most of the <xref:System.Xml.Xsl.XslTransform.Load%2A> methods shown above take an <xref:System.Xml.XmlResolver> as a parameter.</span></span> <span data-ttu-id="d9119-120"><xref:System.Xml.XmlResolver> Jest używana do ładowania arkusza stylów i wszelkie arkusze stylów w elementu xsl: Import i xsl: obejmują elementy.</span><span class="sxs-lookup"><span data-stu-id="d9119-120">The <xref:System.Xml.XmlResolver> is used to load the style sheet and any style sheet(s) referenced in xsl:import and xsl:include elements.</span></span>  
  
 <span data-ttu-id="d9119-121">Większość <xref:System.Xml.Xsl.XslTransform.Load%2A> metody przyjmują również dowody jako parametr.</span><span class="sxs-lookup"><span data-stu-id="d9119-121">Most of the <xref:System.Xml.Xsl.XslTransform.Load%2A> methods also take evidence as a parameter.</span></span> <span data-ttu-id="d9119-122">Parametr dowód <xref:System.Security.Policy.Evidence> skojarzonego z arkusza stylów.</span><span class="sxs-lookup"><span data-stu-id="d9119-122">The evidence parameter is the <xref:System.Security.Policy.Evidence> that is associated with the style sheet.</span></span> <span data-ttu-id="d9119-123">Poziom zabezpieczeń arkusza stylów wpływa na poziom zabezpieczeń wszystkie kolejne zasoby, które odwołuje się do, takich jak skryptu w nim dowolne `document()` wykorzystuje funkcje i obiekty rozszerzeń używane przez <xref:System.Xml.Xsl.XsltArgumentList>.</span><span class="sxs-lookup"><span data-stu-id="d9119-123">The security level of the style sheet affects the security level of any subsequent resources it references, such as the script it contains, any `document()` functions it uses, and any extension objects used by the <xref:System.Xml.Xsl.XsltArgumentList>.</span></span>  
  
 <span data-ttu-id="d9119-124">Jeśli arkusz stylów jest ładowany za pomocą <xref:System.Xml.Xsl.XslTransform.Load%2A> metodę, która zawiera parametr adresu URL i oznak jest dostarczany, dowód arkusza stylów jest obliczana przez połączenie danego adresu URL z jej witryny i strefy.</span><span class="sxs-lookup"><span data-stu-id="d9119-124">If the style sheet is loaded using a <xref:System.Xml.Xsl.XslTransform.Load%2A> method that contains a URL parameter and no evidence is provided, the evidence of the style sheet is calculated by combining the given URL with its site and zone.</span></span>  
  
 <span data-ttu-id="d9119-125">Jeśli nie podano żadnych identyfikatora URI lub dowód, dowodów dla arkusza stylów jest w pełni zaufany.</span><span class="sxs-lookup"><span data-stu-id="d9119-125">If no URI or evidence is provided, then the evidence set for the style sheet is fully trusted.</span></span> <span data-ttu-id="d9119-126">Nie załadować arkusze stylów ze źródeł niezaufanych lub dodać obiekty niezaufane rozszerzenia do <xref:System.Xml.Xsl.XsltArgumentList>.</span><span class="sxs-lookup"><span data-stu-id="d9119-126">Do not load style sheets from untrusted sources, or add untrusted extension objects into the <xref:System.Xml.Xsl.XsltArgumentList>.</span></span>  
  
 <span data-ttu-id="d9119-127">Aby uzyskać więcej informacji na temat poziomów zabezpieczeń i dowody i jak wpływa on na wykonywanie skryptów, zobacz [XSLT skryptów przy użyciu arkusza stylów \<msxsl: script >](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md).</span><span class="sxs-lookup"><span data-stu-id="d9119-127">For more information about security levels and evidence and how it affects scripting, see [XSLT Stylesheet Scripting Using \<msxsl:script>](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md).</span></span> <span data-ttu-id="d9119-128">Aby uzyskać informacje na temat poziomów zabezpieczeń i dowody i jak wpływa na obiekty rozszerzeń, zobacz [XsltArgumentList — parametry arkusza stylów i obiekty rozszerzeń](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md).</span><span class="sxs-lookup"><span data-stu-id="d9119-128">For information about security levels and evidence and how it affects extension objects, see [XsltArgumentList for Style Sheet Parameters and Extension Objects](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md).</span></span>  
  
 <span data-ttu-id="d9119-129">Aby uzyskać informacji na temat poziomów zabezpieczeń i dowody i jak wpływa na `document()` funkcji, zobacz [Rozpoznawanie zewnętrznych arkuszy stylów XSLT i dokumenty](../../../../docs/standard/data/xml/resolving-external-xslt-style-sheets-and-documents.md).</span><span class="sxs-lookup"><span data-stu-id="d9119-129">For information about security levels and evidence and how it affects the `document()` function, see [Resolving External XSLT Style Sheets and Documents](../../../../docs/standard/data/xml/resolving-external-xslt-style-sheets-and-documents.md).</span></span>  
  
 <span data-ttu-id="d9119-130">Arkusz stylów można podać z liczbą parametrów wejściowych.</span><span class="sxs-lookup"><span data-stu-id="d9119-130">A style sheet can be supplied with a number of input parameters.</span></span> <span data-ttu-id="d9119-131">Arkusz stylów można również wywołać funkcje na obiekty rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="d9119-131">The style sheet can also call functions on extension objects.</span></span> <span data-ttu-id="d9119-132">Parametry i obiekty rozszerzeń, które są dostarczane do przy użyciu arkusza stylów <xref:System.Xml.Xsl.XsltArgumentList> klasy.</span><span class="sxs-lookup"><span data-stu-id="d9119-132">Both parameters and extension objects are supplied to the style sheet using the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span> <span data-ttu-id="d9119-133">Aby uzyskać więcej informacji na temat <xref:System.Xml.Xsl.XsltArgumentList>, zobacz <xref:System.Xml.Xsl.XsltArgumentList>.</span><span class="sxs-lookup"><span data-stu-id="d9119-133">For more information about the <xref:System.Xml.Xsl.XsltArgumentList>, see <xref:System.Xml.Xsl.XsltArgumentList>.</span></span>  
  
## <a name="recommended-secure-use-of-xsltransform-class"></a><span data-ttu-id="d9119-134">Zalecane bezpieczne użycie klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="d9119-134">Recommended Secure Use of XslTransform Class</span></span>  
 <span data-ttu-id="d9119-135">Uprawnienia zabezpieczeń w arkuszu stylów są zależne od dowody dostarczone.</span><span class="sxs-lookup"><span data-stu-id="d9119-135">The security privileges of the style sheet depend on the evidence provided.</span></span> <span data-ttu-id="d9119-136">Poniższa tabela zawiera podsumowanie Lokalizacja arkusza stylów i zawiera wyjaśnienie, jakiego rodzaju dowody, aby nadać.</span><span class="sxs-lookup"><span data-stu-id="d9119-136">The following table summarizes the location of the style sheet and gives an explanation of what type of evidence to give.</span></span>  
  
-   <span data-ttu-id="d9119-137">Arkusz stylów XSLT nie ma zewnętrznych odwołań, lub arkusz stylów pochodzi z bazy kodu, którym ufasz.</span><span class="sxs-lookup"><span data-stu-id="d9119-137">The XSLT style sheet has no external references, or the style sheet comes from a code base that you trust.</span></span>  
  
    -   <span data-ttu-id="d9119-138">Podaj dowód z zestawu:</span><span class="sxs-lookup"><span data-stu-id="d9119-138">Provide the evidence from your assembly:</span></span>  
  
         `Dim xslt = New XslTransform() xslt.Load(stylesheet, resolver, Me.GetType().Assembly.Evidence)`  
  
         `XsltTransform xslt = new XslTransform();  xslt.Load(stylesheet, resolver, this.GetType().Assembly.Evidence);`  
  
-   <span data-ttu-id="d9119-139">Arkusz stylów XSLT jest dostarczany ze źródła zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="d9119-139">The XSLT style sheet comes from an outside source.</span></span> <span data-ttu-id="d9119-140">Pochodzenie źródła jest znane, i jest możliwe do zweryfikowania identyfikatorem URI.</span><span class="sxs-lookup"><span data-stu-id="d9119-140">The origin of the source is known and there is a verifiable URI.</span></span>  
  
    -   <span data-ttu-id="d9119-141">Tworzenie dokumentów, używając identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="d9119-141">Create evidence using the URI.</span></span>  
  
         `Dim xslt As New XslTransform() Dim ev As Evidence = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri) xslt.Load(stylesheet, resolver, evidence)`  
  
         `XslTransform xslt = new XslTransform(); Evidence ev = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri); xslt.Load(stylesheet, resolver, evidence);`  
  
-   <span data-ttu-id="d9119-142">Arkusz stylów XSLT jest dostarczany ze źródła zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="d9119-142">The XSLT style sheet comes from an outside source.</span></span> <span data-ttu-id="d9119-143">Pochodzenie źródła nie jest znany.</span><span class="sxs-lookup"><span data-stu-id="d9119-143">The origin of the source is not known.</span></span>  
  
    -   <span data-ttu-id="d9119-144">Ustaw dowód `null`.</span><span class="sxs-lookup"><span data-stu-id="d9119-144">Set evidence to `null`.</span></span> <span data-ttu-id="d9119-145">Bloki skryptu nie są przetwarzane, XSLT `document()` funkcja nie jest obsługiwana i obiekty rozszerzeń uprzywilejowanych są niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="d9119-145">Script blocks are not processed, the XSLT `document()` function is not supported, and privileged extension objects are disallowed.</span></span>  
  
         <span data-ttu-id="d9119-146">Ponadto można również ustawić `resolver` parametr `null` gwarantuje to, że `xsl:import` i `xsl:include` elementy nie zostały przetworzone.</span><span class="sxs-lookup"><span data-stu-id="d9119-146">Additionally, you can also set the `resolver` parameter to `null` This ensures that `xsl:import` and `xsl:include` elements are not processed.</span></span>  
  
-   <span data-ttu-id="d9119-147">Arkusz stylów XSLT jest dostarczany ze źródła zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="d9119-147">The XSLT style sheet comes from an outside source.</span></span> <span data-ttu-id="d9119-148">Pochodzenie źródła nie jest znany, ale wymagają obsługi skryptów.</span><span class="sxs-lookup"><span data-stu-id="d9119-148">The origin of the source is not known, but you require script support.</span></span>  
  
    -   <span data-ttu-id="d9119-149">Żądanie dowód od elementu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="d9119-149">Request evidence from the caller.</span></span>  
  
## <a name="transformation-of-xml-data"></a><span data-ttu-id="d9119-150">Przekształcania danych XML</span><span class="sxs-lookup"><span data-stu-id="d9119-150">Transformation of XML Data</span></span>  
 <span data-ttu-id="d9119-151">Po załadowaniu arkusza stylów transformacja rozpoczyna się przez wywołanie jednej z <xref:System.Xml.Xsl.XslTransform.Transform%2A> metod i dostarczenie dokument źródła danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="d9119-151">Once a style sheet is loaded, the transformation starts by calling one of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> methods and supplying an input source document.</span></span> <span data-ttu-id="d9119-152"><xref:System.Xml.Xsl.XslTransform.Transform%2A> Metody jest przeciążona, aby zapewnić różne przekształcenia danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="d9119-152">The <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is overloaded to provide different transformation outputs.</span></span> <span data-ttu-id="d9119-153">Transformacja może spowodować następujące formaty danych wyjściowych:</span><span class="sxs-lookup"><span data-stu-id="d9119-153">The transformation can result in the following output formats:</span></span>  
  
-   <xref:System.Xml.XmlReader>  
  
-   <xref:System.Xml.XmlWriter>  
  
-   <xref:System.IO.TextWriter>  
  
-   <xref:System.IO.Stream>  
  
-   <span data-ttu-id="d9119-154">Ciąg adresu URL w pliku</span><span class="sxs-lookup"><span data-stu-id="d9119-154">String URL of file</span></span>  
  
 <span data-ttu-id="d9119-155">Ten ostatni format ciągu adresu URL, zawiera często używane scenariusza w przekształcaniu dokument wejściowy znajduje się w adresie URL i zapisywania dokumentu do adresu URL danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="d9119-155">This last format, the string URL, provides for a commonly used scenario in transforming an input document located in a URL and writing the document to the output URL.</span></span> <span data-ttu-id="d9119-156">To <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody jest to wygodna metoda można załadować dokumentu XML z pliku, wykonywanie transformacji XSLT i zapisać dane wyjściowe do pliku.</span><span class="sxs-lookup"><span data-stu-id="d9119-156">This <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is a convenience method to load an XML document from a file, perform the XSLT transformation, and write the output to a file.</span></span> <span data-ttu-id="d9119-157">Zapobiega konieczności utworzyć i załadować dokument źródła danych wejściowych, a następnie zapisać do strumienia pliku.</span><span class="sxs-lookup"><span data-stu-id="d9119-157">This prevents you from having to create and load the input source document, and then write to a file stream.</span></span> <span data-ttu-id="d9119-158">Poniższy przykładowy kod pokazuje zastosowanie <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody przy użyciu adresu URL ciąg jako dane wejściowe i wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="d9119-158">The following code sample shows this use of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method using the string URL as input and output:</span></span>  
  
```vb  
Dim xsltransform As XslTransform = New XslTransform()  
xsltransform.Load("favorite.xsl")  
xsltransform.Transform("MyDocument.Xml", "TransformResult.xml", Nothing)  
```  
  
```csharp  
XslTransform xsltransform = new XslTransform();  
xsltransform.Load("favorite.xsl");  
xsltransform.Transform("MyDocument.xml", "TransformResult.xml", null);  
```  
  
## <a name="transforming-a-section-of-an-xml-document"></a><span data-ttu-id="d9119-159">Przekształcanie części dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="d9119-159">Transforming a Section of an XML Document</span></span>  
 <span data-ttu-id="d9119-160">Przekształcenia mają zastosowanie do dokumentu jako całości.</span><span class="sxs-lookup"><span data-stu-id="d9119-160">Transformations apply to the document as a whole.</span></span> <span data-ttu-id="d9119-161">Innymi słowy Jeśli przekażesz w węźle innym niż węzeł główny dokument, to nie uniemożliwia proces przekształcania uzyskiwania dostępu do wszystkich węzłów w dokumencie załadowane.</span><span class="sxs-lookup"><span data-stu-id="d9119-161">In other words, if you pass in a node other than the document root node, this does not prevent the transformation process from accessing all nodes in the loaded document.</span></span> <span data-ttu-id="d9119-162">Aby przekształcić wynikowego fragmentu drzewa, musisz utworzyć <xref:System.Xml.XmlDocument> zawierający tylko drzewa wynik fragmentu i przekazać go <xref:System.Xml.XmlDocument> do <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="d9119-162">To transform a result tree fragment, you must create an <xref:System.Xml.XmlDocument> containing just the result tree fragment and pass that <xref:System.Xml.XmlDocument> to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span> <span data-ttu-id="d9119-163">Poniższy przykład wykonuje przekształcenie na wynikowego fragmentu drzewa.</span><span class="sxs-lookup"><span data-stu-id="d9119-163">The following example performs a transformation on a result tree fragment.</span></span>  
  
```vb  
Dim xslt As New XslTransform()  
xslt.Load("print_root.xsl")  
Dim doc As New XmlDocument()  
doc.Load("library.xml")  
' Create a new document containing just the result tree fragment.  
Dim testNode As XmlNode = doc.DocumentElement.FirstChild  
Dim tmpDoc As New XmlDocument()  
tmpDoc.LoadXml(testNode.OuterXml)  
' Pass the document containing the result tree fragment   
' to the Transform method.  
Console.WriteLine(("Passing " + tmpDoc.OuterXml + " to print_root.xsl"))  
xslt.Transform(tmpDoc, Nothing, Console.Out, Nothing)  
```  
  
```csharp  
XslTransform xslt = new XslTransform();       
xslt.Load("print_root.xsl");  
XmlDocument doc = new XmlDocument();  
doc.Load("library.xml");  
// Create a new document containing just the result tree fragment.  
XmlNode testNode = doc.DocumentElement.FirstChild;   
XmlDocument tmpDoc = new XmlDocument();   
tmpDoc.LoadXml(testNode.OuterXml);  
// Pass the document containing the result tree fragment   
// to the Transform method.  
Console.WriteLine("Passing " + tmpDoc.OuterXml + " to print_root.xsl");  
xslt.Transform(tmpDoc, null, Console.Out, null);  
```  
  
 <span data-ttu-id="d9119-164">W przykładzie użyto library.xml i print_root.xsl pliki jako dane wejściowe i dane wyjściowe konsoli następującą zawartość.</span><span class="sxs-lookup"><span data-stu-id="d9119-164">The example uses the library.xml and print_root.xsl files as input and outputs the following to the console.</span></span>  
  
```  
Passing <book genre="novel" ISBN="1-861001-57-5"><title>Pride And Prejudice</title></book> to print_root.xsl   
Root node is book.  
```  
  
 <span data-ttu-id="d9119-165">Library.XML</span><span class="sxs-lookup"><span data-stu-id="d9119-165">library.xml</span></span>  
  
```xml  
<library>  
  <book genre='novel' ISBN='1-861001-57-5'>  
     <title>Pride And Prejudice</title>  
  </book>  
  <book genre='novel' ISBN='1-81920-21-2'>  
     <title>Hook</title>  
  </book>  
</library>  
```  
  
 <span data-ttu-id="d9119-166">print_root.xsl</span><span class="sxs-lookup"><span data-stu-id="d9119-166">print_root.xsl</span></span>  
  
```xml  
<stylesheet version="1.0" xmlns="http://www.w3.org/1999/XSL/Transform" >  
  <output method="text" />   
  <template match="/">  
     Root node is  <value-of select="local-name(//*[position() = 1])" />   
  </template>  
</stylesheet>  
```  
  
## <a name="migration-of-xslt-from-net-framework-version-10-to-net-framework-version-11"></a><span data-ttu-id="d9119-167">Migracja XSLT z .NET Framework w wersji 1.0 do .NET Framework w wersji 1.1</span><span class="sxs-lookup"><span data-stu-id="d9119-167">Migration of XSLT from .NET Framework version 1.0 to .NET Framework version 1.1</span></span>  
 <span data-ttu-id="d9119-168">W poniższej tabeli przedstawiono przestarzałe [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] metod w wersji 1.0 i nowe [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] wersji 1.1 metody <xref:System.Xml.Xsl.XslTransform.Load%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="d9119-168">The following table shows the obsolete [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] version 1.0 methods and new [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] version 1.1 methods for the <xref:System.Xml.Xsl.XslTransform.Load%2A> method.</span></span> <span data-ttu-id="d9119-169">Nowe metody umożliwiają ograniczenie uprawnień arkusza stylów, określając dowodów.</span><span class="sxs-lookup"><span data-stu-id="d9119-169">The new methods enable you to limit the permissions of the style sheet by specifying evidence.</span></span>  
  
|<span data-ttu-id="d9119-170">.NET Framework w wersji 1.0 obciążenia metody przestarzałe</span><span class="sxs-lookup"><span data-stu-id="d9119-170">Obsolete .NET Framework version 1.0 Load Methods</span></span>|<span data-ttu-id="d9119-171">Zastąpienie .NET Framework w wersji 1.1 obciążenia metody</span><span class="sxs-lookup"><span data-stu-id="d9119-171">Replacement .NET Framework version 1.1 Load Methods</span></span>|  
|------------------------------------------------------|---------------------------------------------------------|  
|<span data-ttu-id="d9119-172">Załaduj (dane wejściowe klasy XPathNavigator);</span><span class="sxs-lookup"><span data-stu-id="d9119-172">Load(XPathNavigator input);</span></span><br /><br /> <span data-ttu-id="d9119-173">Obciążenia (klasy XPathNavigator danych wejściowych, element XmlResolver rozpoznawania nazw);</span><span class="sxs-lookup"><span data-stu-id="d9119-173">Load(XPathNavigator input, XmlResolver resolver);</span></span>|<span data-ttu-id="d9119-174">Obciążenia (klasy XPathNavigator arkusza stylów, element XmlResolver programu rozpoznawania nazw, dowód dowód);</span><span class="sxs-lookup"><span data-stu-id="d9119-174">Load(XPathNavigator stylesheet, XmlResolver resolver, Evidence evidence);</span></span>|  
|<span data-ttu-id="d9119-175">Załaduj (arkusza stylów IXPathNavigable);</span><span class="sxs-lookup"><span data-stu-id="d9119-175">Load(IXPathNavigable stylesheet);</span></span><br /><br /> <span data-ttu-id="d9119-176">Obciążenia (IXPathNavigable arkusza stylów, rozpoznawania element XmlResolver);</span><span class="sxs-lookup"><span data-stu-id="d9119-176">Load(IXPathNavigable stylesheet, XmlResolver resolver);</span></span>|<span data-ttu-id="d9119-177">Obciążenia (IXPathNavigable arkusza stylów, element XmlResolver programu rozpoznawania nazw, dowód dowód);</span><span class="sxs-lookup"><span data-stu-id="d9119-177">Load(IXPathNavigable stylesheet, XmlResolver resolver, Evidence evidence);</span></span>|  
|<span data-ttu-id="d9119-178">Załaduj (arkusza stylów XmlReader);</span><span class="sxs-lookup"><span data-stu-id="d9119-178">Load(XmlReader stylesheet);</span></span><br /><br /> <span data-ttu-id="d9119-179">Obciążenia (element XmlReader arkusza stylów, rozpoznawania element XmlResolver);</span><span class="sxs-lookup"><span data-stu-id="d9119-179">Load(XmlReader stylesheet, XmlResolver resolver);</span></span>|<span data-ttu-id="d9119-180">Obciążenia (element XmlReader arkusza stylów, element XmlResolver programu rozpoznawania nazw, dowód dowód);</span><span class="sxs-lookup"><span data-stu-id="d9119-180">Load(XmlReader stylesheet, XmlResolver resolver, Evidence evidence);</span></span>|  
  
 <span data-ttu-id="d9119-181">W poniższej tabeli przedstawiono metody przestarzałe i nowe <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="d9119-181">The following table shows the obsolete and new methods for the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span> <span data-ttu-id="d9119-182">Nowe metody przyjmują <xref:System.Xml.XmlResolver> obiektu.</span><span class="sxs-lookup"><span data-stu-id="d9119-182">The new methods take an <xref:System.Xml.XmlResolver> object.</span></span>  
  
|<span data-ttu-id="d9119-183">.NET Framework w wersji 1.0 Przekształcanie metody przestarzałe</span><span class="sxs-lookup"><span data-stu-id="d9119-183">Obsolete .NET Framework version 1.0 Transform Methods</span></span>|<span data-ttu-id="d9119-184">Wersja programu .NET Framework zastąpienie Przekształcanie metody 1.1</span><span class="sxs-lookup"><span data-stu-id="d9119-184">Replacement .NET Framework version Transform 1.1 Methods</span></span>|  
|-----------------------------------------------------------|--------------------------------------------------------------|  
|<span data-ttu-id="d9119-185">Element XmlReader Transform(XPathNavigator input, XsltArgumentList args)</span><span class="sxs-lookup"><span data-stu-id="d9119-185">XmlReader Transform(XPathNavigator input, XsltArgumentList args)</span></span>|<span data-ttu-id="d9119-186">Element XmlReader Transform(XPathNavigator input, XsltArgumentList args, XmlResolver resolver)</span><span class="sxs-lookup"><span data-stu-id="d9119-186">XmlReader Transform(XPathNavigator  input, XsltArgumentList args, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="d9119-187">Element XmlReader Transform(IXPathNavigable input, XsltArgumentList args)</span><span class="sxs-lookup"><span data-stu-id="d9119-187">XmlReader Transform(IXPathNavigable input, XsltArgumentList args)</span></span>|<span data-ttu-id="d9119-188">Element XmlReader Transform(IXPathNavigable input, XsltArgumentList args, XmlResolver resolver)</span><span class="sxs-lookup"><span data-stu-id="d9119-188">XmlReader Transform(IXPathNavigable input, XsltArgumentList args, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="d9119-189">Void Przekształcanie (dane wejściowe klasy XPathNavigator, argumenty XsltArgumentList, dane wyjściowe XmlWriter)</span><span class="sxs-lookup"><span data-stu-id="d9119-189">Void Transform(XPathNavigator input, XsltArgumentList args, XmlWriter output)</span></span>|<span data-ttu-id="d9119-190">Void Przekształcanie (dane wejściowe klasy XPathNavigator XsltArgumentList argumenty, dane wyjściowe XmlWriter, element XmlResolver programu rozpoznawania nazw)</span><span class="sxs-lookup"><span data-stu-id="d9119-190">Void Transform(XPathNavigator input, XsltArgumentList args, XmlWriter output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="d9119-191">Void Przekształcanie (dane wejściowe IXPathNavigable, argumenty XsltArgumentList, XmlWriter dane wyjściowe)</span><span class="sxs-lookup"><span data-stu-id="d9119-191">Void Transform(IXPathNavigable input, XsltArgumentList args, XmlWriter output)</span></span>|<span data-ttu-id="d9119-192">Void Przekształcanie (dane wejściowe IXpathNavigable XsltArgumentList argumenty, XmlWriter dane wyjściowe, element XmlResolver programu rozpoznawania nazw)</span><span class="sxs-lookup"><span data-stu-id="d9119-192">Void Transform(IXpathNavigable input, XsltArgumentList args, XmlWriter output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="d9119-193">Void Przekształcanie (dane wejściowe klasy XPathNavigator, argumenty XsltArgumentList, dane wyjściowe TextWriter)</span><span class="sxs-lookup"><span data-stu-id="d9119-193">Void Transform(XPathNavigator input, XsltArgumentList args, TextWriter output)</span></span>|<span data-ttu-id="d9119-194">Void Przekształcanie (dane wejściowe klasy XPathNavigator XsltArgumentList argumenty, dane wyjściowe TextWriter, element XmlResolver programu rozpoznawania nazw)</span><span class="sxs-lookup"><span data-stu-id="d9119-194">Void Transform(XPathNavigator input, XsltArgumentList args, TextWriter output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="d9119-195">Void Przekształcanie (IXPathNavigable danych wejściowych, argumenty XsltArgumentList, dane wyjściowe TextWriter)</span><span class="sxs-lookup"><span data-stu-id="d9119-195">Void Transform(IXPathNavigable input, XsltArgumentList args, TextWriter output)</span></span>|<span data-ttu-id="d9119-196">Void Przekształcanie (IXPathNavigable danych wejściowych, argumenty XsltArgumentList, dane wyjściowe TextWriter, element XmlResolver programu rozpoznawania nazw)</span><span class="sxs-lookup"><span data-stu-id="d9119-196">Void Transform(IXPathNavigable input, XsltArgumentList args, TextWriter output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="d9119-197">Void Przekształcanie (dane wejściowe klasy XPathNavigator, argumenty XsltArgumentList, dane wyjściowe Stream)</span><span class="sxs-lookup"><span data-stu-id="d9119-197">Void Transform(XPathNavigator input, XsltArgumentList args, Stream output)</span></span>|<span data-ttu-id="d9119-198">Void Przekształcanie (dane wejściowe klasy XPathNavigator XsltArgumentList argumenty, dane wyjściowe Stream, element XmlResolver programu rozpoznawania nazw)</span><span class="sxs-lookup"><span data-stu-id="d9119-198">Void Transform(XPathNavigator input, XsltArgumentList args, Stream output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="d9119-199">Void Przekształcanie (IXPathNavigable danych wejściowych, argumenty XsltArgumentList, dane wyjściowe Stream)</span><span class="sxs-lookup"><span data-stu-id="d9119-199">Void Transform(IXPathNavigable input, XsltArgumentList args, Stream output)</span></span>|<span data-ttu-id="d9119-200">Void Przekształcanie (dane wejściowe IXPathNavigable XsltArgumentList argumenty, Stream dane wyjściowe, element XmlResolver programu rozpoznawania nazw)</span><span class="sxs-lookup"><span data-stu-id="d9119-200">Void Transform(IXPathNavigable input, XsltArgumentList args, Stream output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="d9119-201">Void Przekształcanie (ciąg wejściowy, ciąg dane wyjściowe);</span><span class="sxs-lookup"><span data-stu-id="d9119-201">Void Transform(String input, String output);</span></span>|<span data-ttu-id="d9119-202">Void Przekształcanie (ciąg wejściowy, ciąg danych wyjściowych element XmlResolver programu rozpoznawania nazw);</span><span class="sxs-lookup"><span data-stu-id="d9119-202">Void Transform(String input, String output, XmlResolver resolver);</span></span>|  
  
 <span data-ttu-id="d9119-203"><xref:System.Xml.Xsl.XslTransform.XmlResolver%2A?displayProperty=nameWithType> Właściwość jest przestarzała w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] wersji 1.1.</span><span class="sxs-lookup"><span data-stu-id="d9119-203">The <xref:System.Xml.Xsl.XslTransform.XmlResolver%2A?displayProperty=nameWithType> property is obsolete in [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] version 1.1.</span></span> <span data-ttu-id="d9119-204">Zamiast tego należy użyć nowego <xref:System.Xml.Xsl.XslTransform.Transform%2A> przeciążeń przybierają które <xref:System.Xml.XmlResolver> obiektu.</span><span class="sxs-lookup"><span data-stu-id="d9119-204">Instead, use the new <xref:System.Xml.Xsl.XslTransform.Transform%2A> overloads which take an <xref:System.Xml.XmlResolver> object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9119-205">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d9119-205">See also</span></span>

- <xref:System.Xml.Xsl.XslTransform>  
- [<span data-ttu-id="d9119-206">Przekształcenia XSLT przy użyciu klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="d9119-206">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
- [<span data-ttu-id="d9119-207">Klasa XPathNavigator w przekształceniach</span><span class="sxs-lookup"><span data-stu-id="d9119-207">XPathNavigator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
- [<span data-ttu-id="d9119-208">Klasa XPathNodeIterator w przekształceniach</span><span class="sxs-lookup"><span data-stu-id="d9119-208">XPathNodeIterator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
- [<span data-ttu-id="d9119-209">Dane wejściowe obiektu XPathDocument klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="d9119-209">XPathDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
- [<span data-ttu-id="d9119-210">Dane wejściowe obiektu XmlDataDocument klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="d9119-210">XmlDataDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)  
- [<span data-ttu-id="d9119-211">Dane wejściowe obiektu XmlDocument klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="d9119-211">XmlDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
