---
title: Rozszerzanie modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: b5489c96-4afd-439a-a25d-fc82eb4a148d
ms.openlocfilehash: 11c7e8c8d2ea3b49fe73ab4dde4e2ccc8bc917ff
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159679"
---
# <a name="extending-the-dom"></a>Rozszerzanie modelu DOM

Struktura Microsoft .NET obejmuje podstawowy zestaw klas, który zapewnia implementację Document Object Model XML (DOM). <xref:System.Xml.XmlNode>i jej klasy pochodne udostępniają metody i właściwości, które umożliwiają nawigowanie, wykonywanie zapytań i modyfikowanie zawartości i struktury dokumentu XML.

Gdy zawartość XML jest ładowana do pamięci przy użyciu modelu DOM, utworzone węzły zawierają informacje takie jak nazwa węzła, typ węzła i tak dalej. Mogą wystąpić sytuacje, w których wymagane są określone informacje o węzłach, których nie zapewniają klasy bazowe. Na przykład możesz chcieć zobaczyć numer wiersza i położenie węzła. W takim przypadku można utworzyć nowe klasy z istniejących klas DOM i dodać dodatkowe funkcje.

Podczas wyprowadzania nowych klas istnieją dwie ogólne wytyczne:

- Zaleca się, aby nigdy nie dziedziczyć z klasy <xref:System.Xml.XmlNode>. Zamiast tego zaleca się, aby dziedziczyć klasy z klasy odpowiadającej typowi węzła, który Cię interesuje. Na przykład jeśli chcesz zwrócić dodatkowe informacje na temat węzłów atrybutów, można utworzyć z klasy <xref:System.Xml.XmlAttribute>.

- Z wyjątkiem metod tworzenia węzłów zaleca się, aby podczas przesłaniania funkcji zawsze wywoływać podstawową wersję funkcji, a następnie dodać dodatkowe przetwarzanie.

## <a name="creating-your-own-node-instances"></a>Tworzenie własnych wystąpień węzłów

Klasa <xref:System.Xml.XmlDocument> zawiera metody tworzenia węzłów. Po załadowaniu pliku XML te metody są wywoływane w celu utworzenia węzłów. Można zastąpić te metody, aby wystąpienia węzłów były tworzone po załadowaniu dokumentu. Na przykład, jeśli rozszerzono klasę <xref:System.Xml.XmlElement>, dziedziczymy klasę <xref:System.Xml.XmlDocument> i zastąpimy metodę <xref:System.Xml.XmlDocument.CreateElement%2A>.

Poniższy przykład pokazuje, jak zastąpić metodę <xref:System.Xml.XmlDocument.CreateElement%2A>, aby zwrócić implementację klasy <xref:System.Xml.XmlElement>.

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

## <a name="extending-a-class"></a>Rozszerzanie klasy

Aby zwiększyć klasę, należy utworzyć klasę z jednej z istniejących klas DOM. Następnie można zastąpić wszystkie metody lub właściwości wirtualne w klasie podstawowej lub dodać własne.

W poniższym przykładzie tworzona jest nowa klasa, która implementuje klasę <xref:System.Xml.XmlElement> i interfejs <xref:System.Xml.IXmlLineInfo>. Zdefiniowano dodatkowe metody i właściwości, które umożliwiają użytkownikom gromadzenie informacji o wierszach.

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

W poniższym przykładzie liczba elementów w dokumencie XML:

```vb
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

Book. XML

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

## <a name="node-event-handler"></a>Procedura obsługi zdarzeń węzła

.NET Framework implementacja modelu DOM obejmuje również system zdarzeń, który umożliwia odbieranie i obsługę zdarzeń w przypadku zmiany węzłów w dokumencie XML. Korzystając z klas <xref:System.Xml.XmlNodeChangedEventHandler> i <xref:System.Xml.XmlNodeChangedEventArgs>, można przechwytywać `NodeChanged`, `NodeChanging`, `NodeInserted`, `NodeInserting`, `NodeRemoved`i `NodeRemoving` zdarzeń.

Proces obsługi zdarzeń działa dokładnie tak samo w klasach pochodnych, jak w oryginalnych klasach DOM.

Aby uzyskać więcej informacji na temat obsługi zdarzeń węzłów, zobacz [zdarzenia](../../../../docs/standard/events/index.md) i <xref:System.Xml.XmlNodeChangedEventHandler>.

## <a name="default-attributes-and-the-createelement-method"></a>Atrybuty domyślne i Metoda CreateElement

Jeśli zastępujesz metodę <xref:System.Xml.XmlDocument.CreateElement%2A> w klasie pochodnej, atrybuty domyślne nie są dodawane podczas tworzenia nowych elementów podczas edytowania dokumentu. Jest to problem tylko podczas edycji. Ponieważ metoda <xref:System.Xml.XmlDocument.CreateElement%2A> jest odpowiedzialna za dodawanie atrybutów domyślnych do <xref:System.Xml.XmlDocument>, należy zakodować tę funkcję w metodzie <xref:System.Xml.XmlDocument.CreateElement%2A>. W przypadku ładowania <xref:System.Xml.XmlDocument> zawierającego atrybuty domyślne zostaną one obsłużone prawidłowo. Aby uzyskać więcej informacji na temat atrybutów domyślnych, zobacz [Tworzenie nowych atrybutów dla elementów w modelu dom](creating-new-attributes-for-elements-in-the-dom.md).

## <a name="see-also"></a>Zobacz też

- [Model DOM (XML Document Object Model)](xml-document-object-model-dom.md)
