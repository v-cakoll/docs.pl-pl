---
title: "Znajdowanie domyślny styl akapitu (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: be102177-8ab0-444a-b671-7023e555ffdb
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e2664620127e6e3ed9f723a7c23012905be3781b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="finding-the-default-paragraph-style-c"></a>Znajdowanie domyślny styl akapitu (C#)
Pierwszym zadaniem manipulowanie dane w samouczku schemat WordprocessingML dokumentu jest można znaleźć w dokumencie domyślny styl akapitów.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład powoduje otwarcie dokumentu schemat WordprocessingML Office Open XML, znajduje dokumentu i styl części pakietu, a następnie wykonuje kwerendę, która wyszukuje domyślną nazwę stylu. Aby uzyskać informacje o pakietach dokumentu pakietu Office Open XML i części składają się z, zobacz [szczegóły z dokumentów pakietu Office Open XML schemat WordprocessingML (C#)](../../../../csharp/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md).  
  
 Zapytanie znajdzie węzła o nazwie `w:style` zawierającego atrybut o nazwie `w:type` o wartości "akapitu", a także ma atrybut o nazwie `w:default` o wartości "1". Ponieważ będzie istniało tylko jeden węzeł XML z tymi atrybutami, zapytanie używa <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operatora, aby przekonwertować kolekcji jako pojedyncza. Następnie pobiera wartość atrybutu o nazwie `w:styleId`.  
  
 W tym przykładzie użyto klasy z zestawu WindowsBase. Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> przestrzeni nazw.  
  
### <a name="code"></a>Kod  
  
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
  
// The following query finds all the paragraphs that have the default style.  
string defaultStyle =   
    (string)(  
        from style in styleDoc.Root.Elements(w + "style")  
        where (string)style.Attribute(w + "type") == "paragraph"&&  
              (string)style.Attribute(w + "default") == "1"  
              select style  
    ).First().Attribute(w + "styleId");  
  
Console.WriteLine("The default style is: {0}", defaultStyle);  
```  
  
### <a name="comments"></a>Komentarze  
 Ten przykład generuje następujące wyniki:  
  
```  
The default style is: Normal  
```  
  
## <a name="next-steps"></a>Następne kroki  
 W następnym przykładzie utworzysz podobne kwerendę, która wyszukuje wszystkie akapity w dokumencie i ich style:  
  
-   [Trwa pobieranie akapitów i ich style (C#)](../../../../csharp/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Samouczek: Manipulowanie zawartości w dokumencie schemat WordprocessingML](http://msdn.microsoft.com/library/2696355e-4f83-4eaf-91b2-baa721f42fb4)
