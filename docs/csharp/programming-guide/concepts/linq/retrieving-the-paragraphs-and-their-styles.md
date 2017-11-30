---
title: "Trwa pobieranie akapitów i ich style (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: c2f767f8-57b1-4b4b-af04-89ffb1f7067d
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d7619ede02e9a384ddceec23a232a53de1dad0aa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="retrieving-the-paragraphs-and-their-styles-c"></a><span data-ttu-id="d3ed6-102">Trwa pobieranie akapitów i ich style (C#)</span><span class="sxs-lookup"><span data-stu-id="d3ed6-102">Retrieving the Paragraphs and Their Styles (C#)</span></span>
<span data-ttu-id="d3ed6-103">W tym przykładzie mamy Napisz zapytanie, które pobiera węzły akapitu z dokumentu schemat WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="d3ed6-103">In this example, we write a query that retrieves the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="d3ed6-104">Identyfikuje styl każdego akapitu.</span><span class="sxs-lookup"><span data-stu-id="d3ed6-104">It also identifies the style of each paragraph.</span></span>  
  
 <span data-ttu-id="d3ed6-105">To zapytanie opiera się na zapytanie w poprzednim przykładzie [znajdowanie domyślny styl akapitu (C#)](../../../../csharp/programming-guide/concepts/linq/finding-the-default-paragraph-style.md), który pobiera styl domyślny z listy stylów.</span><span class="sxs-lookup"><span data-stu-id="d3ed6-105">This query builds on the query in the previous example, [Finding the Default Paragraph Style (C#)](../../../../csharp/programming-guide/concepts/linq/finding-the-default-paragraph-style.md), which retrieves the default style from the list of styles.</span></span> <span data-ttu-id="d3ed6-106">Te informacje są niezbędne, aby zapytanie można zidentyfikować styl akapitów, które nie mają jawnie ustawiona stylu.</span><span class="sxs-lookup"><span data-stu-id="d3ed6-106">This information is required so that the query can identify the style of paragraphs that do not have a style explicitly set.</span></span> <span data-ttu-id="d3ed6-107">Style są ustawiane za pomocą `w:pPr` element; Jeśli akapitu nie zawiera tego elementu, jest sformatowany przy użyciu domyślnego stylu.</span><span class="sxs-lookup"><span data-stu-id="d3ed6-107">Paragraph styles are set through the `w:pPr` element; if a paragraph does not contain this element, it is formatted with the default style.</span></span>  
  
 <span data-ttu-id="d3ed6-108">W tym temacie wyjaśniono znaczenie niektóre elementy zapytania, a następnie wyświetla zapytanie w ramach zakończeniu przykładu pracy.</span><span class="sxs-lookup"><span data-stu-id="d3ed6-108">This topic explains the significance of some pieces of the query, then shows the query as part of a complete, working example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3ed6-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="d3ed6-109">Example</span></span>  
 <span data-ttu-id="d3ed6-110">Źródłem zapytania można pobrać wszystkich akapitów dokumentu oraz ich stylów jest następujący:</span><span class="sxs-lookup"><span data-stu-id="d3ed6-110">The source of the query to retrieve all the paragraphs in a document and their styles is as follows:</span></span>  
  
```csharp  
xDoc.Root.Element(w + "body").Descendants(w + "p")  
```  
  
 <span data-ttu-id="d3ed6-111">To wyrażenie jest podobny do źródła zapytania w poprzednim przykładzie [znajdowanie domyślny styl akapitu (C#)](../../../../csharp/programming-guide/concepts/linq/finding-the-default-paragraph-style.md).</span><span class="sxs-lookup"><span data-stu-id="d3ed6-111">This expression is similar to the source of the query in the previous example, [Finding the Default Paragraph Style (C#)](../../../../csharp/programming-guide/concepts/linq/finding-the-default-paragraph-style.md).</span></span> <span data-ttu-id="d3ed6-112">Główną różnicą jest to, że używa <xref:System.Xml.Linq.XContainer.Descendants%2A> osi zamiast <xref:System.Xml.Linq.XContainer.Elements%2A> osi.</span><span class="sxs-lookup"><span data-stu-id="d3ed6-112">The main difference is that it uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis instead of the <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span> <span data-ttu-id="d3ed6-113">Zapytanie używa <xref:System.Xml.Linq.XContainer.Descendants%2A> osi ponieważ w dokumentach zawierających sekcje, akapitów nie będzie bezpośrednimi elementami podrzędnymi elementu body; zamiast akapitów będzie dwa poziomy w dół w hierarchii.</span><span class="sxs-lookup"><span data-stu-id="d3ed6-113">The query uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis because in documents that have sections, the paragraphs will not be the direct children of the body element; rather, the paragraphs will be two levels down in the hierarchy.</span></span> <span data-ttu-id="d3ed6-114">Za pomocą <xref:System.Xml.Linq.XContainer.Descendants%2A> osi, kod będzie działać z czy dokument używa sekcje.</span><span class="sxs-lookup"><span data-stu-id="d3ed6-114">By using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis, the code will work of whether or not the document uses sections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3ed6-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="d3ed6-115">Example</span></span>  
 <span data-ttu-id="d3ed6-116">Zapytanie używa `let` klauzuli, aby określić element, który zawiera węzeł stylu.</span><span class="sxs-lookup"><span data-stu-id="d3ed6-116">The query uses a `let` clause to determine the element that contains the style node.</span></span> <span data-ttu-id="d3ed6-117">Jeśli nie ma żadnych elementów `styleNode` ma ustawioną wartość `null`:</span><span class="sxs-lookup"><span data-stu-id="d3ed6-117">If there is no element, then `styleNode` is set to `null`:</span></span>  
  
```csharp  
let styleNode = para.Elements(w + "pPr").Elements(w + "pStyle").FirstOrDefault()  
```  
  
 <span data-ttu-id="d3ed6-118">`let` Najpierw używa klauzuli <xref:System.Xml.Linq.XContainer.Elements%2A> osi, aby znaleźć wszystkie elementy o nazwie `pPr`, następnie używa <xref:System.Xml.Linq.Extensions.Elements%2A> — metoda rozszerzenia, aby znaleźć wszystkie elementy podrzędne o nazwie `pStyle`, a na koniec używa <xref:System.Linq.Enumerable.FirstOrDefault%2A> standardowej kwerendy Operator do przekonwertowania kolekcji na pojedynczą.</span><span class="sxs-lookup"><span data-stu-id="d3ed6-118">The `let` clause first uses the <xref:System.Xml.Linq.XContainer.Elements%2A> axis to find all elements named `pPr`, then uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method to find all child elements named `pStyle`, and finally uses the <xref:System.Linq.Enumerable.FirstOrDefault%2A> standard query operator to convert the collection to a singleton.</span></span> <span data-ttu-id="d3ed6-119">Jeśli kolekcja jest pusta, `styleNode` ma ustawioną wartość `null`.</span><span class="sxs-lookup"><span data-stu-id="d3ed6-119">If the collection is empty, `styleNode` is set to `null`.</span></span> <span data-ttu-id="d3ed6-120">Jest to przydatne idiom do wyszukania `pStyle` podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="d3ed6-120">This is a useful idiom to look for the `pStyle` descendant node.</span></span> <span data-ttu-id="d3ed6-121">Należy pamiętać, że jeśli `pPr` węzeł podrzędny nie istnieje, kod nie ani nie zakończyć się niepowodzeniem przez Zgłaszanie wyjątku; zamiast tego `styleNode` ustawiono `null`, która jest zachowanie tej `let` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="d3ed6-121">Note that if the `pPr` child node does not exist, the code does nor fail by throwing an exception; instead, `styleNode` is set to `null`, which is the desired behavior of this `let` clause.</span></span>  
  
 <span data-ttu-id="d3ed6-122">Zapytanie projektów kolekcję typu anonimowego z dwóch członków `StyleName` i `ParagraphNode`.</span><span class="sxs-lookup"><span data-stu-id="d3ed6-122">The query projects a collection of an anonymous type with two members, `StyleName` and `ParagraphNode`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3ed6-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="d3ed6-123">Example</span></span>  
 <span data-ttu-id="d3ed6-124">W tym przykładzie przetwarza dokument schemat WordprocessingML pobieranie węzłów akapitu z dokumentem schemat WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="d3ed6-124">This example processes a WordprocessingML document, retrieving the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="d3ed6-125">Identyfikuje styl każdego akapitu.</span><span class="sxs-lookup"><span data-stu-id="d3ed6-125">It also identifies the style of each paragraph.</span></span> <span data-ttu-id="d3ed6-126">W tym przykładzie kompilacje w poprzednich przykładach, w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="d3ed6-126">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="d3ed6-127">Nowe zapytanie jest podana w komentarzach w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="d3ed6-127">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="d3ed6-128">Można znaleźć instrukcje dotyczące tworzenia w tym przykładzie w dokumencie źródłowym [tworzenie źródło dokumentu pakietu Office Open XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="d3ed6-128">You can find instructions for creating the source document for this example in [Creating the Source Office Open XML Document (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="d3ed6-129">W tym przykładzie użyto znaleziony w zestawie WindowsBase klasy.</span><span class="sxs-lookup"><span data-stu-id="d3ed6-129">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="d3ed6-130">Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d3ed6-130">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
 <span data-ttu-id="d3ed6-131">Ten przykład generuje dane wyjściowe w przypadku zastosowanego do dokumentu opisano w następujących [tworzenie źródło dokumentu pakietu Office Open XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="d3ed6-131">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
```  
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
  
## <a name="next-steps"></a><span data-ttu-id="d3ed6-132">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="d3ed6-132">Next Steps</span></span>  
 <span data-ttu-id="d3ed6-133">W następnym temacie [pobieranie tekstu akapitów (C#)](../../../../csharp/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), utworzysz kwerendę, aby pobrać tekst akapitów.</span><span class="sxs-lookup"><span data-stu-id="d3ed6-133">In the next topic, [Retrieving the Text of the Paragraphs (C#)](../../../../csharp/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), you'll create a query to retrieve the text of paragraphs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3ed6-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d3ed6-134">See Also</span></span>  
 [<span data-ttu-id="d3ed6-135">Samouczek: Manipulowanie zawartości w dokumencie schemat WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="d3ed6-135">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
