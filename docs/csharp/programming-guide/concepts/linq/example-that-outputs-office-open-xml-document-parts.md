---
title: Przykład danych wyjściowych części dokumentu programu Office Open XML (C#)
ms.date: 07/20/2015
ms.assetid: 6cd37055-89b4-42e8-bf27-5a29717e35f3
ms.openlocfilehash: e63f6eafb32a6426d6c3fd7296c0e8fa6595efee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="example-that-outputs-office-open-xml-document-parts-c"></a><span data-ttu-id="6149c-102">Przykład danych wyjściowych części dokumentu programu Office Open XML (C#)</span><span class="sxs-lookup"><span data-stu-id="6149c-102">Example that Outputs Office Open XML Document Parts (C#)</span></span>
<span data-ttu-id="6149c-103">W tym temacie pokazano, jak otworzyć dokument XML otwórz pakietu Office i dostępu do części w niej.</span><span class="sxs-lookup"><span data-stu-id="6149c-103">This topic shows how to open an Office Open XML document and access parts within it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6149c-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="6149c-104">Example</span></span>  
 <span data-ttu-id="6149c-105">Poniższy przykład powoduje otwarcie dokumentu pakietu Office Open XML, a następnie drukuje dokument i część stylu w konsoli.</span><span class="sxs-lookup"><span data-stu-id="6149c-105">The following example opens an Office Open XML document, and prints the document part and the style part to the console.</span></span>  
  
 <span data-ttu-id="6149c-106">W tym przykładzie użyto klasy z zestawu WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="6149c-106">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="6149c-107">Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="6149c-107">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6149c-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6149c-108">See Also</span></span>  
 [<span data-ttu-id="6149c-109">Szczegóły pakietu Office otwieranie dokumentów schemat WordprocessingML XML (C#)</span><span class="sxs-lookup"><span data-stu-id="6149c-109">Details of Office Open XML WordprocessingML Documents (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md)
