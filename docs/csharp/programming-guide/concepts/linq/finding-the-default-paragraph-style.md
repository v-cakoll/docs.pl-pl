---
title: Znajdowanie domyślnego stylu akapitu (C#)
ms.date: 07/20/2015
ms.assetid: be102177-8ab0-444a-b671-7023e555ffdb
ms.openlocfilehash: 7c81ad1aed25eea3b8363caebe0eb980ca69c557
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43479828"
---
# <a name="finding-the-default-paragraph-style-c"></a>Znajdowanie domyślnego stylu akapitu (C#)
Pierwsze zadanie w manipulowanie informacje przedstawione w samouczku dokumentu WordprocessingML jest znajdowanie domyślnego stylu akapitów w dokumencie.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład spowoduje otwarcie dokumentu Office Open XML WordprocessingML, znajduje dokument i styl części pakietu, a następnie wykonuje zapytanie, które znajdzie domyślną nazwę stylu. Dla informacji na temat pakietów dokumentu Office Open XML i części składają się one z [szczegóły dla dokumentów pakietu Office Open XML WordprocessingML (C#)](../../../../csharp/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md).  
  
 Zapytanie znajdzie węzła o nazwie `w:style` zawierającego atrybut o nazwie `w:type` z wartością "akapitu", a także ma atrybut o nazwie `w:default` z wartością "1". Ponieważ będzie istniało tylko jeden węzeł XML za pomocą tych atrybutów, zapytanie używa <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operatora do przekonwertowania kolekcji na wzorzec singleton. Następnie pobiera wartość atrybutu o nazwie `w:styleId`.  
  
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
 W następnym przykładzie utworzysz podobne zapytanie, które umożliwia znalezienie wszystkich akapitów w dokumencie i ich stylów:  
  
-   [Pobieranie akapitów i ich stylów (C#)](../../../../csharp/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Samouczek: manipulowanie zawartością w dokumencie WordprocessingML](https://msdn.microsoft.com/library/2696355e-4f83-4eaf-91b2-baa721f42fb4)
