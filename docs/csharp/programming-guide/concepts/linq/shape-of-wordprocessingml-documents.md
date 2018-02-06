---
title: "Kształt schemat WordprocessingML dokumentów (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: 3791b5e0-c502-469b-bb75-a7bf6fdd0a94
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ee03c9cd64c3c3b251049be0826c7b29abe80bfa
ms.sourcegitcommit: 099aa20d9b6450d1b7452d782a55771a6ad8ff35
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/05/2018
---
# <a name="shape-of-wordprocessingml-documents-c"></a><span data-ttu-id="d4a9c-102">Kształt schemat WordprocessingML dokumentów (C#)</span><span class="sxs-lookup"><span data-stu-id="d4a9c-102">Shape of WordprocessingML Documents (C#)</span></span>
<span data-ttu-id="d4a9c-103">W tym temacie przedstawiono kształtu XML dokumentu schemat WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="d4a9c-103">This topic introduces the XML shape of a WordprocessingML document.</span></span>  
  
## <a name="microsoft-office-formats"></a><span data-ttu-id="d4a9c-104">Formaty pakietu Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="d4a9c-104">Microsoft Office Formats</span></span>  
 <span data-ttu-id="d4a9c-105">Format natywny plik pakietu Microsoft Office system 2007 jest Office Open XML (często nazywany Open XML).</span><span class="sxs-lookup"><span data-stu-id="d4a9c-105">The native file format for the 2007 Microsoft Office system is Office Open XML (commonly called Open XML).</span></span> <span data-ttu-id="d4a9c-106">Otwieranie pliku XML jest oparte na języku XML format standardu Ecma i jest obecnie przechodzi przez proces normy ISO IEC.</span><span class="sxs-lookup"><span data-stu-id="d4a9c-106">Open XML is an XML-based format that an Ecma standard and is currently going through the ISO-IEC standards process.</span></span> <span data-ttu-id="d4a9c-107">Język znaczników dla edytora plików w Open XML nosi nazwę schemat WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="d4a9c-107">The markup language for word processing files within Open XML is called WordprocessingML.</span></span> <span data-ttu-id="d4a9c-108">Ten samouczek używa plików źródłowych schemat WordprocessingML jako dane wejściowe dla przykładów.</span><span class="sxs-lookup"><span data-stu-id="d4a9c-108">This tutorial uses WordprocessingML source files as input for the examples.</span></span>  
  
 <span data-ttu-id="d4a9c-109">Jeśli używasz programu Microsoft Office 2003 można zapisywać dokumenty w formacie Office Open XML po zainstalowaniu pakietu zgodności Microsoft Office dla programów Word, Excel i PowerPoint 2007.</span><span class="sxs-lookup"><span data-stu-id="d4a9c-109">If you are using Microsoft Office 2003, you can save documents in the Office Open XML format if you have installed the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="the-shape-of-wordprocessingml-documents"></a><span data-ttu-id="d4a9c-110">Kształt schemat WordprocessingML dokumentów</span><span class="sxs-lookup"><span data-stu-id="d4a9c-110">The Shape of WordprocessingML Documents</span></span>  
 <span data-ttu-id="d4a9c-111">Najpierw zrozumieć jest kształtu schemat WordprocessingML dokumentów.</span><span class="sxs-lookup"><span data-stu-id="d4a9c-111">The first thing to understand is the shape of WordprocessingML documents.</span></span> <span data-ttu-id="d4a9c-112">Schemat WordprocessingML dokument zawiera body element (o nazwie `w:body`) zawierający akapitów dokumentu.</span><span class="sxs-lookup"><span data-stu-id="d4a9c-112">A WordprocessingML document contains a body element (named `w:body`) that contains the paragraphs of the document.</span></span> <span data-ttu-id="d4a9c-113">Każdego akapitu zawiera co najmniej jeden przebieg tekstu (o nazwie `w:r`).</span><span class="sxs-lookup"><span data-stu-id="d4a9c-113">Each paragraph contains one or more text runs (named `w:r`).</span></span> <span data-ttu-id="d4a9c-114">Każdego tekstu Uruchom zawiera jeden lub kilka fragmentów tekstu (o nazwie `w:t`).</span><span class="sxs-lookup"><span data-stu-id="d4a9c-114">Each text run contains one or more text pieces (named `w:t`).</span></span>  
  
 <span data-ttu-id="d4a9c-115">Poniżej znajduje się bardzo proste dokumentu schemat WordprocessingML:</span><span class="sxs-lookup"><span data-stu-id="d4a9c-115">The following is a very simple WordprocessingML document:</span></span>  
  
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
  
 <span data-ttu-id="d4a9c-116">Ten dokument zawiera dwa akapitów.</span><span class="sxs-lookup"><span data-stu-id="d4a9c-116">This document contains two paragraphs.</span></span> <span data-ttu-id="d4a9c-117">Zawierają jeden tekst Uruchom, a każdy tekst Uruchom zawiera element jeden tekst.</span><span class="sxs-lookup"><span data-stu-id="d4a9c-117">They both contain a single text run, and each text run contains a single text piece.</span></span>  
  
 <span data-ttu-id="d4a9c-118">Najprostszym sposobem wyświetlenia zawartości dokumentu schemat WordprocessingML w postaci XML jest aby go utworzyć za pomocą programu Microsoft Word, zapisz go, a następnie uruchom następujący program, który wyświetla kod XML do konsoli.</span><span class="sxs-lookup"><span data-stu-id="d4a9c-118">The easiest way to see the contents of a WordprocessingML document in XML form is to create one using Microsoft Word, save it, and then run the following program that prints the XML to the console.</span></span>  
  
 <span data-ttu-id="d4a9c-119">W tym przykładzie użyto znaleziony w zestawie WindowsBase klasy.</span><span class="sxs-lookup"><span data-stu-id="d4a9c-119">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="d4a9c-120">Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d4a9c-120">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
## <a name="external-resources"></a><span data-ttu-id="d4a9c-121">Zasoby zewnętrzne</span><span class="sxs-lookup"><span data-stu-id="d4a9c-121">External Resources</span></span>  
 [<span data-ttu-id="d4a9c-122">Wprowadzenie do formatów pakietu Office (2007) Open XML</span><span class="sxs-lookup"><span data-stu-id="d4a9c-122">Introducing the Office (2007) Open XML File Formats</span></span>](https://msdn.microsoft.com/library/ms406049.aspx)  
 <span data-ttu-id="d4a9c-123">[Omówienie schemat WordprocessingML](https://msdn.microsoft.com/library/aa212812(office.11).aspx)</span><span class="sxs-lookup"><span data-stu-id="d4a9c-123">[Overview of WordprocessingML](https://msdn.microsoft.com/library/aa212812(office.11).aspx)</span></span>  
 [<span data-ttu-id="d4a9c-124">Anatomia pliku schemat WordProcessingML</span><span class="sxs-lookup"><span data-stu-id="d4a9c-124">Anatomy of a WordProcessingML File</span></span>](http://officeopenxml.com/anatomyofOOXML.php)  
 [<span data-ttu-id="d4a9c-125">Wprowadzenie do schemat WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="d4a9c-125">Introduction to WordprocessingML</span></span>](http://ericwhite.com/blog/introduction-to-wordprocessingml-series/)  
 [<span data-ttu-id="d4a9c-126">Pakietu Office 2003: Strona pobierania schematy odwołanie XML</span><span class="sxs-lookup"><span data-stu-id="d4a9c-126">Office 2003: XML Reference Schemas Download page</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=101)  
  
## <a name="see-also"></a><span data-ttu-id="d4a9c-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d4a9c-127">See Also</span></span>  
 [<span data-ttu-id="d4a9c-128">Samouczek: Manipulowanie zawartości w dokumencie schemat WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="d4a9c-128">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
