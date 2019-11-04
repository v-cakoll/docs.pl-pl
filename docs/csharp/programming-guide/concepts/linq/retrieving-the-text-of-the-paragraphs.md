---
title: Pobieranie tekstu akapitów (C#)
ms.date: 07/20/2015
ms.assetid: 127d635e-e559-408f-90c8-2bb621ca50ac
ms.openlocfilehash: cedca9df84ee687a9e304cde0015b46d07956364
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423341"
---
# <a name="retrieving-the-text-of-the-paragraphs-c"></a>Pobieranie tekstu akapitów (C#)
Ten przykład kompiluje się w poprzednim przykładzie, [pobierając akapity i ich styleC#()](./retrieving-the-paragraphs-and-their-styles.md). Ten nowy przykład pobiera tekst każdego akapitu w postaci ciągu.  
  
 Aby pobrać tekst, ten przykład dodaje dodatkowe zapytanie, które iteruje przez kolekcję typów anonimowych i projektów nowej kolekcji typu anonimowego z dodaniem nowego elementu członkowskiego `Text`. Używa standardowego operatora zapytań <xref:System.Linq.Enumerable.Aggregate%2A> do łączenia wielu ciągów w jeden ciąg.  
  
 Ta technika (czyli najpierw projekcja do kolekcji typu anonimowego, a następnie użycie tej kolekcji w celu utworzenia nowej kolekcji typu anonimowego) jest powszechną i użyteczną idiom. To zapytanie mogło zostać zapisaną bez projekcji pierwszego typu anonimowego. Jednak ze względu na ocenę z opóźnieniem nie jest używana znacznie dodatkowa moc obliczeniowa. Idiom tworzy więcej krótkich obiektów na stercie, ale nie zmniejsza to wydajności.  
  
 Oczywiście można napisać pojedyncze zapytanie, które zawiera funkcje umożliwiające pobranie akapitów, stylu każdego akapitu i tekstu każdego akapitu. Często jednak warto rozdzielić bardziej skomplikowane zapytanie na wiele zapytań, ponieważ otrzymany kod jest bardziej modularny i łatwiejszy w obsłudze. Ponadto, jeśli konieczne jest ponowne użycie części zapytania, łatwiej jest refaktoryzację, jeśli zapytania są zapisywane w ten sposób.  
  
 Te zapytania, które są powiązane ze sobą, wykorzystują model przetwarzania, który jest szczegółowo rozpatrywany w [samouczku tematu: Łączenie łańcuchowe zapytańC#()](deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).  
  
## <a name="example"></a>Przykład  
 Ten przykład przetwarza dokument WordprocessingML, określając węzeł elementu, nazwę stylu i tekst każdego akapitu. Ten przykład kompiluje się zgodnie z poprzednimi przykładami w tym samouczku. Nowe zapytanie jest wywoływane w komentarzach w poniższym kodzie.  
  
 Aby uzyskać instrukcje dotyczące tworzenia dokumentu źródłowego dla tego przykładu, zobacz [Tworzenie źródłowego dokumentu Office Open XML (C#)](./creating-the-source-office-open-xml-document.md).  
  
 W tym przykładzie zastosowano klasy z zestawu 'Windowsbase. Używa typów w przestrzeni nazw <xref:System.IO.Packaging?displayProperty=nameWithType>.  
  
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
  
 Ten przykład generuje następujące dane wyjściowe w przypadku zastosowania do dokumentu opisanego w temacie [Tworzenie źródłowego dokumentu Office Open XML (C#)](./creating-the-source-office-open-xml-document.md).  
  
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
 W następnym przykładzie pokazano, jak używać metody rozszerzenia zamiast <xref:System.Linq.Enumerable.Aggregate%2A>, aby połączyć wiele ciągów w jeden ciąg.  
  
- [Refaktoryzacja przy użyciu metody rozszerzającej (C#)](./refactoring-using-an-extension-method.md)  
  
## <a name="see-also"></a>Zobacz także

- [Samouczek: manipulowanie zawartością w dokumencie WordprocessingML (C#)](shape-of-wordprocessingml-documents.md)
- [Wykonywanie odroczone i Ocena z opóźnieniem w LINQ to XMLC#()](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
