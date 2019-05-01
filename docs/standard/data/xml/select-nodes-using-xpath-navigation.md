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
ms.openlocfilehash: 9e02dd304893e4d9354144c5b412dfd145161c6e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026981"
---
# <a name="select-nodes-using-xpath-navigation"></a>Wybieranie węzłów za pomocą nawigacji XPath
XML Document Object Model (DOM) zawiera metody, które pozwalają na korzystanie z nawigacji z XML Path Language (XPath) do zapytania w modelu DOM. Można odnaleźć węzła jednej, określonej lub aby znaleźć wszystkie węzły, które spełniają pewne kryteria, można użyć języka XPath.  
  
## <a name="xpath-select-methods"></a>Metody Wybierz wyrażenie XPath  
 Klasy modelu DOM zapewniają dwie metody elementu XPath: <xref:System.Xml.XmlNode.SelectSingleNode%2A> metody i <xref:System.Xml.XmlNode.SelectNodes%2A> metody. <xref:System.Xml.XmlNode.SelectSingleNode%2A> Metoda zwraca pierwszy węzeł, który pasuje do kryteriów wyboru. <xref:System.Xml.XmlNode.SelectNodes%2A> Metoda zwraca <xref:System.Xml.XmlNodeList> zawierający pasujące węzły.  
  
 W poniższym przykładzie użyto <xref:System.Xml.XmlNode.SelectSingleNode%2A> metody, zaznacz pierwszą pozycję `book` węzła, w którym nazwisko autora spełnia określone kryteria. Plik bookstore.xml, (która znajduje się na końcu tego tematu) jest używany jako plik wejściowy.  
  
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
  
 W następnym przykładzie użyto <xref:System.Xml.XmlNode.SelectNodes%2A> metodę, aby zaznaczyć wszystkie węzły książki, w których cena jest większy niż określony. Dziesięć procent następnie zmniejszono programowo w ceny dla każdej książki z wybranej listy. Na koniec zaktualizowany plik jest zapisywany do konsoli. Plik bookstore.xml, (która znajduje się na końcu tego tematu) jest używany jako plik wejściowy.  
  
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
  
 Powyższe przykłady uruchom zapytanie XPath w element dokumentu. Ustawienie punkt początkowy dla wyrażenia XPath zapytania ustawia węzła kontekstu, który jest punktem wyjścia dla kwerendy XPath. Jeśli nie chcesz rozpocząć od element dokumentu, ale chcesz rozpocząć od pierwszego elementu podrzędnego elementu dokumentu, możesz programować instrukcji select w następujący sposób:  
  
```vb  
doc.DocumentElement.FirstChild.SelectNodes(. . . )  
```  
  
```csharp  
this doc.DocumentElement.FirstChild.SelectNodes(. . .);  
```  
  
 Wszystkie <xref:System.Xml.XmlNodeList> obiekty są synchronizowane z podstawowej dokumentu. W związku z tym jeśli iteracji przez listę węzłów, a następnie zmodyfikuj wartość węzła, węzeł zostaje również zaktualizowany w dokumencie, z której pochodzi. Powiadomienie w poprzednim przykładzie, gdy węzeł zostanie zmodyfikowany w wybranym <xref:System.Xml.XmlNodeList> dokumentu podstawowego jest modyfikowana również.  
  
> [!NOTE]
>  Po zmodyfikowaniu dokumentu podstawowego, zalecane jest ponowne uruchomienie wyboru. Jeśli węzeł zmodyfikowane jest taki, który może spowodować, że węzeł, który ma zostać dodany do listy węzłów, gdy nie był wcześniej lub teraz spowoduje usunięcie z listy węzłów, ma żadnej gwarancji, że listy węzłów jest prawidłowo wprowadzony.  
  
## <a name="namespaces-in-xpath-expressions"></a>Przestrzenie nazw w wyrażeniach języka XPath  
 Wyrażenia XPath mogą obejmować obszary nazw. Rozpoznawanie Namespace jest obsługiwane przy użyciu <xref:System.Xml.XmlNamespaceManager>. Jeśli wyrażenie XPath zawiera prefiks, pary prefiksu i obszaru nazw. identyfikator URI musi zostać dodany do <xref:System.Xml.XmlNamespaceManager>i <xref:System.Xml.XmlNamespaceManager> jest przekazywany do <xref:System.Xml.XmlNode.SelectNodes%28System.String%2CSystem.Xml.XmlNamespaceManager%29> lub <xref:System.Xml.XmlNode.SelectSingleNode%28System.String%2CSystem.Xml.XmlNamespaceManager%29> metody. Należy zauważyć, że powyższe przykłady kodu, użyj <xref:System.Xml.XmlNamespaceManager> można rozpoznać przestrzeni nazw dokumentu bookstore.xml.  
  
> [!NOTE]
>  Jeśli wyrażenie XPath nie zawiera prefiksu, zakłada się, że przestrzeń nazw identyfikator (URI) jest pusta przestrzeń nazw. Jeśli dane XML zawiera domyślny obszar nazw, nadal należy dodać prefiksu i identyfikator URI przestrzeni nazw do <xref:System.Xml.XmlNamespaceManager>; w przeciwnym razie zostanie wybrany żadnych węzłów.  
  
#### <a name="input-file"></a>Plik wejściowy  
 Poniżej znajduje się plik bookstore.xml, która jest używana jako plik wejściowy w przykładach w tym temacie:  
  
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
