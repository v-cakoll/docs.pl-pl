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
# <a name="retrieving-the-paragraphs-and-their-styles-c"></a>Pobieranie akapitów i ich stylów (C#)
W tym przykładzie napiszemy zapytanie, które pobiera węzły akapitu z dokumentu WordprocessingML. Identyfikuje także styl każdego akapitu.  
  
 To zapytanie kompiluje zapytanie w poprzednim przykładzie, [wyszukując domyślny styl akapituC#()](./finding-the-default-paragraph-style.md), który Pobiera domyślny styl z listy stylów. Te informacje są wymagane, aby zapytanie mogło identyfikować styl akapitów, w których styl nie został jawnie ustawiony. Style akapitu są ustawiane `w:pPr` za pomocą elementu. Jeśli akapit nie zawiera tego elementu, zostanie sformatowany przy użyciu stylu domyślnego.  
  
 W tym temacie wyjaśniono znaczenie niektórych fragmentów zapytania, a następnie przedstawiono zapytanie w ramach kompletnego, działającego przykładu.  
  
## <a name="example"></a>Przykład  
 Źródło zapytania do pobrania wszystkich akapitów w dokumencie i ich stylów jest następująca:  
  
```csharp  
xDoc.Root.Element(w + "body").Descendants(w + "p")  
```  
  
 To wyrażenie jest podobne do źródła zapytania w poprzednim przykładzie, co umożliwia [znalezienie domyślnego stylu akapitu (C#)](./finding-the-default-paragraph-style.md). Główną różnicą jest to, że używa <xref:System.Xml.Linq.XContainer.Descendants%2A> osi zamiast <xref:System.Xml.Linq.XContainer.Elements%2A> osi. Zapytanie używa <xref:System.Xml.Linq.XContainer.Descendants%2A> osi, ponieważ w dokumentach, w których znajdują się sekcje, akapity nie będą bezpośrednimi elementami podrzędnymi elementu body, a akapity będą dwa poziomy w hierarchii. Korzystając <xref:System.Xml.Linq.XContainer.Descendants%2A> z osi, kod będzie działał niezależnie od tego, czy dokument korzysta z sekcji.  
  
## <a name="example"></a>Przykład  
 Zapytanie używa `let` klauzuli do określenia elementu, który zawiera węzeł stylu. Jeśli nie ma elementu, `styleNode` zostanie `null`ustawiona wartość:  
  
```csharp  
let styleNode = para.Elements(w + "pPr").Elements(w + "pStyle").FirstOrDefault()  
```  
  
 `pPr` <xref:System.Xml.Linq.Extensions.Elements%2A> `pStyle` <xref:System.Linq.Enumerable.FirstOrDefault%2A> Klauzula najpierw <xref:System.Xml.Linq.XContainer.Elements%2A> używa osi, aby znaleźć wszystkie elementy o nazwie, następnie używa metody rozszerzenia do znajdowania wszystkich elementów podrzędnych o nazwie, a wreszcie używa zapytania standardowego `let` operator do konwersji kolekcji na pojedynczą. Jeśli kolekcja jest pusta, `styleNode` jest ustawiona na. `null` Jest to przydatny idiom do wyszukiwania `pStyle` węzła podrzędnego. Należy pamiętać, że `pPr` Jeśli węzeł podrzędny nie istnieje, kod jest lub nie powiedzie się, zwracając wyjątek; `styleNode` zamiast tego jest ustawiony `null`na, który jest pożądanym zachowaniem tej `let` klauzuli.  
  
 Zapytanie projektuje kolekcję typu anonimowego z dwoma członkami `StyleName` i. `ParagraphNode`  
  
## <a name="example"></a>Przykład  
 Ten przykład przetwarza dokument WordprocessingML, pobierając węzły akapitu z dokumentu WordprocessingML. Identyfikuje także styl każdego akapitu. Ten przykład kompiluje się zgodnie z poprzednimi przykładami w tym samouczku. Nowe zapytanie jest wywoływane w komentarzach w poniższym kodzie.  
  
 Instrukcje dotyczące tworzenia dokumentu źródłowego dla tego przykładu można znaleźć w temacie [Tworzenie źródłowego dokumentu Office Open XMLC#()](./creating-the-source-office-open-xml-document.md).  
  
 Ten przykład używa klas znalezionych w zestawie 'Windowsbase. Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> przestrzeni nazw.  
  
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
  
 Ten przykład generuje następujące dane wyjściowe w przypadku zastosowania do dokumentu opisanego w temacie [Tworzenie źródłowego dokumentu Office Open XML (C#)](./creating-the-source-office-open-xml-document.md).  
  
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
 W następnym temacie, [pobierając tekst akapitówC#()](./retrieving-the-text-of-the-paragraphs.md), utworzysz zapytanie umożliwiające pobranie tekstu akapitów.  
  
## <a name="see-also"></a>Zobacz także

- [Samouczek: Manipulowanie zawartością w dokumencie WordprocessingML (C#)](./shape-of-wordprocessingml-documents.md)
