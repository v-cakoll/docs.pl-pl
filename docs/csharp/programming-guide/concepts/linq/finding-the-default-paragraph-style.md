---
title: Znajdowanie domyślnego stylu akapitu (C#)
ms.date: 07/20/2015
ms.assetid: be102177-8ab0-444a-b671-7023e555ffdb
ms.openlocfilehash: 8cc1f1b9df208b0b180e5fe4a50922b5ee46b480
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169535"
---
# <a name="finding-the-default-paragraph-style-c"></a>Znajdowanie domyślnego stylu akapitu (C#)
Pierwszym zadaniem w samouczku Manipulowanie informacjami w samouczku dokumentu WordprocessingML jest znalezienie domyślnego stylu akapitów w dokumencie.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie otwiera dokument Języka WordprocessingML pakietu Office Open, znajduje części dokumentu i stylu pakietu, a następnie wykonuje kwerendę, która znajduje domyślną nazwę stylu. Aby uzyskać informacje o pakietach dokumentów XML pakietu Office Open i ich częściach, zobacz [Szczegóły dokumentów WordprocessingML pakietu Office (C#).](./wordprocessingml-document-with-styles.md)  
  
 Kwerenda znajduje węzeł `w:style` o nazwie, `w:type` który ma atrybut o nazwie o wartości `w:default` "akapit", a także ma atrybut o nazwie o wartości "1". Ponieważ będzie tylko jeden węzeł XML z tymi atrybutami, kwerenda używa <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operatora do konwersji kolekcji na singleton. Następnie pobiera wartość atrybutu o `w:styleId`nazwie .  
  
 W tym przykładzie użyto klas z zestawu WindowsBase. Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> obszarze nazw.  
  
### <a name="code"></a>Code  
  
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
  
```output  
The default style is: Normal  
```  
  
## <a name="next-steps"></a>Następne kroki  
 W następnym przykładzie utworzysz podobną kwerendę, która znajdzie wszystkie akapity w dokumencie i ich style:  
  
- [Pobieranie akapitów i ich stylów (C#)](./retrieving-the-paragraphs-and-their-styles.md)  
