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
# <a name="extending-the-dom"></a><span data-ttu-id="b49da-102">Rozszerzanie modelu DOM</span><span class="sxs-lookup"><span data-stu-id="b49da-102">Extending the DOM</span></span>

<span data-ttu-id="b49da-103">Struktura Microsoft .NET obejmuje podstawowy zestaw klas, który zapewnia implementację Document Object Model XML (DOM).</span><span class="sxs-lookup"><span data-stu-id="b49da-103">The Microsoft .NET Framework includes a base set of classes that provides an implementation of the XML Document Object Model (DOM).</span></span> <span data-ttu-id="b49da-104"><xref:System.Xml.XmlNode>, I jej klasy pochodne, udostępniają metody i właściwości, które umożliwiają nawigowanie, wykonywanie zapytań i modyfikowanie zawartości i struktury dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="b49da-104">The <xref:System.Xml.XmlNode>, and its derived classes, provides methods and properties that allow you to navigate, query, and modify the content and structure of an XML document.</span></span>

<span data-ttu-id="b49da-105">Gdy zawartość XML jest ładowana do pamięci przy użyciu modelu DOM, utworzone węzły zawierają informacje takie jak nazwa węzła, typ węzła i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="b49da-105">When XML content is loaded into memory using the DOM, the nodes created contain information such as node name, node type, and so on.</span></span> <span data-ttu-id="b49da-106">Mogą wystąpić sytuacje, w których wymagane są określone informacje o węzłach, których nie zapewniają klasy bazowe.</span><span class="sxs-lookup"><span data-stu-id="b49da-106">There may be occasions where you require specific node information that the base classes do not provide.</span></span> <span data-ttu-id="b49da-107">Na przykład możesz chcieć zobaczyć numer wiersza i położenie węzła.</span><span class="sxs-lookup"><span data-stu-id="b49da-107">For example, you may want to see the line number and position of the node.</span></span> <span data-ttu-id="b49da-108">W takim przypadku można utworzyć nowe klasy z istniejących klas DOM i dodać dodatkowe funkcje.</span><span class="sxs-lookup"><span data-stu-id="b49da-108">In this case, you can derive new classes from the existing DOM classes and add additional functionality.</span></span>

<span data-ttu-id="b49da-109">Podczas wyprowadzania nowych klas istnieją dwie ogólne wytyczne:</span><span class="sxs-lookup"><span data-stu-id="b49da-109">There are two general guidelines when deriving new classes:</span></span>

- <span data-ttu-id="b49da-110">Zaleca się, aby nigdy nie dziedziczyć z <xref:System.Xml.XmlNode> klasy.</span><span class="sxs-lookup"><span data-stu-id="b49da-110">It is recommended that you never derive from the <xref:System.Xml.XmlNode> class.</span></span> <span data-ttu-id="b49da-111">Zamiast tego zaleca się, aby dziedziczyć klasy z klasy odpowiadającej typowi węzła, który Cię interesuje.</span><span class="sxs-lookup"><span data-stu-id="b49da-111">Instead, it is recommended that you derive classes from the class corresponding to the node type that you are interested in.</span></span> <span data-ttu-id="b49da-112">Na przykład jeśli chcesz zwrócić dodatkowe informacje o węzłach atrybutów, można utworzyć pochodną <xref:System.Xml.XmlAttribute> klasy.</span><span class="sxs-lookup"><span data-stu-id="b49da-112">For example, if you want to return additional information on attribute nodes, you can derive from the <xref:System.Xml.XmlAttribute> class.</span></span>

- <span data-ttu-id="b49da-113">Z wyjątkiem metod tworzenia węzłów zaleca się, aby podczas przesłaniania funkcji zawsze wywoływać podstawową wersję funkcji, a następnie dodać dodatkowe przetwarzanie.</span><span class="sxs-lookup"><span data-stu-id="b49da-113">Except for the node creation methods, it is recommended that when overriding a function, you should always call the base version of the function and then add any additional processing.</span></span>

## <a name="creating-your-own-node-instances"></a><span data-ttu-id="b49da-114">Tworzenie własnych wystąpień węzłów</span><span class="sxs-lookup"><span data-stu-id="b49da-114">Creating Your Own Node Instances</span></span>

<span data-ttu-id="b49da-115"><xref:System.Xml.XmlDocument> Klasa zawiera metody tworzenia węzłów.</span><span class="sxs-lookup"><span data-stu-id="b49da-115">The <xref:System.Xml.XmlDocument> class contains node creation methods.</span></span> <span data-ttu-id="b49da-116">Po załadowaniu pliku XML te metody są wywoływane w celu utworzenia węzłów.</span><span class="sxs-lookup"><span data-stu-id="b49da-116">When an XML file is loaded, these methods are called to create the nodes.</span></span> <span data-ttu-id="b49da-117">Można zastąpić te metody, aby wystąpienia węzłów były tworzone po załadowaniu dokumentu.</span><span class="sxs-lookup"><span data-stu-id="b49da-117">You can override these methods so that your node instances are created when a document is loaded.</span></span> <span data-ttu-id="b49da-118">Na przykład, jeśli rozszerzono <xref:System.Xml.XmlElement> klasę, należy odziedziczyć <xref:System.Xml.XmlDocument> klasę i zastąpić <xref:System.Xml.XmlDocument.CreateElement%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="b49da-118">For example, if you have extended the <xref:System.Xml.XmlElement> class, you would inherit the <xref:System.Xml.XmlDocument> class and override the <xref:System.Xml.XmlDocument.CreateElement%2A> method.</span></span>

<span data-ttu-id="b49da-119">Poniższy przykład pokazuje, <xref:System.Xml.XmlDocument.CreateElement%2A> jak zastąpić metodę w celu zwrócenia implementacji <xref:System.Xml.XmlElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="b49da-119">The following example shows how to override the <xref:System.Xml.XmlDocument.CreateElement%2A> method to return your implementation of the <xref:System.Xml.XmlElement> class.</span></span>

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

## <a name="extending-a-class"></a><span data-ttu-id="b49da-120">Rozszerzanie klasy</span><span class="sxs-lookup"><span data-stu-id="b49da-120">Extending a Class</span></span>

<span data-ttu-id="b49da-121">Aby zwiększyć klasę, należy utworzyć klasę z jednej z istniejących klas DOM.</span><span class="sxs-lookup"><span data-stu-id="b49da-121">To extend a class, derive your class from one of the existing DOM classes.</span></span> <span data-ttu-id="b49da-122">Następnie można zastąpić wszystkie metody lub właściwości wirtualne w klasie podstawowej lub dodać własne.</span><span class="sxs-lookup"><span data-stu-id="b49da-122">You can then override any of the virtual methods or properties in the base class, or add your own.</span></span>

<span data-ttu-id="b49da-123">W poniższym przykładzie zostanie utworzona nowa klasa, która implementuje <xref:System.Xml.XmlElement> klasę i <xref:System.Xml.IXmlLineInfo> interfejs.</span><span class="sxs-lookup"><span data-stu-id="b49da-123">In the following example, a new class is created, which implements the <xref:System.Xml.XmlElement> class and the <xref:System.Xml.IXmlLineInfo> interface.</span></span> <span data-ttu-id="b49da-124">Zdefiniowano dodatkowe metody i właściwości, które umożliwiają użytkownikom gromadzenie informacji o wierszach.</span><span class="sxs-lookup"><span data-stu-id="b49da-124">Additional methods and properties are defined which allows users to gather line information.</span></span>

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

### <a name="example"></a><span data-ttu-id="b49da-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="b49da-125">Example</span></span>

<span data-ttu-id="b49da-126">W poniższym przykładzie liczba elementów w dokumencie XML:</span><span class="sxs-lookup"><span data-stu-id="b49da-126">The following example counts the number of elements in an XML document:</span></span>

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

#### <a name="input"></a><span data-ttu-id="b49da-127">Dane wejściowe</span><span class="sxs-lookup"><span data-stu-id="b49da-127">Input</span></span>

<span data-ttu-id="b49da-128">Book. XML</span><span class="sxs-lookup"><span data-stu-id="b49da-128">book.xml</span></span>

```xml
<!--sample XML fragment-->
<book genre='novel' ISBN='1-861001-57-5' misc='sale-item'>
  <title>The Handmaid's Tale</title>
  <price>14.95</price>
</book>
```

#### <a name="output"></a><span data-ttu-id="b49da-129">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="b49da-129">Output</span></span>

```console
Number of elements in book.xml: 3
```

## <a name="node-event-handler"></a><span data-ttu-id="b49da-130">Procedura obsługi zdarzeń węzła</span><span class="sxs-lookup"><span data-stu-id="b49da-130">Node Event Handler</span></span>

<span data-ttu-id="b49da-131">.NET Framework implementacja modelu DOM obejmuje również system zdarzeń, który umożliwia odbieranie i obsługę zdarzeń w przypadku zmiany węzłów w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="b49da-131">The .NET Framework implementation of the DOM also includes an event system that enables you to receive and handle events when nodes in an XML document change.</span></span> <span data-ttu-id="b49da-132">Korzystając z <xref:System.Xml.XmlNodeChangedEventHandler> klas <xref:System.Xml.XmlNodeChangedEventArgs> i, można przechwytywać `NodeChanged`, `NodeChanging` `NodeInserted` `NodeInserting` `NodeRemoved`,,, i `NodeRemoving` zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="b49da-132">Using the <xref:System.Xml.XmlNodeChangedEventHandler> and <xref:System.Xml.XmlNodeChangedEventArgs> classes, you can capture `NodeChanged`, `NodeChanging`, `NodeInserted`, `NodeInserting`, `NodeRemoved`, and `NodeRemoving` events.</span></span>

<span data-ttu-id="b49da-133">Proces obsługi zdarzeń działa dokładnie tak samo w klasach pochodnych, jak w oryginalnych klasach DOM.</span><span class="sxs-lookup"><span data-stu-id="b49da-133">The event-handling process works exactly the same in derived classes as it would in the original DOM classes.</span></span>

<span data-ttu-id="b49da-134">Aby uzyskać więcej informacji na temat obsługi zdarzeń węzłów [Events](../../../../docs/standard/events/index.md) , zobacz <xref:System.Xml.XmlNodeChangedEventHandler>zdarzenia i.</span><span class="sxs-lookup"><span data-stu-id="b49da-134">For more information regarding node event handling, see [Events](../../../../docs/standard/events/index.md) and <xref:System.Xml.XmlNodeChangedEventHandler>.</span></span>

## <a name="default-attributes-and-the-createelement-method"></a><span data-ttu-id="b49da-135">Atrybuty domyślne i Metoda CreateElement</span><span class="sxs-lookup"><span data-stu-id="b49da-135">Default Attributes and the CreateElement Method</span></span>

<span data-ttu-id="b49da-136">Jeśli zastępujesz <xref:System.Xml.XmlDocument.CreateElement%2A> metodę w klasie pochodnej, atrybuty domyślne nie są dodawane podczas tworzenia nowych elementów podczas edytowania dokumentu.</span><span class="sxs-lookup"><span data-stu-id="b49da-136">If you are overriding the <xref:System.Xml.XmlDocument.CreateElement%2A> method in a derived class, default attributes are not added when you are creating new elements while editing the document.</span></span> <span data-ttu-id="b49da-137">Jest to problem tylko podczas edycji.</span><span class="sxs-lookup"><span data-stu-id="b49da-137">This is only an issue while editing.</span></span> <span data-ttu-id="b49da-138">Ponieważ <xref:System.Xml.XmlDocument.CreateElement%2A> Metoda jest odpowiedzialna za dodawanie atrybutów domyślnych do <xref:System.Xml.XmlDocument>, należy zakodować tę funkcję w <xref:System.Xml.XmlDocument.CreateElement%2A> metodzie.</span><span class="sxs-lookup"><span data-stu-id="b49da-138">Because the <xref:System.Xml.XmlDocument.CreateElement%2A> method is responsible for adding default attributes to an <xref:System.Xml.XmlDocument>, you must code this functionality in the <xref:System.Xml.XmlDocument.CreateElement%2A> method.</span></span> <span data-ttu-id="b49da-139">W przypadku ładowania programu <xref:System.Xml.XmlDocument> zawierającego atrybuty domyślne zostaną one obsłużone prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="b49da-139">If you are loading an <xref:System.Xml.XmlDocument> that includes default attributes, they will be handled correctly.</span></span> <span data-ttu-id="b49da-140">Aby uzyskać więcej informacji na temat atrybutów domyślnych, zobacz [Tworzenie nowych atrybutów dla elementów w modelu dom](creating-new-attributes-for-elements-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="b49da-140">For more information on default attributes, see [Creating New Attributes for Elements in the DOM](creating-new-attributes-for-elements-in-the-dom.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b49da-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b49da-141">See also</span></span>

- [<span data-ttu-id="b49da-142">XML Document Object Model (DOM)</span><span class="sxs-lookup"><span data-stu-id="b49da-142">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
