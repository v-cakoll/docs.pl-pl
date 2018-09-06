---
title: Kształt dokumentów WordprocessingML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 2dfb446b-5a07-4c00-9ab3-a74ba734ff3a
ms.openlocfilehash: 30ec7a0c6b03d0c6f00561ce08cb836aab3c167b
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43777645"
---
# <a name="shape-of-wordprocessingml-documents-visual-basic"></a><span data-ttu-id="76401-102">Kształt dokumentów WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="76401-102">Shape of WordprocessingML Documents (Visual Basic)</span></span>
<span data-ttu-id="76401-103">W tym temacie przedstawiono kształt XML w dokumencie WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="76401-103">This topic introduces the XML shape of a WordprocessingML document.</span></span>  
  
## <a name="microsoft-office-formats"></a><span data-ttu-id="76401-104">Formaty pakietu Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="76401-104">Microsoft Office Formats</span></span>  
 <span data-ttu-id="76401-105">Format pliku natywnych dla systemu 2007 Microsoft Office to Office Open XML (często nazywany Open XML).</span><span class="sxs-lookup"><span data-stu-id="76401-105">The native file format for the 2007 Microsoft Office system is Office Open XML (commonly called Open XML).</span></span> <span data-ttu-id="76401-106">Otwieranie pliku XML jest oparty na składni XML format standard Ecma i jest obecnie wykonywana przez proces normy ISO IEC.</span><span class="sxs-lookup"><span data-stu-id="76401-106">Open XML is an XML-based format that an Ecma standard and is currently going through the ISO-IEC standards process.</span></span> <span data-ttu-id="76401-107">Język znaczników dla plików przetwarzania tekstu w Open XML nosi nazwę WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="76401-107">The markup language for word processing files within Open XML is called WordprocessingML.</span></span> <span data-ttu-id="76401-108">Ten samouczek używa plików źródłowych WordprocessingML jako dane wejściowe dla przykładów.</span><span class="sxs-lookup"><span data-stu-id="76401-108">This tutorial uses WordprocessingML source files as input for the examples.</span></span>  
  
 <span data-ttu-id="76401-109">Jeśli używasz programu Microsoft Office 2003 można zapisywać dokumenty w format Office Open XML, jeśli zainstalowano pakiet zgodności programu Microsoft Office Word, Excel i PowerPoint 2007 File Formats.</span><span class="sxs-lookup"><span data-stu-id="76401-109">If you are using Microsoft Office 2003, you can save documents in the Office Open XML format if you have installed the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="the-shape-of-wordprocessingml-documents"></a><span data-ttu-id="76401-110">Kształt dokumentów WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="76401-110">The Shape of WordprocessingML Documents</span></span>  
 <span data-ttu-id="76401-111">Pierwszą rzeczą, aby dowiedzieć się, jest kształt dokumentów WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="76401-111">The first thing to understand is the shape of WordprocessingML documents.</span></span> <span data-ttu-id="76401-112">Dokument WordprocessingML zawiera body element (o nazwie `w:body`) zawierający akapitów dokumentu.</span><span class="sxs-lookup"><span data-stu-id="76401-112">A WordprocessingML document contains a body element (named `w:body`) that contains the paragraphs of the document.</span></span> <span data-ttu-id="76401-113">Każdego akapitu zawiera co najmniej jeden przebieg tekstu (o nazwie `w:r`).</span><span class="sxs-lookup"><span data-stu-id="76401-113">Each paragraph contains one or more text runs (named `w:r`).</span></span> <span data-ttu-id="76401-114">Każdego tekstu, uruchom zawiera jeden lub kilka fragmentów tekstu (o nazwie `w:t`).</span><span class="sxs-lookup"><span data-stu-id="76401-114">Each text run contains one or more text pieces (named `w:t`).</span></span>  
  
 <span data-ttu-id="76401-115">Poniżej przedstawiono bardzo prosty dokumentu WordprocessingML:</span><span class="sxs-lookup"><span data-stu-id="76401-115">The following is a very simple WordprocessingML document:</span></span>  
  
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
  
 <span data-ttu-id="76401-116">Ten dokument zawiera dwa akapitach.</span><span class="sxs-lookup"><span data-stu-id="76401-116">This document contains two paragraphs.</span></span> <span data-ttu-id="76401-117">Zawierają jeden tekst, uruchom, a każdy tekst Uruchom zawiera element jeden tekst.</span><span class="sxs-lookup"><span data-stu-id="76401-117">They both contain a single text run, and each text run contains a single text piece.</span></span>  
  
 <span data-ttu-id="76401-118">Najprostszym sposobem wyświetlenia zawartości dokumentu WordprocessingML w postaci XML jest ją utworzyć za pomocą programu Microsoft Word, zapisz go, a następnie uruchom następujący program, który wyświetla kod XML do konsoli.</span><span class="sxs-lookup"><span data-stu-id="76401-118">The easiest way to see the contents of a WordprocessingML document in XML form is to create one using Microsoft Word, save it, and then run the following program that prints the XML to the console.</span></span>  
  
 <span data-ttu-id="76401-119">W tym przykładzie użyto klasy znalezione w zestawie WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="76401-119">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="76401-120">Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="76401-120">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
    Sub Main()  
        Dim documentRelationshipType = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
  
        Using wdPackage As Package = _  
          Package.Open("SampleDoc.docx", _  
                       FileMode.Open, FileAccess.Read)  
            Dim docPackageRelationship As PackageRelationship = wdPackage _  
                .GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
            If (docPackageRelationship IsNot Nothing) Then  
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri( _  
                            New Uri("/", UriKind.Relative), _  
                            docPackageRelationship.TargetUri)  
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
                ' Get the officeDocument part from the package.  
                ' Load the XML in the part into an XDocument instance.  
                Dim xDoc As XDocument = _  
                    XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
                Console.WriteLine(xDoc.Root)  
            End If  
        End Using  
    End Sub  
End Module  
```  
  
## <a name="external-resources"></a><span data-ttu-id="76401-121">Zasoby zewnętrzne</span><span class="sxs-lookup"><span data-stu-id="76401-121">External Resources</span></span>  
 <span data-ttu-id="76401-122">[Wprowadzenie do formatów pakietu Office (2007) Open XML](https://docs.microsoft.com/previous-versions/office/developer/office-2007/aa338205(v=office.12))</span><span class="sxs-lookup"><span data-stu-id="76401-122">[Introducing the Office (2007) Open XML File Formats](https://docs.microsoft.com/previous-versions/office/developer/office-2007/aa338205(v=office.12))</span></span>  
  
 <span data-ttu-id="76401-123">[Omówienie WordprocessingML](https://msdn.microsoft.com/en-us/library/aa212812(office.11).aspx)</span><span class="sxs-lookup"><span data-stu-id="76401-123">[Overview of WordprocessingML](https://msdn.microsoft.com/en-us/library/aa212812(office.11).aspx)</span></span>  
  
 [<span data-ttu-id="76401-124">Office 2003: XML odwołanie schematów strony plików do pobrania</span><span class="sxs-lookup"><span data-stu-id="76401-124">Office 2003: XML Reference Schemas Download page</span></span>](https://go.microsoft.com/fwlink/?LinkId=98095)  
  
## <a name="see-also"></a><span data-ttu-id="76401-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="76401-125">See Also</span></span>  
 [<span data-ttu-id="76401-126">Samouczek: Manipulowanie zawartością w dokumencie WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="76401-126">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
