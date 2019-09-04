---
title: Pobieranie akapitów i ich stylów (C#)
ms.date: 07/20/2015
ms.assetid: c2f767f8-57b1-4b4b-af04-89ffb1f7067d
ms.openlocfilehash: ec59ef0ac36f8691ca93a4c21c5379118ee0491f
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253073"
---
# <a name="retrieving-the-paragraphs-and-their-styles-c"></a><span data-ttu-id="417a0-102">Pobieranie akapitów i ich stylów (C#)</span><span class="sxs-lookup"><span data-stu-id="417a0-102">Retrieving the Paragraphs and Their Styles (C#)</span></span>
<span data-ttu-id="417a0-103">W tym przykładzie napiszemy zapytanie, które pobiera węzły akapitu z dokumentu WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="417a0-103">In this example, we write a query that retrieves the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="417a0-104">Identyfikuje także styl każdego akapitu.</span><span class="sxs-lookup"><span data-stu-id="417a0-104">It also identifies the style of each paragraph.</span></span>  
  
 <span data-ttu-id="417a0-105">To zapytanie kompiluje zapytanie w poprzednim przykładzie, [wyszukując domyślny styl akapituC#()](./finding-the-default-paragraph-style.md), który Pobiera domyślny styl z listy stylów.</span><span class="sxs-lookup"><span data-stu-id="417a0-105">This query builds on the query in the previous example, [Finding the Default Paragraph Style (C#)](./finding-the-default-paragraph-style.md), which retrieves the default style from the list of styles.</span></span> <span data-ttu-id="417a0-106">Te informacje są wymagane, aby zapytanie mogło identyfikować styl akapitów, w których styl nie został jawnie ustawiony.</span><span class="sxs-lookup"><span data-stu-id="417a0-106">This information is required so that the query can identify the style of paragraphs that do not have a style explicitly set.</span></span> <span data-ttu-id="417a0-107">Style akapitu są ustawiane `w:pPr` za pomocą elementu. Jeśli akapit nie zawiera tego elementu, zostanie sformatowany przy użyciu stylu domyślnego.</span><span class="sxs-lookup"><span data-stu-id="417a0-107">Paragraph styles are set through the `w:pPr` element; if a paragraph does not contain this element, it is formatted with the default style.</span></span>  
  
 <span data-ttu-id="417a0-108">W tym temacie wyjaśniono znaczenie niektórych fragmentów zapytania, a następnie przedstawiono zapytanie w ramach kompletnego, działającego przykładu.</span><span class="sxs-lookup"><span data-stu-id="417a0-108">This topic explains the significance of some pieces of the query, then shows the query as part of a complete, working example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="417a0-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="417a0-109">Example</span></span>  
 <span data-ttu-id="417a0-110">Źródło zapytania do pobrania wszystkich akapitów w dokumencie i ich stylów jest następująca:</span><span class="sxs-lookup"><span data-stu-id="417a0-110">The source of the query to retrieve all the paragraphs in a document and their styles is as follows:</span></span>  
  
```csharp  
xDoc.Root.Element(w + "body").Descendants(w + "p")  
```  
  
 <span data-ttu-id="417a0-111">To wyrażenie jest podobne do źródła zapytania w poprzednim przykładzie, co umożliwia [znalezienie domyślnego stylu akapitu (C#)](./finding-the-default-paragraph-style.md).</span><span class="sxs-lookup"><span data-stu-id="417a0-111">This expression is similar to the source of the query in the previous example, [Finding the Default Paragraph Style (C#)](./finding-the-default-paragraph-style.md).</span></span> <span data-ttu-id="417a0-112">Główną różnicą jest to, że używa <xref:System.Xml.Linq.XContainer.Descendants%2A> osi zamiast <xref:System.Xml.Linq.XContainer.Elements%2A> osi.</span><span class="sxs-lookup"><span data-stu-id="417a0-112">The main difference is that it uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis instead of the <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span> <span data-ttu-id="417a0-113">Zapytanie używa <xref:System.Xml.Linq.XContainer.Descendants%2A> osi, ponieważ w dokumentach, w których znajdują się sekcje, akapity nie będą bezpośrednimi elementami podrzędnymi elementu body, a akapity będą dwa poziomy w hierarchii.</span><span class="sxs-lookup"><span data-stu-id="417a0-113">The query uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis because in documents that have sections, the paragraphs will not be the direct children of the body element; rather, the paragraphs will be two levels down in the hierarchy.</span></span> <span data-ttu-id="417a0-114">Korzystając <xref:System.Xml.Linq.XContainer.Descendants%2A> z osi, kod będzie działał niezależnie od tego, czy dokument korzysta z sekcji.</span><span class="sxs-lookup"><span data-stu-id="417a0-114">By using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis, the code will work of whether or not the document uses sections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="417a0-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="417a0-115">Example</span></span>  
 <span data-ttu-id="417a0-116">Zapytanie używa `let` klauzuli do określenia elementu, który zawiera węzeł stylu.</span><span class="sxs-lookup"><span data-stu-id="417a0-116">The query uses a `let` clause to determine the element that contains the style node.</span></span> <span data-ttu-id="417a0-117">Jeśli nie ma elementu, `styleNode` zostanie `null`ustawiona wartość:</span><span class="sxs-lookup"><span data-stu-id="417a0-117">If there is no element, then `styleNode` is set to `null`:</span></span>  
  
```csharp  
let styleNode = para.Elements(w + "pPr").Elements(w + "pStyle").FirstOrDefault()  
```  
  
 <span data-ttu-id="417a0-118">`pPr` <xref:System.Xml.Linq.Extensions.Elements%2A> `pStyle` <xref:System.Linq.Enumerable.FirstOrDefault%2A> Klauzula najpierw <xref:System.Xml.Linq.XContainer.Elements%2A> używa osi, aby znaleźć wszystkie elementy o nazwie, następnie używa metody rozszerzenia do znajdowania wszystkich elementów podrzędnych o nazwie, a wreszcie używa zapytania standardowego `let` operator do konwersji kolekcji na pojedynczą.</span><span class="sxs-lookup"><span data-stu-id="417a0-118">The `let` clause first uses the <xref:System.Xml.Linq.XContainer.Elements%2A> axis to find all elements named `pPr`, then uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method to find all child elements named `pStyle`, and finally uses the <xref:System.Linq.Enumerable.FirstOrDefault%2A> standard query operator to convert the collection to a singleton.</span></span> <span data-ttu-id="417a0-119">Jeśli kolekcja jest pusta, `styleNode` jest ustawiona na. `null`</span><span class="sxs-lookup"><span data-stu-id="417a0-119">If the collection is empty, `styleNode` is set to `null`.</span></span> <span data-ttu-id="417a0-120">Jest to przydatny idiom do wyszukiwania `pStyle` węzła podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="417a0-120">This is a useful idiom to look for the `pStyle` descendant node.</span></span> <span data-ttu-id="417a0-121">Należy pamiętać, że `pPr` Jeśli węzeł podrzędny nie istnieje, kod jest lub nie powiedzie się, zwracając wyjątek; `styleNode` zamiast tego jest ustawiony `null`na, który jest pożądanym zachowaniem tej `let` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="417a0-121">Note that if the `pPr` child node does not exist, the code does nor fail by throwing an exception; instead, `styleNode` is set to `null`, which is the desired behavior of this `let` clause.</span></span>  
  
 <span data-ttu-id="417a0-122">Zapytanie projektuje kolekcję typu anonimowego z dwoma członkami `StyleName` i. `ParagraphNode`</span><span class="sxs-lookup"><span data-stu-id="417a0-122">The query projects a collection of an anonymous type with two members, `StyleName` and `ParagraphNode`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="417a0-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="417a0-123">Example</span></span>  
 <span data-ttu-id="417a0-124">Ten przykład przetwarza dokument WordprocessingML, pobierając węzły akapitu z dokumentu WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="417a0-124">This example processes a WordprocessingML document, retrieving the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="417a0-125">Identyfikuje także styl każdego akapitu.</span><span class="sxs-lookup"><span data-stu-id="417a0-125">It also identifies the style of each paragraph.</span></span> <span data-ttu-id="417a0-126">Ten przykład kompiluje się zgodnie z poprzednimi przykładami w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="417a0-126">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="417a0-127">Nowe zapytanie jest wywoływane w komentarzach w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="417a0-127">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="417a0-128">Instrukcje dotyczące tworzenia dokumentu źródłowego dla tego przykładu można znaleźć w temacie [Tworzenie źródłowego dokumentu Office Open XMLC#()](./creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="417a0-128">You can find instructions for creating the source document for this example in [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="417a0-129">Ten przykład używa klas znalezionych w zestawie 'Windowsbase.</span><span class="sxs-lookup"><span data-stu-id="417a0-129">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="417a0-130">Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="417a0-130">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```csharp  
const string fileName = "SampleDoc.docx";  
  
const string documentRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";  
const string stylesRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles";  
const string wordmlNamespace = "http://schemas.openxmlformats.org/wordprocessingml/2006/main";  
XNamespace w = wordmlNamespace;  
  
XDocument xDoc = null;  
XDocument styleDoc = null;  
  
using (Package wdPackage = Package.Open(fileName, FileMode.Open, FileAccess.Read))  
{  
    PackageRelationship docPackageRelationship = wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault();  
    if (docPackageRelationship != null)  
    {  
        Uri documentUri = PackUriHelper.ResolvePartUri(new Uri("/", UriKind.Relative), docPackageRelationship.TargetUri);  
        PackagePart documentPart = wdPackage.GetPart(documentUri);  
  
        //  Load the document XML in the part into an XDocument instance.  
        xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()));  
  
        //  Find the styles part. There will only be one.  
        PackageRelationship styleRelation = documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault();  
        if (styleRelation != null)  
        {  
            Uri styleUri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri);  
            PackagePart stylePart = wdPackage.GetPart(styleUri);  
  
            //  Load the style XML in the part into an XDocument instance.  
            styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()));  
        }  
    }  
}  
  
string defaultStyle =   
    (string)(  
        from style in styleDoc.Root.Elements(w + "style")  
        where (string)style.Attribute(w + "type") == "paragraph"&&  
              (string)style.Attribute(w + "default") == "1"  
              select style  
    ).First().Attribute(w + "styleId");  
  
// Following is the new query that finds all paragraphs in the  
// document and their styles.  
var paragraphs =  
    from para in xDoc  
                 .Root  
                 .Element(w + "body")  
                 .Descendants(w + "p")  
    let styleNode = para  
                    .Elements(w + "pPr")  
                    .Elements(w + "pStyle")  
                    .FirstOrDefault()  
    select new  
    {  
        ParagraphNode = para,  
        StyleName = styleNode != null ?  
            (string)styleNode.Attribute(w + "val") :  
            defaultStyle  
    };  
  
foreach (var p in paragraphs)  
    Console.WriteLine("StyleName:{0}", p.StyleName);  
```  
  
 <span data-ttu-id="417a0-131">Ten przykład generuje następujące dane wyjściowe w przypadku zastosowania do dokumentu opisanego w temacie [Tworzenie źródłowego dokumentu Office Open XML (C#)](./creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="417a0-131">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
```output  
StyleName:Heading1  
StyleName:Normal  
StyleName:Normal  
StyleName:Normal  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Normal  
StyleName:Normal  
StyleName:Normal  
StyleName:Code  
```  
  
## <a name="next-steps"></a><span data-ttu-id="417a0-132">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="417a0-132">Next Steps</span></span>  
 <span data-ttu-id="417a0-133">W następnym temacie, [pobierając tekst akapitówC#()](./retrieving-the-text-of-the-paragraphs.md), utworzysz zapytanie umożliwiające pobranie tekstu akapitów.</span><span class="sxs-lookup"><span data-stu-id="417a0-133">In the next topic, [Retrieving the Text of the Paragraphs (C#)](./retrieving-the-text-of-the-paragraphs.md), you'll create a query to retrieve the text of paragraphs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="417a0-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="417a0-134">See also</span></span>

- [<span data-ttu-id="417a0-135">Samouczek: Manipulowanie zawartością w dokumencie WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="417a0-135">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](./shape-of-wordprocessingml-documents.md)
