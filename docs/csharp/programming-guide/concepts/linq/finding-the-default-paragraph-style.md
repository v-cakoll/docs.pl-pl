---
title: Znajdowanie domyślny styl akapitu (C#)
ms.date: 07/20/2015
ms.assetid: be102177-8ab0-444a-b671-7023e555ffdb
ms.openlocfilehash: e29ca281e1867a72a76a28765912c39675ca0f27
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33335955"
---
# <a name="finding-the-default-paragraph-style-c"></a><span data-ttu-id="d9890-102">Znajdowanie domyślny styl akapitu (C#)</span><span class="sxs-lookup"><span data-stu-id="d9890-102">Finding the Default Paragraph Style (C#)</span></span>
<span data-ttu-id="d9890-103">Pierwszym zadaniem manipulowanie dane w samouczku schemat WordprocessingML dokumentu jest można znaleźć w dokumencie domyślny styl akapitów.</span><span class="sxs-lookup"><span data-stu-id="d9890-103">The first task in the Manipulating Information in a WordprocessingML Document tutorial is to find the default style of paragraphs in the document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9890-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="d9890-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="d9890-105">Opis</span><span class="sxs-lookup"><span data-stu-id="d9890-105">Description</span></span>  
 <span data-ttu-id="d9890-106">Poniższy przykład powoduje otwarcie dokumentu schemat WordprocessingML Office Open XML, znajduje dokumentu i styl części pakietu, a następnie wykonuje kwerendę, która wyszukuje domyślną nazwę stylu.</span><span class="sxs-lookup"><span data-stu-id="d9890-106">The following example opens an Office Open XML WordprocessingML document, finds the document and style parts of the package, and then executes a query that finds the default style name.</span></span> <span data-ttu-id="d9890-107">Aby uzyskać informacje o pakietach dokumentu pakietu Office Open XML i części składają się z, zobacz [szczegóły z dokumentów pakietu Office Open XML schemat WordprocessingML (C#)](../../../../csharp/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md).</span><span class="sxs-lookup"><span data-stu-id="d9890-107">For information about Office Open XML document packages, and the parts they consist of, see [Details of Office Open XML WordprocessingML Documents (C#)](../../../../csharp/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md).</span></span>  
  
 <span data-ttu-id="d9890-108">Zapytanie znajdzie węzła o nazwie `w:style` zawierającego atrybut o nazwie `w:type` o wartości "akapitu", a także ma atrybut o nazwie `w:default` o wartości "1".</span><span class="sxs-lookup"><span data-stu-id="d9890-108">The query finds a node named `w:style` that has an attribute named `w:type` with a value of "paragraph", and also has an attribute named `w:default` with a value of "1".</span></span> <span data-ttu-id="d9890-109">Ponieważ będzie istniało tylko jeden węzeł XML z tymi atrybutami, zapytanie używa <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operatora, aby przekonwertować kolekcji jako pojedyncza.</span><span class="sxs-lookup"><span data-stu-id="d9890-109">Because there will be only one XML node with these attributes, the query uses the <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operator to convert a collection to a singleton.</span></span> <span data-ttu-id="d9890-110">Następnie pobiera wartość atrybutu o nazwie `w:styleId`.</span><span class="sxs-lookup"><span data-stu-id="d9890-110">It then gets the value of the attribute with the name `w:styleId`.</span></span>  
  
 <span data-ttu-id="d9890-111">W tym przykładzie użyto klasy z zestawu WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="d9890-111">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="d9890-112">Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d9890-112">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
### <a name="code"></a><span data-ttu-id="d9890-113">Kod</span><span class="sxs-lookup"><span data-stu-id="d9890-113">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="d9890-114">Komentarze</span><span class="sxs-lookup"><span data-stu-id="d9890-114">Comments</span></span>  
 <span data-ttu-id="d9890-115">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="d9890-115">This example produces the following output:</span></span>  
  
```  
The default style is: Normal  
```  
  
## <a name="next-steps"></a><span data-ttu-id="d9890-116">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="d9890-116">Next Steps</span></span>  
 <span data-ttu-id="d9890-117">W następnym przykładzie utworzysz podobne kwerendę, która wyszukuje wszystkie akapity w dokumencie i ich style:</span><span class="sxs-lookup"><span data-stu-id="d9890-117">In the next example, you'll create a similar query that finds all the paragraphs in a document and their styles:</span></span>  
  
-   [<span data-ttu-id="d9890-118">Trwa pobieranie akapitów i ich style (C#)</span><span class="sxs-lookup"><span data-stu-id="d9890-118">Retrieving the Paragraphs and Their Styles (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md)  
  
## <a name="see-also"></a><span data-ttu-id="d9890-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d9890-119">See Also</span></span>  
 [<span data-ttu-id="d9890-120">Samouczek: manipulowanie zawartością w dokumencie WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="d9890-120">Tutorial: Manipulating Content in a WordprocessingML Document</span></span>](http://msdn.microsoft.com/library/2696355e-4f83-4eaf-91b2-baa721f42fb4)
