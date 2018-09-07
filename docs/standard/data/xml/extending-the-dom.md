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
ms.openlocfilehash: 70e13893cf350a193411f1833e2e3b21c9b64182
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44061068"
---
# <a name="extending-the-dom"></a>Rozszerzanie modelu DOM

Microsoft .NET Framework zawiera podstawowy zestaw klas, która dostarcza implementację XML Document Object Model (DOM). <xref:System.Xml.XmlNode>i ich pochodne klasy, udostępnia metody i właściwości, które umożliwiają przechodzenie, zapytań i modyfikowanie zawartości i struktury dokumentu XML.

Gdy zawartość XML jest ładowany do pamięci przy użyciu modelu DOM, węzłów tworzonych zawierają informacje, takie jak nazwa węzła, typ węzła i tak dalej. Mogą wystąpić sytuacje, gdy wymagają informacji określonego węzła, które klasy bazowe nie są oferowane. Na przykład można wyświetlić numer wiersza i pozycja węzła. W takim przypadku może wyprowadzać nowe klasy z istniejących klas modelu DOM i dodają dodatkową funkcję.

Istnieją dwa ogólne wytyczne podczas wyprowadzania nowe klasy:

- Zalecane jest, że nigdy nie klasy wyprowadzonej z <xref:System.Xml.XmlNode> klasy. Zamiast tego zaleca się pochodną klasy z klasy odpowiadający typ węzła, który Cię interesuje. Na przykład, jeśli chcesz zostały zwrócone informacje dodatkowe na węzłów atrybutu, użytkownik może pochodzić z <xref:System.Xml.XmlAttribute> klasy.

- Z wyjątkiem metody tworzenia węzła zalecane jest, że podczas zastępowania funkcję, należy zawsze wywołać funkcję w wersji podstawowej i następnie dodaj wszelkie dodatkowe przetwarzanie.

## <a name="creating-your-own-node-instances"></a>Tworzenie wystąpień węzła

<xref:System.Xml.XmlDocument> Klasa zawiera metody tworzenia węzła. Po załadowaniu pliku XML, te metody są wywoływane w celu tworzenia węzłów. Tak, aby wystąpieniami danego węzła są tworzone podczas ładowania dokumentu, można zastąpić tych metod. Na przykład, jeśli został rozszerzony <xref:System.Xml.XmlElement> klasa będzie dziedziczyć <xref:System.Xml.XmlDocument> klasy, a także Przesłoń <xref:System.Xml.XmlDocument.CreateElement%2A> metody.

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
class LineInfoDocument : XmlDocument 
{
    public override XmlElement CreateElement(string prefix, string localname, string nsURI) 
    {
        LineInfoElement elem = new LineInfoElement(prefix, localname, nsURI, this);
        return elem;
    }
}
```

## <a name="extending-a-class"></a>Rozszerzania klasy

Aby rozszerzyć klasę, dziedziczyć klasy jeden z istniejących klas DOM. Następnie można przesłonić wirtualnej metody lub właściwości w klasie bazowej lub dodać własne.

W poniższym przykładzie jest tworzony nową klasę, która implementuje <xref:System.Xml.XmlElement> klasy i <xref:System.Xml.IXmlLineInfo> interfejsu. Dodatkowe metody i właściwości są zdefiniowane, co pozwala użytkownikom zebrać informacje wiersza.

```vb
Class LineInfoElement
   Inherits XmlElement
   Implements IXmlLineInfo
   Private lineNumber As Integer = 0
   Private linePosition As Integer = 0

   Friend Sub New(prefix As String, localname As String, nsURI As String, doc As XmlDocument)
      MyBase.New(prefix, localname, nsURI, doc)
      CType(doc, LineInfoDocument).IncrementElementCount()
   End Sub

   Public Sub SetLineInfo(linenum As Integer, linepos As Integer)
      lineNumber = linenum
      linePosition = linepos
   End Sub

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
   End Function
End Class ' End LineInfoElement class.
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

Poniższy przykład zlicza liczbę elementów w dokumencie XML:

```vb
Imports System
Imports System.Xml
Imports System.IO

Class LineInfoDocument
   Inherits XmlDocument

   Private elementCount As Integer

   Friend Sub New()
      elementCount = 0
   End Sub

   Public Overrides Function CreateElement(prefix As String, localname As String, nsURI As String) As XmlElement
      Dim elem As New LineInfoElement(prefix, localname, nsURI, Me)
      Return elem
   End Function

   Public Sub IncrementElementCount()
      elementCount += 1
   End Sub

   Public Function GetCount() As Integer
      Return elementCount
   End Function
End Class 'End LineInfoDocument class.

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
   End Sub
End Class
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

#### <a name="input"></a>Dane wejściowe

Book.XML

```xml
<!--sample XML fragment-->
<book genre='novel' ISBN='1-861001-57-5' misc='sale-item'>
  <title>The Handmaid's Tale</title>
  <price>14.95</price>
</book>
```

#### <a name="output"></a>Dane wyjściowe

```console
Number of elements in book.xml: 3
```

## <a name="node-event-handler"></a>Program obsługi zdarzeń węzła

Wdrożenia programu .NET Framework w modelu DOM zawiera także system zdarzeń, która pozwala na otrzymywanie i obsługę zdarzeń, gdy zmienią się węzły w dokumencie XML. Za pomocą <xref:System.Xml.XmlNodeChangedEventHandler> i <xref:System.Xml.XmlNodeChangedEventArgs> klasy, można przechwycić `NodeChanged`, `NodeChanging`, `NodeInserted`, `NodeInserting`, `NodeRemoved`, i `NodeRemoving` zdarzenia.

Proces obsługi zdarzeń działa tak samo w klasach pochodnych, tak jak w oryginalnym klasy modelu DOM.

Aby uzyskać więcej informacji na temat obsługi zdarzeń węzła, zobacz [zdarzenia](../../../../docs/standard/events/index.md) i <xref:System.Xml.XmlNodeChangedEventHandler>.

## <a name="default-attributes-and-the-createelement-method"></a>Atrybuty domyślne, a także metoda CreateElement

Jeśli są zastępują <xref:System.Xml.XmlDocument.CreateElement%2A> metody w klasie pochodnej, domyślne atrybuty nie są dodawane podczas tworzenia nowych elementów podczas edytowania dokumentu. Ten problem występuje tylko podczas edytowania. Ponieważ <xref:System.Xml.XmlDocument.CreateElement%2A> metodą jest odpowiedzialny za dodawanie atrybutów, które domyślne mają <xref:System.Xml.XmlDocument>, musi kodu tę funkcję w <xref:System.Xml.XmlDocument.CreateElement%2A> metody. Jeśli są ładowane <xref:System.Xml.XmlDocument> zawierającej atrybutów domyślnych, będą one poprawnie obsługiwane. Aby uzyskać więcej informacji na temat atrybutów domyślnych, zobacz [tworzenie nowych atrybutów dla elementów w modelu DOM](creating-new-attributes-for-elements-in-the-dom.md).

## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](xml-document-object-model-dom.md)  
