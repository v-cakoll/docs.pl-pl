---
title: Pobieranie akapitów i ich stylów (C#)
ms.date: 07/20/2015
ms.assetid: c2f767f8-57b1-4b4b-af04-89ffb1f7067d
ms.openlocfilehash: 47127b6f1d6bfaa0d8d93333882a0d0b59f1bae6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168300"
---
# <a name="retrieving-the-paragraphs-and-their-styles-c"></a>Pobieranie akapitów i ich stylów (C#)
W tym przykładzie piszemy kwerendę, która pobiera węzły akapitu z dokumentu WordprocessingML. Identyfikuje również styl każdego akapitu.  
  
 Ta kwerenda opiera się na kwerendzie w poprzednim [przykładzie, Znajdowanie domyślnego stylu akapitu (C#),](./finding-the-default-paragraph-style.md)który pobiera domyślny styl z listy stylów. Te informacje są wymagane, aby kwerenda mogła zidentyfikować styl akapitów, które nie mają styljawnie ustawiony. Style akapitowe `w:pPr` są ustawiane przez element; Jeśli akapit nie zawiera tego elementu, jest sformatowany przy pomocą domyślnego stylu.  
  
 W tym temacie wyjaśniono znaczenie niektórych fragmentów kwerendy, a następnie pokazuje kwerendę jako część pełnego, działającego przykładu.  
  
## <a name="example"></a>Przykład  
 Źródło kwerendy w celu pobrania wszystkich akapitów w dokumencie i ich stylów jest następujące:  
  
```csharp  
xDoc.Root.Element(w + "body").Descendants(w + "p")  
```  
  
 To wyrażenie jest podobne do źródła kwerendy w poprzednim [przykładzie, Znajdowanie domyślnego stylu akapitu (C#)](./finding-the-default-paragraph-style.md). Główną różnicą jest to, że używa <xref:System.Xml.Linq.XContainer.Descendants%2A> osi zamiast <xref:System.Xml.Linq.XContainer.Elements%2A> osi. Kwerenda używa <xref:System.Xml.Linq.XContainer.Descendants%2A> osi, ponieważ w dokumentach, które mają sekcje, akapity nie będą bezpośrednimi elementami podrzędnymi elementu body; akapity będą raczej dwa poziomy w dół w hierarchii. Za pomocą <xref:System.Xml.Linq.XContainer.Descendants%2A> osi, kod będzie działać, czy dokument używa sekcji.  
  
## <a name="example"></a>Przykład  
 Kwerenda używa `let` klauzuli, aby określić element, który zawiera węzeł stylu. Jeśli nie ma elementu, `styleNode` jest `null`ustawiony na:  
  
```csharp  
let styleNode = para.Elements(w + "pPr").Elements(w + "pStyle").FirstOrDefault()  
```  
  
 Klauzula `let` najpierw <xref:System.Xml.Linq.XContainer.Elements%2A> używa osi, aby `pPr`znaleźć wszystkie <xref:System.Xml.Linq.Extensions.Elements%2A> elementy o nazwie, `pStyle`a następnie używa <xref:System.Linq.Enumerable.FirstOrDefault%2A> metody rozszerzenia, aby znaleźć wszystkie elementy podrzędne o nazwie , a na końcu używa standardowego operatora kwerendy do konwersji kolekcji na singleton. Jeśli kolekcja jest `styleNode` pusta, `null`jest ustawiona na . Jest to przydatne idiom szukać `pStyle` węzła podrzędnego. Należy zauważyć, `pPr` że jeśli węzeł podrzędny nie istnieje, kod nie działa ani nie powiedzie się, zgłaszając wyjątek; zamiast `styleNode` tego jest `null`ustawiona na , co `let` jest pożądane zachowanie tej klauzuli.  
  
 Kwerenda wyświetla kolekcję typu anonimowego `StyleName` z `ParagraphNode`dwoma członkami i .  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przetwarza dokument WordprocessingML, pobierając węzły akapitu z dokumentu WordprocessingML. Identyfikuje również styl każdego akapitu. W tym przykładzie opiera się na poprzednich przykładach w tym samouczku. Nowe zapytanie jest wywoływane w komentarzach w poniższym kodzie.  
  
 Instrukcje dotyczące tworzenia dokumentu źródłowego dla tego przykładu można znaleźć w [dokumencie Tworzenie dokumentu XML open pakietu Source Office (C#).](./creating-the-source-office-open-xml-document.md)  
  
 W tym przykładzie użyto klas znalezionych w zestawie WindowsBase. Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> obszarze nazw.  
  
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
  
 W tym przykładzie po zastosowaniu do dokumentu opisanego w [dokumencie Tworzenie dokumentu XML pakietu Source Office Open (C#).](./creating-the-source-office-open-xml-document.md)  
  
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
  
## <a name="next-steps"></a>Następne kroki  
 W następnym temacie [Pobieranie tekstu akapitów (C#)](./retrieving-the-text-of-the-paragraphs.md)zostanie utworzone kwerenda, aby pobrać tekst akapitów.  
  
## <a name="see-also"></a>Zobacz też

- [Samouczek: manipulowanie zawartością w dokumencie WordprocessingML (C#)](./shape-of-wordprocessingml-documents.md)
