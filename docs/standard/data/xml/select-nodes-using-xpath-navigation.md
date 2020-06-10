---
title: Wybieranie węzłów za pomocą nawigacji XPath
description: Dowiedz się, jak wybrać węzły XML w programie .NET. Użyj metod Document Object Model (DOM), aby móc używać nawigacji języka ścieżki XML (XPath) do wykonywania zapytań dotyczących informacji DOM.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 8e4450dc-56b3-472b-b467-32f5694f83ad
ms.openlocfilehash: aa8b6d93e25d974a0e1b53ae8be9868f6bf64be6
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662514"
---
# <a name="select-nodes-using-xpath-navigation"></a>Wybieranie węzłów za pomocą nawigacji XPath
Document Object Model XML (DOM) zawiera metody umożliwiające użycie nawigacji języka ścieżki XML (XPath) do wykonywania zapytań dotyczących informacji w modelu DOM. Możesz użyć XPath, aby znaleźć pojedynczy, konkretny węzeł lub znaleźć wszystkie węzły, które pasują do niektórych kryteriów.  
  
## <a name="xpath-select-methods"></a>Metody Select XPath  
 Klasy DOM zapewniają dwie metody wyboru XPath: <xref:System.Xml.XmlNode.SelectSingleNode%2A> metodę i <xref:System.Xml.XmlNode.SelectNodes%2A> metodę. <xref:System.Xml.XmlNode.SelectSingleNode%2A>Metoda zwraca pierwszy węzeł, który pasuje do kryteriów wyboru. <xref:System.Xml.XmlNode.SelectNodes%2A>Metoda zwraca obiekt <xref:System.Xml.XmlNodeList> , który zawiera pasujące węzły.  
  
 W poniższym przykładzie zastosowano <xref:System.Xml.XmlNode.SelectSingleNode%2A> metodę, aby wybrać pierwszy `book` węzeł, w którym nazwisko autora spełnia określone kryteria. Plik bookstore.xml (który znajduje się na końcu tego tematu) jest używany jako plik wejściowy.  
  
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
  
 W następnym przykładzie używa się <xref:System.Xml.XmlNode.SelectNodes%2A> metody, aby wybrać wszystkie węzły książek, w których cena jest większa niż określona wartość. Cena dla każdej książki na wybranej liście jest następnie programowo zmniejszona o dziesięć procent. Na koniec zaktualizowany plik jest zapisywana w konsoli programu. Plik bookstore.xml (który znajduje się na końcu tego tematu) jest używany jako plik wejściowy.  
  
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
 Wyrażenia XPath mogą zawierać przestrzenie nazw. Rozpoznawanie przestrzeni nazw jest obsługiwane przy użyciu <xref:System.Xml.XmlNamespaceManager> . Jeśli wyrażenie XPath zawiera prefiks, para identyfikatorów URI prefiksu i przestrzeni nazw musi zostać dodana do <xref:System.Xml.XmlNamespaceManager> i <xref:System.Xml.XmlNamespaceManager> jest przenoszona do <xref:System.Xml.XmlNode.SelectNodes%28System.String%2CSystem.Xml.XmlNamespaceManager%29> <xref:System.Xml.XmlNode.SelectSingleNode%28System.String%2CSystem.Xml.XmlNamespaceManager%29> metody lub. Zauważ, że w przykładach kodu Użyj, <xref:System.Xml.XmlNamespaceManager> Aby rozpoznać przestrzeń nazw bookstore.xml dokumentu.  
  
> [!NOTE]
> Jeśli wyrażenie XPath nie zawiera prefiksu, zakłada się, że przestrzeń nazw Uniform Resource Identifier (URI) jest pustą przestrzenią nazw. Jeśli plik XML zawiera domyślną przestrzeń nazw, nadal trzeba dodać prefiks i identyfikator URI przestrzeni nazw do <xref:System.Xml.XmlNamespaceManager> ; w przeciwnym razie nie zostaną wybrane węzły.  
  
#### <a name="input-file"></a>Plik wejściowy  
 Poniżej znajduje się plik bookstore.xml, który jest używany jako plik wejściowy w przykładach w tym temacie:  
  
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

- [XML Document Object Model (DOM)](xml-document-object-model-dom.md)
