---
title: Obsługa zdarzeń w dokumencie XML przy użyciu klasy XmlNodeChangedEventArgs
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 0fe844e3-5b6f-4fe7-ad15-22459501738b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0c382b22825512000a906af8a865b6b7c5f4c73c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61966619"
---
# <a name="event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs"></a>Obsługa zdarzeń w dokumencie XML przy użyciu klasy XmlNodeChangedEventArgs
**Klasy XmlNodeChangedEventArgs** hermetyzuje Argumenty przekazane do obsługi zdarzeń zarejestrowane na **XmlDocument** obiektu do obsługi zdarzeń. Zdarzenia i opis tego kiedy są one uruchamiane jest podana w poniższej tabeli.  
  
|Zdarzenie|Wyzwolone|  
|-----------|-----------|  
|<xref:System.Xml.XmlDocument.NodeInserting>|Gdy węzeł należące do bieżącego dokumentu zostanie wstawiony do innego węzła.|  
|<xref:System.Xml.XmlDocument.NodeInserted>|Gdy węzeł należące do bieżącego dokumentu został wstawiony do innego węzła.|  
|<xref:System.Xml.XmlDocument.NodeRemoving>|Gdy węzeł należących do tego dokumentu zostanie usunięte z dokumentu.|  
|<xref:System.Xml.XmlDocument.NodeRemoved>|Gdy węzeł należących do tego dokumentu został usunięty z jego elementu nadrzędnego.|  
|<xref:System.Xml.XmlDocument.NodeChanging>|Wartość węzła po zostanie zmieniony.|  
|<xref:System.Xml.XmlDocument.NodeChanged>|Jeśli zmieniono wartości węzła.|  
  
> [!NOTE]
>  Jeśli **XmlDataDocument** użycie pamięci jest w pełni zoptymalizowana do użytku **DataSet** magazynu **XmlDataDocument** mogą nie zgłaszać dowolnego zdarzenia wymienione powyżej, gdy zmiany zostaną wprowadzone do podstawowej **zestawu danych**. Jeśli potrzebujesz tych zdarzeń, musi przechodzić przez cały **XmlDocument** raz, aby nie jest w pełni zoptymalizowane pod kątem użycia pamięci.  
  
 Poniższy przykład kodu pokazuje, jak zdefiniować procedurę obsługi zdarzeń oraz sposób dodawania programu obsługi zdarzeń do zdarzenia.  
  
```vb  
' Attach the event handler, NodeInsertedHandler, to the NodeInserted  
' event.  
Dim doc as XmlDocument = new XmlDocument()  
Dim XmlNodeChgEHdlr as XmlNodeChangedEventHandler = new XmlNodeChangedEventHandler(addressof MyNodeChangedEvent)   
AddHandler doc.NodeInserted, XmlNodeChgEHdlr   
  
Dim n as XmlNode = doc.CreateElement( "element" )  
Console.WriteLine( "Before Event Inserting" )   
  
' This is the point where the new node is being inserted in the tree,  
' and this is the point where the NodeInserted event is raised.  
doc.AppendChild( n )  
Console.WriteLine( "After Event Inserting" )   
  
' Define the event handler that handles the NodeInserted event.  
sub NodeInsertedHandler(src as Object, args as XmlNodeChangedEventArgs)  
    Console.WriteLine("Node " + args.Node.Name + " inserted!!")  
end sub  
```  
  
```csharp  
// Attach the event handler, NodeInsertedHandler, to the NodeInserted  
// event.  
XmlDocument doc = new XmlDocument();  
doc.NodeInserted += new XmlNodeChangedEventHandler(NodeInsertedHandler);  
XmlNode n = doc.CreateElement( "element" );  
Console.WriteLine( "Before Event Inserting" );  
  
// This is the point where the new node is being inserted in the tree,  
// and this is the point where the NodeInserted event is raised.  
doc.AppendChild( n );  
Console.WriteLine( "After Event Inserting" );   
  
// Define the event handler that handles the NodeInserted event.  
void NodeInsertedHandler(Object src, XmlNodeChangedEventArgs args)  
{  
    Console.WriteLine("Node " + args.Node.Name + " inserted!!");  
}  
```  
  
 Niektóre operacje XML Document Object Model (DOM) są złożone operacje, które może spowodować wiele zdarzeń, które są wywoływane. Na przykład **AppendChild** może być też koniecznie Usuń węzeł dołączanie od jego poprzedniego elementu nadrzędnego. W takim przypadku zobaczysz **NodeRemoved** zdarzenia wywoływane po pierwsze, a następnie **NodeInserted** zdarzeń. Operacje, takie jak ustawienie **InnerXml** może spowodować wiele zdarzeń.  
  
 W poniższym przykładzie kodu pokazano tworzenie obsługi zdarzeń i obsługa **NodeInserted** zdarzeń.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports Microsoft.VisualBasic  
  
Public Class Sample  
  
    Private Const filename As String = "books.xml"  
  
    Shared Sub Main()  
        Dim mySample As Sample = New Sample()  
        mySample.Run(filename)  
    End Sub  
  
    Public Sub Run(ByVal args As String)  
        ' Create and load the XML document.  
        Console.WriteLine("Loading file 0 ...", args)  
        Dim doc As XmlDocument = New XmlDocument()  
        doc.Load(args)  
  
        ' Create the event handlers.  
        Dim XmlNodeChgEHdlr As XmlNodeChangedEventHandler = New XmlNodeChangedEventHandler(AddressOf MyNodeChangedEvent)  
        Dim XmlNodeInsrtEHdlr As XmlNodeChangedEventHandler = New XmlNodeChangedEventHandler(AddressOf MyNodeInsertedEvent)  
        AddHandler doc.NodeChanged, XmlNodeChgEHdlr  
        AddHandler doc.NodeInserted, XmlNodeInsrtEHdlr  
  
        ' Change the book price.  
        doc.DocumentElement.LastChild.InnerText = "5.95"  
  
        ' Add a new element.  
        Dim newElem As XmlElement = doc.CreateElement("style")  
        newElem.InnerText = "hardcover"  
        doc.DocumentElement.AppendChild(newElem)  
  
        Console.WriteLine(Chr(13) + Chr(10) + "Display the modified XML...")  
        Console.WriteLine(doc.OuterXml)  
    End Sub  
  
    ' Handle the NodeChanged event.  
    Public Sub MyNodeChangedEvent(ByVal src As Object, ByVal args As XmlNodeChangedEventArgs)  
        Console.Write("Node Changed Event: <0> changed", args.Node.Name)  
        If Not (args.Node.Value Is Nothing) Then  
            Console.WriteLine(" with value  0", args.Node.Value)  
        Else  
            Console.WriteLine("")  
        End If  
    End Sub  
  
    ' Handle the NodeInserted event.  
    Public Sub MyNodeInsertedEvent(ByVal src As Object, ByVal args As XmlNodeChangedEventArgs)  
        Console.Write("Node Inserted Event: <0> inserted", args.Node.Name)  
        If Not (args.Node.Value Is Nothing) Then  
            Console.WriteLine(" with value 0", args.Node.Value)  
        Else  
            Console.WriteLine("")  
        End If  
    End Sub  
  
End Class        ' End class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
  private const String filename = "books.xml";  
  
  public static void Main()  
  {  
     Sample mySample = new Sample();  
     mySample.Run(filename);  
  }  
  
  public void Run(String args)  
  {  
  
     // Create and load the XML document.  
     Console.WriteLine ("Loading file {0} ...", args);  
     XmlDocument doc = new XmlDocument();  
     doc.Load (args);  
  
     // Create the event handlers.  
     doc.NodeChanged += new XmlNodeChangedEventHandler(this.MyNodeChangedEvent);  
     doc.NodeInserted += new XmlNodeChangedEventHandler(this.MyNodeInsertedEvent);  
  
     // Change the book price.  
     doc.DocumentElement.LastChild.InnerText = "5.95";  
  
     // Add a new element.  
     XmlElement newElem = doc.CreateElement("style");  
     newElem.InnerText = "hardcover";  
     doc.DocumentElement.AppendChild(newElem);  
  
     Console.WriteLine("\r\nDisplay the modified XML...");  
     Console.WriteLine(doc.OuterXml);             
  
  }  
  
  // Handle the NodeChanged event.  
  public void MyNodeChangedEvent(Object src, XmlNodeChangedEventArgs args)  
  {  
     Console.Write("Node Changed Event: <{0}> changed", args.Node.Name);  
     if (args.Node.Value != null)  
     {  
        Console.WriteLine(" with value  {0}", args.Node.Value);  
     }  
     else  
       Console.WriteLine("");  
  }  
  
  // Handle the NodeInserted event.  
  public void MyNodeInsertedEvent(Object src, XmlNodeChangedEventArgs args)  
  {  
     Console.Write("Node Inserted Event: <{0}> inserted", args.Node.Name);  
     if (args.Node.Value != null)  
     {  
        Console.WriteLine(" with value {0}", args.Node.Value);  
     }  
     else  
        Console.WriteLine("");  
  }  
  
} // End class   
```  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Xml.XmlNodeChangedEventArgs> i <xref:System.Xml.XmlNodeChangedEventHandler>.  
  
## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
