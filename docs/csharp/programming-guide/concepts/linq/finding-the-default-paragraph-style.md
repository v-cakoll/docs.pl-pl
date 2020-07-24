---
title: Znajdowanie domyślnego stylu akapitu (C#)
description: Dowiedz się, jak przetwarzać dokument WordprocessingML za pomocą LINQ w języku C#. Ten przykład umożliwia znalezienie domyślnego stylu akapitów w dokumencie.
ms.date: 07/20/2015
ms.assetid: be102177-8ab0-444a-b671-7023e555ffdb
ms.openlocfilehash: e18bbbdbd5b2627c9ff4c3c3eedd84d7cb166a62
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103827"
---
# <a name="finding-the-default-paragraph-style-c"></a><span data-ttu-id="483c3-104">Znajdowanie domyślnego stylu akapitu (C#)</span><span class="sxs-lookup"><span data-stu-id="483c3-104">Finding the Default Paragraph Style (C#)</span></span>
<span data-ttu-id="483c3-105">Pierwsze zadanie w informacjach manipulowania w programie WordprocessingML Documents to znalezienie domyślnego stylu akapitów w dokumencie.</span><span class="sxs-lookup"><span data-stu-id="483c3-105">The first task in the Manipulating Information in a WordprocessingML Document tutorial is to find the default style of paragraphs in the document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="483c3-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="483c3-106">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="483c3-107">Opis</span><span class="sxs-lookup"><span data-stu-id="483c3-107">Description</span></span>  
 <span data-ttu-id="483c3-108">W poniższym przykładzie zostanie otwarty dokument pakietu Office Open XML WordprocessingML, znajduje się w nim części dokumentu i stylu pakietu, a następnie wykonywana jest kwerenda, która znajduje domyślną nazwę stylu.</span><span class="sxs-lookup"><span data-stu-id="483c3-108">The following example opens an Office Open XML WordprocessingML document, finds the document and style parts of the package, and then executes a query that finds the default style name.</span></span> <span data-ttu-id="483c3-109">Aby uzyskać informacje na temat pakietów dokumentów Office Open XML i części, które składają się z, zobacz [szczegóły dotyczące dokumentów pakietu Office Open XML WordprocessingML (C#)](./wordprocessingml-document-with-styles.md).</span><span class="sxs-lookup"><span data-stu-id="483c3-109">For information about Office Open XML document packages, and the parts they consist of, see [Details of Office Open XML WordprocessingML Documents (C#)](./wordprocessingml-document-with-styles.md).</span></span>  
  
 <span data-ttu-id="483c3-110">Zapytanie znajduje węzeł o nazwie `w:style` , który ma atrybut o nazwie o `w:type` wartości "Paragraph", a także ma atrybut o nazwie o `w:default` wartości "1".</span><span class="sxs-lookup"><span data-stu-id="483c3-110">The query finds a node named `w:style` that has an attribute named `w:type` with a value of "paragraph", and also has an attribute named `w:default` with a value of "1".</span></span> <span data-ttu-id="483c3-111">Ponieważ będzie istnieć tylko jeden węzeł XML z tymi atrybutami, zapytanie używa <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operatora do konwersji kolekcji na pojedynczą.</span><span class="sxs-lookup"><span data-stu-id="483c3-111">Because there will be only one XML node with these attributes, the query uses the <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operator to convert a collection to a singleton.</span></span> <span data-ttu-id="483c3-112">Następnie pobiera wartość atrybutu o nazwie `w:styleId` .</span><span class="sxs-lookup"><span data-stu-id="483c3-112">It then gets the value of the attribute with the name `w:styleId`.</span></span>  
  
 <span data-ttu-id="483c3-113">W tym przykładzie zastosowano klasy z zestawu 'Windowsbase.</span><span class="sxs-lookup"><span data-stu-id="483c3-113">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="483c3-114">Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="483c3-114">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
### <a name="code"></a><span data-ttu-id="483c3-115">Kod</span><span class="sxs-lookup"><span data-stu-id="483c3-115">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="483c3-116">Komentarze</span><span class="sxs-lookup"><span data-stu-id="483c3-116">Comments</span></span>  
 <span data-ttu-id="483c3-117">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="483c3-117">This example produces the following output:</span></span>  
  
```output  
The default style is: Normal  
```  
  
## <a name="next-steps"></a><span data-ttu-id="483c3-118">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="483c3-118">Next Steps</span></span>  
 <span data-ttu-id="483c3-119">W następnym przykładzie utworzysz podobne zapytanie, które znajdzie wszystkie akapity w dokumencie i ich style:</span><span class="sxs-lookup"><span data-stu-id="483c3-119">In the next example, you'll create a similar query that finds all the paragraphs in a document and their styles:</span></span>  
  
- [<span data-ttu-id="483c3-120">Pobieranie akapitów i ich stylów (C#)</span><span class="sxs-lookup"><span data-stu-id="483c3-120">Retrieving the Paragraphs and Their Styles (C#)</span></span>](./retrieving-the-paragraphs-and-their-styles.md)  
