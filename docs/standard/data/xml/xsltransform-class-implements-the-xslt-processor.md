---
title: Implementowanie procesora XSLT przy użyciu klasy XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 88373fe2-4a6b-44f9-8a62-8a3e348e3a46
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8cc3eb3e3f147d8ed15587946af743c96739a9b1
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71956863"
---
# <a name="xsltransform-class-implements-the-xslt-processor"></a><span data-ttu-id="97b9a-102">Implementowanie procesora XSLT przy użyciu klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="97b9a-102">XslTransform Class Implements the XSLT Processor</span></span>

> [!NOTE]
> <span data-ttu-id="97b9a-103">Klasa <xref:System.Xml.Xsl.XslTransform> jest przestarzała w .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="97b9a-103">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="97b9a-104">Można wykonywać przekształcenia Extensible Stylesheet Language for Transformations (XSLT) przy użyciu klasy <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="97b9a-104">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="97b9a-105">Aby uzyskać więcej informacji, zobacz [Używanie klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) i [Migrowanie z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .</span><span class="sxs-lookup"><span data-stu-id="97b9a-105">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>

<span data-ttu-id="97b9a-106">Klasa <xref:System.Xml.Xsl.XslTransform> to procesor XSLT implementujący zalecenia dotyczące wersji 1,0 języka XSL (XSLT).</span><span class="sxs-lookup"><span data-stu-id="97b9a-106">The <xref:System.Xml.Xsl.XslTransform> class is an XSLT processor implementing the XSL Transformations (XSLT) Version 1.0 recommendation.</span></span> <span data-ttu-id="97b9a-107">Metoda <xref:System.Xml.Xsl.XslTransform.Load%2A> lokalizuje i odczytuje arkusze stylów, a metoda <xref:System.Xml.Xsl.XslTransform.Transform%2A> przekształca dany dokument źródłowy.</span><span class="sxs-lookup"><span data-stu-id="97b9a-107">The <xref:System.Xml.Xsl.XslTransform.Load%2A> method locates and reads style sheets, and the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method transforms the given source document.</span></span> <span data-ttu-id="97b9a-108">Dowolny magazyn, który implementuje interfejs <xref:System.Xml.XPath.IXPathNavigable>, może być używany jako dokument źródłowy dla <xref:System.Xml.Xsl.XslTransform>.</span><span class="sxs-lookup"><span data-stu-id="97b9a-108">Any store that implements the <xref:System.Xml.XPath.IXPathNavigable> interface can be used as the source document for the <xref:System.Xml.Xsl.XslTransform>.</span></span> <span data-ttu-id="97b9a-109">.NET Framework obecnie implementuje interfejs <xref:System.Xml.XPath.IXPathNavigable> na <xref:System.Xml.XmlDocument>, <xref:System.Xml.XmlDataDocument> i <xref:System.Xml.XPath.XPathDocument>, dlatego wszystkie te wartości mogą być używane jako wejściowy dokument źródłowy do przekształcenia.</span><span class="sxs-lookup"><span data-stu-id="97b9a-109">The .NET Framework currently implements the <xref:System.Xml.XPath.IXPathNavigable> interface on the <xref:System.Xml.XmlDocument>, the <xref:System.Xml.XmlDataDocument>, and the <xref:System.Xml.XPath.XPathDocument>, so all of these can be used as the input source document to a transformation.</span></span>

<span data-ttu-id="97b9a-110">Obiekt <xref:System.Xml.Xsl.XslTransform> w .NET Framework obsługuje specyfikację XSLT 1,0, zdefiniowaną za pomocą następującej przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="97b9a-110">The <xref:System.Xml.Xsl.XslTransform> object in the .NET Framework only supports the XSLT 1.0 specification, defined with the following namespace:</span></span>

```xml
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
```

<span data-ttu-id="97b9a-111">Arkusz stylów można załadować przy użyciu metody <xref:System.Xml.Xsl.XslTransform.Load%2A> z jednej z następujących klas:</span><span class="sxs-lookup"><span data-stu-id="97b9a-111">The style sheet can be loaded, using the <xref:System.Xml.Xsl.XslTransform.Load%2A> method, from one of the following classes:</span></span>

- <span data-ttu-id="97b9a-112">Pustym XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="97b9a-112">XPathNavigator</span></span>

- <span data-ttu-id="97b9a-113">Elementu</span><span class="sxs-lookup"><span data-stu-id="97b9a-113">XmlReader</span></span>

- <span data-ttu-id="97b9a-114">Ciąg reprezentujący adres URL</span><span class="sxs-lookup"><span data-stu-id="97b9a-114">A string representing a URL</span></span>

<span data-ttu-id="97b9a-115">Istnieje inna metoda <xref:System.Xml.Xsl.XslTransform.Load%2A> dla każdej z powyższych klas wejściowych.</span><span class="sxs-lookup"><span data-stu-id="97b9a-115">There is a different <xref:System.Xml.Xsl.XslTransform.Load%2A> method for each of the above input classes.</span></span> <span data-ttu-id="97b9a-116">Niektóre metody przyjmują kombinację jednej z tych klas i klasy <xref:System.Xml.XmlResolver> jako argumenty.</span><span class="sxs-lookup"><span data-stu-id="97b9a-116">Some methods take in a combination of one of these classes and the <xref:System.Xml.XmlResolver> class as arguments.</span></span> <span data-ttu-id="97b9a-117">@No__t-0 lokalizuje zasoby, do których odwołuje się `<xsl:import>` lub `<xsl:include>` Znalezione w arkuszu stylów.</span><span class="sxs-lookup"><span data-stu-id="97b9a-117">The <xref:System.Xml.XmlResolver> locates resources referenced by `<xsl:import>` or `<xsl:include>` found in the style sheet.</span></span> <span data-ttu-id="97b9a-118">Następujące metody przyjmują ciąg, <xref:System.Xml.XmlReader> lub <xref:System.Xml.XPath.XPathNavigator> jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="97b9a-118">The following methods take a string, <xref:System.Xml.XmlReader>, or <xref:System.Xml.XPath.XPathNavigator> as input.</span></span>

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

<span data-ttu-id="97b9a-119">Większość metod <xref:System.Xml.Xsl.XslTransform.Load%2A> pokazanych powyżej przyjmuje <xref:System.Xml.XmlResolver> jako parametr.</span><span class="sxs-lookup"><span data-stu-id="97b9a-119">Most of the <xref:System.Xml.Xsl.XslTransform.Load%2A> methods shown above take an <xref:System.Xml.XmlResolver> as a parameter.</span></span> <span data-ttu-id="97b9a-120">@No__t-0 służy do ładowania arkusza stylów i wszystkich arkuszy stylów, do których odwołuje się element xsl: import i xsl: include.</span><span class="sxs-lookup"><span data-stu-id="97b9a-120">The <xref:System.Xml.XmlResolver> is used to load the style sheet and any style sheet(s) referenced in xsl:import and xsl:include elements.</span></span>

<span data-ttu-id="97b9a-121">Większość metod <xref:System.Xml.Xsl.XslTransform.Load%2A> przyjmuje również dowody jako parametr.</span><span class="sxs-lookup"><span data-stu-id="97b9a-121">Most of the <xref:System.Xml.Xsl.XslTransform.Load%2A> methods also take evidence as a parameter.</span></span> <span data-ttu-id="97b9a-122">Parametr zeznania jest <xref:System.Security.Policy.Evidence>, który jest skojarzony z arkuszem stylów.</span><span class="sxs-lookup"><span data-stu-id="97b9a-122">The evidence parameter is the <xref:System.Security.Policy.Evidence> that is associated with the style sheet.</span></span> <span data-ttu-id="97b9a-123">Poziom zabezpieczeń arkusza stylów ma wpływ na poziom zabezpieczeń wszelkich kolejnych zasobów, do których się odwołuje, takich jak skrypt, który zawiera, do wszystkich funkcji `document()` i wszystkich obiektów rozszerzeń używanych przez <xref:System.Xml.Xsl.XsltArgumentList>.</span><span class="sxs-lookup"><span data-stu-id="97b9a-123">The security level of the style sheet affects the security level of any subsequent resources it references, such as the script it contains, any `document()` functions it uses, and any extension objects used by the <xref:System.Xml.Xsl.XsltArgumentList>.</span></span>

<span data-ttu-id="97b9a-124">Jeśli arkusz stylów jest ładowany przy użyciu metody <xref:System.Xml.Xsl.XslTransform.Load%2A>, która zawiera parametr adresu URL, a żadne dowody nie są dostarczane, dowód arkusza stylów jest obliczany przez połączenie podanego adresu URL ze swoją lokacją i strefą.</span><span class="sxs-lookup"><span data-stu-id="97b9a-124">If the style sheet is loaded using a <xref:System.Xml.Xsl.XslTransform.Load%2A> method that contains a URL parameter and no evidence is provided, the evidence of the style sheet is calculated by combining the given URL with its site and zone.</span></span>

<span data-ttu-id="97b9a-125">Jeśli nie podano żadnego identyfikatora URI lub dowodu, oznacza to, że dowody ustawione dla arkusza stylów są w pełni zaufane.</span><span class="sxs-lookup"><span data-stu-id="97b9a-125">If no URI or evidence is provided, then the evidence set for the style sheet is fully trusted.</span></span> <span data-ttu-id="97b9a-126">Nie Ładuj arkuszy stylów z niezaufanych źródeł ani nie dodawaj niezaufanych obiektów rozszerzeń do <xref:System.Xml.Xsl.XsltArgumentList>.</span><span class="sxs-lookup"><span data-stu-id="97b9a-126">Do not load style sheets from untrusted sources, or add untrusted extension objects into the <xref:System.Xml.Xsl.XsltArgumentList>.</span></span>

<span data-ttu-id="97b9a-127">Aby uzyskać więcej informacji na temat poziomów zabezpieczeń i dowodów, jak ma to wpływ na skrypty, zobacz [XSLT stylesheet Scripting Using \<msxsl: script >](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md).</span><span class="sxs-lookup"><span data-stu-id="97b9a-127">For more information about security levels and evidence and how it affects scripting, see [XSLT Stylesheet Scripting Using \<msxsl:script>](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md).</span></span> <span data-ttu-id="97b9a-128">Aby uzyskać informacje na temat poziomów zabezpieczeń i dowodów, jak ma to wpływ na obiekty rozszerzeń, zobacz [XsltArgumentList for Style Sheet Parameters and Extension Objects](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md).</span><span class="sxs-lookup"><span data-stu-id="97b9a-128">For information about security levels and evidence and how it affects extension objects, see [XsltArgumentList for Style Sheet Parameters and Extension Objects](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md).</span></span>

<span data-ttu-id="97b9a-129">Aby uzyskać informacje na temat poziomów zabezpieczeń i dowodów, jak ma to wpływ na funkcję `document()`, zobacz [rozpoznawanie zewnętrznych arkuszy stylów XSLT i dokumentów](../../../../docs/standard/data/xml/resolving-external-xslt-style-sheets-and-documents.md).</span><span class="sxs-lookup"><span data-stu-id="97b9a-129">For information about security levels and evidence and how it affects the `document()` function, see [Resolving External XSLT Style Sheets and Documents](../../../../docs/standard/data/xml/resolving-external-xslt-style-sheets-and-documents.md).</span></span>

<span data-ttu-id="97b9a-130">Arkusz stylów może być dostarczony z liczbą parametrów wejściowych.</span><span class="sxs-lookup"><span data-stu-id="97b9a-130">A style sheet can be supplied with a number of input parameters.</span></span> <span data-ttu-id="97b9a-131">Arkusz stylów może również wywoływać funkcje dla obiektów rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="97b9a-131">The style sheet can also call functions on extension objects.</span></span> <span data-ttu-id="97b9a-132">Parametry i obiekty rozszerzeń są dostarczane do arkusza stylów przy użyciu klasy <xref:System.Xml.Xsl.XsltArgumentList>.</span><span class="sxs-lookup"><span data-stu-id="97b9a-132">Both parameters and extension objects are supplied to the style sheet using the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span> <span data-ttu-id="97b9a-133">Aby uzyskać więcej informacji na temat <xref:System.Xml.Xsl.XsltArgumentList>, zobacz <xref:System.Xml.Xsl.XsltArgumentList>.</span><span class="sxs-lookup"><span data-stu-id="97b9a-133">For more information about the <xref:System.Xml.Xsl.XsltArgumentList>, see <xref:System.Xml.Xsl.XsltArgumentList>.</span></span>

## <a name="recommended-secure-use-of-xsltransform-class"></a><span data-ttu-id="97b9a-134">Zalecane bezpieczne użycie klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="97b9a-134">Recommended Secure Use of XslTransform Class</span></span>

<span data-ttu-id="97b9a-135">Uprawnienia zabezpieczeń arkusza stylów zależą od dostarczonych dowodów.</span><span class="sxs-lookup"><span data-stu-id="97b9a-135">The security privileges of the style sheet depend on the evidence provided.</span></span> <span data-ttu-id="97b9a-136">Poniższa tabela zawiera podsumowanie lokalizacji arkusza stylów i zawiera objaśnienie typu dowodu do przekazania.</span><span class="sxs-lookup"><span data-stu-id="97b9a-136">The following table summarizes the location of the style sheet and gives an explanation of what type of evidence to give.</span></span>

- <span data-ttu-id="97b9a-137">Arkusz stylów XSLT nie ma odwołań zewnętrznych lub arkusz stylów pochodzi z zaufanej podstawy kodu.</span><span class="sxs-lookup"><span data-stu-id="97b9a-137">The XSLT style sheet has no external references, or the style sheet comes from a code base that you trust.</span></span>

  - <span data-ttu-id="97b9a-138">Podaj dowody z Twojego zestawu:</span><span class="sxs-lookup"><span data-stu-id="97b9a-138">Provide the evidence from your assembly:</span></span>

    ```vb
    Dim xslt = New XslTransform() xslt.Load(stylesheet, resolver, Me.GetType().Assembly.Evidence)

    XsltTransform xslt = new XslTransform();  xslt.Load(stylesheet, resolver, this.GetType().Assembly.Evidence);
    ```

- <span data-ttu-id="97b9a-139">Arkusz stylów XSLT pochodzi ze źródła zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="97b9a-139">The XSLT style sheet comes from an outside source.</span></span> <span data-ttu-id="97b9a-140">Źródło źródła jest znane i istnieje zweryfikowany identyfikator URI.</span><span class="sxs-lookup"><span data-stu-id="97b9a-140">The origin of the source is known and there is a verifiable URI.</span></span>

  - <span data-ttu-id="97b9a-141">Utwórz dowód przy użyciu identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="97b9a-141">Create evidence using the URI.</span></span>

    ```vb
    Dim xslt As New XslTransform() Dim ev As Evidence = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri) xslt.Load(stylesheet, resolver, evidence)

    XslTransform xslt = new XslTransform(); Evidence ev = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri); xslt.Load(stylesheet, resolver, evidence);
    ```

- <span data-ttu-id="97b9a-142">Arkusz stylów XSLT pochodzi ze źródła zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="97b9a-142">The XSLT style sheet comes from an outside source.</span></span> <span data-ttu-id="97b9a-143">Źródło źródła jest nieznane.</span><span class="sxs-lookup"><span data-stu-id="97b9a-143">The origin of the source is not known.</span></span>

  - <span data-ttu-id="97b9a-144">Ustaw dowód na `null`.</span><span class="sxs-lookup"><span data-stu-id="97b9a-144">Set evidence to `null`.</span></span> <span data-ttu-id="97b9a-145">Bloki skryptów nie są przetwarzane, funkcja XSLT `document()` nie jest obsługiwana, a uprzywilejowane obiekty rozszerzeń są niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="97b9a-145">Script blocks are not processed, the XSLT `document()` function is not supported, and privileged extension objects are disallowed.</span></span>

    <span data-ttu-id="97b9a-146">Ponadto można również ustawić parametr `resolver` na `null`, co gwarantuje, że elementy `xsl:import` i `xsl:include` nie są przetwarzane.</span><span class="sxs-lookup"><span data-stu-id="97b9a-146">Additionally, you can also set the `resolver` parameter to `null` This ensures that `xsl:import` and `xsl:include` elements are not processed.</span></span>

- <span data-ttu-id="97b9a-147">Arkusz stylów XSLT pochodzi ze źródła zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="97b9a-147">The XSLT style sheet comes from an outside source.</span></span> <span data-ttu-id="97b9a-148">Źródło źródła jest nieznane, ale wymagana jest obsługa skryptów.</span><span class="sxs-lookup"><span data-stu-id="97b9a-148">The origin of the source is not known, but you require script support.</span></span>

  - <span data-ttu-id="97b9a-149">Zażądaj dowodu od wywołującego.</span><span class="sxs-lookup"><span data-stu-id="97b9a-149">Request evidence from the caller.</span></span>

## <a name="transformation-of-xml-data"></a><span data-ttu-id="97b9a-150">Przekształcanie danych XML</span><span class="sxs-lookup"><span data-stu-id="97b9a-150">Transformation of XML Data</span></span>

<span data-ttu-id="97b9a-151">Po załadowaniu arkusza stylów przekształcenie rozpocznie się, wywołując jedną z metod <xref:System.Xml.Xsl.XslTransform.Transform%2A> i dostarczając dokument źródła danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="97b9a-151">Once a style sheet is loaded, the transformation starts by calling one of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> methods and supplying an input source document.</span></span> <span data-ttu-id="97b9a-152">Metoda <xref:System.Xml.Xsl.XslTransform.Transform%2A> jest przeciążona, aby zapewnić różne wyjścia transformacji.</span><span class="sxs-lookup"><span data-stu-id="97b9a-152">The <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is overloaded to provide different transformation outputs.</span></span> <span data-ttu-id="97b9a-153">Transformacja może spowodować następujące formaty wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="97b9a-153">The transformation can result in the following output formats:</span></span>

- <xref:System.Xml.XmlReader>

- <xref:System.Xml.XmlWriter>

- <xref:System.IO.TextWriter>

- <xref:System.IO.Stream>

- <span data-ttu-id="97b9a-154">Adres URL ciągu pliku</span><span class="sxs-lookup"><span data-stu-id="97b9a-154">String URL of file</span></span>

<span data-ttu-id="97b9a-155">Ten ostatni format, adres URL ciągu, zapewnia często używany scenariusz do przekształcania dokumentu wejściowego znajdującego się w adresie URL i zapisywania dokumentu w wyjściowym adresie URL.</span><span class="sxs-lookup"><span data-stu-id="97b9a-155">This last format, the string URL, provides for a commonly used scenario in transforming an input document located in a URL and writing the document to the output URL.</span></span> <span data-ttu-id="97b9a-156">Ta metoda <xref:System.Xml.Xsl.XslTransform.Transform%2A> jest wygodną metodą ładowania dokumentu XML z pliku, wykonywania transformacji XSLT i zapisywania danych wyjściowych do pliku.</span><span class="sxs-lookup"><span data-stu-id="97b9a-156">This <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is a convenience method to load an XML document from a file, perform the XSLT transformation, and write the output to a file.</span></span> <span data-ttu-id="97b9a-157">Uniemożliwia to utworzenie i załadowanie wejściowego dokumentu źródłowego, a następnie zapisanie go w strumieniu pliku.</span><span class="sxs-lookup"><span data-stu-id="97b9a-157">This prevents you from having to create and load the input source document, and then write to a file stream.</span></span> <span data-ttu-id="97b9a-158">Poniższy przykład kodu pokazuje użycie metody <xref:System.Xml.Xsl.XslTransform.Transform%2A> przy użyciu ciągu adresu URL jako danych wejściowych i wyjściowych:</span><span class="sxs-lookup"><span data-stu-id="97b9a-158">The following code sample shows this use of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method using the string URL as input and output:</span></span>

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

## <a name="transforming-a-section-of-an-xml-document"></a><span data-ttu-id="97b9a-159">Przekształcanie sekcji dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="97b9a-159">Transforming a Section of an XML Document</span></span>

<span data-ttu-id="97b9a-160">Przekształcenia są stosowane do dokumentu jako całości.</span><span class="sxs-lookup"><span data-stu-id="97b9a-160">Transformations apply to the document as a whole.</span></span> <span data-ttu-id="97b9a-161">Innymi słowy, jeśli przejdziesz do węzła innego niż węzeł główny dokumentu, nie uniemożliwi to proces przekształcania uzyskuje dostęp do wszystkich węzłów w załadowanym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="97b9a-161">In other words, if you pass in a node other than the document root node, this does not prevent the transformation process from accessing all nodes in the loaded document.</span></span> <span data-ttu-id="97b9a-162">Aby przekształcić fragment drzewa wyników, należy utworzyć <xref:System.Xml.XmlDocument> zawierający tylko fragment drzewa wynik i przekazać go <xref:System.Xml.XmlDocument> do metody <xref:System.Xml.Xsl.XslTransform.Transform%2A>.</span><span class="sxs-lookup"><span data-stu-id="97b9a-162">To transform a result tree fragment, you must create an <xref:System.Xml.XmlDocument> containing just the result tree fragment and pass that <xref:System.Xml.XmlDocument> to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span> <span data-ttu-id="97b9a-163">Poniższy przykład wykonuje transformację fragmentu drzewa wynik.</span><span class="sxs-lookup"><span data-stu-id="97b9a-163">The following example performs a transformation on a result tree fragment.</span></span>

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

<span data-ttu-id="97b9a-164">W przykładzie są stosowane pliki Library. XML i print_root. xsl jako dane wejściowe i wyprowadzane przez konsolę następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="97b9a-164">The example uses the library.xml and print_root.xsl files as input and outputs the following to the console:</span></span>

```console
Passing <book genre="novel" ISBN="1-861001-57-5"><title>Pride And Prejudice</title></book> to print_root.xsl
Root node is book.
```

<span data-ttu-id="97b9a-165">Library. XML</span><span class="sxs-lookup"><span data-stu-id="97b9a-165">library.xml</span></span>

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

<span data-ttu-id="97b9a-166">print_root. xsl</span><span class="sxs-lookup"><span data-stu-id="97b9a-166">print_root.xsl</span></span>

```xml
<stylesheet version="1.0" xmlns="http://www.w3.org/1999/XSL/Transform" >
  <output method="text" />
  <template match="/">
     Root node is  <value-of select="local-name(//*[position() = 1])" />
  </template>
</stylesheet>
```

## <a name="migration-of-xslt-from-net-framework-version-10-to-net-framework-version-11"></a><span data-ttu-id="97b9a-167">Migracja XSLT z .NET Framework wersja 1,0 do .NET Framework wersja 1,1</span><span class="sxs-lookup"><span data-stu-id="97b9a-167">Migration of XSLT from .NET Framework version 1.0 to .NET Framework version 1.1</span></span>

<span data-ttu-id="97b9a-168">W poniższej tabeli przedstawiono przestarzałe metody .NET Framework w wersji 1,0 oraz nowe metody .NET Framework w wersji 1,1 dla metody <xref:System.Xml.Xsl.XslTransform.Load%2A>.</span><span class="sxs-lookup"><span data-stu-id="97b9a-168">The following table shows the obsolete .NET Framework version 1.0 methods and new .NET Framework version 1.1 methods for the <xref:System.Xml.Xsl.XslTransform.Load%2A> method.</span></span> <span data-ttu-id="97b9a-169">Nowe metody umożliwiają ograniczenie uprawnień arkusza stylów przez określenie dowodu.</span><span class="sxs-lookup"><span data-stu-id="97b9a-169">The new methods enable you to limit the permissions of the style sheet by specifying evidence.</span></span>

|<span data-ttu-id="97b9a-170">Przestarzałe metody ładowania .NET Framework w wersji 1,0</span><span class="sxs-lookup"><span data-stu-id="97b9a-170">Obsolete .NET Framework version 1.0 Load Methods</span></span>|<span data-ttu-id="97b9a-171">Zastępowanie metod ładowania .NET Framework w wersji 1,1</span><span class="sxs-lookup"><span data-stu-id="97b9a-171">Replacement .NET Framework version 1.1 Load Methods</span></span>|
|------------------------------------------------------|---------------------------------------------------------|
|<span data-ttu-id="97b9a-172">Załaduj (dane wejściowe XPathNavigator);</span><span class="sxs-lookup"><span data-stu-id="97b9a-172">Load(XPathNavigator input);</span></span><br /><br /> <span data-ttu-id="97b9a-173">Załaduj (dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="97b9a-173">Load(XPathNavigator input, XmlResolver resolver);</span></span>|<span data-ttu-id="97b9a-174">Załaduj (XPathNavigator StyleSheet, sqlresolverer, dowód potwierdzający);</span><span class="sxs-lookup"><span data-stu-id="97b9a-174">Load(XPathNavigator stylesheet, XmlResolver resolver, Evidence evidence);</span></span>|
|<span data-ttu-id="97b9a-175">Ładowanie (arkusz stylów IXPathNavigable);</span><span class="sxs-lookup"><span data-stu-id="97b9a-175">Load(IXPathNavigable stylesheet);</span></span><br /><br /> <span data-ttu-id="97b9a-176">Załaduj (IXPathNavigable StyleSheet, sqlresolverer);</span><span class="sxs-lookup"><span data-stu-id="97b9a-176">Load(IXPathNavigable stylesheet, XmlResolver resolver);</span></span>|<span data-ttu-id="97b9a-177">Load (IXPathNavigable StyleSheet, procedura rozpoznawania nazw XmlResolver, dowód dowodu);</span><span class="sxs-lookup"><span data-stu-id="97b9a-177">Load(IXPathNavigable stylesheet, XmlResolver resolver, Evidence evidence);</span></span>|
|<span data-ttu-id="97b9a-178">Ładowanie (arkusz stylów XmlReader);</span><span class="sxs-lookup"><span data-stu-id="97b9a-178">Load(XmlReader stylesheet);</span></span><br /><br /> <span data-ttu-id="97b9a-179">Załaduj (XmlReader StyleSheet, xmlresolverer);</span><span class="sxs-lookup"><span data-stu-id="97b9a-179">Load(XmlReader stylesheet, XmlResolver resolver);</span></span>|<span data-ttu-id="97b9a-180">Załaduj (XmlReader StyleSheet, XmlResolver, resolver, dowód potwierdzający);</span><span class="sxs-lookup"><span data-stu-id="97b9a-180">Load(XmlReader stylesheet, XmlResolver resolver, Evidence evidence);</span></span>|

<span data-ttu-id="97b9a-181">W poniższej tabeli przedstawiono przestarzałe i nowe metody dla metody <xref:System.Xml.Xsl.XslTransform.Transform%2A>.</span><span class="sxs-lookup"><span data-stu-id="97b9a-181">The following table shows the obsolete and new methods for the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span> <span data-ttu-id="97b9a-182">Nowe metody przyjmują obiekt <xref:System.Xml.XmlResolver>.</span><span class="sxs-lookup"><span data-stu-id="97b9a-182">The new methods take an <xref:System.Xml.XmlResolver> object.</span></span>

|<span data-ttu-id="97b9a-183">Przestarzałe metody transformacji .NET Framework w wersji 1,0</span><span class="sxs-lookup"><span data-stu-id="97b9a-183">Obsolete .NET Framework version 1.0 Transform Methods</span></span>|<span data-ttu-id="97b9a-184">Zastępowanie metod 1,1 .NET Framework wersja przekształcenia</span><span class="sxs-lookup"><span data-stu-id="97b9a-184">Replacement .NET Framework version Transform 1.1 Methods</span></span>|
|-----------------------------------------------------------|--------------------------------------------------------------|
|<span data-ttu-id="97b9a-185">Transformacja XmlReader (dane wejściowe XPathNavigator, XsltArgumentList args)</span><span class="sxs-lookup"><span data-stu-id="97b9a-185">XmlReader Transform(XPathNavigator input, XsltArgumentList args)</span></span>|<span data-ttu-id="97b9a-186">Przekształcanie XmlReader (dane wejściowe XPathNavigator, XsltArgumentList args, mechanizm rozwiązywania konfliktów XmlResolver)</span><span class="sxs-lookup"><span data-stu-id="97b9a-186">XmlReader Transform(XPathNavigator  input, XsltArgumentList args, XmlResolver resolver)</span></span>|
|<span data-ttu-id="97b9a-187">XmlReader Transform (IXPathNavigable Input, XsltArgumentList args)</span><span class="sxs-lookup"><span data-stu-id="97b9a-187">XmlReader Transform(IXPathNavigable input, XsltArgumentList args)</span></span>|<span data-ttu-id="97b9a-188">XmlReader Transform (IXPathNavigable Input, XsltArgumentList args, xmlresolverer)</span><span class="sxs-lookup"><span data-stu-id="97b9a-188">XmlReader Transform(IXPathNavigable input, XsltArgumentList args, XmlResolver resolver)</span></span>|
|<span data-ttu-id="97b9a-189">Unieważnij transformację (dane wejściowe XPathNavigator, XsltArgumentList args, wynik XmlWriter)</span><span class="sxs-lookup"><span data-stu-id="97b9a-189">Void Transform(XPathNavigator input, XsltArgumentList args, XmlWriter output)</span></span>|<span data-ttu-id="97b9a-190">Unieważnij transformację (dane wejściowe XPathNavigator, XsltArgumentList args, dane wyjściowe XmlWriter, mechanizm rozwiązywania konfliktów XmlResolver)</span><span class="sxs-lookup"><span data-stu-id="97b9a-190">Void Transform(XPathNavigator input, XsltArgumentList args, XmlWriter output, XmlResolver resolver)</span></span>|
|<span data-ttu-id="97b9a-191">Void Transform (dane wejściowe IXPathNavigable, XsltArgumentList args, dane wyjściowe XmlWriter)</span><span class="sxs-lookup"><span data-stu-id="97b9a-191">Void Transform(IXPathNavigable input, XsltArgumentList args, XmlWriter output)</span></span>|<span data-ttu-id="97b9a-192">Unieważnij transformację (dane wejściowe IXpathNavigable, XsltArgumentList args, dane wyjściowe XmlWriter, mechanizm rozwiązywania konfliktów XmlResolver)</span><span class="sxs-lookup"><span data-stu-id="97b9a-192">Void Transform(IXpathNavigable input, XsltArgumentList args, XmlWriter output, XmlResolver resolver)</span></span>|
|<span data-ttu-id="97b9a-193">Void Transform (dane wejściowe XPathNavigator, XsltArgumentList argumentów, wynik TextWriter)</span><span class="sxs-lookup"><span data-stu-id="97b9a-193">Void Transform(XPathNavigator input, XsltArgumentList args, TextWriter output)</span></span>|<span data-ttu-id="97b9a-194">Unieważnij transformację (dane wejściowe XPathNavigator, XsltArgumentList args, dane wyjściowe TextWriter, mechanizm rozwiązywania konfliktów XmlResolver)</span><span class="sxs-lookup"><span data-stu-id="97b9a-194">Void Transform(XPathNavigator input, XsltArgumentList args, TextWriter output, XmlResolver resolver)</span></span>|
|<span data-ttu-id="97b9a-195">Void Transform (IXPathNavigable Input, XsltArgumentList args, TextWriter Output)</span><span class="sxs-lookup"><span data-stu-id="97b9a-195">Void Transform(IXPathNavigable input, XsltArgumentList args, TextWriter output)</span></span>|<span data-ttu-id="97b9a-196">Void Transform (dane wejściowe IXPathNavigable, XsltArgumentList args, TextWriter Output, resolver XmlResolver)</span><span class="sxs-lookup"><span data-stu-id="97b9a-196">Void Transform(IXPathNavigable input, XsltArgumentList args, TextWriter output, XmlResolver resolver)</span></span>|
|<span data-ttu-id="97b9a-197">Void Transform (dane wejściowe XPathNavigator, XsltArgumentList args, wyjście strumienia)</span><span class="sxs-lookup"><span data-stu-id="97b9a-197">Void Transform(XPathNavigator input, XsltArgumentList args, Stream output)</span></span>|<span data-ttu-id="97b9a-198">Void Transform (dane wejściowe XPathNavigator, XsltArgumentList args, dane wyjściowe strumienia, mechanizm rozwiązywania konfliktów XmlResolver)</span><span class="sxs-lookup"><span data-stu-id="97b9a-198">Void Transform(XPathNavigator input, XsltArgumentList args, Stream output, XmlResolver resolver)</span></span>|
|<span data-ttu-id="97b9a-199">Void Transform (IXPathNavigable Input, XsltArgumentList args, strumień wyjściowy)</span><span class="sxs-lookup"><span data-stu-id="97b9a-199">Void Transform(IXPathNavigable input, XsltArgumentList args, Stream output)</span></span>|<span data-ttu-id="97b9a-200">Void Transform (dane wejściowe IXPathNavigable, XsltArgumentList args, dane wyjściowe strumienia, mechanizm rozwiązywania konfliktów XmlResolver)</span><span class="sxs-lookup"><span data-stu-id="97b9a-200">Void Transform(IXPathNavigable input, XsltArgumentList args, Stream output, XmlResolver resolver)</span></span>|
|<span data-ttu-id="97b9a-201">Void Transform (ciąg wejściowy, ciąg wyjściowy);</span><span class="sxs-lookup"><span data-stu-id="97b9a-201">Void Transform(String input, String output);</span></span>|<span data-ttu-id="97b9a-202">Unieważnij transformację (dane wejściowe ciągów, ciągi danych wyjściowych, mechanizm rozwiązywania konfliktów XmlResolver);</span><span class="sxs-lookup"><span data-stu-id="97b9a-202">Void Transform(String input, String output, XmlResolver resolver);</span></span>|

<span data-ttu-id="97b9a-203">Właściwość <xref:System.Xml.Xsl.XslTransform.XmlResolver%2A?displayProperty=nameWithType> jest przestarzała w .NET Framework wersji 1,1.</span><span class="sxs-lookup"><span data-stu-id="97b9a-203">The <xref:System.Xml.Xsl.XslTransform.XmlResolver%2A?displayProperty=nameWithType> property is obsolete in .NET Framework version 1.1.</span></span> <span data-ttu-id="97b9a-204">Zamiast tego należy użyć nowych przeciążeń <xref:System.Xml.Xsl.XslTransform.Transform%2A>, które pobierają obiekt <xref:System.Xml.XmlResolver>.</span><span class="sxs-lookup"><span data-stu-id="97b9a-204">Instead, use the new <xref:System.Xml.Xsl.XslTransform.Transform%2A> overloads which take an <xref:System.Xml.XmlResolver> object.</span></span>

## <a name="see-also"></a><span data-ttu-id="97b9a-205">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="97b9a-205">See also</span></span>

- <xref:System.Xml.Xsl.XslTransform>
- [<span data-ttu-id="97b9a-206">Przekształcenia XSLT przy użyciu klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="97b9a-206">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)
- [<span data-ttu-id="97b9a-207">Klasa XPathNavigator w przekształceniach</span><span class="sxs-lookup"><span data-stu-id="97b9a-207">XPathNavigator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)
- [<span data-ttu-id="97b9a-208">Klasa XPathNodeIterator w przekształceniach</span><span class="sxs-lookup"><span data-stu-id="97b9a-208">XPathNodeIterator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)
- [<span data-ttu-id="97b9a-209">Dane wejściowe obiektu XPathDocument klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="97b9a-209">XPathDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)
- [<span data-ttu-id="97b9a-210">Dane wejściowe obiektu XmlDataDocument klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="97b9a-210">XmlDataDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)
- [<span data-ttu-id="97b9a-211">Dane wejściowe obiektu XmlDocument klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="97b9a-211">XmlDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
