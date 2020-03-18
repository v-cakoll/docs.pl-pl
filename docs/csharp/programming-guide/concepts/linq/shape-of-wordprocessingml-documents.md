---
title: Kształt dokumentów WordprocessingML (C#)
ms.date: 07/20/2015
ms.assetid: 3791b5e0-c502-469b-bb75-a7bf6fdd0a94
ms.openlocfilehash: 58c028fed465f45fdcf8f63f2119eb8e8b201e32
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76732671"
---
# <a name="shape-of-wordprocessingml-documents-c"></a><span data-ttu-id="b0f43-102">Kształt dokumentów WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="b0f43-102">Shape of WordprocessingML Documents (C#)</span></span>
<span data-ttu-id="b0f43-103">W tym temacie przedstawiono kształt XML dokumentu WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="b0f43-103">This topic introduces the XML shape of a WordprocessingML document.</span></span>  
  
## <a name="microsoft-office-formats"></a><span data-ttu-id="b0f43-104">Formaty pakietu Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="b0f43-104">Microsoft Office Formats</span></span>  
 <span data-ttu-id="b0f43-105">Natywnym formatem pliku dla pakietu Microsoft Office system 2007 jest office Open XML (powszechnie nazywany Open XML).</span><span class="sxs-lookup"><span data-stu-id="b0f43-105">The native file format for the 2007 Microsoft Office system is Office Open XML (commonly called Open XML).</span></span> <span data-ttu-id="b0f43-106">Open XML to format oparty na XML, który jest standardem Ecma i obecnie przechodzi proces standardów ISO-IEC.</span><span class="sxs-lookup"><span data-stu-id="b0f43-106">Open XML is an XML-based format that an Ecma standard and is currently going through the ISO-IEC standards process.</span></span> <span data-ttu-id="b0f43-107">Język znaczników dla plików edytora tekstu w otwartym pliku XML nosi nazwę WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="b0f43-107">The markup language for word processing files within Open XML is called WordprocessingML.</span></span> <span data-ttu-id="b0f43-108">W tym samouczku użyto plików źródłowych WordprocessingML jako danych wejściowych dla przykładów.</span><span class="sxs-lookup"><span data-stu-id="b0f43-108">This tutorial uses WordprocessingML source files as input for the examples.</span></span>  
  
 <span data-ttu-id="b0f43-109">Jeśli używasz pakietu Microsoft Office 2003, możesz zapisywać dokumenty w formacie Otwartych xml pakietu Office, jeśli zainstalowano pakiet zgodności pakietu Microsoft Office dla formatów plików programów Word, Excel i PowerPoint 2007.</span><span class="sxs-lookup"><span data-stu-id="b0f43-109">If you are using Microsoft Office 2003, you can save documents in the Office Open XML format if you have installed the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="the-shape-of-wordprocessingml-documents"></a><span data-ttu-id="b0f43-110">Kształt dokumentów wordprocessingML</span><span class="sxs-lookup"><span data-stu-id="b0f43-110">The Shape of WordprocessingML Documents</span></span>  
 <span data-ttu-id="b0f43-111">Pierwszą rzeczą do zrozumienia jest kształt dokumentów WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="b0f43-111">The first thing to understand is the shape of WordprocessingML documents.</span></span> <span data-ttu-id="b0f43-112">Dokument WordprocessingML zawiera element treści `w:body`(o nazwie), który zawiera akapity dokumentu.</span><span class="sxs-lookup"><span data-stu-id="b0f43-112">A WordprocessingML document contains a body element (named `w:body`) that contains the paragraphs of the document.</span></span> <span data-ttu-id="b0f43-113">Każdy akapit zawiera jeden lub `w:r`więcej przebiegów tekstu (o nazwie).</span><span class="sxs-lookup"><span data-stu-id="b0f43-113">Each paragraph contains one or more text runs (named `w:r`).</span></span> <span data-ttu-id="b0f43-114">Każdy uruchomiony tekst zawiera jeden lub `w:t`więcej fragmentów tekstu (o nazwie).</span><span class="sxs-lookup"><span data-stu-id="b0f43-114">Each text run contains one or more text pieces (named `w:t`).</span></span>  
  
 <span data-ttu-id="b0f43-115">Poniżej znajduje się bardzo prosty dokument WordprocessingML:</span><span class="sxs-lookup"><span data-stu-id="b0f43-115">The following is a very simple WordprocessingML document:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
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
    <w:p w:rsidR="00E22EB6"  
         w:rsidRDefault="00E22EB6">  
      <w:r>  
        <w:t>This is a paragraph.</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00E22EB6"  
         w:rsidRDefault="00E22EB6">  
      <w:r>  
        <w:t>This is another paragraph.</w:t>  
      </w:r>  
    </w:p>  
  </w:body>  
</w:document>  
```  
  
 <span data-ttu-id="b0f43-116">Ten dokument zawiera dwa akapity.</span><span class="sxs-lookup"><span data-stu-id="b0f43-116">This document contains two paragraphs.</span></span> <span data-ttu-id="b0f43-117">Oba zawierają jeden przebieg tekstu, a każdy przebieg tekstu zawiera pojedynczy fragment tekstu.</span><span class="sxs-lookup"><span data-stu-id="b0f43-117">They both contain a single text run, and each text run contains a single text piece.</span></span>  
  
 <span data-ttu-id="b0f43-118">Najprostszym sposobem wyświetlenia zawartości dokumentu WordprocessingML w formularzu XML jest utworzenie go przy użyciu programu Microsoft Word, zapisanie go, a następnie uruchomienie następującego programu, który drukuje kod XML na konsoli.</span><span class="sxs-lookup"><span data-stu-id="b0f43-118">The easiest way to see the contents of a WordprocessingML document in XML form is to create one using Microsoft Word, save it, and then run the following program that prints the XML to the console.</span></span>  
  
 <span data-ttu-id="b0f43-119">W tym przykładzie użyto klas znalezionych w zestawie WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="b0f43-119">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="b0f43-120">Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="b0f43-120">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```csharp  
const string documentRelationshipType =  
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";  
const string wordmlNamespace =  
  "http://schemas.openxmlformats.org/wordprocessingml/2006/main";  
XNamespace w = wordmlNamespace;  
  
using (Package wdPackage = Package.Open("SampleDoc.docx", FileMode.Open, FileAccess.Read))  
{  
    PackageRelationship relationship =  
        wdPackage  
        .GetRelationshipsByType(documentRelationshipType)  
        .FirstOrDefault();  
    if (relationship != null)  
    {  
        Uri documentUri =  
            PackUriHelper.ResolvePartUri(  
                new Uri("/", UriKind.Relative),  
                relationship.TargetUri);  
        PackagePart documentPart = wdPackage.GetPart(documentUri);  
  
        //  Get the officeDocument part from the package.  
        //  Load the XML in the part into an XDocument instance.  
        XDocument xdoc =  
            XDocument.Load(XmlReader.Create(documentPart.GetStream()));  
        Console.WriteLine(xdoc.Root);  
    }  
}  
```  
  
## <a name="external-resources"></a><span data-ttu-id="b0f43-121">Zasoby zewnętrzne</span><span class="sxs-lookup"><span data-stu-id="b0f43-121">External resources</span></span>

- [<span data-ttu-id="b0f43-122">Przedstawiamy otwierane formaty plików XML pakietu Office (2007)</span><span class="sxs-lookup"><span data-stu-id="b0f43-122">Introducing the Office (2007) Open XML File Formats</span></span>](https://docs.microsoft.com/previous-versions/office/developer/office-2007/aa338205%28v=office.12%29)
- [<span data-ttu-id="b0f43-123">Omówienie języka WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="b0f43-123">Overview of WordprocessingML</span></span>](https://docs.microsoft.com/previous-versions/office/developer/office-2003/aa212812%28v=office.11%29)
- [<span data-ttu-id="b0f43-124">Anatomia pliku WordProcessingML</span><span class="sxs-lookup"><span data-stu-id="b0f43-124">Anatomy of a WordProcessingML File</span></span>](http://officeopenxml.com/anatomyofOOXML.php)
- [<span data-ttu-id="b0f43-125">Wprowadzenie do wordprocessingML</span><span class="sxs-lookup"><span data-stu-id="b0f43-125">Introduction to WordprocessingML</span></span>](https://ericwhite.com/blog/introduction-to-wordprocessingml-series/)

## <a name="see-also"></a><span data-ttu-id="b0f43-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b0f43-126">See also</span></span>

- [<span data-ttu-id="b0f43-127">Samouczek: manipulowanie zawartością w dokumencie WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="b0f43-127">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](./shape-of-wordprocessingml-documents.md)
