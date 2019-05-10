---
title: Znajdowanie domyślnego stylu akapitu (C#)
ms.date: 07/20/2015
ms.assetid: be102177-8ab0-444a-b671-7023e555ffdb
ms.openlocfilehash: 89c70fcbc9d5286e2c9381250b30d525ebb1eb36
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64596699"
---
# <a name="finding-the-default-paragraph-style-c"></a><span data-ttu-id="71b26-102">Znajdowanie domyślnego stylu akapitu (C#)</span><span class="sxs-lookup"><span data-stu-id="71b26-102">Finding the Default Paragraph Style (C#)</span></span>
<span data-ttu-id="71b26-103">Pierwsze zadanie w manipulowanie informacje przedstawione w samouczku dokumentu WordprocessingML jest znajdowanie domyślnego stylu akapitów w dokumencie.</span><span class="sxs-lookup"><span data-stu-id="71b26-103">The first task in the Manipulating Information in a WordprocessingML Document tutorial is to find the default style of paragraphs in the document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71b26-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="71b26-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="71b26-105">Opis</span><span class="sxs-lookup"><span data-stu-id="71b26-105">Description</span></span>  
 <span data-ttu-id="71b26-106">Poniższy przykład spowoduje otwarcie dokumentu Office Open XML WordprocessingML, znajduje dokument i styl części pakietu, a następnie wykonuje zapytanie, które znajdzie domyślną nazwę stylu.</span><span class="sxs-lookup"><span data-stu-id="71b26-106">The following example opens an Office Open XML WordprocessingML document, finds the document and style parts of the package, and then executes a query that finds the default style name.</span></span> <span data-ttu-id="71b26-107">Dla informacji na temat pakietów dokumentu Office Open XML i części składają się one z [szczegóły dla dokumentów pakietu Office Open XML WordprocessingML (C#)](../../../../csharp/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md).</span><span class="sxs-lookup"><span data-stu-id="71b26-107">For information about Office Open XML document packages, and the parts they consist of, see [Details of Office Open XML WordprocessingML Documents (C#)](../../../../csharp/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md).</span></span>  
  
 <span data-ttu-id="71b26-108">Zapytanie znajdzie węzła o nazwie `w:style` zawierającego atrybut o nazwie `w:type` z wartością "akapitu", a także ma atrybut o nazwie `w:default` z wartością "1".</span><span class="sxs-lookup"><span data-stu-id="71b26-108">The query finds a node named `w:style` that has an attribute named `w:type` with a value of "paragraph", and also has an attribute named `w:default` with a value of "1".</span></span> <span data-ttu-id="71b26-109">Ponieważ będzie istniało tylko jeden węzeł XML za pomocą tych atrybutów, zapytanie używa <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operatora do przekonwertowania kolekcji na wzorzec singleton.</span><span class="sxs-lookup"><span data-stu-id="71b26-109">Because there will be only one XML node with these attributes, the query uses the <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operator to convert a collection to a singleton.</span></span> <span data-ttu-id="71b26-110">Następnie pobiera wartość atrybutu o nazwie `w:styleId`.</span><span class="sxs-lookup"><span data-stu-id="71b26-110">It then gets the value of the attribute with the name `w:styleId`.</span></span>  
  
 <span data-ttu-id="71b26-111">W tym przykładzie użyto klasy z zestawu WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="71b26-111">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="71b26-112">Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="71b26-112">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
### <a name="code"></a><span data-ttu-id="71b26-113">Kod</span><span class="sxs-lookup"><span data-stu-id="71b26-113">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="71b26-114">Komentarze</span><span class="sxs-lookup"><span data-stu-id="71b26-114">Comments</span></span>  
 <span data-ttu-id="71b26-115">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="71b26-115">This example produces the following output:</span></span>  
  
```  
The default style is: Normal  
```  
  
## <a name="next-steps"></a><span data-ttu-id="71b26-116">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="71b26-116">Next Steps</span></span>  
 <span data-ttu-id="71b26-117">W następnym przykładzie utworzysz podobne zapytanie, które umożliwia znalezienie wszystkich akapitów w dokumencie i ich stylów:</span><span class="sxs-lookup"><span data-stu-id="71b26-117">In the next example, you'll create a similar query that finds all the paragraphs in a document and their styles:</span></span>  
  
- [<span data-ttu-id="71b26-118">Pobieranie akapitów i ich stylów (C#)</span><span class="sxs-lookup"><span data-stu-id="71b26-118">Retrieving the Paragraphs and Their Styles (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md)  
  
## <a name="see-also"></a><span data-ttu-id="71b26-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="71b26-119">See also</span></span>

- [<span data-ttu-id="71b26-120">Samouczek: Manipulowanie zawartością w dokumencie WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="71b26-120">Tutorial: Manipulating Content in a WordprocessingML Document</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
