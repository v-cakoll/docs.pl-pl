---
title: Trwa pobieranie tekstu akapitów (C#)
ms.date: 07/20/2015
ms.assetid: 127d635e-e559-408f-90c8-2bb621ca50ac
ms.openlocfilehash: 1d23addb4c4c1ea17343585392fbe08fef08568a
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46009846"
---
# <a name="retrieving-the-text-of-the-paragraphs-c"></a>Trwa pobieranie tekstu akapitów (C#)
W tym przykładzie opiera się na poprzednim przykładzie [pobieranie akapitów i ich stylów (C#)](../../../../csharp/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md). W tym przykładzie nowe pobiera tekst każdego akapitu jako ciąg.  
  
 Aby pobrać tekstu, ten przykład dodaje dodatkowe zapytania, który iteruje po kolekcji typów anonimowych i projekty Nowa kolekcja typu anonimowego dodając nowy element członkowski `Text`. Używa ona <xref:System.Linq.Enumerable.Aggregate%2A> standardowego operatora zapytania na łączenie wielu ciągów w jeden ciąg.  
  
 Ta technika (czyli projekcji pierwszej kolekcji typu anonimowego, a następnie przy użyciu tej kolekcji do projektu do nowej kolekcji typu anonimowego) to idiom typowe i przydatne. To zapytanie może zapisywane bez wyświetlanie na pierwszym typu anonimowego. Jednak ze względu na obliczanie z opóźnieniem, spowoduje to więc nie korzysta z dużo mocy dodatkowego przetwarzania. Idiom tworzy więcej krótki czas życia obiektów na stosie, ale to nie znacznie zmniejszyć wydajność.  
  
 Oczywiście będzie możliwość napisania jednego zapytania, który zawiera funkcje umożliwiające pobieranie akapitów, styl każdego akapitu, a tekst każdego akapitu. Jednak często warto podzielić bardziej skomplikowane zapytanie do wielu zapytań, ponieważ wynikowy kod jest bardziej modułowego i łatwiejsze w konserwacji. Ponadto jeśli zajdzie potrzeba ponownego użycia część zapytania, łatwiej jest Refaktoryzacja Jeśli zapytania są zapisywane w ten sposób.  
  
 Te zapytania, które są połączone, użyj przetwarzania modelu, który jest sprawdzany pod szczegółowo w temacie [samouczek: tworzenie łańcuchów zapytania ze sobą (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przetwarza dokumentu WordprocessingML określania węzła elementu, nazwę stylu i tekst każdego akapitu. W tym przykładzie opiera się na poprzednich przykładach w tym samouczku. Nowe zapytanie jest wywoływane w komentarzach, w poniższym kodzie.  
  
 Aby uzyskać instrukcje dotyczące tworzenia dokumentu źródłowego, w tym przykładzie, zobacz [tworzenie źródłowego dokumentu pakietu Office Open XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
 W tym przykładzie użyto klasy z zestawu WindowsBase. Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> przestrzeni nazw.  
  
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
  
 Ten przykład generuje następujące dane wyjściowe po zastosowaniu do dokumentu opisano w [tworzenie źródłowego dokumentu pakietu Office Open XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
```  
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
 W kolejnym przykładzie pokazano sposób użycia metody rozszerzenia, zamiast <xref:System.Linq.Enumerable.Aggregate%2A>, aby łączenie wielu ciągów w jeden ciąg.  
  
-   [Refaktoryzacja przy użyciu metody rozszerzenia (C#)](../../../../csharp/programming-guide/concepts/linq/refactoring-using-an-extension-method.md)  
  
## <a name="see-also"></a>Zobacz też

- [Samouczek: Manipulowanie zawartością w dokumencie WordprocessingML (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)  
- [Wykonanie odroczone i obliczanie z opóźnieniem w LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
