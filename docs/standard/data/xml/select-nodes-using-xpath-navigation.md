---
title: Wybieranie węzłów za pomocą nawigacji XPath
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 8e4450dc-56b3-472b-b467-32f5694f83ad
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b2fc0846b3f3801d64ee3bf1f1dc4b347034ad38
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939564"
---
# <a name="select-nodes-using-xpath-navigation"></a>Wybieranie węzłów za pomocą nawigacji XPath
Document Object Model XML (DOM) zawiera metody umożliwiające użycie nawigacji języka ścieżki XML (XPath) do wykonywania zapytań dotyczących informacji w modelu DOM. Możesz użyć XPath, aby znaleźć pojedynczy, konkretny węzeł lub znaleźć wszystkie węzły, które pasują do niektórych kryteriów.  
  
## <a name="xpath-select-methods"></a>Metody Select XPath  
 Klasy dom zapewniają dwie metody wyboru XPath: <xref:System.Xml.XmlNode.SelectSingleNode%2A> metodę <xref:System.Xml.XmlNode.SelectNodes%2A> i metodę. <xref:System.Xml.XmlNode.SelectSingleNode%2A> Metoda zwraca pierwszy węzeł, który pasuje do kryteriów wyboru. Metoda zwraca obiekt <xref:System.Xml.XmlNodeList> , który zawiera pasujące węzły. <xref:System.Xml.XmlNode.SelectNodes%2A>  
  
 W poniższym przykładzie zastosowano <xref:System.Xml.XmlNode.SelectSingleNode%2A> metodę, aby wybrać pierwszy `book` węzeł, w którym nazwisko autora spełnia określone kryteria. Plik księgarni. XML (który znajduje się na końcu tego tematu) jest używany jako plik wejściowy.  
  
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
  
 W następnym przykładzie używa się <xref:System.Xml.XmlNode.SelectNodes%2A> metody, aby wybrać wszystkie węzły książek, w których cena jest większa niż określona wartość. Cena dla każdej książki na wybranej liście jest następnie programowo zmniejszona o dziesięć procent. Na koniec zaktualizowany plik jest zapisywana w konsoli programu. Plik księgarni. XML (który znajduje się na końcu tego tematu) jest używany jako plik wejściowy.  
  
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
  
 Powyższe przykłady rozpoczynają kwerendę XPath w elemencie dokumentu. Ustawienie punktu początkowego dla zapytania XPath ustawia węzeł kontekstu, który jest punktem początkowym zapytania XPath. Jeśli nie chcesz zacząć od elementu dokumentu, ale chcesz zacząć od pierwszego obiektu podrzędnego elementu dokumentu, możesz kod instrukcji SELECT w następujący sposób:  
  
```vb  
doc.DocumentElement.FirstChild.SelectNodes(. . . )  
```  
  
```csharp  
this doc.DocumentElement.FirstChild.SelectNodes(. . .);  
```  
  
 Wszystkie <xref:System.Xml.XmlNodeList> obiekty są synchronizowane z dokumentem źródłowym. W związku z tym, jeśli przeprowadzisz iterację listy węzłów i zmodyfikujesz wartość węzła, ten węzeł zostanie również zaktualizowany w dokumencie, z którego pochodzi. Zwróć uwagę, że w poprzednim przykładzie modyfikowany jest również węzeł w wybranym <xref:System.Xml.XmlNodeList> dokumencie źródłowym.  
  
> [!NOTE]
> Po zmodyfikowaniu dokumentu bazowego zaleca się ponowne uruchomienie SELECT. Jeśli zmodyfikowany węzeł to taki, który może spowodować dodanie węzła do listy węzłów, gdy nie był wcześniej, lub spowoduje usunięcie go z listy węzłów, nie ma gwarancji, że lista węzłów jest teraz dokładna.  
  
## <a name="namespaces-in-xpath-expressions"></a>Przestrzenie nazw w wyrażeniach XPath  
 Wyrażenia XPath mogą zawierać przestrzenie nazw. Rozpoznawanie przestrzeni nazw jest obsługiwane przy <xref:System.Xml.XmlNamespaceManager>użyciu. Jeśli wyrażenie XPath zawiera prefiks, para identyfikatorów <xref:System.Xml.XmlNamespaceManager>URI prefiksu i przestrzeni nazw musi zostać dodana do <xref:System.Xml.XmlNamespaceManager> i jest przenoszona do <xref:System.Xml.XmlNode.SelectNodes%28System.String%2CSystem.Xml.XmlNamespaceManager%29> metody lub <xref:System.Xml.XmlNode.SelectSingleNode%28System.String%2CSystem.Xml.XmlNamespaceManager%29> . Zwróć uwagę, że przykłady kodu używają <xref:System.Xml.XmlNamespaceManager> do rozpoznawania przestrzeni nazw dokumentu księgarni. XML.  
  
> [!NOTE]
> Jeśli wyrażenie XPath nie zawiera prefiksu, zakłada się, że przestrzeń nazw Uniform Resource Identifier (URI) jest pustą przestrzenią nazw. Jeśli plik XML zawiera domyślną przestrzeń nazw, nadal trzeba dodać prefiks i identyfikator URI przestrzeni nazw do <xref:System.Xml.XmlNamespaceManager>; w przeciwnym razie nie zostaną wybrane węzły.  
  
#### <a name="input-file"></a>Plik wejściowy  
 Poniżej znajduje się plik księgarni. XML, który jest używany jako plik wejściowy w przykładach w tym temacie:  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
