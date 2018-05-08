---
title: Rozszerzanie modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: b5489c96-4afd-439a-a25d-fc82eb4a148d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 93821b844d35f005afa1702e4f7922ca1320c962
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="extending-the-dom"></a>Rozszerzanie modelu DOM
Microsoft .NET Framework zawiera podstawowy zestaw klas, który zawiera implementację elementu XML modelu DOM (Document Object). <xref:System.Xml.XmlNode>i ich pochodne klasy, udostępnia metody i właściwości, które umożliwiają nawigowanie, zapytania i modyfikować zawartości i struktury dokumentu XML.  
  
 Gdy zawartość XML jest ładowany do pamięci przy użyciu modelu DOM, węzłów tworzonych zawierają informacje, takie jak nazwa węzła, węzeł typu i tak dalej. Może istnieć przypadkach gdy wymagają klas podstawowych nie udostępniają informacje określonego węzła. Można na przykład, zapoznaj się z numeru wiersza i pozycja węzła. W takim przypadku można wyprowadzać nowe klasy z istniejącej klasy modelu DOM i dodać dodatkowe funkcje.  
  
 Istnieją dwa ogólne wytyczne podczas wyprowadzania nowe klasy:  
  
-   Zaleca się, że nigdy nie wyprowadzona z <xref:System.Xml.XmlNode> klasy. Zamiast tego zaleca się wyprowadzać klasy z klasy odpowiadający typ węzła, który chcesz. Na przykład, jeśli chcesz przywrócić dodatkowe informacje w węzłach atrybutu, może pochodzić z <xref:System.Xml.XmlAttribute> klasy.  
  
-   Z wyjątkiem metody tworzenia węzła zaleca się, że podczas zastępowania funkcji, należy zawsze wywołania funkcji wersja podstawowa i następnie dodać żadnych dodatkowych czynności.  
  
## <a name="creating-your-own-node-instances"></a>Tworzenie wystąpień własne węzła  
 <xref:System.Xml.XmlDocument> Klasa zawiera metody tworzenia węzła. Po załadowaniu pliku XML, te metody są wywoływane w celu tworzenia węzłów. Tych metod można zastąpić, dzięki czemu swoich wystąpień węzła są tworzone podczas ładowania dokumentu. Na przykład, jeśli został rozszerzony <xref:System.Xml.XmlElement> dziedziczy klasa, <xref:System.Xml.XmlDocument> klasy i zastąpić <xref:System.Xml.XmlDocument.CreateElement%2A> metody.  
  
 Poniższy przykład przedstawia sposób przesłonięcia <xref:System.Xml.XmlDocument.CreateElement%2A> metodę, aby zwrócić implementacji <xref:System.Xml.XmlElement> klasy.  
  
```vb  
Class LineInfoDocument  
    Inherits XmlDocument  
        Public Overrides Function CreateElement(prefix As String, localname As String, nsURI As String) As XmlElement  
        Dim elem As New LineInfoElement(prefix, localname, nsURI, Me)  
        Return elem  
    End Function 'CreateElement  
End Class 'LineInfoDocument  
```  
  
```csharp  
class LineInfoDocument : XmlDocument {  
  public override XmlElement CreateElement(string prefix, string localname, string nsURI) {  
  LineInfoElement elem = new LineInfoElement(prefix, localname, nsURI, this);  
  return elem;  
  }  
```  
  
## <a name="extending-a-class"></a>Rozszerzenie klasy  
 Rozszerzyć klasę, pochodzi z klasy z jednego z istniejących klas modelu DOM. Następnie można przesłonić wirtualnej metody lub właściwości w klasie podstawowej lub dodać własne.  
  
 W poniższym przykładzie jest tworzony nową klasę, która implementuje <xref:System.Xml.XmlElement> klasy i <xref:System.Xml.IXmlLineInfo> interfejsu. Dodatkowe metody i właściwości są zdefiniowane, co pozwala użytkownikom zebrać informacje dotyczące wiersza.  
  
```vb  
Class LineInfoElement  
   Inherits XmlElement  
   Implements IXmlLineInfo  
   Private lineNumber As Integer = 0  
   Private linePosition As Integer = 0  
  
   Friend Sub New(prefix As String, localname As String, nsURI As String, doc As XmlDocument)  
      MyBase.New(prefix, localname, nsURI, doc)  
      CType(doc, LineInfoDocument).IncrementElementCount()  
   End Sub 'New  
  
   Public Sub SetLineInfo(linenum As Integer, linepos As Integer)  
      lineNumber = linenum  
      linePosition = linepos  
   End Sub 'SetLineInfo  
  
   Public ReadOnly Property LineNumber() As Integer  
      Get  
         Return lineNumber  
      End Get  
   End Property  
  
   Public ReadOnly Property LinePosition() As Integer  
      Get  
         Return linePosition  
      End Get  
   End Property  
  
   Public Function HasLineInfo() As Boolean  
      Return True  
   End Function 'HasLineInfo  
End Class 'LineInfoElement ' End LineInfoElement class.  
```  
  
```csharp  
class LineInfoElement : XmlElement, IXmlLineInfo {  
   int lineNumber = 0;  
   int linePosition = 0;  
   internal LineInfoElement( string prefix, string localname, string nsURI, XmlDocument doc ) : base( prefix, localname, nsURI, doc ) {  
       ( (LineInfoDocument)doc ).IncrementElementCount();  
  }     
  public void SetLineInfo( int linenum, int linepos ) {  
      lineNumber = linenum;  
      linePosition = linepos;  
  }  
  public int LineNumber {  
     get {  
       return lineNumber;  
     }  
  }  
  public int LinePosition {  
      get {  
        return linePosition;  
      }  
  }  
  public bool HasLineInfo() {   
    return true;   
  }  
} // End LineInfoElement class.  
```  
  
### <a name="example"></a>Przykład  
 Poniższy przykład zlicza liczbę elementów w dokumencie XML.  
  
```vb  
Imports System  
Imports System.Xml  
Imports System.IO  
  
 _  
  
Class LineInfoDocument  
   Inherits XmlDocument  
  
   Private elementCount As Integer  
  
   Friend Sub New()  
      elementCount = 0  
   End Sub 'New  
  
   Public Overrides Function CreateElement(prefix As String, localname As String, nsURI As String) As XmlElement  
      Dim elem As New LineInfoElement(prefix, localname, nsURI, Me)  
      Return elem  
   End Function 'CreateElement  
  
   Public Sub IncrementElementCount()  
      elementCount += 1  
   End Sub 'IncrementElementCount  
  
   Public Function GetCount() As Integer  
      Return elementCount  
   End Function 'GetCount  
End Class 'LineInfoDocument  
 _ 'End LineInfoDocument class.  
  
Class LineInfoElement  
   Inherits XmlElement  
  
   Friend Sub New(prefix As String, localname As String, nsURI As String, doc As XmlDocument)  
      MyBase.New(prefix, localname, nsURI, doc)  
      CType(doc, LineInfoDocument).IncrementElementCount()  
   End Sub 'New  
End Class 'LineInfoElement  
 _ 'End LineInfoElement class.  
  
Public Class Test  
  
   Private filename As [String] = "book.xml"  
  
   Public Shared Sub Main()  
  
      Dim doc As New LineInfoDocument()  
      doc.Load(filename)  
      Console.WriteLine("Number of elements in {0}: {1}", filename, doc.GetCount())  
   End Sub 'Main   
End Class 'Test  
```  
  
```csharp  
using System;  
using System.Xml;  
using System.IO;  
  
class LineInfoDocument : XmlDocument {  
  
  int elementCount;  
  internal LineInfoDocument():base() {  
    elementCount = 0;  
  }  
  
  public override XmlElement CreateElement( string prefix, string localname, string nsURI) {  
    LineInfoElement elem = new LineInfoElement(prefix, localname, nsURI, this );  
    return elem;  
  }  
  
  public void IncrementElementCount() {  
     elementCount++;  
  }  
  
  public int GetCount() {  
     return elementCount;  
  }  
} // End LineInfoDocument class.  
  
class LineInfoElement:XmlElement {  
  
    internal LineInfoElement( string prefix, string localname, string nsURI, XmlDocument doc ):base( prefix,localname,nsURI, doc ){  
      ((LineInfoDocument)doc).IncrementElementCount();  
    }     
} // End LineInfoElement class.  
  
public class Test {  
  
  const String filename = "book.xml";  
  public static void Main() {  
  
     LineInfoDocument doc =new LineInfoDocument();  
     doc.Load(filename);      
     Console.WriteLine("Number of elements in {0}: {1}", filename, doc.GetCount());  
  
  }  
}   
```  
  
##### <a name="input"></a>Dane wejściowe  
 Book.XML  
  
```xml  
<!--sample XML fragment-->  
<book genre='novel' ISBN='1-861001-57-5' misc='sale-item'>  
  <title>The Handmaid's Tale</title>  
  <price>14.95</price>  
</book>  
```  
  
##### <a name="output"></a>Dane wyjściowe  
  
```  
Number of elements in book.xml: 3  
```  
  
 Na przykład przedstawiający sposób rozszerzyć klasy XML modelu DOM (System.Xml) zobacz www.gotdotnet.com/userfiles/XMLDom/extendDOM.zip.  
  
## <a name="node-event-handler"></a>Program obsługi zdarzeń węzła  
 Wdrożenia programu .NET Framework w modelu DOM obejmuje również system zdarzeń, umożliwiająca otrzymywanie i obsługę zdarzeń zmiany węzły w dokumencie XML. Przy użyciu <xref:System.Xml.XmlNodeChangedEventHandler> i <xref:System.Xml.XmlNodeChangedEventArgs> klas, można przechwytywać `NodeChanged`, `NodeChanging`, `NodeInserted`, `NodeInserting`, `NodeRemoved`, i `NodeRemoving` zdarzenia.  
  
 Proces obsługi zdarzeń działa tak samo w klasach pochodnych, tak jak w oryginalnym klasy modelu DOM.  
  
 Aby uzyskać więcej informacji na temat obsługi zdarzeń węzła zobacz [zdarzenia](../../../../docs/standard/events/index.md) i <xref:System.Xml.XmlNodeChangedEventHandler>.  
  
## <a name="default-attributes-and-the-createelement-method"></a>Domyślne atrybuty i sposób funkcji CreateElement  
 Jeśli są zastępowanie <xref:System.Xml.XmlDocument.CreateElement%2A> metody w klasie pochodnej domyślne atrybuty nie są dodawane podczas tworzenia nowych elementów podczas edytowania dokumentu. Ten problem występuje tylko podczas edytowania. Ponieważ <xref:System.Xml.XmlDocument.CreateElement%2A> metoda jest odpowiedzialna za dodanie atrybutów domyślnych do <xref:System.Xml.XmlDocument>, musi kodu tę funkcję w <xref:System.Xml.XmlDocument.CreateElement%2A> metody. Gdy ładowany <xref:System.Xml.XmlDocument> zawierającą domyślne atrybuty, będą one poprawnie obsługiwane. Aby uzyskać więcej informacji dotyczących atrybutów domyślnych, zobacz [tworzenie nowych atrybutów elementów w modelu DOM](../../../../docs/standard/data/xml/creating-new-attributes-for-elements-in-the-dom.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
