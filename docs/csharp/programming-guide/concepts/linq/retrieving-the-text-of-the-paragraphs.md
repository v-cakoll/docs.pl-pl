---
title: Pobieranie tekstu akapitów (C#)
ms.date: 07/20/2015
ms.assetid: 127d635e-e559-408f-90c8-2bb621ca50ac
ms.openlocfilehash: 7c47420045def3fe973169e01143646c0f60a8eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168248"
---
# <a name="retrieving-the-text-of-the-paragraphs-c"></a>Pobieranie tekstu akapitów (C#)
W tym przykładzie opiera się na poprzednim [przykładzie, Pobieranie akapity i ich style (C#)](./retrieving-the-paragraphs-and-their-styles.md). W tym nowym przykładzie pobiera tekst każdego akapitu jako ciąg.  
  
 Aby pobrać tekst, w tym przykładzie dodaje dodatkowe zapytanie, które iteruje poprzez kolekcję typów anonimowych `Text`i projektów nowej kolekcji typu anonimowego z dodatkiem nowego elementu członkowskiego. Używa standardowego <xref:System.Linq.Enumerable.Aggregate%2A> operatora kwerendy do łączenia wielu ciągów w jeden ciąg.  
  
 Ta technika (czyli najpierw rzutowanie do kolekcji typu anonimowego, a następnie za pomocą tej kolekcji do projektu do nowej kolekcji typu anonimowego) jest typowyi i przydatne idiom. Ta kwerenda mogła zostać napisana bez rzutowania na pierwszy typ anonimowy. Jednak z powodu oceny z opóźnieniem, w ten sposób nie zużywa wiele dodatkowej mocy obliczeniowej. Idiom tworzy bardziej krótkotrwałe obiekty na stercie, ale nie obniża to znacznie wydajności.  
  
 Oczywiście możliwe byłoby napisanie pojedynczej kwerendy zawierającej funkcje pobierania akapitów, styl każdego akapitu i tekst każdego akapitu. Jednak często jest przydatne do podziału bardziej skomplikowane zapytanie na wiele zapytań, ponieważ wynikowy kod jest bardziej modułowe i łatwiejsze w utrzymaniu. Ponadto jeśli trzeba ponownie użyć części kwerendy, łatwiej jest refaktoryzacji, jeśli zapytania są zapisywane w ten sposób.  
  
 Te zapytania, które są ze sobą połączone łańcuchem, używają modelu przetwarzania, który jest szczegółowo sprawdzany w temacie [Samouczek: Łączenie zapytań razem (C#)](deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przetwarza dokument WordprocessingML, określając węzeł elementu, nazwę stylu i tekst każdego akapitu. W tym przykładzie opiera się na poprzednich przykładach w tym samouczku. Nowe zapytanie jest wywoływane w komentarzach w poniższym kodzie.  
  
 Aby uzyskać instrukcje dotyczące tworzenia dokumentu źródłowego dla tego [przykładu, zobacz Tworzenie dokumentu XML open pakietu Source Office (C#).](./creating-the-source-office-open-xml-document.md)  
  
 W tym przykładzie użyto klas z zestawu WindowsBase. Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> obszarze nazw.  
  
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
  
string defaultStyle =
    (string)(  
        from style in styleDoc.Root.Elements(w + "style")  
        where (string)style.Attribute(w + "type") == "paragraph"&&  
              (string)style.Attribute(w + "default") == "1"  
              select style  
    ).First().Attribute(w + "styleId");  
  
// Find all paragraphs in the document.  
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
  
// Following is the new query that retrieves the text of  
// each paragraph.  
var paraWithText =  
    from para in paragraphs  
    select new  
    {  
        ParagraphNode = para.ParagraphNode,  
        StyleName = para.StyleName,  
        Text = para  
               .ParagraphNode  
               .Elements(w + "r")  
               .Elements(w + "t")  
               .Aggregate(  
                   new StringBuilder(),  
                   (s, i) => s.Append((string)i),  
                   s => s.ToString()  
               )  
    };  
  
foreach (var p in paraWithText)  
    Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text);  
```  
  
 W tym przykładzie po zastosowaniu do dokumentu opisanego w [dokumencie Tworzenie dokumentu XML pakietu Source Office Open (C#).](./creating-the-source-office-open-xml-document.md)  
  
```output  
StyleName:Heading1 >Parsing WordprocessingML with LINQ to XML<  
StyleName:Normal ><  
StyleName:Normal >The following example prints to the console.<  
StyleName:Normal ><  
StyleName:Code >using System;<  
StyleName:Code ><  
StyleName:Code >class Program {<  
StyleName:Code >    public static void (string[] args) {<  
StyleName:Code >        Console.WriteLine("Hello World");<  
StyleName:Code >    }<  
StyleName:Code >}<  
StyleName:Normal ><  
StyleName:Normal >This example produces the following output:<  
StyleName:Normal ><  
StyleName:Code >Hello World<  
```  
  
## <a name="next-steps"></a>Następne kroki  
 W następnym przykładzie pokazano, jak używać <xref:System.Linq.Enumerable.Aggregate%2A>metody rozszerzenia, zamiast , połączyć wiele ciągów w jeden ciąg.  
  
- [Refaktoryzacja przy użyciu metody rozszerzenia (C#)](./refactoring-using-an-extension-method.md)  
  
## <a name="see-also"></a>Zobacz też

- [Samouczek: manipulowanie zawartością w dokumencie WordprocessingML (C#)](shape-of-wordprocessingml-documents.md)
- [Odroczone wykonanie i ocena z opóźnieniem w LINQ do XML (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
