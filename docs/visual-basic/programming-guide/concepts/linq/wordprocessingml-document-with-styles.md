---
title: Dokument WordprocessingML z Styles2
ms.date: 07/20/2015
ms.assetid: a9136e4d-c368-4661-8049-7d45c679a236
ms.openlocfilehash: caf80014077bf57dc1ffb8eaeac6390cf4258015
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403553"
---
# <a name="wordprocessingml-document-with-styles"></a><span data-ttu-id="2da2c-102">Dokument WordprocessingML ze stylami</span><span class="sxs-lookup"><span data-stu-id="2da2c-102">WordprocessingML Document with Styles</span></span>
<span data-ttu-id="2da2c-103">Bardziej skomplikowane dokumenty WordprocessingML mają akapity sformatowane przy użyciu stylów.</span><span class="sxs-lookup"><span data-stu-id="2da2c-103">More complicated WordprocessingML documents have paragraphs that are formatted with styles.</span></span>  
  
 <span data-ttu-id="2da2c-104">Przydatne są kilka informacji na temat korzeń dokumentów WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="2da2c-104">A few notes about the makeup of WordprocessingML documents are helpful.</span></span> <span data-ttu-id="2da2c-105">Dokumenty WordprocessingML są przechowywane w pakietach.</span><span class="sxs-lookup"><span data-stu-id="2da2c-105">WordprocessingML documents are stored in packages.</span></span> <span data-ttu-id="2da2c-106">Pakiety mają wiele części (części mają jawne znaczenie, gdy są używane w kontekście pakietów; zasadniczo części są plikami, które są spakowane razem w celu podzielenia pakietu).</span><span class="sxs-lookup"><span data-stu-id="2da2c-106">Packages have multiple parts (parts have an explicit meaning when used in the context of packages; essentially, parts are files that are zipped together to comprise a package).</span></span> <span data-ttu-id="2da2c-107">Jeśli dokument zawiera akapity sformatowane za pomocą stylów, będzie to część dokumentu zawierająca akapity, do których zastosowano style.</span><span class="sxs-lookup"><span data-stu-id="2da2c-107">If a document contains paragraphs that are formatted with styles, there will be a document part that contains paragraphs that have styles applied to them.</span></span> <span data-ttu-id="2da2c-108">Będzie również częścią stylu, która zawiera style, do których odwołuje się dokument.</span><span class="sxs-lookup"><span data-stu-id="2da2c-108">There will also be a style part that contains the styles that are referred to by the document.</span></span>  
  
 <span data-ttu-id="2da2c-109">Podczas uzyskiwania dostępu do pakietów ważne jest, aby wykonać tę czynność poprzez relacje między częściami, zamiast korzystać z dowolnej ścieżki.</span><span class="sxs-lookup"><span data-stu-id="2da2c-109">When accessing packages, it is important that you do so through the relationships between parts, rather than using an arbitrary path.</span></span> <span data-ttu-id="2da2c-110">Ten problem jest poza zakresem manipulowania zawartością w samouczku dokumentu WordprocessingML, ale przykładowe programy, które są zawarte w tym samouczku, przedstawiają odpowiednie podejście.</span><span class="sxs-lookup"><span data-stu-id="2da2c-110">This issue is beyond the scope of the Manipulating Content in a WordprocessingML Document tutorial, but the example programs that are included in this tutorial demonstrate the correct approach.</span></span>  
  
## <a name="a-document-that-uses-styles"></a><span data-ttu-id="2da2c-111">Dokument, który używa stylów</span><span class="sxs-lookup"><span data-stu-id="2da2c-111">A Document that Uses Styles</span></span>  
 <span data-ttu-id="2da2c-112">Przykład elementu WordML przedstawiony w [kształcie WordprocessingML (Visual Basic)](shape-of-wordprocessingml-documents.md) tematu jest bardzo prosty.</span><span class="sxs-lookup"><span data-stu-id="2da2c-112">The WordML example presented in the [Shape of WordprocessingML Documents (Visual Basic)](shape-of-wordprocessingml-documents.md) topic is a very simple one.</span></span> <span data-ttu-id="2da2c-113">Następujący dokument jest bardziej skomplikowany: zawiera akapity sformatowane za pomocą stylów.</span><span class="sxs-lookup"><span data-stu-id="2da2c-113">The following document is more complicated: It has paragraphs that are formatted with styles.</span></span> <span data-ttu-id="2da2c-114">Najprostszym sposobem na wyświetlenie kodu XML, który stanowi dokument pakietu Office Open XML, jest uruchomienie [przykładu, który wyprowadza składniki Office Open XML Documents (Visual Basic)](example-that-outputs-office-open-xml-document-parts.md).</span><span class="sxs-lookup"><span data-stu-id="2da2c-114">The easiest way to see the XML that makes up an Office Open XML document is to run the [Example that Outputs Office Open XML Document Parts (Visual Basic)](example-that-outputs-office-open-xml-document-parts.md).</span></span>  
  
 <span data-ttu-id="2da2c-115">W poniższym dokumencie pierwszy akapit ma styl `Heading1` .</span><span class="sxs-lookup"><span data-stu-id="2da2c-115">In the following document, the first paragraph has the style `Heading1`.</span></span> <span data-ttu-id="2da2c-116">Istnieje kilka akapitów z stylem domyślnym.</span><span class="sxs-lookup"><span data-stu-id="2da2c-116">There are a number of paragraphs that have the default style.</span></span> <span data-ttu-id="2da2c-117">Istnieje również kilka akapitów, które mają styl `Code` .</span><span class="sxs-lookup"><span data-stu-id="2da2c-117">There are also a number of paragraphs that have the style `Code`.</span></span> <span data-ttu-id="2da2c-118">Z powodu tej względnej złożoności jest to bardziej interesujący dokument, który można analizować za pomocą LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="2da2c-118">Because of this relative complexity, this is a more interesting document to parse with LINQ to XML.</span></span>  
  
 <span data-ttu-id="2da2c-119">W tych akapitach o stylach innych niż domyślne elementy akapitu mają element podrzędny o nazwie `w:pPr` , który z kolei ma element podrzędny `w:pStyle` .</span><span class="sxs-lookup"><span data-stu-id="2da2c-119">In those paragraphs with non-default styles, the paragraph elements have a child element named `w:pPr`, which in turn has a child element `w:pStyle`.</span></span> <span data-ttu-id="2da2c-120">Ten element ma atrybut, `w:val` który zawiera nazwę stylu.</span><span class="sxs-lookup"><span data-stu-id="2da2c-120">That element has an attribute, `w:val`, which contains the style name.</span></span> <span data-ttu-id="2da2c-121">Jeśli akapit ma styl domyślny, oznacza to, że element akapitu nie ma `w:p.Pr` elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="2da2c-121">If the paragraph has the default style, it means that the paragraph element does not have a `w:p.Pr` child element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2da2c-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2da2c-122">See also</span></span>

- [<span data-ttu-id="2da2c-123">Szczegóły dotyczące dokumentów Office Open XML WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2da2c-123">Details of Office Open XML WordprocessingML Documents (Visual Basic)</span></span>](details-of-office-open-xml-wordprocessingml-documents.md)
