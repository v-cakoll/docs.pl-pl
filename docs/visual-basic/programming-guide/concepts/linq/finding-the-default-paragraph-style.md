---
title: Znajdowanie domyślny styl akapitu (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9d094a4a-ec8c-41b0-b7ab-a3deb2a01d45
ms.openlocfilehash: 77e6e6db321b5f8ef338706e5f938daa02d115eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="finding-the-default-paragraph-style-visual-basic"></a><span data-ttu-id="e0304-102">Znajdowanie domyślny styl akapitu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e0304-102">Finding the Default Paragraph Style (Visual Basic)</span></span>
<span data-ttu-id="e0304-103">Pierwszym zadaniem manipulowanie dane w samouczku schemat WordprocessingML dokumentu jest można znaleźć w dokumencie domyślny styl akapitów.</span><span class="sxs-lookup"><span data-stu-id="e0304-103">The first task in the Manipulating Information in a WordprocessingML Document tutorial is to find the default style of paragraphs in the document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0304-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="e0304-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="e0304-105">Opis</span><span class="sxs-lookup"><span data-stu-id="e0304-105">Description</span></span>  
 <span data-ttu-id="e0304-106">Poniższy przykład powoduje otwarcie dokumentu schemat WordprocessingML Office Open XML, znajduje dokumentu i styl części pakietu, a następnie wykonuje kwerendę, która wyszukuje domyślną nazwę stylu.</span><span class="sxs-lookup"><span data-stu-id="e0304-106">The following example opens an Office Open XML WordprocessingML document, finds the document and style parts of the package, and then executes a query that finds the default style name.</span></span> <span data-ttu-id="e0304-107">Aby uzyskać informacje o pakietach dokumentu pakietu Office Open XML i części składają się z, zobacz [szczegóły z dokumentów pakietu Office Open XML schemat WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md).</span><span class="sxs-lookup"><span data-stu-id="e0304-107">For information about Office Open XML document packages, and the parts they consist of, see [Details of Office Open XML WordprocessingML Documents (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md).</span></span>  
  
 <span data-ttu-id="e0304-108">Zapytanie znajdzie węzła o nazwie `w:style` zawierającego atrybut o nazwie `w:type` o wartości "akapitu", a także ma atrybut o nazwie `w:default` o wartości "1".</span><span class="sxs-lookup"><span data-stu-id="e0304-108">The query finds a node named `w:style` that has an attribute named `w:type` with a value of "paragraph", and also has an attribute named `w:default` with a value of "1".</span></span> <span data-ttu-id="e0304-109">Ponieważ będzie istniało tylko jeden węzeł XML z tymi atrybutami, zapytanie używa <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operatora, aby przekonwertować kolekcji jako pojedyncza.</span><span class="sxs-lookup"><span data-stu-id="e0304-109">Because there will be only one XML node with these attributes, the query uses the <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operator to convert a collection to a singleton.</span></span> <span data-ttu-id="e0304-110">Następnie pobiera wartość atrybutu o nazwie `w:styleId`.</span><span class="sxs-lookup"><span data-stu-id="e0304-110">It then gets the value of the attribute with the name `w:styleId`.</span></span>  
  
 <span data-ttu-id="e0304-111">W tym przykładzie użyto klasy z zestawu WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="e0304-111">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="e0304-112">Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e0304-112">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
### <a name="code"></a><span data-ttu-id="e0304-113">Kod</span><span class="sxs-lookup"><span data-stu-id="e0304-113">Code</span></span>  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
  
    Sub Main()  
  
        Const fileName As String = "SampleDoc.docx"  
  
        Const documentRelationshipType As String = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
        Const stylesRelationshipType As String = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"  
  
        Dim xDoc As XDocument = Nothing  
        Dim styleDoc As XDocument = Nothing  
  
        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)  
            Dim docPackageRelationship As PackageRelationship = _  
              wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
            If docPackageRelationship IsNot Nothing Then  
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", UriKind.Relative), _  
                  docPackageRelationship.TargetUri)  
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
                ' Load the document XML in the part into an XDocument instance.  
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
  
                ' Find the styles part. There will only be one.  
                Dim styleRelation As PackageRelationship = _  
                  documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()  
                If styleRelation IsNot Nothing Then  
                    Dim styleUri As Uri = _  
                      PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)  
                    Dim stylePart As PackagePart = wdPackage.GetPart(styleUri)  
  
                    ' Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()))  
                End If  
            End If  
        End Using  
  
        ' The following query finds all the paragraphs that have the default style.  
        Dim defParas As IEnumerable(Of XElement) = _  
            From style In styleDoc.Root.<w:style> _  
            Where style.@w:type.Equals("paragraph") And _  
                   style.@w:default.Equals("1") _  
            Select style  
        ' Then find the style of the first.  
        Dim defaultStyle As String = defParas.First().@w:styleId  
  
        Console.WriteLine("The default style is: " & defaultStyle)  
    End Sub  
End Module  
```  
  
### <a name="comments"></a><span data-ttu-id="e0304-114">Komentarze</span><span class="sxs-lookup"><span data-stu-id="e0304-114">Comments</span></span>  
 <span data-ttu-id="e0304-115">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="e0304-115">This example produces the following output:</span></span>  
  
```  
The default style is: Normal  
```  
  
## <a name="next-steps"></a><span data-ttu-id="e0304-116">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="e0304-116">Next Steps</span></span>  
 <span data-ttu-id="e0304-117">W następnym przykładzie utworzysz podobne kwerendę, która wyszukuje wszystkie akapity w dokumencie i ich style:</span><span class="sxs-lookup"><span data-stu-id="e0304-117">In the next example, you'll create a similar query that finds all the paragraphs in a document and their styles:</span></span>  
  
-   [<span data-ttu-id="e0304-118">Trwa pobieranie akapitów i ich style (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e0304-118">Retrieving the Paragraphs and Their Styles (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md)  
  
## <a name="see-also"></a><span data-ttu-id="e0304-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e0304-119">See Also</span></span>  
 [<span data-ttu-id="e0304-120">Samouczek: Manipulowanie zawartości w dokumencie schemat WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e0304-120">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
