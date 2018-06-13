---
title: 'Porady: Tworzenie drzewa z element XmlReader (C#)'
ms.date: 07/20/2015
ms.assetid: 60951c9c-7087-406c-b5bb-c60e58609b21
ms.openlocfilehash: 1a0f56655f2b328be5a6615088ef242061ddbd5a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33317274"
---
# <a name="how-to-create-a-tree-from-an-xmlreader-c"></a>Porady: Tworzenie drzewa z element XmlReader (C#)
W tym temacie przedstawiono sposób tworzenia drzewo XML bezpośrednio z <xref:System.Xml.XmlReader>. Aby utworzyć <xref:System.Xml.Linq.XElement> z <xref:System.Xml.XmlReader>, należy umieścić <xref:System.Xml.XmlReader> w węźle elementu. <xref:System.Xml.XmlReader> Pominie komentarze i przetwarzanie instrukcji, ale jeśli <xref:System.Xml.XmlReader> znajduje się w węźle tekstu, zostanie zgłoszony błąd. Aby uniknąć tych błędów, umieść zawsze <xref:System.Xml.XmlReader> w elemencie przed utworzeniem drzewo XML z <xref:System.Xml.XmlReader>.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: książek (LINQ do XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).  
  
 Poniższy kod tworzy `T:System.Xml.XmlReader` obiektu, a następnie odczyty węzłów aż do znalezienia pierwszy węzeł elementu. Następnie ładuje <xref:System.Xml.Linq.XElement> obiektu.  
  
```csharp  
XmlReader r = XmlReader.Create("books.xml");  
while (r.NodeType != XmlNodeType.Element)  
    r.Read();  
XElement e = XElement.Load(r);  
Console.WriteLine(e);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Catalog>  
   <Book id="bk101">  
      <Author>Garghentini, Davide</Author>  
      <Title>XML Developer's Guide</Title>  
      <Genre>Computer</Genre>  
      <Price>44.95</Price>  
      <PublishDate>2000-10-01</PublishDate>  
      <Description>An in-depth look at creating applications   
      with XML.</Description>  
   </Book>  
   <Book id="bk102">  
      <Author>Garcia, Debra</Author>  
      <Title>Midnight Rain</Title>  
      <Genre>Fantasy</Genre>  
      <Price>5.95</Price>  
      <PublishDate>2000-12-16</PublishDate>  
      <Description>A former architect battles corporate zombies,   
      an evil sorceress, and her own childhood to become queen   
      of the world.</Description>  
   </Book>  
</Catalog>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Analiza kodu XML (C#)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
