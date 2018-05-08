---
title: Trwa pobieranie akapitów i ich style (C#)
ms.date: 07/20/2015
ms.assetid: c2f767f8-57b1-4b4b-af04-89ffb1f7067d
ms.openlocfilehash: 11788c1fa46c63c78a9db0255c8e84250285863e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="retrieving-the-paragraphs-and-their-styles-c"></a>Trwa pobieranie akapitów i ich style (C#)
W tym przykładzie mamy Napisz zapytanie, które pobiera węzły akapitu z dokumentu schemat WordprocessingML. Identyfikuje styl każdego akapitu.  
  
 To zapytanie opiera się na zapytanie w poprzednim przykładzie [znajdowanie domyślny styl akapitu (C#)](../../../../csharp/programming-guide/concepts/linq/finding-the-default-paragraph-style.md), który pobiera styl domyślny z listy stylów. Te informacje są niezbędne, aby zapytanie można zidentyfikować styl akapitów, które nie mają jawnie ustawiona stylu. Style są ustawiane za pomocą `w:pPr` element; Jeśli akapitu nie zawiera tego elementu, jest sformatowany przy użyciu domyślnego stylu.  
  
 W tym temacie wyjaśniono znaczenie niektóre elementy zapytania, a następnie wyświetla zapytanie w ramach zakończeniu przykładu pracy.  
  
## <a name="example"></a>Przykład  
 Źródłem zapytania można pobrać wszystkich akapitów dokumentu oraz ich stylów jest następujący:  
  
```csharp  
xDoc.Root.Element(w + "body").Descendants(w + "p")  
```  
  
 To wyrażenie jest podobny do źródła zapytania w poprzednim przykładzie [znajdowanie domyślny styl akapitu (C#)](../../../../csharp/programming-guide/concepts/linq/finding-the-default-paragraph-style.md). Główną różnicą jest to, że używa <xref:System.Xml.Linq.XContainer.Descendants%2A> osi zamiast <xref:System.Xml.Linq.XContainer.Elements%2A> osi. Zapytanie używa <xref:System.Xml.Linq.XContainer.Descendants%2A> osi ponieważ w dokumentach zawierających sekcje, akapitów nie będzie bezpośrednimi elementami podrzędnymi elementu body; zamiast akapitów będzie dwa poziomy w dół w hierarchii. Za pomocą <xref:System.Xml.Linq.XContainer.Descendants%2A> osi, kod będzie działać z czy dokument używa sekcje.  
  
## <a name="example"></a>Przykład  
 Zapytanie używa `let` klauzuli, aby określić element, który zawiera węzeł stylu. Jeśli nie ma żadnych elementów `styleNode` ma ustawioną wartość `null`:  
  
```csharp  
let styleNode = para.Elements(w + "pPr").Elements(w + "pStyle").FirstOrDefault()  
```  
  
 `let` Najpierw używa klauzuli <xref:System.Xml.Linq.XContainer.Elements%2A> osi, aby znaleźć wszystkie elementy o nazwie `pPr`, następnie używa <xref:System.Xml.Linq.Extensions.Elements%2A> — metoda rozszerzenia, aby znaleźć wszystkie elementy podrzędne o nazwie `pStyle`, a na koniec używa <xref:System.Linq.Enumerable.FirstOrDefault%2A> standardowej kwerendy Operator do przekonwertowania kolekcji na pojedynczą. Jeśli kolekcja jest pusta, `styleNode` ma ustawioną wartość `null`. Jest to przydatne idiom do wyszukania `pStyle` podrzędnego. Należy pamiętać, że jeśli `pPr` węzeł podrzędny nie istnieje, kod nie ani nie zakończyć się niepowodzeniem przez Zgłaszanie wyjątku; zamiast tego `styleNode` ustawiono `null`, która jest zachowanie tej `let` klauzuli.  
  
 Zapytanie projektów kolekcję typu anonimowego z dwóch członków `StyleName` i `ParagraphNode`.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przetwarza dokument schemat WordprocessingML pobieranie węzłów akapitu z dokumentem schemat WordprocessingML. Identyfikuje styl każdego akapitu. W tym przykładzie kompilacje w poprzednich przykładach, w tym samouczku. Nowe zapytanie jest podana w komentarzach w poniższym kodzie.  
  
 Można znaleźć instrukcje dotyczące tworzenia w tym przykładzie w dokumencie źródłowym [tworzenie źródło dokumentu pakietu Office Open XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
 W tym przykładzie użyto znaleziony w zestawie WindowsBase klasy. Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> przestrzeni nazw.  
  
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
  
 Ten przykład generuje dane wyjściowe w przypadku zastosowanego do dokumentu opisano w następujących [tworzenie źródło dokumentu pakietu Office Open XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
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
  
## <a name="next-steps"></a>Następne kroki  
 W następnym temacie [pobieranie tekstu akapitów (C#)](../../../../csharp/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), utworzysz kwerendę, aby pobrać tekst akapitów.  
  
## <a name="see-also"></a>Zobacz też  
 [Samouczek: Manipulowanie zawartości w dokumencie schemat WordprocessingML (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
