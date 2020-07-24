---
title: Przykład, który wyprowadza fragmenty dokumentu Office Open XML (C#)
description: Dowiedz się, jak otworzyć dokument pakietu Office Open XML i uzyskać dostęp do jego części za pomocą LINQ w języku C#. Ten przykład drukuje część dokumentu oraz część stylu dokumentu.
ms.date: 07/20/2015
ms.assetid: 6cd37055-89b4-42e8-bf27-5a29717e35f3
ms.openlocfilehash: c5755ad8e8772195c056b0c1c896c914b1a63a55
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103915"
---
# <a name="example-that-outputs-office-open-xml-document-parts-c"></a><span data-ttu-id="06038-104">Przykład, który wyprowadza fragmenty dokumentu Office Open XML (C#)</span><span class="sxs-lookup"><span data-stu-id="06038-104">Example that Outputs Office Open XML Document Parts (C#)</span></span>
<span data-ttu-id="06038-105">W tym temacie przedstawiono sposób otwierania dokumentu Office Open XML i części dostępu w nim.</span><span class="sxs-lookup"><span data-stu-id="06038-105">This topic shows how to open an Office Open XML document and access parts within it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06038-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="06038-106">Example</span></span>  
 <span data-ttu-id="06038-107">Poniższy przykład otwiera dokument Office Open XML i drukuje część dokumentu oraz część stylu do konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="06038-107">The following example opens an Office Open XML document, and prints the document part and the style part to the console.</span></span>  
  
 <span data-ttu-id="06038-108">W tym przykładzie zastosowano klasy z zestawu 'Windowsbase.</span><span class="sxs-lookup"><span data-stu-id="06038-108">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="06038-109">Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="06038-109">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```csharp  
const string fileName = "SampleDoc.docx";  
  
const string documentRelationshipType =  
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";  
const string stylesRelationshipType =  
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles";  
const string wordmlNamespace =  
  "http://schemas.openxmlformats.org/wordprocessingml/2006/main";  
XNamespace w = wordmlNamespace;  
  
using (Package wdPackage = Package.Open(fileName, FileMode.Open, FileAccess.Read))  
{  
    PackageRelationship docPackageRelationship =  
      wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault();  
    if (docPackageRelationship != null)  
    {  
        Uri documentUri = PackUriHelper.ResolvePartUri(new Uri("/", UriKind.Relative),  
          docPackageRelationship.TargetUri);  
        PackagePart documentPart = wdPackage.GetPart(documentUri);  
  
        //  Load the document XML in the part into an XDocument instance.  
        XDocument xdoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()));  
  
        Console.WriteLine("TargetUri:{0}", docPackageRelationship.TargetUri);  
        Console.WriteLine("==================================================================");  
        Console.WriteLine(xdoc.Root);  
        Console.WriteLine();  
  
        //  Find the styles part. There will only be one.  
        PackageRelationship styleRelation =  
          documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault();  
        if (styleRelation != null)  
        {  
            Uri styleUri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri);  
            PackagePart stylePart = wdPackage.GetPart(styleUri);  
  
            //  Load the style XML in the part into an XDocument instance.  
            XDocument styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()));  
  
            Console.WriteLine("TargetUri:{0}", styleRelation.TargetUri);  
            Console.WriteLine("==================================================================");  
            Console.WriteLine(styleDoc.Root);  
            Console.WriteLine();  
        }  
    }  
}  
```  
