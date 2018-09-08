---
title: Refaktoryzacja przy użyciu metody rozszerzenia (C#)
ms.date: 07/20/2015
ms.assetid: c5fc123d-af10-4a2f-b8e4-db921efb2639
ms.openlocfilehash: 08c37923792e1ac6ee922bf052d39fb63b1685c7
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44201053"
---
# <a name="refactoring-using-an-extension-method-c"></a>Refaktoryzacja przy użyciu metody rozszerzenia (C#)
W tym przykładzie opiera się na poprzednim przykładzie [pobieranie tekstu akapitów (C#)](../../../../csharp/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), przez refaktoryzacji łączenia ciągów przy użyciu czystej funkcji, który jest implementowany jako metodę rozszerzenia.  
  
 W poprzednim przykładzie użyto <xref:System.Linq.Enumerable.Aggregate%2A> standardowego operatora zapytania na łączenie wielu ciągów w jeden ciąg. Jednak jest bardziej wygodne do zapisania metodę rozszerzenia, aby to zrobić, ponieważ wynikowy zapytania mniejsze i bardziej proste.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przetwarza dokumentu WordprocessingML pobieranie akapitów, styl każdego akapitu, a tekst każdego akapitu. W tym przykładzie opiera się na poprzednich przykładach w tym samouczku.  
  
 Przykład zawiera wiele przeciążeń `StringConcatenate` metody.  
  
 Można znaleźć instrukcje dotyczące tworzenia dokumentu źródłowego, w tym przykładzie w [tworzenie źródłowego dokumentu pakietu Office Open XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
 W tym przykładzie użyto klasy z zestawu WindowsBase. Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> przestrzeni nazw.  
  
```csharp  
public static class LocalExtensions  
{  
    public static string StringConcatenate(this IEnumerable<string> source)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (string s in source)  
            sb.Append(s);  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate<T>(this IEnumerable<T> source,  
        Func<T, string> func)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (T item in source)  
            sb.Append(func(item));  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate(this IEnumerable<string> source, string separator)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (string s in source)  
            sb.Append(s).Append(separator);  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate<T>(this IEnumerable<T> source,  
        Func<T, string> func, string separator)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (T item in source)  
            sb.Append(func(item)).Append(separator);  
        return sb.ToString();  
    }  
}  
```  
  
## <a name="example"></a>Przykład  
 Istnieją cztery przeciążenia `StringConcatenate` metody. Kilkoma przeciążeniami po prostu kolekcji ciągów i zwraca jeden ciąg. Innego przeciążenia metody może potrwać kolekcji dowolnego typu i delegata tego projektów z pojedynczego kolekcji na ciąg. Istnieją dwa więcej przeciążenia metody, które pozwalają na określenie ciągu separatora.  
  
 W poniższym kodzie użyto wszystkie cztery przeciążenia.  
  
```csharp  
string[] numbers = { "one", "two", "three" };  
  
Console.WriteLine("{0}", numbers.StringConcatenate());  
Console.WriteLine("{0}", numbers.StringConcatenate(":"));  
  
int[] intNumbers = { 1, 2, 3 };  
Console.WriteLine("{0}", intNumbers.StringConcatenate(i => i.ToString()));  
Console.WriteLine("{0}", intNumbers.StringConcatenate(i => i.ToString(), ":"));  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```  
onetwothree  
one:two:three:  
123  
1:2:3:  
```  
  
## <a name="example"></a>Przykład  
 Teraz można zmodyfikować przykładu, aby korzystać z zalet nowej metody rozszerzenia:  
  
```csharp  
public static class LocalExtensions  
{  
    public static string StringConcatenate(this IEnumerable<string> source)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (string s in source)  
            sb.Append(s);  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate<T>(this IEnumerable<T> source,  
        Func<T, string> func)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (T item in source)  
            sb.Append(func(item));  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate(this IEnumerable<string> source, string separator)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (string s in source)  
            sb.Append(s).Append(separator);  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate<T>(this IEnumerable<T> source,  
        Func<T, string> func, string separator)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (T item in source)  
            sb.Append(func(item)).Append(separator);  
        return sb.ToString();  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
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
                    Uri styleUri =  
                      PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri);  
                    PackagePart stylePart = wdPackage.GetPart(styleUri);  
  
                    //  Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()));  
                }  
            }  
        }  
  
        string defaultStyle =  
            (string)(  
                from style in styleDoc.Root.Elements(w + "style")  
                where (string)style.Attribute(w + "type") == "paragraph" &&  
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
  
        // Retrieve the text of each paragraph.  
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
                       .StringConcatenate(e => (string)e)  
            };  
  
        foreach (var p in paraWithText)  
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text);  
    }  
}  
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
  
 Należy pamiętać, że ta Refaktoryzacja jest wariant Refaktoryzacja do czystych funkcji. Następny temat przedstawiono koncepcję wyprowadzenie do czystych funkcji bardziej szczegółowo.  
  
## <a name="next-steps"></a>Następne kroki  
 W kolejnym przykładzie pokazano sposób Refaktoryzuj ten kod w inny sposób, przy użyciu czystej funkcji:  
  
-   [Refaktoryzacja przy użyciu czystej funkcji (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/refactoring-using-a-pure-function.md)  
  
## <a name="see-also"></a>Zobacz też

- [Samouczek: Manipulowanie zawartością w dokumencie WordprocessingML (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)  
- [Refaktoryzacja do czystych funkcji (C#)](../../../../csharp/programming-guide/concepts/linq/refactoring-into-pure-functions.md)
