---
title: 'Porady: Tworzenie drzewa z element XmlReader (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6de683d8-177d-402b-b0de-d0539f1ce5d8
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4ceae7c2bee85e7b368322c8ba195dea9feff672
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-tree-from-an-xmlreader-visual-basic"></a>Porady: Tworzenie drzewa z element XmlReader (Visual Basic)
W tym temacie przedstawiono sposób tworzenia drzewo XML bezpośrednio z <xref:System.Xml.XmlReader>. Aby utworzyć <xref:System.Xml.Linq.XElement> z <xref:System.Xml.XmlReader>, należy umieścić <xref:System.Xml.XmlReader> w węźle elementu. <xref:System.Xml.XmlReader> Pominie komentarze i przetwarzanie instrukcji, ale jeśli <xref:System.Xml.XmlReader> znajduje się w węźle tekstu, zostanie zgłoszony błąd. Aby uniknąć tych błędów, umieść zawsze <xref:System.Xml.XmlReader> w elemencie przed utworzeniem drzewo XML z <xref:System.Xml.XmlReader>.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: książek (LINQ do XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).  
  
 Poniższy kod tworzy `T:System.Xml.XmlReader` obiektu, a następnie odczyty węzłów aż do znalezienia pierwszy węzeł elementu. Następnie ładuje <xref:System.Xml.Linq.XElement> obiektu.  
  
```vb  
Dim r As XmlReader = XmlReader.Create("books.xml")  
Do While r.NodeType <> XmlNodeType.Element  
    r.Read()  
Loop  
Dim e As XElement = XElement.Load(r)  
Console.WriteLine(e)  
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
 [Analiza kodu XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
