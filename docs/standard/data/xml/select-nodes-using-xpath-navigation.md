---
title: "Wybierz węzeł, za pomocą wyrażenia XPath nawigacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 8e4450dc-56b3-472b-b467-32f5694f83ad
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 34fe3d74adc94930710cf7ee55013b471a2bd43c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="select-nodes-using-xpath-navigation"></a>Wybierz węzeł, za pomocą wyrażenia XPath nawigacji
XML modelu DOM (Document Object) zawiera metody, które umożliwiają użycie nawigacji XML Path Language (XPath) do informacji dotyczących zapytań w modelu DOM. Można znaleźć węzła jednej, określonej lub aby znaleźć wszystkie węzły, które spełniają pewne kryteria, można użyć wyrażenia XPath.  
  
## <a name="xpath-select-methods"></a>Wybierz XPath metody  
 Klasy modelu DOM Podaj dwie metody składnik elementu XPath: <xref:System.Xml.XmlNode.SelectSingleNode%2A> — metoda i <xref:System.Xml.XmlNode.SelectNodes%2A> metody. <xref:System.Xml.XmlNode.SelectSingleNode%2A> Metoda zwraca pierwszy węzeł, który spełnia kryteria wyboru. <xref:System.Xml.XmlNode.SelectNodes%2A> Metoda zwraca <xref:System.Xml.XmlNodeList> zawierający zgodne węzły.  
  
 W poniższym przykładzie użyto <xref:System.Xml.XmlNode.SelectSingleNode%2A> metody, aby zaznaczyć pierwszy `book` węzła, w którym nazwisko autora spełnia określone kryteria. Plik bookstore.xml (która jest dostępna na końcu tego tematu) jest używany jako plik wejściowy.  
  
```vb  
Dim doc As New XmlDocument()  
doc.Load("bookstore.xml")  
Dim root As XmlNode = doc.DocumentElement  
  
' Add the namespace.  
Dim nsmgr As New XmlNamespaceManager(doc.NameTable)  
nsmgr.AddNamespace("bk", "urn:newbooks-schema")  
  
' Select and display the first node in which the author's   
' last name is Kingsolver.  
Dim node As XmlNode = root.SelectSingleNode( _  
     "descendant::bk:book[bk:author/bk:last-name='Kingsolver']", nsmgr)  
Console.WriteLine(node.InnerXml)  
```  
  
```csharp  
// Load the document and set the root element.  
XmlDocument doc = new XmlDocument();  
doc.Load("bookstore.xml");  
XmlNode root = doc.DocumentElement;  
  
// Add the namespace.  
XmlNamespaceManager nsmgr = new XmlNamespaceManager(doc.NameTable);  
nsmgr.AddNamespace("bk", "urn:newbooks-schema");  
  
// Select and display the first node in which the author's   
// last name is Kingsolver.  
XmlNode node = root.SelectSingleNode(  
    "descendant::bk:book[bk:author/bk:last-name='Kingsolver']", nsmgr);  
Console.WriteLine(node.InnerXml);  
```  
  
 W następnym przykładzie użyto <xref:System.Xml.XmlNode.SelectNodes%2A> metoda, aby wybrać wszystkie węzły książki, w których cena jest większa od określonej wartości. Ceny dla każdej księgi na wybranej liście jest programowo zmniejszana o 10 procent. Na koniec zaktualizowany plik zostanie zapisany do konsoli. Plik bookstore.xml (która jest dostępna na końcu tego tematu) jest używany jako plik wejściowy.  
  
```vb  
' Load the document and set the root element.  
Dim doc As New XmlDocument()  
doc.Load("bookstore.xml")  
Dim root As XmlNode = doc.DocumentElement  
  
' Add the namespace.  
Dim nsmgr As New XmlNamespaceManager(doc.NameTable)  
nsmgr.AddNamespace("bk", "urn:newbooks-schema")  
  
' Select all nodes where the book price is greater than 10.00.  
Dim nodeList As XmlNodeList = root.SelectNodes( _  
     "descendant::bk:book[bk:price>10.00]", nsmgr)  
For Each book As XmlNode In nodeList  
     Dim price As Double  
     price = Math.Round(Convert.ToSingle( _  
          book.LastChild.InnerText) * 0.9, 2)  
     book.LastChild.InnerText = price.ToString()  
Next  
  
' Display the updated document.  
doc.Save(Console.Out)  
```  
  
```csharp  
// Load the document and set the root element.  
XmlDocument doc = new XmlDocument();  
doc.Load("bookstore.xml");  
XmlNode root = doc.DocumentElement;  
  
// Add the namespace.  
XmlNamespaceManager nsmgr = new XmlNamespaceManager(doc.NameTable);  
nsmgr.AddNamespace("bk", "urn:newbooks-schema");  
  
// Select all nodes where the book price is greater than 10.00.  
XmlNodeList nodeList = root.SelectNodes(  
     "descendant::bk:book[bk:price>10.00]", nsmgr);  
foreach (XmlNode book in nodeList)  
{  
     // Discount prices by 10%.  
     double price;  
     price = Math.Round(Convert.ToSingle(  
          book.LastChild.InnerText) * 0.9, 2);  
     book.LastChild.InnerText = price.ToString();  
}  
  
// Display the updated document.  
doc.Save(Console.Out);  
```  
  
 Powyższe przykłady uruchomić zapytanie XPath w elemencie dokumentu. Ustawianie punkt początkowy dla wyrażenia XPath zapytania ustawia węzeł kontekstu, czyli punkt początkowy dla zapytania XPath. Jeśli nie chcesz rozpocząć od element dokumentu, ale chcesz rozpocząć od pierwszego elementu podrzędnego elementu dokumentu, można kodu instrukcji select w następujący sposób:  
  
```vb  
doc.DocumentElement.FirstChild.SelectNodes(. . . )  
```  
  
```csharp  
this doc.DocumentElement.FirstChild.SelectNodes(. . .);  
```  
  
 Wszystkie <xref:System.Xml.XmlNodeList> obiekty są synchronizowane z dokumentu źródłowego. W związku z tym jeśli Iterowanie za pomocą listy węzłów i zmodyfikuj wartość węzła tego węzła zostaje również zaktualizowany w dokumencie, z której pochodzi. W poprzednim przykładzie który modyfikacji węzła w wybranym <xref:System.Xml.XmlNodeList> dokumentu podstawowego również jest modyfikowany.  
  
> [!NOTE]
>  Podczas modyfikacji dokumentu podstawowego zalecane jest ponowne uruchomienie wyboru. Jeśli węzeł zmodyfikowane jest taki, który może spowodować, że węzeł, które mają zostać dodane do listy węzłów, gdy nie został wcześniej lub teraz spowodowałoby ma zostać usunięty z listy węzłów, nie ma żadnej gwarancji, że listy węzłów są prawidłowe.  
  
## <a name="namespaces-in-xpath-expressions"></a>Przestrzenie nazw w wyrażeniach języka XPath  
 Wyrażenia XPath mogą zawierać przestrzeni nazw. Rozdzielczość Namespace jest obsługiwana przy użyciu <xref:System.Xml.XmlNamespaceManager>. Jeśli wyrażenie XPath zawiera prefiks, pary prefiksu i przestrzeni nazw. identyfikator URI musi zostać dodany do <xref:System.Xml.XmlNamespaceManager>i <xref:System.Xml.XmlNamespaceManager> jest przekazywana do <xref:System.Xml.XmlNode.SelectNodes%28System.String%2CSystem.Xml.XmlNamespaceManager%29> lub <xref:System.Xml.XmlNode.SelectSingleNode%28System.String%2CSystem.Xml.XmlNamespaceManager%29> metody. Należy zauważyć, że powyższe przykłady kodu, użyj <xref:System.Xml.XmlNamespaceManager> można rozpoznać przestrzeni nazw bookstore.xml dokumentu.  
  
> [!NOTE]
>  Jeśli wyrażenie XPath nie zawiera prefiks, zakłada się, że identyfikator URI (Uniform Resource) przestrzeń nazw jest pusta przestrzeń nazw. Jeśli dane XML zawiera domyślnej przestrzeni nazw, nadal należy dodać prefiks i identyfikator URI przestrzeni nazw do <xref:System.Xml.XmlNamespaceManager>; w przeciwnym razie zostanie wybrany żadnych węzłów.  
  
#### <a name="input-file"></a>Plik wejściowy  
 Poniżej znajduje się plik bookstore.xml, który jest używany jako pliku wejściowego w przykładach w niniejszym temacie:  
  
```xml  
<?xml version='1.0'?>  
<bookstore xmlns="urn:newbooks-schema">  
  <book genre="novel" style="hardcover">  
    <title>The Handmaid's Tale</title>  
    <author>  
      <first-name>Margaret</first-name>  
      <last-name>Atwood</last-name>  
    </author>  
    <price>19.95</price>  
  </book>  
  <book genre="novel" style="other">  
    <title>The Poisonwood Bible</title>  
    <author>  
      <first-name>Barbara</first-name>  
      <last-name>Kingsolver</last-name>  
    </author>  
    <price>11.99</price>  
  </book>  
  <book genre="novel" style="paperback">  
    <title>The Bean Trees</title>  
    <author>  
      <first-name>Barbara</first-name>  
      <last-name>Kingsolver</last-name>  
    </author>  
    <price>5.99</price>  
  </book>  
</bookstore>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Modelu obiektu dokumentu XML modelu DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
