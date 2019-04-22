---
title: 'Instrukcje: Tworzenie drzewa na podstawie elementu XmlReader (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 6de683d8-177d-402b-b0de-d0539f1ce5d8
ms.openlocfilehash: d0826112821394ac6a81ba03e7803187aaec2796
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58836470"
---
# <a name="how-to-create-a-tree-from-an-xmlreader-visual-basic"></a>Instrukcje: Tworzenie drzewa na podstawie elementu XmlReader (Visual Basic)
W tym temacie przedstawiono sposób tworzenia drzewa XML bezpośrednio z <xref:System.Xml.XmlReader>. Aby utworzyć <xref:System.Xml.Linq.XElement> z <xref:System.Xml.XmlReader>, należy umieścić <xref:System.Xml.XmlReader> węzeł elementu. <xref:System.Xml.XmlReader> Pozwoli na pominięcie komentarze i przetwarzania instrukcji, ale jeśli <xref:System.Xml.XmlReader> znajduje się w węźle tekst, zostanie zgłoszony błąd. Aby uniknąć takich błędów, umieść zawsze <xref:System.Xml.XmlReader> w elemencie przed przystąpieniem do tworzenia drzewa XML z <xref:System.Xml.XmlReader>.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto następujący dokument XML: [Przykładowy plik XML: Książki (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).  
  
 Poniższy kod tworzy `T:System.Xml.XmlReader` obiektu, a następnie odczytuje węzłów do momentu znalezienia pierwszego węzła elementu. Następnie ładuje <xref:System.Xml.Linq.XElement> obiektu.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Analizowanie kodu XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
