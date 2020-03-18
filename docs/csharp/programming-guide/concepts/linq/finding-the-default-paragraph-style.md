---
title: Znajdowanie domyślnego stylu akapitu (C#)
ms.date: 07/20/2015
ms.assetid: be102177-8ab0-444a-b671-7023e555ffdb
ms.openlocfilehash: 8cc1f1b9df208b0b180e5fe4a50922b5ee46b480
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169535"
---
# <a name="finding-the-default-paragraph-style-c"></a><span data-ttu-id="c8e8f-102">Znajdowanie domyślnego stylu akapitu (C#)</span><span class="sxs-lookup"><span data-stu-id="c8e8f-102">Finding the Default Paragraph Style (C#)</span></span>
<span data-ttu-id="c8e8f-103">Pierwszym zadaniem w samouczku Manipulowanie informacjami w samouczku dokumentu WordprocessingML jest znalezienie domyślnego stylu akapitów w dokumencie.</span><span class="sxs-lookup"><span data-stu-id="c8e8f-103">The first task in the Manipulating Information in a WordprocessingML Document tutorial is to find the default style of paragraphs in the document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8e8f-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="c8e8f-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="c8e8f-105">Opis</span><span class="sxs-lookup"><span data-stu-id="c8e8f-105">Description</span></span>  
 <span data-ttu-id="c8e8f-106">W poniższym przykładzie otwiera dokument Języka WordprocessingML pakietu Office Open, znajduje części dokumentu i stylu pakietu, a następnie wykonuje kwerendę, która znajduje domyślną nazwę stylu.</span><span class="sxs-lookup"><span data-stu-id="c8e8f-106">The following example opens an Office Open XML WordprocessingML document, finds the document and style parts of the package, and then executes a query that finds the default style name.</span></span> <span data-ttu-id="c8e8f-107">Aby uzyskać informacje o pakietach dokumentów XML pakietu Office Open i ich częściach, zobacz [Szczegóły dokumentów WordprocessingML pakietu Office (C#).](./wordprocessingml-document-with-styles.md)</span><span class="sxs-lookup"><span data-stu-id="c8e8f-107">For information about Office Open XML document packages, and the parts they consist of, see [Details of Office Open XML WordprocessingML Documents (C#)](./wordprocessingml-document-with-styles.md).</span></span>  
  
 <span data-ttu-id="c8e8f-108">Kwerenda znajduje węzeł `w:style` o nazwie, `w:type` który ma atrybut o nazwie o wartości `w:default` "akapit", a także ma atrybut o nazwie o wartości "1".</span><span class="sxs-lookup"><span data-stu-id="c8e8f-108">The query finds a node named `w:style` that has an attribute named `w:type` with a value of "paragraph", and also has an attribute named `w:default` with a value of "1".</span></span> <span data-ttu-id="c8e8f-109">Ponieważ będzie tylko jeden węzeł XML z tymi atrybutami, kwerenda używa <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operatora do konwersji kolekcji na singleton.</span><span class="sxs-lookup"><span data-stu-id="c8e8f-109">Because there will be only one XML node with these attributes, the query uses the <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operator to convert a collection to a singleton.</span></span> <span data-ttu-id="c8e8f-110">Następnie pobiera wartość atrybutu o `w:styleId`nazwie .</span><span class="sxs-lookup"><span data-stu-id="c8e8f-110">It then gets the value of the attribute with the name `w:styleId`.</span></span>  
  
 <span data-ttu-id="c8e8f-111">W tym przykładzie użyto klas z zestawu WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="c8e8f-111">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="c8e8f-112">Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="c8e8f-112">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c8e8f-113">Code</span><span class="sxs-lookup"><span data-stu-id="c8e8f-113">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="c8e8f-114">Komentarze</span><span class="sxs-lookup"><span data-stu-id="c8e8f-114">Comments</span></span>  
 <span data-ttu-id="c8e8f-115">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="c8e8f-115">This example produces the following output:</span></span>  
  
```output  
The default style is: Normal  
```  
  
## <a name="next-steps"></a><span data-ttu-id="c8e8f-116">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="c8e8f-116">Next Steps</span></span>  
 <span data-ttu-id="c8e8f-117">W następnym przykładzie utworzysz podobną kwerendę, która znajdzie wszystkie akapity w dokumencie i ich style:</span><span class="sxs-lookup"><span data-stu-id="c8e8f-117">In the next example, you'll create a similar query that finds all the paragraphs in a document and their styles:</span></span>  
  
- [<span data-ttu-id="c8e8f-118">Pobieranie akapitów i ich stylów (C#)</span><span class="sxs-lookup"><span data-stu-id="c8e8f-118">Retrieving the Paragraphs and Their Styles (C#)</span></span>](./retrieving-the-paragraphs-and-their-styles.md)  
