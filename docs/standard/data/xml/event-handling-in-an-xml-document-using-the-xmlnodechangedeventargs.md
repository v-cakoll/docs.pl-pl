---
title: Obsługa zdarzeń w dokumencie XML przy użyciu klasy XmlNodeChangedEventArgs
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 0fe844e3-5b6f-4fe7-ad15-22459501738b
ms.openlocfilehash: 7bca8600468d3715b1d1cca46049eb07bb8e3d03
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287782"
---
# <a name="event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs"></a>Obsługa zdarzeń w dokumencie XML przy użyciu klasy XmlNodeChangedEventArgs
**XmlNodeChangedEventArgs** hermetyzuje argumenty przekazane do programów obsługi zdarzeń zarejestrowanych w obiekcie **XmlDocument** na potrzeby obsługi zdarzeń. Zdarzenia i opis po ich uruchomieniu podano w poniższej tabeli.  
  
|Zdarzenie|Uruchamiany|  
|-----------|-----------|  
|<xref:System.Xml.XmlDocument.NodeInserting>|Gdy węzeł należący do bieżącego dokumentu zostanie wstawiony do innego węzła.|  
|<xref:System.Xml.XmlDocument.NodeInserted>|Gdy węzeł należący do bieżącego dokumentu został wstawiony do innego węzła.|  
|<xref:System.Xml.XmlDocument.NodeRemoving>|Gdy węzeł należący do tego dokumentu zostanie usunięty z dokumentu.|  
|<xref:System.Xml.XmlDocument.NodeRemoved>|Gdy węzeł należący do tego dokumentu został usunięty z jego elementu nadrzędnego.|  
|<xref:System.Xml.XmlDocument.NodeChanging>|Gdy wartość węzła ma zostać zmieniona.|  
|<xref:System.Xml.XmlDocument.NodeChanged>|Po zmianie wartości węzła.|  
  
> [!NOTE]
> Jeśli użycie pamięci przez program **XmlDataDocument** jest w pełni zoptymalizowane pod kątem korzystania z magazynu **DataSet** , **XmlDataDocument** może nie zgłaszać żadnych zdarzeń wymienionych powyżej, gdy zmiany są wprowadzane do bazowego **zestawu danych**. Jeśli potrzebujesz tych zdarzeń, musisz przechodzenie całych **dokumentów XmlDocument** raz, aby użycie pamięci było w pełni zoptymalizowane.  
  
 Poniższy przykład kodu przedstawia sposób definiowania programu obsługi zdarzeń oraz dodawania obsługi zdarzeń do zdarzenia.  
  
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
  
 Niektóre operacje w języku XML Document Object Model (DOM) to operacje złożone, które mogą powodować wyzwalanie wielu zdarzeń. Na przykład **AppendChild** może również mieć możliwość usunięcia węzła dołączanego z jego poprzedniego elementu nadrzędnego. W takim przypadku zobaczysz najpierw zdarzenie **NodeRemoved** , po którym następuje zdarzenie **NodeInserted** . Operacje, takie jak ustawienie **InnerXml** , mogą spowodować powstanie wielu zdarzeń.  
  
 Poniższy przykład kodu pokazuje Tworzenie programu obsługi zdarzeń i obsługę zdarzenia **NodeInserted** .  
  
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

- [XML Document Object Model (DOM)](xml-document-object-model-dom.md)
