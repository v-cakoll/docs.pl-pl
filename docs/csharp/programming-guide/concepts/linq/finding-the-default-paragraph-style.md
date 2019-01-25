---
title: Znajdowanie domyślnego stylu akapitu (C#)
ms.date: 07/20/2015
ms.assetid: be102177-8ab0-444a-b671-7023e555ffdb
ms.openlocfilehash: 052accf31007001c0fa0d46870ee6e4cd30f6bb8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54674079"
---
# <a name="finding-the-default-paragraph-style-c"></a><span data-ttu-id="46ecf-102">Znajdowanie domyślnego stylu akapitu (C#)</span><span class="sxs-lookup"><span data-stu-id="46ecf-102">Finding the Default Paragraph Style (C#)</span></span>
<span data-ttu-id="46ecf-103">Pierwsze zadanie w manipulowanie informacje przedstawione w samouczku dokumentu WordprocessingML jest znajdowanie domyślnego stylu akapitów w dokumencie.</span><span class="sxs-lookup"><span data-stu-id="46ecf-103">The first task in the Manipulating Information in a WordprocessingML Document tutorial is to find the default style of paragraphs in the document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46ecf-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="46ecf-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="46ecf-105">Opis</span><span class="sxs-lookup"><span data-stu-id="46ecf-105">Description</span></span>  
 <span data-ttu-id="46ecf-106">Poniższy przykład spowoduje otwarcie dokumentu Office Open XML WordprocessingML, znajduje dokument i styl części pakietu, a następnie wykonuje zapytanie, które znajdzie domyślną nazwę stylu.</span><span class="sxs-lookup"><span data-stu-id="46ecf-106">The following example opens an Office Open XML WordprocessingML document, finds the document and style parts of the package, and then executes a query that finds the default style name.</span></span> <span data-ttu-id="46ecf-107">Dla informacji na temat pakietów dokumentu Office Open XML i części składają się one z [szczegóły dla dokumentów pakietu Office Open XML WordprocessingML (C#)](../../../../csharp/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md).</span><span class="sxs-lookup"><span data-stu-id="46ecf-107">For information about Office Open XML document packages, and the parts they consist of, see [Details of Office Open XML WordprocessingML Documents (C#)](../../../../csharp/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md).</span></span>  
  
 <span data-ttu-id="46ecf-108">Zapytanie znajdzie węzła o nazwie `w:style` zawierającego atrybut o nazwie `w:type` z wartością "akapitu", a także ma atrybut o nazwie `w:default` z wartością "1".</span><span class="sxs-lookup"><span data-stu-id="46ecf-108">The query finds a node named `w:style` that has an attribute named `w:type` with a value of "paragraph", and also has an attribute named `w:default` with a value of "1".</span></span> <span data-ttu-id="46ecf-109">Ponieważ będzie istniało tylko jeden węzeł XML za pomocą tych atrybutów, zapytanie używa <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operatora do przekonwertowania kolekcji na wzorzec singleton.</span><span class="sxs-lookup"><span data-stu-id="46ecf-109">Because there will be only one XML node with these attributes, the query uses the <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operator to convert a collection to a singleton.</span></span> <span data-ttu-id="46ecf-110">Następnie pobiera wartość atrybutu o nazwie `w:styleId`.</span><span class="sxs-lookup"><span data-stu-id="46ecf-110">It then gets the value of the attribute with the name `w:styleId`.</span></span>  
  
 <span data-ttu-id="46ecf-111">W tym przykładzie użyto klasy z zestawu WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="46ecf-111">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="46ecf-112">Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="46ecf-112">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
### <a name="code"></a><span data-ttu-id="46ecf-113">Kod</span><span class="sxs-lookup"><span data-stu-id="46ecf-113">Code</span></span>  
  
```csharp  
const string fileName = "SampleDoc.docx";  
  
const string documentRelationshipType =  
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";  
const string stylesRelationshipType =  
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles";  
const string wordmlNamespace =  
  "http://schemas.openxmlformats.org/wordprocessingml/2006/main";  
XNamespace w = wordmlNamespace;  
  
XDocument xDoc = null;  
XDocument styleDoc = null;  
  
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
        xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()));  
  
        //  Find the styles part. There will only be one.  
        PackageRelationship styleRelation =  
          documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault();  
        if (styleRelation != null)  
        {  
            Uri styleUri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri);  
            PackagePart stylePart = wdPackage.GetPart(styleUri);  
  
            //  Load the style XML in the part into an XDocument instance.  
            styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()));  
        }  
    }  
}  
  
// The following query finds all the paragraphs that have the default style.  
string defaultStyle =   
    (string)(  
        from style in styleDoc.Root.Elements(w + "style")  
        where (string)style.Attribute(w + "type") == "paragraph"&&  
              (string)style.Attribute(w + "default") == "1"  
              select style  
    ).First().Attribute(w + "styleId");  
  
Console.WriteLine("The default style is: {0}", defaultStyle);  
```  
  
### <a name="comments"></a><span data-ttu-id="46ecf-114">Komentarze</span><span class="sxs-lookup"><span data-stu-id="46ecf-114">Comments</span></span>  
 <span data-ttu-id="46ecf-115">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="46ecf-115">This example produces the following output:</span></span>  
  
```  
The default style is: Normal  
```  
  
## <a name="next-steps"></a><span data-ttu-id="46ecf-116">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="46ecf-116">Next Steps</span></span>  
 <span data-ttu-id="46ecf-117">W następnym przykładzie utworzysz podobne zapytanie, które umożliwia znalezienie wszystkich akapitów w dokumencie i ich stylów:</span><span class="sxs-lookup"><span data-stu-id="46ecf-117">In the next example, you'll create a similar query that finds all the paragraphs in a document and their styles:</span></span>  
  
-   [<span data-ttu-id="46ecf-118">Pobieranie akapitów i ich stylów (C#)</span><span class="sxs-lookup"><span data-stu-id="46ecf-118">Retrieving the Paragraphs and Their Styles (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md)  
  
## <a name="see-also"></a><span data-ttu-id="46ecf-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="46ecf-119">See also</span></span>

- [<span data-ttu-id="46ecf-120">Samouczek: Manipulowanie zawartością w dokumencie WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="46ecf-120">Tutorial: Manipulating Content in a WordprocessingML Document</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
