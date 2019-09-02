---
title: Znajdowanie domyślnego stylu akapitu (C#)
ms.date: 07/20/2015
ms.assetid: be102177-8ab0-444a-b671-7023e555ffdb
ms.openlocfilehash: 45a3e293a88fc0d7fc6aa70d21d1d3a6a8bb9b13
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204107"
---
# <a name="finding-the-default-paragraph-style-c"></a><span data-ttu-id="059e8-102">Znajdowanie domyślnego stylu akapitu (C#)</span><span class="sxs-lookup"><span data-stu-id="059e8-102">Finding the Default Paragraph Style (C#)</span></span>
<span data-ttu-id="059e8-103">Pierwsze zadanie w informacjach manipulowania w programie WordprocessingML Documents to znalezienie domyślnego stylu akapitów w dokumencie.</span><span class="sxs-lookup"><span data-stu-id="059e8-103">The first task in the Manipulating Information in a WordprocessingML Document tutorial is to find the default style of paragraphs in the document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="059e8-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="059e8-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="059e8-105">Opis</span><span class="sxs-lookup"><span data-stu-id="059e8-105">Description</span></span>  
 <span data-ttu-id="059e8-106">W poniższym przykładzie zostanie otwarty dokument pakietu Office Open XML WordprocessingML, znajduje się w nim części dokumentu i stylu pakietu, a następnie wykonywana jest kwerenda, która znajduje domyślną nazwę stylu.</span><span class="sxs-lookup"><span data-stu-id="059e8-106">The following example opens an Office Open XML WordprocessingML document, finds the document and style parts of the package, and then executes a query that finds the default style name.</span></span> <span data-ttu-id="059e8-107">Aby uzyskać informacje na temat pakietów dokumentów Office Open XML i części, które składają się z, zobacz [Szczegóły pakietu Office Open XML WordprocessingMLC#Documents ()](./wordprocessingml-document-with-styles.md).</span><span class="sxs-lookup"><span data-stu-id="059e8-107">For information about Office Open XML document packages, and the parts they consist of, see [Details of Office Open XML WordprocessingML Documents (C#)](./wordprocessingml-document-with-styles.md).</span></span>  
  
 <span data-ttu-id="059e8-108">Zapytanie znajduje węzeł o nazwie `w:style` , który ma atrybut o nazwie `w:type` o wartości "Paragraph", a także ma atrybut o nazwie `w:default` o wartości "1".</span><span class="sxs-lookup"><span data-stu-id="059e8-108">The query finds a node named `w:style` that has an attribute named `w:type` with a value of "paragraph", and also has an attribute named `w:default` with a value of "1".</span></span> <span data-ttu-id="059e8-109">Ponieważ będzie istnieć tylko jeden węzeł XML z tymi atrybutami, zapytanie używa <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operatora do konwersji kolekcji na pojedynczą.</span><span class="sxs-lookup"><span data-stu-id="059e8-109">Because there will be only one XML node with these attributes, the query uses the <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operator to convert a collection to a singleton.</span></span> <span data-ttu-id="059e8-110">Następnie pobiera wartość atrybutu o nazwie `w:styleId`.</span><span class="sxs-lookup"><span data-stu-id="059e8-110">It then gets the value of the attribute with the name `w:styleId`.</span></span>  
  
 <span data-ttu-id="059e8-111">W tym przykładzie zastosowano klasy z zestawu 'Windowsbase.</span><span class="sxs-lookup"><span data-stu-id="059e8-111">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="059e8-112">Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="059e8-112">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
### <a name="code"></a><span data-ttu-id="059e8-113">Kod</span><span class="sxs-lookup"><span data-stu-id="059e8-113">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="059e8-114">Komentarze</span><span class="sxs-lookup"><span data-stu-id="059e8-114">Comments</span></span>  
 <span data-ttu-id="059e8-115">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="059e8-115">This example produces the following output:</span></span>  
  
```output  
The default style is: Normal  
```  
  
## <a name="next-steps"></a><span data-ttu-id="059e8-116">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="059e8-116">Next Steps</span></span>  
 <span data-ttu-id="059e8-117">W następnym przykładzie utworzysz podobne zapytanie, które znajdzie wszystkie akapity w dokumencie i ich style:</span><span class="sxs-lookup"><span data-stu-id="059e8-117">In the next example, you'll create a similar query that finds all the paragraphs in a document and their styles:</span></span>  
  
- [<span data-ttu-id="059e8-118">Pobieranie akapitów i ich stylów (C#)</span><span class="sxs-lookup"><span data-stu-id="059e8-118">Retrieving the Paragraphs and Their Styles (C#)</span></span>](./retrieving-the-paragraphs-and-their-styles.md)  
