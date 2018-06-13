---
title: Schemat WordprocessingML dokument z Styles3
ms.date: 07/20/2015
ms.assetid: 40e35de6-ac93-4bba-88ab-a018cbe93873
ms.openlocfilehash: 6d0d1026edf9a9dbef84eaf3d68412902749e121
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332225"
---
# <a name="wordprocessingml-document-with-styles"></a><span data-ttu-id="e590e-102">Schemat WordprocessingML dokumentu przy użyciu stylów</span><span class="sxs-lookup"><span data-stu-id="e590e-102">WordprocessingML Document with Styles</span></span>
<span data-ttu-id="e590e-103">Bardziej złożone dokumenty schemat WordprocessingML mają akapitów sformatowanych przy użyciu stylów.</span><span class="sxs-lookup"><span data-stu-id="e590e-103">More complicated WordprocessingML documents have paragraphs that are formatted with styles.</span></span>  
  
 <span data-ttu-id="e590e-104">Kilka uwagi dotyczące organizację schemat WordprocessingML dokumenty są przydatne.</span><span class="sxs-lookup"><span data-stu-id="e590e-104">A few notes about the makeup of WordprocessingML documents are helpful.</span></span> <span data-ttu-id="e590e-105">Schemat WordprocessingML dokumenty są przechowywane w pakietach.</span><span class="sxs-lookup"><span data-stu-id="e590e-105">WordprocessingML documents are stored in packages.</span></span> <span data-ttu-id="e590e-106">Pakiety zawierają wiele części (części mają jawne znaczenie, gdy są używane w kontekście pakietów; zasadniczo części są pliki, które są ze sobą zip obejmuje pakietu).</span><span class="sxs-lookup"><span data-stu-id="e590e-106">Packages have multiple parts (parts have an explicit meaning when used in the context of packages; essentially, parts are files that are zipped together to comprise a package).</span></span> <span data-ttu-id="e590e-107">Jeśli dokument zawiera akapitów sformatowanych przy użyciu stylów, będzie części dokumentu zawierającego akapitów, które mają style zastosowanych do nich.</span><span class="sxs-lookup"><span data-stu-id="e590e-107">If a document contains paragraphs that are formatted with styles, there will be a document part that contains paragraphs that have styles applied to them.</span></span> <span data-ttu-id="e590e-108">Będzie również części styl zawiera style, które odwołuje się dokument.</span><span class="sxs-lookup"><span data-stu-id="e590e-108">There will also be a style part that contains the styles that are referred to by the document.</span></span>  
  
 <span data-ttu-id="e590e-109">Podczas uzyskiwania dostępu do pakietów, należy to robić przy użyciu relacji między częściami, a nie przy użyciu dowolnego ścieżki.</span><span class="sxs-lookup"><span data-stu-id="e590e-109">When accessing packages, it is important that you do so through the relationships between parts, rather than using an arbitrary path.</span></span> <span data-ttu-id="e590e-110">Ten problem jest poza zakres manipulowanie zawartości w samouczku schemat WordprocessingML dokumentu, ale programy przykładzie, które znajdują się w tym samouczku pokazują właściwe podejście.</span><span class="sxs-lookup"><span data-stu-id="e590e-110">This issue is beyond the scope of the Manipulating Content in a WordprocessingML Document tutorial, but the example programs that are included in this tutorial demonstrate the correct approach.</span></span>  
  
## <a name="a-document-that-uses-styles"></a><span data-ttu-id="e590e-111">Dokument, który używa style</span><span class="sxs-lookup"><span data-stu-id="e590e-111">A Document that Uses Styles</span></span>  
 <span data-ttu-id="e590e-112">Przykład WordML przedstawiony w [kształtu schemat WordprocessingML dokumentów (C#)](../../../../csharp/programming-guide/concepts/linq/shape-of-wordprocessingml-documents.md) tematu jest bardzo proste.</span><span class="sxs-lookup"><span data-stu-id="e590e-112">The WordML example presented in the [Shape of WordprocessingML Documents (C#)](../../../../csharp/programming-guide/concepts/linq/shape-of-wordprocessingml-documents.md) topic is a very simple one.</span></span> <span data-ttu-id="e590e-113">Ten dokument jest bardziej skomplikowany: ma akapitów sformatowanych przy użyciu stylów.</span><span class="sxs-lookup"><span data-stu-id="e590e-113">The following document is more complicated: It has paragraphs that are formatted with styles.</span></span> <span data-ttu-id="e590e-114">Najprostszym sposobem wyświetlenia, XML, tworzącą dokumentu pakietu Office Open XML jest uruchomienie [przykład tego wyjść Office Open XML części dokumentu (C#)](../../../../csharp/programming-guide/concepts/linq/example-that-outputs-office-open-xml-document-parts.md).</span><span class="sxs-lookup"><span data-stu-id="e590e-114">The easiest way to see the XML that makes up an Office Open XML document is to run the [Example that Outputs Office Open XML Document Parts (C#)](../../../../csharp/programming-guide/concepts/linq/example-that-outputs-office-open-xml-document-parts.md).</span></span>  
  
 <span data-ttu-id="e590e-115">W następującym dokumencie ust ma styl `Heading1`.</span><span class="sxs-lookup"><span data-stu-id="e590e-115">In the following document, the first paragraph has the style `Heading1`.</span></span> <span data-ttu-id="e590e-116">Istnieje wiele akapitów, które mają domyślny styl.</span><span class="sxs-lookup"><span data-stu-id="e590e-116">There are a number of paragraphs that have the default style.</span></span> <span data-ttu-id="e590e-117">Istnieje również kilka akapitów, które mają styl `Code`.</span><span class="sxs-lookup"><span data-stu-id="e590e-117">There are also a number of paragraphs that have the style `Code`.</span></span> <span data-ttu-id="e590e-118">Złożoność Ta względna jest bardziej interesującego dokument do analizy LINQ do XML.</span><span class="sxs-lookup"><span data-stu-id="e590e-118">Because of this relative complexity, this is a more interesting document to parse with LINQ to XML.</span></span>  
  
 <span data-ttu-id="e590e-119">W tych punktach z innych niż domyślne style elementów akapitu ma element podrzędny o nazwie `w:pPr`, który z kolei ma element podrzędny `w:pStyle`.</span><span class="sxs-lookup"><span data-stu-id="e590e-119">In those paragraphs with non-default styles, the paragraph elements have a child element named `w:pPr`, which in turn has a child element `w:pStyle`.</span></span> <span data-ttu-id="e590e-120">Ten element ma atrybut `w:val`, który zawiera nazwę stylu.</span><span class="sxs-lookup"><span data-stu-id="e590e-120">That element has an attribute, `w:val`, which contains the style name.</span></span> <span data-ttu-id="e590e-121">Jeśli akapitu ma domyślny styl, oznacza to, że nie ma elementu akapitu `w:p.Pr` element podrzędny.</span><span class="sxs-lookup"><span data-stu-id="e590e-121">If the paragraph has the default style, it means that the paragraph element does not have a `w:p.Pr` child element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e590e-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e590e-122">See Also</span></span>  
 [<span data-ttu-id="e590e-123">Szczegóły pakietu Office otwieranie dokumentów schemat WordprocessingML XML (C#)</span><span class="sxs-lookup"><span data-stu-id="e590e-123">Details of Office Open XML WordprocessingML Documents (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md)
