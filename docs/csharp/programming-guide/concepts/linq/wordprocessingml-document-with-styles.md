---
title: Dokument WordprocessingML ze stylem3
ms.date: 07/20/2015
ms.assetid: 40e35de6-ac93-4bba-88ab-a018cbe93873
ms.openlocfilehash: 10697744680276a40fb7a175e4c04920c9e3c243
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167871"
---
# <a name="wordprocessingml-document-with-styles"></a><span data-ttu-id="bd885-102">Dokument WordprocessingML ze stylami</span><span class="sxs-lookup"><span data-stu-id="bd885-102">WordprocessingML Document with Styles</span></span>
<span data-ttu-id="bd885-103">Bardziej skomplikowane dokumenty WordprocessingML mają akapity sformatowane za pomocą stylów.</span><span class="sxs-lookup"><span data-stu-id="bd885-103">More complicated WordprocessingML documents have paragraphs that are formatted with styles.</span></span>  
  
 <span data-ttu-id="bd885-104">Kilka uwag na temat makijażu dokumentów WordprocessingML są pomocne.</span><span class="sxs-lookup"><span data-stu-id="bd885-104">A few notes about the makeup of WordprocessingML documents are helpful.</span></span> <span data-ttu-id="bd885-105">Dokumenty WordprocessingML są przechowywane w opakowaniach.</span><span class="sxs-lookup"><span data-stu-id="bd885-105">WordprocessingML documents are stored in packages.</span></span> <span data-ttu-id="bd885-106">Pakiety mają wiele części (części mają wyraźne znaczenie, gdy są używane w kontekście pakietów; zasadniczo części są plikami, które są spakowane razem, aby składać się z pakietu).</span><span class="sxs-lookup"><span data-stu-id="bd885-106">Packages have multiple parts (parts have an explicit meaning when used in the context of packages; essentially, parts are files that are zipped together to comprise a package).</span></span> <span data-ttu-id="bd885-107">Jeśli dokument zawiera akapity sformatowane za pomocą stylów, będzie istniała część dokumentu zawierająca akapity, które mają zastosowane do nich style.</span><span class="sxs-lookup"><span data-stu-id="bd885-107">If a document contains paragraphs that are formatted with styles, there will be a document part that contains paragraphs that have styles applied to them.</span></span> <span data-ttu-id="bd885-108">Będzie również część stylu, która zawiera style, które są określone przez dokument.</span><span class="sxs-lookup"><span data-stu-id="bd885-108">There will also be a style part that contains the styles that are referred to by the document.</span></span>  
  
 <span data-ttu-id="bd885-109">Podczas uzyskiwania dostępu do pakietów, ważne jest, aby to zrobić za pośrednictwem relacji między częściami, a nie przy użyciu dowolnej ścieżki.</span><span class="sxs-lookup"><span data-stu-id="bd885-109">When accessing packages, it is important that you do so through the relationships between parts, rather than using an arbitrary path.</span></span> <span data-ttu-id="bd885-110">Ten problem wykracza poza zakres manipulowania zawartościw samouczku dokumentu WordprocessingML, ale przykładowe programy, które są zawarte w tym samouczku wykazać poprawne podejście.</span><span class="sxs-lookup"><span data-stu-id="bd885-110">This issue is beyond the scope of the Manipulating Content in a WordprocessingML Document tutorial, but the example programs that are included in this tutorial demonstrate the correct approach.</span></span>  
  
## <a name="a-document-that-uses-styles"></a><span data-ttu-id="bd885-111">Dokument, który używa stylów</span><span class="sxs-lookup"><span data-stu-id="bd885-111">A Document that Uses Styles</span></span>  
 <span data-ttu-id="bd885-112">Przykład wordml przedstawiony w [kształt dokumentów WordprocessingML (C#)](./shape-of-wordprocessingml-documents.md) jest bardzo prosty.</span><span class="sxs-lookup"><span data-stu-id="bd885-112">The WordML example presented in the [Shape of WordprocessingML Documents (C#)](./shape-of-wordprocessingml-documents.md) topic is a very simple one.</span></span> <span data-ttu-id="bd885-113">Poniższy dokument jest bardziej skomplikowany: zawiera akapity, które są sformatowane za pomocą stylów.</span><span class="sxs-lookup"><span data-stu-id="bd885-113">The following document is more complicated: It has paragraphs that are formatted with styles.</span></span> <span data-ttu-id="bd885-114">Najprostszym sposobem wyświetlenie pliku XML, który składa się na dokument XML pakietu Office Open, jest uruchomienie [przykładu, który wprowadza otwarte części dokumentów XML pakietu Office (C#).](./example-that-outputs-office-open-xml-document-parts.md)</span><span class="sxs-lookup"><span data-stu-id="bd885-114">The easiest way to see the XML that makes up an Office Open XML document is to run the [Example that Outputs Office Open XML Document Parts (C#)](./example-that-outputs-office-open-xml-document-parts.md).</span></span>  
  
 <span data-ttu-id="bd885-115">W poniższym dokumencie akapit pierwszy `Heading1`ma styl .</span><span class="sxs-lookup"><span data-stu-id="bd885-115">In the following document, the first paragraph has the style `Heading1`.</span></span> <span data-ttu-id="bd885-116">Istnieje kilka akapitów, które mają domyślny styl.</span><span class="sxs-lookup"><span data-stu-id="bd885-116">There are a number of paragraphs that have the default style.</span></span> <span data-ttu-id="bd885-117">Istnieje również kilka akapitów, które `Code`mają styl .</span><span class="sxs-lookup"><span data-stu-id="bd885-117">There are also a number of paragraphs that have the style `Code`.</span></span> <span data-ttu-id="bd885-118">Ze względu na tę względną złożoność jest to bardziej interesujący dokument do analizy z LINQ do XML.</span><span class="sxs-lookup"><span data-stu-id="bd885-118">Because of this relative complexity, this is a more interesting document to parse with LINQ to XML.</span></span>  
  
 <span data-ttu-id="bd885-119">W tych akapitach ze stylami innymi niż domyślne `w:pPr`elementy akapitu mają element `w:pStyle`podrzędny o nazwie , który z kolei ma element podrzędny.</span><span class="sxs-lookup"><span data-stu-id="bd885-119">In those paragraphs with non-default styles, the paragraph elements have a child element named `w:pPr`, which in turn has a child element `w:pStyle`.</span></span> <span data-ttu-id="bd885-120">Ten element ma `w:val`atrybut, który zawiera nazwę stylu.</span><span class="sxs-lookup"><span data-stu-id="bd885-120">That element has an attribute, `w:val`, which contains the style name.</span></span> <span data-ttu-id="bd885-121">Jeśli akapit ma styl domyślny, oznacza to, że `w:p.Pr` element akapitu nie ma elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="bd885-121">If the paragraph has the default style, it means that the paragraph element does not have a `w:p.Pr` child element.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<w:document  
    xmlns:ve="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    xmlns:o="urn:schemas-microsoft-com:office:office"  
    xmlns:r="http://schemas.openxmlformats.org/officeDocument/2006/relationships"  
    xmlns:m="http://schemas.openxmlformats.org/officeDocument/2006/math"  
    xmlns:v="urn:schemas-microsoft-com:vml"  
    xmlns:wp="http://schemas.openxmlformats.org/drawingml/2006/wordprocessingDrawing"  
    xmlns:w10="urn:schemas-microsoft-com:office:word"  
    xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
    xmlns:wne="http://schemas.microsoft.com/office/word/2006/wordml">  
  <w:body>  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Heading1" />  
      </w:pPr>  
      <w:r>  
        <w:t>Parsing WordprocessingML with LINQ to XML</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0">  
      <w:r>  
        <w:t>The following example prints to the console.</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r>  
        <w:t>using System;</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r w:rsidRPr="00876F34">  
        <w:t>class Program {</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r w:rsidRPr="00876F34">  
        <w:t xml:space="preserve">    public static void </w:t>  
      </w:r>  
      <w:smartTag w:uri="urn:schemas-microsoft-com:office:smarttags" w:element="place">  
        <w:r w:rsidRPr="00876F34">  
          <w:t>Main</w:t>  
        </w:r>  
      </w:smartTag>  
      <w:r w:rsidRPr="00876F34">  
        <w:t>(string[] args) {</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r w:rsidRPr="00876F34">  
        <w:t xml:space="preserve">        Console.WriteLine("Hello World");</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r w:rsidRPr="00876F34">  
        <w:t xml:space="preserve">    }</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r w:rsidRPr="00876F34">  
        <w:t>}</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0">  
      <w:r>  
        <w:t>This example produces the following output:</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r>  
        <w:t>Hello World</w:t>  
      </w:r>  
    </w:p>  
    <w:sectPr w:rsidR="00A75AE0" w:rsidSect="00A75AE0">  
      <w:pgSz w:w="12240" w:h="15840" />  
      <w:pgMar w:top="1440" w:right="1800" w:bottom="1440" w:left="1800" w:header="720" w:footer="720" w:gutter="0" />  
      <w:cols w:space="720" />  
      <w:docGrid w:linePitch="360" />  
    </w:sectPr>  
  </w:body>  
</w:document>  
```  
