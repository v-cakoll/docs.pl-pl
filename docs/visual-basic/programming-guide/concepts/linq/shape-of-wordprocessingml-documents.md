---
title: "Kształt schemat WordprocessingML dokumentów (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2dfb446b-5a07-4c00-9ab3-a74ba734ff3a
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5809e8148e7ac426b876ad11948878ee0bfcd016
ms.sourcegitcommit: 8ed4ebc15b5ef89d06a7507dc9d5e306e30accf7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2017
---
# <a name="shape-of-wordprocessingml-documents-visual-basic"></a><span data-ttu-id="b879e-102">Kształt schemat WordprocessingML dokumentów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b879e-102">Shape of WordprocessingML Documents (Visual Basic)</span></span>
<span data-ttu-id="b879e-103">W tym temacie przedstawiono kształtu XML dokumentu schemat WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="b879e-103">This topic introduces the XML shape of a WordprocessingML document.</span></span>  
  
## <a name="microsoft-office-formats"></a><span data-ttu-id="b879e-104">Formaty pakietu Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="b879e-104">Microsoft Office Formats</span></span>  
 <span data-ttu-id="b879e-105">Format natywny plik pakietu Microsoft Office system 2007 jest Office Open XML (często nazywany Open XML).</span><span class="sxs-lookup"><span data-stu-id="b879e-105">The native file format for the 2007 Microsoft Office system is Office Open XML (commonly called Open XML).</span></span> <span data-ttu-id="b879e-106">Otwieranie pliku XML jest oparte na języku XML format standardu Ecma i jest obecnie przechodzi przez proces normy ISO IEC.</span><span class="sxs-lookup"><span data-stu-id="b879e-106">Open XML is an XML-based format that an Ecma standard and is currently going through the ISO-IEC standards process.</span></span> <span data-ttu-id="b879e-107">Język znaczników dla edytora plików w Open XML nosi nazwę schemat WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="b879e-107">The markup language for word processing files within Open XML is called WordprocessingML.</span></span> <span data-ttu-id="b879e-108">Ten samouczek używa plików źródłowych schemat WordprocessingML jako dane wejściowe dla przykładów.</span><span class="sxs-lookup"><span data-stu-id="b879e-108">This tutorial uses WordprocessingML source files as input for the examples.</span></span>  
  
 <span data-ttu-id="b879e-109">Jeśli używasz programu Microsoft Office 2003 można zapisywać dokumenty w formacie Office Open XML po zainstalowaniu pakietu zgodności Microsoft Office dla programów Word, Excel i PowerPoint 2007.</span><span class="sxs-lookup"><span data-stu-id="b879e-109">If you are using Microsoft Office 2003, you can save documents in the Office Open XML format if you have installed the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="the-shape-of-wordprocessingml-documents"></a><span data-ttu-id="b879e-110">Kształt schemat WordprocessingML dokumentów</span><span class="sxs-lookup"><span data-stu-id="b879e-110">The Shape of WordprocessingML Documents</span></span>  
 <span data-ttu-id="b879e-111">Najpierw zrozumieć jest kształtu schemat WordprocessingML dokumentów.</span><span class="sxs-lookup"><span data-stu-id="b879e-111">The first thing to understand is the shape of WordprocessingML documents.</span></span> <span data-ttu-id="b879e-112">Schemat WordprocessingML dokument zawiera body element (o nazwie `w:body`) zawierający akapitów dokumentu.</span><span class="sxs-lookup"><span data-stu-id="b879e-112">A WordprocessingML document contains a body element (named `w:body`) that contains the paragraphs of the document.</span></span> <span data-ttu-id="b879e-113">Każdego akapitu zawiera co najmniej jeden przebieg tekstu (o nazwie `w:r`).</span><span class="sxs-lookup"><span data-stu-id="b879e-113">Each paragraph contains one or more text runs (named `w:r`).</span></span> <span data-ttu-id="b879e-114">Każdego tekstu Uruchom zawiera jeden lub kilka fragmentów tekstu (o nazwie `w:t`).</span><span class="sxs-lookup"><span data-stu-id="b879e-114">Each text run contains one or more text pieces (named `w:t`).</span></span>  
  
 <span data-ttu-id="b879e-115">Poniżej znajduje się bardzo proste dokumentu schemat WordprocessingML:</span><span class="sxs-lookup"><span data-stu-id="b879e-115">The following is a very simple WordprocessingML document:</span></span>  
  
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
  
 <span data-ttu-id="b879e-116">Ten dokument zawiera dwa akapitów.</span><span class="sxs-lookup"><span data-stu-id="b879e-116">This document contains two paragraphs.</span></span> <span data-ttu-id="b879e-117">Zawierają jeden tekst Uruchom, a każdy tekst Uruchom zawiera element jeden tekst.</span><span class="sxs-lookup"><span data-stu-id="b879e-117">They both contain a single text run, and each text run contains a single text piece.</span></span>  
  
 <span data-ttu-id="b879e-118">Najprostszym sposobem wyświetlenia zawartości dokumentu schemat WordprocessingML w postaci XML jest aby go utworzyć za pomocą programu Microsoft Word, zapisz go, a następnie uruchom następujący program, który wyświetla kod XML do konsoli.</span><span class="sxs-lookup"><span data-stu-id="b879e-118">The easiest way to see the contents of a WordprocessingML document in XML form is to create one using Microsoft Word, save it, and then run the following program that prints the XML to the console.</span></span>  
  
 <span data-ttu-id="b879e-119">W tym przykładzie użyto znaleziony w zestawie WindowsBase klasy.</span><span class="sxs-lookup"><span data-stu-id="b879e-119">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="b879e-120">Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b879e-120">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
## <a name="external-resources"></a><span data-ttu-id="b879e-121">Zasoby zewnętrzne</span><span class="sxs-lookup"><span data-stu-id="b879e-121">External Resources</span></span>  
 [<span data-ttu-id="b879e-122">Wprowadzenie do formatów pakietu Office (2007) Open XML</span><span class="sxs-lookup"><span data-stu-id="b879e-122">Introducing the Office (2007) Open XML File Formats</span></span>](http://go.microsoft.com/fwlink/?LinkId=98093)  
  
 [<span data-ttu-id="b879e-123">Omówienie schemat WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="b879e-123">Overview of WordprocessingML</span></span>](http://go.microsoft.com/fwlink/?LinkId=98094)  
  
 [<span data-ttu-id="b879e-124">Pakietu Office 2003: Strona pobierania schematy odwołanie XML</span><span class="sxs-lookup"><span data-stu-id="b879e-124">Office 2003: XML Reference Schemas Download page</span></span>](http://go.microsoft.com/fwlink/?LinkId=98095)  
  
## <a name="see-also"></a><span data-ttu-id="b879e-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b879e-125">See Also</span></span>  
 [<span data-ttu-id="b879e-126">Samouczek: Manipulowanie zawartości w dokumencie schemat WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b879e-126">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
