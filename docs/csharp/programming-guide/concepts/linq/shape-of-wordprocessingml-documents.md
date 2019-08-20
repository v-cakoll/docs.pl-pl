---
title: Kształt dokumentów WordprocessingML (C#)
ms.date: 07/20/2015
ms.assetid: 3791b5e0-c502-469b-bb75-a7bf6fdd0a94
ms.openlocfilehash: 84d893267c37ecf99a457ebb683d0451e2b4b68f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591057"
---
# <a name="shape-of-wordprocessingml-documents-c"></a><span data-ttu-id="cd0a3-102">Kształt dokumentów WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="cd0a3-102">Shape of WordprocessingML Documents (C#)</span></span>
<span data-ttu-id="cd0a3-103">Ten temat zawiera wprowadzenie do kształtu XML dokumentu WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="cd0a3-103">This topic introduces the XML shape of a WordprocessingML document.</span></span>  
  
## <a name="microsoft-office-formats"></a><span data-ttu-id="cd0a3-104">Formaty Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="cd0a3-104">Microsoft Office Formats</span></span>  
 <span data-ttu-id="cd0a3-105">Format pliku natywnego dla systemu 2007 Microsoft Office to Office Open XML (często nazywanego Open XML).</span><span class="sxs-lookup"><span data-stu-id="cd0a3-105">The native file format for the 2007 Microsoft Office system is Office Open XML (commonly called Open XML).</span></span> <span data-ttu-id="cd0a3-106">Open XML jest formatem opartym na formacie XML, który Standard ECMA i jest obecnie przechodzący przez proces standardów ISO-IEC.</span><span class="sxs-lookup"><span data-stu-id="cd0a3-106">Open XML is an XML-based format that an Ecma standard and is currently going through the ISO-IEC standards process.</span></span> <span data-ttu-id="cd0a3-107">Język znaczników dla plików edytora tekstu w formacie Open XML ma nazwę WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="cd0a3-107">The markup language for word processing files within Open XML is called WordprocessingML.</span></span> <span data-ttu-id="cd0a3-108">Ten samouczek używa plików źródłowych WordprocessingML jako danych wejściowych dla przykładów.</span><span class="sxs-lookup"><span data-stu-id="cd0a3-108">This tutorial uses WordprocessingML source files as input for the examples.</span></span>  
  
 <span data-ttu-id="cd0a3-109">Jeśli używasz Microsoft Office 2003, możesz zapisać dokumenty w formacie Office Open XML, jeśli zainstalowano pakiet zgodności Microsoft Office dla formatów plików programów Word, Excel i PowerPoint 2007.</span><span class="sxs-lookup"><span data-stu-id="cd0a3-109">If you are using Microsoft Office 2003, you can save documents in the Office Open XML format if you have installed the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="the-shape-of-wordprocessingml-documents"></a><span data-ttu-id="cd0a3-110">Kształt dokumentów WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="cd0a3-110">The Shape of WordprocessingML Documents</span></span>  
 <span data-ttu-id="cd0a3-111">Pierwszą rzeczą, którą należy zrozumieć, jest kształt dokumentów WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="cd0a3-111">The first thing to understand is the shape of WordprocessingML documents.</span></span> <span data-ttu-id="cd0a3-112">Dokument WordprocessingML zawiera element Body (o nazwie `w:body`) zawierający akapity dokumentu.</span><span class="sxs-lookup"><span data-stu-id="cd0a3-112">A WordprocessingML document contains a body element (named `w:body`) that contains the paragraphs of the document.</span></span> <span data-ttu-id="cd0a3-113">Każdy akapit zawiera jeden lub więcej uruchomień tekstu ( `w:r`o nazwie).</span><span class="sxs-lookup"><span data-stu-id="cd0a3-113">Each paragraph contains one or more text runs (named `w:r`).</span></span> <span data-ttu-id="cd0a3-114">Każdy przebieg tekstowy zawiera jedną lub więcej fragmentów tekstu ( `w:t`o nazwie).</span><span class="sxs-lookup"><span data-stu-id="cd0a3-114">Each text run contains one or more text pieces (named `w:t`).</span></span>  
  
 <span data-ttu-id="cd0a3-115">Oto bardzo prosty dokument WordprocessingML:</span><span class="sxs-lookup"><span data-stu-id="cd0a3-115">The following is a very simple WordprocessingML document:</span></span>  
  
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
  
 <span data-ttu-id="cd0a3-116">Ten dokument zawiera dwa akapity.</span><span class="sxs-lookup"><span data-stu-id="cd0a3-116">This document contains two paragraphs.</span></span> <span data-ttu-id="cd0a3-117">Oba te elementy zawierają pojedynczy przebieg tekstowy, a każdy z nich jest pojedynczym fragmentem tekstu.</span><span class="sxs-lookup"><span data-stu-id="cd0a3-117">They both contain a single text run, and each text run contains a single text piece.</span></span>  
  
 <span data-ttu-id="cd0a3-118">Najprostszym sposobem wyświetlenia zawartości dokumentu WordprocessingML w formularzu XML jest utworzenie go przy użyciu programu Microsoft Word, zapisanie go, a następnie uruchomienie następującego programu, który drukuje plik XML do konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="cd0a3-118">The easiest way to see the contents of a WordprocessingML document in XML form is to create one using Microsoft Word, save it, and then run the following program that prints the XML to the console.</span></span>  
  
 <span data-ttu-id="cd0a3-119">Ten przykład używa klas znalezionych w zestawie 'Windowsbase.</span><span class="sxs-lookup"><span data-stu-id="cd0a3-119">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="cd0a3-120">Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="cd0a3-120">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
## <a name="external-resources"></a><span data-ttu-id="cd0a3-121">Zasoby zewnętrzne</span><span class="sxs-lookup"><span data-stu-id="cd0a3-121">External Resources</span></span>  
 [<span data-ttu-id="cd0a3-122">Wprowadzenie do pakietu Office (2007) otwartych formatów plików XML</span><span class="sxs-lookup"><span data-stu-id="cd0a3-122">Introducing the Office (2007) Open XML File Formats</span></span>](https://docs.microsoft.com/previous-versions/office/developer/office-2007/aa338205%28v=office.12%29)  
 [<span data-ttu-id="cd0a3-123">Przegląd WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="cd0a3-123">Overview of WordprocessingML</span></span>](https://docs.microsoft.com/previous-versions/office/developer/office-2003/aa212812%28v=office.11%29)  
 [<span data-ttu-id="cd0a3-124">Anatomia pliku WordProcessingML</span><span class="sxs-lookup"><span data-stu-id="cd0a3-124">Anatomy of a WordProcessingML File</span></span>](http://officeopenxml.com/anatomyofOOXML.php)  
 [<span data-ttu-id="cd0a3-125">Wprowadzenie do WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="cd0a3-125">Introduction to WordprocessingML</span></span>](https://ericwhite.com/blog/introduction-to-wordprocessingml-series/)  
 [<span data-ttu-id="cd0a3-126">Office 2003: Strona pobierania schematów odwołań XML</span><span class="sxs-lookup"><span data-stu-id="cd0a3-126">Office 2003: XML Reference Schemas Download page</span></span>](https://www.microsoft.com/download/details.aspx?id=101)  
  
## <a name="see-also"></a><span data-ttu-id="cd0a3-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cd0a3-127">See also</span></span>

- [<span data-ttu-id="cd0a3-128">Samouczek: Manipulowanie zawartością w dokumencie WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="cd0a3-128">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](./shape-of-wordprocessingml-documents.md)
