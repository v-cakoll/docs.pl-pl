---
title: Klasa XslTransform implementuje procesorze XSLT
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 88373fe2-4a6b-44f9-8a62-8a3e348e3a46
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 167cd81ecbc25ca243e3b4a7a6aa7327679528e0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="xsltransform-class-implements-the-xslt-processor"></a><span data-ttu-id="651e2-102">Klasa XslTransform implementuje procesorze XSLT</span><span class="sxs-lookup"><span data-stu-id="651e2-102">XslTransform Class Implements the XSLT Processor</span></span>
> [!NOTE]
>  <span data-ttu-id="651e2-103"><xref:System.Xml.Xsl.XslTransform> Klasa jest przestarzała w [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="651e2-103">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="651e2-104">Może wykonywać rozszerzalny język arkusza stylów dla transformacji przekształcenia XSLT () przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy.</span><span class="sxs-lookup"><span data-stu-id="651e2-104">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="651e2-105">Zobacz [za pomocą klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) i [migracji z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="651e2-105">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="651e2-106"><xref:System.Xml.Xsl.XslTransform> Klasa jest procesorze XSLT Implementowanie zalecenie transformacji XSL (XSLT) w wersji 1.0.</span><span class="sxs-lookup"><span data-stu-id="651e2-106">The <xref:System.Xml.Xsl.XslTransform> class is an XSLT processor implementing the XSL Transformations (XSLT) Version 1.0 recommendation.</span></span> <span data-ttu-id="651e2-107"><xref:System.Xml.Xsl.XslTransform.Load%2A> Metody lokalizuje i odczytuje arkusze stylów i <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody przekształca dokumentu danego źródła.</span><span class="sxs-lookup"><span data-stu-id="651e2-107">The <xref:System.Xml.Xsl.XslTransform.Load%2A> method locates and reads style sheets, and the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method transforms the given source document.</span></span> <span data-ttu-id="651e2-108">Dowolnego magazynu, który implementuje <xref:System.Xml.XPath.IXPathNavigable> interfejsu może być używany jako dokument źródłowy dla <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="651e2-108">Any store that implements the <xref:System.Xml.XPath.IXPathNavigable> interface can be used as the source document for the <xref:System.Xml.Xsl.XslTransform>.</span></span> <span data-ttu-id="651e2-109">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Implementuje obecnie <xref:System.Xml.XPath.IXPathNavigable> interfejs w <xref:System.Xml.XmlDocument>, <xref:System.Xml.XmlDataDocument>i <xref:System.Xml.XPath.XPathDocument>, więc wszystkie te mogą być używane jako źródło danych wejściowych dokumentu do przekształcenia.</span><span class="sxs-lookup"><span data-stu-id="651e2-109">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] currently implements the <xref:System.Xml.XPath.IXPathNavigable> interface on the <xref:System.Xml.XmlDocument>, the <xref:System.Xml.XmlDataDocument>, and the <xref:System.Xml.XPath.XPathDocument>, so all of these can be used as the input source document to a transformation.</span></span>  
  
 <span data-ttu-id="651e2-110"><xref:System.Xml.Xsl.XslTransform> Obiektu w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] obsługuje tylko specyfikację XSLT 1.0 zdefiniowane z następujących nazw:</span><span class="sxs-lookup"><span data-stu-id="651e2-110">The <xref:System.Xml.Xsl.XslTransform> object in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] only supports the XSLT 1.0 specification, defined with the following namespace:</span></span>  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">    
```  
  
 <span data-ttu-id="651e2-111">Arkusz stylów mogą być ładowane, przy użyciu <xref:System.Xml.Xsl.XslTransform.Load%2A> metody z jednego z następujących klas:</span><span class="sxs-lookup"><span data-stu-id="651e2-111">The style sheet can be loaded, using the <xref:System.Xml.Xsl.XslTransform.Load%2A> method, from one of the following classes:</span></span>  
  
-   <span data-ttu-id="651e2-112">Element XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="651e2-112">XPathNavigator</span></span>  
  
-   <span data-ttu-id="651e2-113">Element XmlReader</span><span class="sxs-lookup"><span data-stu-id="651e2-113">XmlReader</span></span>  
  
-   <span data-ttu-id="651e2-114">Ciąg reprezentujący adres URL</span><span class="sxs-lookup"><span data-stu-id="651e2-114">A string representing a URL</span></span>  
  
 <span data-ttu-id="651e2-115">Istnieje inny <xref:System.Xml.Xsl.XslTransform.Load%2A> metody dla każdego z powyższych klas wejściowego.</span><span class="sxs-lookup"><span data-stu-id="651e2-115">There is a different <xref:System.Xml.Xsl.XslTransform.Load%2A> method for each of the above input classes.</span></span> <span data-ttu-id="651e2-116">W przypadku niektórych metod zająć w połączeniu z jednej z tych klas i <xref:System.Xml.XmlResolver> klasy jako argumenty.</span><span class="sxs-lookup"><span data-stu-id="651e2-116">Some methods take in a combination of one of these classes and the <xref:System.Xml.XmlResolver> class as arguments.</span></span> <span data-ttu-id="651e2-117"><xref:System.Xml.XmlResolver> Lokalizuje zasoby odwołuje się `<xsl:import>` lub `<xsl:include>` znaleziono w arkuszu stylów.</span><span class="sxs-lookup"><span data-stu-id="651e2-117">The <xref:System.Xml.XmlResolver> locates resources referenced by `<xsl:import>` or `<xsl:include>` found in the style sheet.</span></span> <span data-ttu-id="651e2-118">Następujące metody przyjmują ciąg, <xref:System.Xml.XmlReader>, lub <xref:System.Xml.XPath.XPathNavigator> jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="651e2-118">The following methods take a string, <xref:System.Xml.XmlReader>, or <xref:System.Xml.XPath.XPathNavigator> as input.</span></span>  
  
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
  
 <span data-ttu-id="651e2-119">Większość <xref:System.Xml.Xsl.XslTransform.Load%2A> metod przedstawionych powyżej podjęcia <xref:System.Xml.XmlResolver> jako parametr.</span><span class="sxs-lookup"><span data-stu-id="651e2-119">Most of the <xref:System.Xml.Xsl.XslTransform.Load%2A> methods shown above take an <xref:System.Xml.XmlResolver> as a parameter.</span></span> <span data-ttu-id="651e2-120"><xref:System.Xml.XmlResolver> Jest używana do ładowania arkusza stylów i wszystkie arkusze stylów w XSL: Import i xsl: obejmują elementy.</span><span class="sxs-lookup"><span data-stu-id="651e2-120">The <xref:System.Xml.XmlResolver> is used to load the style sheet and any style sheet(s) referenced in xsl:import and xsl:include elements.</span></span>  
  
 <span data-ttu-id="651e2-121">Większość <xref:System.Xml.Xsl.XslTransform.Load%2A> metody również wziąć dowód jako parametr.</span><span class="sxs-lookup"><span data-stu-id="651e2-121">Most of the <xref:System.Xml.Xsl.XslTransform.Load%2A> methods also take evidence as a parameter.</span></span> <span data-ttu-id="651e2-122">Parametr dowód jest <xref:System.Security.Policy.Evidence> skojarzonego z arkusza stylów.</span><span class="sxs-lookup"><span data-stu-id="651e2-122">The evidence parameter is the <xref:System.Security.Policy.Evidence> that is associated with the style sheet.</span></span> <span data-ttu-id="651e2-123">Poziom zabezpieczeń arkusza stylów wpływa na poziom zabezpieczeń kolejnych odwołuje się on do zasobów, takich jak skrypt w nim żadnego `document()` wykorzystuje funkcje i obiekty rozszerzenia używane przez <xref:System.Xml.Xsl.XsltArgumentList>.</span><span class="sxs-lookup"><span data-stu-id="651e2-123">The security level of the style sheet affects the security level of any subsequent resources it references, such as the script it contains, any `document()` functions it uses, and any extension objects used by the <xref:System.Xml.Xsl.XsltArgumentList>.</span></span>  
  
 <span data-ttu-id="651e2-124">Jeśli arkusz stylów został załadowany przy użyciu <xref:System.Xml.Xsl.XslTransform.Load%2A> podano metodę, która zawiera parametr adresu URL i oznak, dowód arkusza stylów jest obliczany przez połączenie podany adres URL z lokacji i strefy.</span><span class="sxs-lookup"><span data-stu-id="651e2-124">If the style sheet is loaded using a <xref:System.Xml.Xsl.XslTransform.Load%2A> method that contains a URL parameter and no evidence is provided, the evidence of the style sheet is calculated by combining the given URL with its site and zone.</span></span>  
  
 <span data-ttu-id="651e2-125">Jeśli podano Brak identyfikatora URI lub dowód, następnie dowodu zestawu dla arkusza stylów jest w pełni zaufany.</span><span class="sxs-lookup"><span data-stu-id="651e2-125">If no URI or evidence is provided, then the evidence set for the style sheet is fully trusted.</span></span> <span data-ttu-id="651e2-126">Nie załadować arkusze stylów ze źródeł niezaufanych lub dodać rozszerzenie niezaufanych obiektów do <xref:System.Xml.Xsl.XsltArgumentList>.</span><span class="sxs-lookup"><span data-stu-id="651e2-126">Do not load style sheets from untrusted sources, or add untrusted extension objects into the <xref:System.Xml.Xsl.XsltArgumentList>.</span></span>  
  
 <span data-ttu-id="651e2-127">Aby uzyskać więcej informacji na temat poziomów zabezpieczeń i dowód i jak wpływa na wykonywanie skryptów, zobacz [XSLT skryptów przy użyciu arkusza stylów \<msxsl:script >](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md).</span><span class="sxs-lookup"><span data-stu-id="651e2-127">For more information about security levels and evidence and how it affects scripting, see [XSLT Stylesheet Scripting Using \<msxsl:script>](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md).</span></span> <span data-ttu-id="651e2-128">Aby informacji na temat poziomów zabezpieczeń i dowód i jak wpływa na obiekty rozszerzenia, zobacz [XsltArgumentList parametry arkusza stylów i obiektów rozszerzenia](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md).</span><span class="sxs-lookup"><span data-stu-id="651e2-128">For information about security levels and evidence and how it affects extension objects, see [XsltArgumentList for Style Sheet Parameters and Extension Objects](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md).</span></span>  
  
 <span data-ttu-id="651e2-129">Informacje dotyczące poziomów zabezpieczeń i dowód i jak wpływa na `document()` funkcji, zobacz [Rozpoznawanie zewnętrznych arkuszy stylów XSLT i dokumentów](../../../../docs/standard/data/xml/resolving-external-xslt-style-sheets-and-documents.md).</span><span class="sxs-lookup"><span data-stu-id="651e2-129">For information about security levels and evidence and how it affects the `document()` function, see [Resolving External XSLT Style Sheets and Documents](../../../../docs/standard/data/xml/resolving-external-xslt-style-sheets-and-documents.md).</span></span>  
  
 <span data-ttu-id="651e2-130">Arkusz stylów można podać z liczbą parametrów wejściowych.</span><span class="sxs-lookup"><span data-stu-id="651e2-130">A style sheet can be supplied with a number of input parameters.</span></span> <span data-ttu-id="651e2-131">Arkusz stylów można również wywołać funkcji rozszerzenia obiektów.</span><span class="sxs-lookup"><span data-stu-id="651e2-131">The style sheet can also call functions on extension objects.</span></span> <span data-ttu-id="651e2-132">Podano zarówno parametrów, jak i obiektów rozszerzeń przy użyciu arkusza stylów <xref:System.Xml.Xsl.XsltArgumentList> klasy.</span><span class="sxs-lookup"><span data-stu-id="651e2-132">Both parameters and extension objects are supplied to the style sheet using the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span> <span data-ttu-id="651e2-133">Aby uzyskać więcej informacji na temat <xref:System.Xml.Xsl.XsltArgumentList>, zobacz <xref:System.Xml.Xsl.XsltArgumentList>.</span><span class="sxs-lookup"><span data-stu-id="651e2-133">For more information about the <xref:System.Xml.Xsl.XsltArgumentList>, see <xref:System.Xml.Xsl.XsltArgumentList>.</span></span>  
  
## <a name="recommended-secure-use-of-xsltransform-class"></a><span data-ttu-id="651e2-134">Zalecane użycie bezpiecznego XslTransform klasy</span><span class="sxs-lookup"><span data-stu-id="651e2-134">Recommended Secure Use of XslTransform Class</span></span>  
 <span data-ttu-id="651e2-135">Uprawnienia zabezpieczeń arkusza stylów zależą od dowody dostarczone.</span><span class="sxs-lookup"><span data-stu-id="651e2-135">The security privileges of the style sheet depend on the evidence provided.</span></span> <span data-ttu-id="651e2-136">Poniższa tabela zawiera podsumowanie Lokalizacja arkusza stylów oraz zawiera wyjaśnienie, jakiego rodzaju dowód umożliwiają.</span><span class="sxs-lookup"><span data-stu-id="651e2-136">The following table summarizes the location of the style sheet and gives an explanation of what type of evidence to give.</span></span>  
  
-   <span data-ttu-id="651e2-137">Arkusz stylów XSLT nie ma zewnętrznych odwołań lub arkusz stylów, z którym ufasz, że określona ścieżka bazowa kodu.</span><span class="sxs-lookup"><span data-stu-id="651e2-137">The XSLT style sheet has no external references, or the style sheet comes from a code base that you trust.</span></span>  
  
    -   <span data-ttu-id="651e2-138">Podaj dowód z Twojego zestawu:</span><span class="sxs-lookup"><span data-stu-id="651e2-138">Provide the evidence from your assembly:</span></span>  
  
         `Dim xslt = New XslTransform() xslt.Load(stylesheet, resolver, Me.GetType().Assembly.Evidence)`  
  
         `XsltTransform xslt = new XslTransform();  xslt.Load(stylesheet, resolver, this.GetType().Assembly.Evidence);`  
  
-   <span data-ttu-id="651e2-139">Arkusz stylów XSLT pochodzą ze źródła zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="651e2-139">The XSLT style sheet comes from an outside source.</span></span> <span data-ttu-id="651e2-140">Jest on znany pochodzenie źródła i jest możliwe do zweryfikowania identyfikatorem URI.</span><span class="sxs-lookup"><span data-stu-id="651e2-140">The origin of the source is known and there is a verifiable URI.</span></span>  
  
    -   <span data-ttu-id="651e2-141">Utwórz dowód przy użyciu identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="651e2-141">Create evidence using the URI.</span></span>  
  
         `Dim xslt As New XslTransform() Dim ev As Evidence = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri) xslt.Load(stylesheet, resolver, evidence)`  
  
         `XslTransform xslt = new XslTransform(); Evidence ev = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri); xslt.Load(stylesheet, resolver, evidence);`  
  
-   <span data-ttu-id="651e2-142">Arkusz stylów XSLT pochodzą ze źródła zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="651e2-142">The XSLT style sheet comes from an outside source.</span></span> <span data-ttu-id="651e2-143">Pochodzenie źródła nie jest znany.</span><span class="sxs-lookup"><span data-stu-id="651e2-143">The origin of the source is not known.</span></span>  
  
    -   <span data-ttu-id="651e2-144">Ustaw dowód `null`.</span><span class="sxs-lookup"><span data-stu-id="651e2-144">Set evidence to `null`.</span></span> <span data-ttu-id="651e2-145">Bloki skryptu nie są przetwarzane, XSLT `document()` funkcja nie jest obsługiwana i obiekty uprzywilejowanych rozszerzenia są niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="651e2-145">Script blocks are not processed, the XSLT `document()` function is not supported, and privileged extension objects are disallowed.</span></span>  
  
         <span data-ttu-id="651e2-146">Ponadto można również ustawić `resolver` parametr `null` gwarantuje to, że `xsl:import` i `xsl:include` elementy nie zostały przetworzone.</span><span class="sxs-lookup"><span data-stu-id="651e2-146">Additionally, you can also set the `resolver` parameter to `null` This ensures that `xsl:import` and `xsl:include` elements are not processed.</span></span>  
  
-   <span data-ttu-id="651e2-147">Arkusz stylów XSLT pochodzą ze źródła zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="651e2-147">The XSLT style sheet comes from an outside source.</span></span> <span data-ttu-id="651e2-148">Pochodzenie źródła nie jest znany, ale wymagają obsługi skryptów.</span><span class="sxs-lookup"><span data-stu-id="651e2-148">The origin of the source is not known, but you require script support.</span></span>  
  
    -   <span data-ttu-id="651e2-149">Żądanie dowodu wywołujący.</span><span class="sxs-lookup"><span data-stu-id="651e2-149">Request evidence from the caller.</span></span>  
  
## <a name="transformation-of-xml-data"></a><span data-ttu-id="651e2-150">Przekształcenia danych XML</span><span class="sxs-lookup"><span data-stu-id="651e2-150">Transformation of XML Data</span></span>  
 <span data-ttu-id="651e2-151">Po załadowaniu arkusz stylów transformacja rozpoczyna się przez wywoływanie jednej z <xref:System.Xml.Xsl.XslTransform.Transform%2A> metod i dostarczenie dokument źródło danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="651e2-151">Once a style sheet is loaded, the transformation starts by calling one of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> methods and supplying an input source document.</span></span> <span data-ttu-id="651e2-152"><xref:System.Xml.Xsl.XslTransform.Transform%2A> Metody jest przeciążona zapewnienie różnych przekształcania danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="651e2-152">The <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is overloaded to provide different transformation outputs.</span></span> <span data-ttu-id="651e2-153">Transformacja może spowodować następujące formaty danych wyjściowych:</span><span class="sxs-lookup"><span data-stu-id="651e2-153">The transformation can result in the following output formats:</span></span>  
  
-   <xref:System.Xml.XmlReader>  
  
-   <xref:System.Xml.XmlWriter>  
  
-   <xref:System.IO.TextWriter>  
  
-   <xref:System.IO.Stream>  
  
-   <span data-ttu-id="651e2-154">Ciąg adres URL pliku</span><span class="sxs-lookup"><span data-stu-id="651e2-154">String URL of file</span></span>  
  
 <span data-ttu-id="651e2-155">Udostępnia tego ostatniego formatu ciągu adresu URL, dla scenariusza często używane w Przekształcanie dokument wejściowy znajduje się w adresie URL i zapisywanie dokumentu do adresu URL danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="651e2-155">This last format, the string URL, provides for a commonly used scenario in transforming an input document located in a URL and writing the document to the output URL.</span></span> <span data-ttu-id="651e2-156">To <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda jest metodą wygody do ładowania dokumentu XML z pliku, przekształcenie XSLT i zapisuje dane wyjściowe do pliku.</span><span class="sxs-lookup"><span data-stu-id="651e2-156">This <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is a convenience method to load an XML document from a file, perform the XSLT transformation, and write the output to a file.</span></span> <span data-ttu-id="651e2-157">Zapobiega konieczności tworzenia i załadować dokument źródło danych wejściowych, a następnie zapisać do strumienia pliku.</span><span class="sxs-lookup"><span data-stu-id="651e2-157">This prevents you from having to create and load the input source document, and then write to a file stream.</span></span> <span data-ttu-id="651e2-158">Poniższy przykład kodu pokazuje to <xref:System.Xml.Xsl.XslTransform.Transform%2A> metodę przy użyciu adresu URL ciąg jako dane wejściowe i wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="651e2-158">The following code sample shows this use of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method using the string URL as input and output:</span></span>  
  
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
  
## <a name="transforming-a-section-of-an-xml-document"></a><span data-ttu-id="651e2-159">Przekształcanie części dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="651e2-159">Transforming a Section of an XML Document</span></span>  
 <span data-ttu-id="651e2-160">Przekształcenia mają zastosowanie do dokumentu jako całość.</span><span class="sxs-lookup"><span data-stu-id="651e2-160">Transformations apply to the document as a whole.</span></span> <span data-ttu-id="651e2-161">Innymi słowy w przypadku przekazania w węźle innym niż węzeł główny dokumentu, to nie zapobiega proces przekształcania podczas uzyskiwania dostępu do wszystkich węzłów w załadowanego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="651e2-161">In other words, if you pass in a node other than the document root node, this does not prevent the transformation process from accessing all nodes in the loaded document.</span></span> <span data-ttu-id="651e2-162">Aby przekształcić wynikowego fragmentu drzewa, musisz utworzyć <xref:System.Xml.XmlDocument> zawierający tylko drzewa wynik fragmentu i przekazać, który <xref:System.Xml.XmlDocument> do <xref:System.Xml.Xsl.XslTransform.Transform%2A> — metoda.</span><span class="sxs-lookup"><span data-stu-id="651e2-162">To transform a result tree fragment, you must create an <xref:System.Xml.XmlDocument> containing just the result tree fragment and pass that <xref:System.Xml.XmlDocument> to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span> <span data-ttu-id="651e2-163">Poniższy przykład wykonuje transformację na wynikowego fragmentu drzewa.</span><span class="sxs-lookup"><span data-stu-id="651e2-163">The following example performs a transformation on a result tree fragment.</span></span>  
  
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
  
 <span data-ttu-id="651e2-164">W przykładzie użyto library.xml i print_root.xsl pliki jako dane wejściowe i wyświetla następujące polecenie, aby konsoli.</span><span class="sxs-lookup"><span data-stu-id="651e2-164">The example uses the library.xml and print_root.xsl files as input and outputs the following to the console.</span></span>  
  
```  
Passing <book genre="novel" ISBN="1-861001-57-5"><title>Pride And Prejudice</title></book> to print_root.xsl   
Root node is book.  
```  
  
 <span data-ttu-id="651e2-165">Library.XML</span><span class="sxs-lookup"><span data-stu-id="651e2-165">library.xml</span></span>  
  
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
  
 <span data-ttu-id="651e2-166">print_root.xsl</span><span class="sxs-lookup"><span data-stu-id="651e2-166">print_root.xsl</span></span>  
  
```xml  
<stylesheet version="1.0" xmlns="http://www.w3.org/1999/XSL/Transform" >  
  <output method="text" />   
  <template match="/">  
     Root node is  <value-of select="local-name(//*[position() = 1])" />   
  </template>  
</stylesheet>  
```  
  
## <a name="migration-of-xslt-from-net-framework-version-10-to-net-framework-version-11"></a><span data-ttu-id="651e2-167">Migracja pliku XSLT z .NET Framework w wersji 1.0 .NET Framework w wersji 1.1</span><span class="sxs-lookup"><span data-stu-id="651e2-167">Migration of XSLT from .NET Framework version 1.0 to .NET Framework version 1.1</span></span>  
 <span data-ttu-id="651e2-168">W poniższej tabeli przedstawiono przestarzałe [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] metod w wersji 1.0 i nowych [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] metody wersji 1.1 <xref:System.Xml.Xsl.XslTransform.Load%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="651e2-168">The following table shows the obsolete [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] version 1.0 methods and new [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] version 1.1 methods for the <xref:System.Xml.Xsl.XslTransform.Load%2A> method.</span></span> <span data-ttu-id="651e2-169">Nowych metod pozwalają ograniczyć uprawnienia arkusza stylów, określając dowód.</span><span class="sxs-lookup"><span data-stu-id="651e2-169">The new methods enable you to limit the permissions of the style sheet by specifying evidence.</span></span>  
  
|<span data-ttu-id="651e2-170">Przestarzałe metody obciążenia programu .NET Framework w wersji 1.0</span><span class="sxs-lookup"><span data-stu-id="651e2-170">Obsolete .NET Framework version 1.0 Load Methods</span></span>|<span data-ttu-id="651e2-171">Zastąpienie środowiska .NET Framework w wersji 1.1 obciążenia metody</span><span class="sxs-lookup"><span data-stu-id="651e2-171">Replacement .NET Framework version 1.1 Load Methods</span></span>|  
|------------------------------------------------------|---------------------------------------------------------|  
|<span data-ttu-id="651e2-172">Obciążenia (dane wejściowe Element XPathNavigator);</span><span class="sxs-lookup"><span data-stu-id="651e2-172">Load(XPathNavigator input);</span></span><br /><br /> <span data-ttu-id="651e2-173">Obciążenia (Element XPathNavigator wejściowych, element XmlResolver rozpoznawania nazw);</span><span class="sxs-lookup"><span data-stu-id="651e2-173">Load(XPathNavigator input, XmlResolver resolver);</span></span>|<span data-ttu-id="651e2-174">Obciążenia (arkusza stylów Element XPathNavigator, element XmlResolver programu rozpoznawania nazw, dowód dowód);</span><span class="sxs-lookup"><span data-stu-id="651e2-174">Load(XPathNavigator stylesheet, XmlResolver resolver, Evidence evidence);</span></span>|  
|<span data-ttu-id="651e2-175">Obciążenia (arkusza stylów IXPathNavigable);</span><span class="sxs-lookup"><span data-stu-id="651e2-175">Load(IXPathNavigable stylesheet);</span></span><br /><br /> <span data-ttu-id="651e2-176">Obciążenia (IXPathNavigable arkusza stylów, element XmlResolver rozpoznawania);</span><span class="sxs-lookup"><span data-stu-id="651e2-176">Load(IXPathNavigable stylesheet, XmlResolver resolver);</span></span>|<span data-ttu-id="651e2-177">Obciążenia (IXPathNavigable arkusza stylów, element XmlResolver programu rozpoznawania nazw, dowód dowód);</span><span class="sxs-lookup"><span data-stu-id="651e2-177">Load(IXPathNavigable stylesheet, XmlResolver resolver, Evidence evidence);</span></span>|  
|<span data-ttu-id="651e2-178">Obciążenia (arkusza stylów XmlReader);</span><span class="sxs-lookup"><span data-stu-id="651e2-178">Load(XmlReader stylesheet);</span></span><br /><br /> <span data-ttu-id="651e2-179">Obciążenia (XmlReader arkusza stylów, element XmlResolver rozpoznawania);</span><span class="sxs-lookup"><span data-stu-id="651e2-179">Load(XmlReader stylesheet, XmlResolver resolver);</span></span>|<span data-ttu-id="651e2-180">Obciążenia (XmlReader arkusza stylów, element XmlResolver programu rozpoznawania nazw, dowód dowód);</span><span class="sxs-lookup"><span data-stu-id="651e2-180">Load(XmlReader stylesheet, XmlResolver resolver, Evidence evidence);</span></span>|  
  
 <span data-ttu-id="651e2-181">W poniższej tabeli przedstawiono metody przestarzałe i nowych <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="651e2-181">The following table shows the obsolete and new methods for the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span> <span data-ttu-id="651e2-182">Nowe metody przyjmują <xref:System.Xml.XmlResolver> obiektu.</span><span class="sxs-lookup"><span data-stu-id="651e2-182">The new methods take an <xref:System.Xml.XmlResolver> object.</span></span>  
  
|<span data-ttu-id="651e2-183">.NET Framework w wersji 1.0 przekształcenie metody przestarzałe</span><span class="sxs-lookup"><span data-stu-id="651e2-183">Obsolete .NET Framework version 1.0 Transform Methods</span></span>|<span data-ttu-id="651e2-184">Wersja programu .NET Framework zastąpienie metody przekształcania 1.1</span><span class="sxs-lookup"><span data-stu-id="651e2-184">Replacement .NET Framework version Transform 1.1 Methods</span></span>|  
|-----------------------------------------------------------|--------------------------------------------------------------|  
|<span data-ttu-id="651e2-185">Element XmlReader Transform(XPathNavigator input, XsltArgumentList args)</span><span class="sxs-lookup"><span data-stu-id="651e2-185">XmlReader Transform(XPathNavigator input, XsltArgumentList args)</span></span>|<span data-ttu-id="651e2-186">Element XmlReader Transform(XPathNavigator input, XsltArgumentList args, XmlResolver resolver)</span><span class="sxs-lookup"><span data-stu-id="651e2-186">XmlReader Transform(XPathNavigator  input, XsltArgumentList args, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="651e2-187">Element XmlReader Transform(IXPathNavigable input, XsltArgumentList args)</span><span class="sxs-lookup"><span data-stu-id="651e2-187">XmlReader Transform(IXPathNavigable input, XsltArgumentList args)</span></span>|<span data-ttu-id="651e2-188">Element XmlReader Transform(IXPathNavigable input, XsltArgumentList args, XmlResolver resolver)</span><span class="sxs-lookup"><span data-stu-id="651e2-188">XmlReader Transform(IXPathNavigable input, XsltArgumentList args, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="651e2-189">Przekształć void (dane wejściowe Element XPathNavigator, XsltArgumentList argumentów, dane wyjściowe XmlWriter)</span><span class="sxs-lookup"><span data-stu-id="651e2-189">Void Transform(XPathNavigator input, XsltArgumentList args, XmlWriter output)</span></span>|<span data-ttu-id="651e2-190">Przekształć void (wejściowy Element XPathNavigator, XsltArgumentList argumentów, dane wyjściowe XmlWriter, element XmlResolver programu rozpoznawania nazw)</span><span class="sxs-lookup"><span data-stu-id="651e2-190">Void Transform(XPathNavigator input, XsltArgumentList args, XmlWriter output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="651e2-191">Przekształć void (dane wejściowe IXPathNavigable, XsltArgumentList argumentów, dane wyjściowe XmlWriter)</span><span class="sxs-lookup"><span data-stu-id="651e2-191">Void Transform(IXPathNavigable input, XsltArgumentList args, XmlWriter output)</span></span>|<span data-ttu-id="651e2-192">Przekształć void (IXpathNavigable danych wejściowych, XsltArgumentList argumentów, dane wyjściowe XmlWriter, element XmlResolver programu rozpoznawania nazw)</span><span class="sxs-lookup"><span data-stu-id="651e2-192">Void Transform(IXpathNavigable input, XsltArgumentList args, XmlWriter output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="651e2-193">Przekształć void (dane wejściowe Element XPathNavigator, XsltArgumentList argumentów, dane wyjściowe TextWriter)</span><span class="sxs-lookup"><span data-stu-id="651e2-193">Void Transform(XPathNavigator input, XsltArgumentList args, TextWriter output)</span></span>|<span data-ttu-id="651e2-194">Przekształć void (dane wejściowe Element XPathNavigator, XsltArgumentList argumentów, dane wyjściowe TextWriter, element XmlResolver programu rozpoznawania nazw)</span><span class="sxs-lookup"><span data-stu-id="651e2-194">Void Transform(XPathNavigator input, XsltArgumentList args, TextWriter output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="651e2-195">Przekształć void (dane wejściowe IXPathNavigable, XsltArgumentList argumentów, dane wyjściowe TextWriter)</span><span class="sxs-lookup"><span data-stu-id="651e2-195">Void Transform(IXPathNavigable input, XsltArgumentList args, TextWriter output)</span></span>|<span data-ttu-id="651e2-196">Przekształć void (dane wejściowe IXPathNavigable, XsltArgumentList argumentów, dane wyjściowe TextWriter, element XmlResolver programu rozpoznawania nazw)</span><span class="sxs-lookup"><span data-stu-id="651e2-196">Void Transform(IXPathNavigable input, XsltArgumentList args, TextWriter output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="651e2-197">Przekształć void (dane wejściowe Element XPathNavigator, XsltArgumentList argumentów, strumieni wyjściowych)</span><span class="sxs-lookup"><span data-stu-id="651e2-197">Void Transform(XPathNavigator input, XsltArgumentList args, Stream output)</span></span>|<span data-ttu-id="651e2-198">Przekształć void (dane wejściowe Element XPathNavigator, XsltArgumentList argumentów, strumieni wyjściowych, element XmlResolver programu rozpoznawania nazw)</span><span class="sxs-lookup"><span data-stu-id="651e2-198">Void Transform(XPathNavigator input, XsltArgumentList args, Stream output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="651e2-199">Przekształć void (dane wejściowe IXPathNavigable, argumentów XsltArgumentList strumieni wyjściowych)</span><span class="sxs-lookup"><span data-stu-id="651e2-199">Void Transform(IXPathNavigable input, XsltArgumentList args, Stream output)</span></span>|<span data-ttu-id="651e2-200">Przekształć void (dane wejściowe IXPathNavigable, XsltArgumentList argumentów, strumieni wyjściowych, element XmlResolver programu rozpoznawania nazw)</span><span class="sxs-lookup"><span data-stu-id="651e2-200">Void Transform(IXPathNavigable input, XsltArgumentList args, Stream output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="651e2-201">Void przekształcenie (ciągu wejściowego, ciąg dane wyjściowe);</span><span class="sxs-lookup"><span data-stu-id="651e2-201">Void Transform(String input, String output);</span></span>|<span data-ttu-id="651e2-202">Void przekształcenie (ciągu wejściowego, ciąg dane wyjściowe, element XmlResolver rozpoznawania);</span><span class="sxs-lookup"><span data-stu-id="651e2-202">Void Transform(String input, String output, XmlResolver resolver);</span></span>|  
  
 <span data-ttu-id="651e2-203"><xref:System.Xml.Xsl.XslTransform.XmlResolver%2A?displayProperty=nameWithType> Właściwość jest przestarzała w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] wersji 1.1.</span><span class="sxs-lookup"><span data-stu-id="651e2-203">The <xref:System.Xml.Xsl.XslTransform.XmlResolver%2A?displayProperty=nameWithType> property is obsolete in [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] version 1.1.</span></span> <span data-ttu-id="651e2-204">Zamiast tego należy użyć nowego <xref:System.Xml.Xsl.XslTransform.Transform%2A> overloads uwzględniającymi <xref:System.Xml.XmlResolver> obiektu.</span><span class="sxs-lookup"><span data-stu-id="651e2-204">Instead, use the new <xref:System.Xml.Xsl.XslTransform.Transform%2A> overloads which take an <xref:System.Xml.XmlResolver> object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="651e2-205">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="651e2-205">See Also</span></span>  
 <xref:System.Xml.Xsl.XslTransform>  
 [<span data-ttu-id="651e2-206">Przekształcenia XSLT przy użyciu klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="651e2-206">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [<span data-ttu-id="651e2-207">Element XPathNavigator w przekształcenia</span><span class="sxs-lookup"><span data-stu-id="651e2-207">XPathNavigator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
 [<span data-ttu-id="651e2-208">Element XPathNodeIterator w przekształcenia</span><span class="sxs-lookup"><span data-stu-id="651e2-208">XPathNodeIterator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
 [<span data-ttu-id="651e2-209">Dane wejściowe XPathDocument XslTransform</span><span class="sxs-lookup"><span data-stu-id="651e2-209">XPathDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
 [<span data-ttu-id="651e2-210">Dane wejściowe dokumentu XmlDataDocument XslTransform</span><span class="sxs-lookup"><span data-stu-id="651e2-210">XmlDataDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)  
 [<span data-ttu-id="651e2-211">Dane wejściowe XmlDocument XslTransform</span><span class="sxs-lookup"><span data-stu-id="651e2-211">XmlDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
