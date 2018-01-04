---
title: Rozszerzanie modelu DOM
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
ms.assetid: b5489c96-4afd-439a-a25d-fc82eb4a148d
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 06cac8d76b17f3ef32931ea21d0556085f05d7b1
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="extending-the-dom"></a><span data-ttu-id="63eae-102">Rozszerzanie modelu DOM</span><span class="sxs-lookup"><span data-stu-id="63eae-102">Extending the DOM</span></span>
<span data-ttu-id="63eae-103">Microsoft .NET Framework zawiera podstawowy zestaw klas, który zawiera implementację elementu XML modelu DOM (Document Object).</span><span class="sxs-lookup"><span data-stu-id="63eae-103">The Microsoft .NET Framework includes a base set of classes that provides an implementation of the XML Document Object Model (DOM).</span></span> <span data-ttu-id="63eae-104"><xref:System.Xml.XmlNode>i ich pochodne klasy, udostępnia metody i właściwości, które umożliwiają nawigowanie, zapytania i modyfikować zawartości i struktury dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="63eae-104">The <xref:System.Xml.XmlNode>, and its derived classes, provides methods and properties that allow you to navigate, query, and modify the content and structure of an XML document.</span></span>  
  
 <span data-ttu-id="63eae-105">Gdy zawartość XML jest ładowany do pamięci przy użyciu modelu DOM, węzłów tworzonych zawierają informacje, takie jak nazwa węzła, węzeł typu i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="63eae-105">When XML content is loaded into memory using the DOM, the nodes created contain information such as node name, node type, and so on.</span></span> <span data-ttu-id="63eae-106">Może istnieć przypadkach gdy wymagają klas podstawowych nie udostępniają informacje określonego węzła.</span><span class="sxs-lookup"><span data-stu-id="63eae-106">There may be occasions where you require specific node information that the base classes do not provide.</span></span> <span data-ttu-id="63eae-107">Można na przykład, zapoznaj się z numeru wiersza i pozycja węzła.</span><span class="sxs-lookup"><span data-stu-id="63eae-107">For example, you may want to see the line number and position of the node.</span></span> <span data-ttu-id="63eae-108">W takim przypadku można wyprowadzać nowe klasy z istniejącej klasy modelu DOM i dodać dodatkowe funkcje.</span><span class="sxs-lookup"><span data-stu-id="63eae-108">In this case, you can derive new classes from the existing DOM classes and add additional functionality.</span></span>  
  
 <span data-ttu-id="63eae-109">Istnieją dwa ogólne wytyczne podczas wyprowadzania nowe klasy:</span><span class="sxs-lookup"><span data-stu-id="63eae-109">There are two general guidelines when deriving new classes:</span></span>  
  
-   <span data-ttu-id="63eae-110">Zaleca się, że nigdy nie wyprowadzona z <xref:System.Xml.XmlNode> klasy.</span><span class="sxs-lookup"><span data-stu-id="63eae-110">It is recommended that you never derive from the <xref:System.Xml.XmlNode> class.</span></span> <span data-ttu-id="63eae-111">Zamiast tego zaleca się wyprowadzać klasy z klasy odpowiadający typ węzła, który chcesz.</span><span class="sxs-lookup"><span data-stu-id="63eae-111">Instead, it is recommended that you derive classes from the class corresponding to the node type that you are interested in.</span></span> <span data-ttu-id="63eae-112">Na przykład, jeśli chcesz przywrócić dodatkowe informacje w węzłach atrybutu, może pochodzić z <xref:System.Xml.XmlAttribute> klasy.</span><span class="sxs-lookup"><span data-stu-id="63eae-112">For example, if you want to return additional information on attribute nodes, you can derive from the <xref:System.Xml.XmlAttribute> class.</span></span>  
  
-   <span data-ttu-id="63eae-113">Z wyjątkiem metody tworzenia węzła zaleca się, że podczas zastępowania funkcji, należy zawsze wywołania funkcji wersja podstawowa i następnie dodać żadnych dodatkowych czynności.</span><span class="sxs-lookup"><span data-stu-id="63eae-113">Except for the node creation methods, it is recommended that when overriding a function, you should always call the base version of the function and then add any additional processing.</span></span>  
  
## <a name="creating-your-own-node-instances"></a><span data-ttu-id="63eae-114">Tworzenie wystąpień własne węzła</span><span class="sxs-lookup"><span data-stu-id="63eae-114">Creating Your Own Node Instances</span></span>  
 <span data-ttu-id="63eae-115"><xref:System.Xml.XmlDocument> Klasa zawiera metody tworzenia węzła.</span><span class="sxs-lookup"><span data-stu-id="63eae-115">The <xref:System.Xml.XmlDocument> class contains node creation methods.</span></span> <span data-ttu-id="63eae-116">Po załadowaniu pliku XML, te metody są wywoływane w celu tworzenia węzłów.</span><span class="sxs-lookup"><span data-stu-id="63eae-116">When an XML file is loaded, these methods are called to create the nodes.</span></span> <span data-ttu-id="63eae-117">Tych metod można zastąpić, dzięki czemu swoich wystąpień węzła są tworzone podczas ładowania dokumentu.</span><span class="sxs-lookup"><span data-stu-id="63eae-117">You can override these methods so that your node instances are created when a document is loaded.</span></span> <span data-ttu-id="63eae-118">Na przykład, jeśli został rozszerzony <xref:System.Xml.XmlElement> dziedziczy klasa, <xref:System.Xml.XmlDocument> klasy i zastąpić <xref:System.Xml.XmlDocument.CreateElement%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="63eae-118">For example, if you have extended the <xref:System.Xml.XmlElement> class, you would inherit the <xref:System.Xml.XmlDocument> class and override the <xref:System.Xml.XmlDocument.CreateElement%2A> method.</span></span>  
  
 <span data-ttu-id="63eae-119">Poniższy przykład przedstawia sposób przesłonięcia <xref:System.Xml.XmlDocument.CreateElement%2A> metodę, aby zwrócić implementacji <xref:System.Xml.XmlElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="63eae-119">The following example shows how to override the <xref:System.Xml.XmlDocument.CreateElement%2A> method to return your implementation of the <xref:System.Xml.XmlElement> class.</span></span>  
  
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
  
## <a name="extending-a-class"></a><span data-ttu-id="63eae-120">Rozszerzenie klasy</span><span class="sxs-lookup"><span data-stu-id="63eae-120">Extending a Class</span></span>  
 <span data-ttu-id="63eae-121">Rozszerzyć klasę, pochodzi z klasy z jednego z istniejących klas modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="63eae-121">To extend a class, derive your class from one of the existing DOM classes.</span></span> <span data-ttu-id="63eae-122">Następnie można przesłonić wirtualnej metody lub właściwości w klasie podstawowej lub dodać własne.</span><span class="sxs-lookup"><span data-stu-id="63eae-122">You can then override any of the virtual methods or properties in the base class, or add your own.</span></span>  
  
 <span data-ttu-id="63eae-123">W poniższym przykładzie jest tworzony nową klasę, która implementuje <xref:System.Xml.XmlElement> klasy i <xref:System.Xml.IXmlLineInfo> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="63eae-123">In the following example, a new class is created, which implements the <xref:System.Xml.XmlElement> class and the <xref:System.Xml.IXmlLineInfo> interface.</span></span> <span data-ttu-id="63eae-124">Dodatkowe metody i właściwości są zdefiniowane, co pozwala użytkownikom zebrać informacje dotyczące wiersza.</span><span class="sxs-lookup"><span data-stu-id="63eae-124">Additional methods and properties are defined which allows users to gather line information.</span></span>  
  
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
  
### <a name="example"></a><span data-ttu-id="63eae-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="63eae-125">Example</span></span>  
 <span data-ttu-id="63eae-126">Poniższy przykład zlicza liczbę elementów w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="63eae-126">The following example counts the number of elements in an XML document.</span></span>  
  
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
  
##### <a name="input"></a><span data-ttu-id="63eae-127">Dane wejściowe</span><span class="sxs-lookup"><span data-stu-id="63eae-127">Input</span></span>  
 <span data-ttu-id="63eae-128">Book.XML</span><span class="sxs-lookup"><span data-stu-id="63eae-128">book.xml</span></span>  
  
```xml  
<!--sample XML fragment-->  
<book genre='novel' ISBN='1-861001-57-5' misc='sale-item'>  
  <title>The Handmaid's Tale</title>  
  <price>14.95</price>  
</book>  
```  
  
##### <a name="output"></a><span data-ttu-id="63eae-129">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="63eae-129">Output</span></span>  
  
```  
Number of elements in book.xml: 3  
```  
  
 <span data-ttu-id="63eae-130">Na przykład przedstawiający sposób rozszerzyć klasy XML modelu DOM (System.Xml) zobacz www.gotdotnet.com/userfiles/XMLDom/extendDOM.zip.</span><span class="sxs-lookup"><span data-stu-id="63eae-130">For an example showing how to extend the XML DOM classes (System.Xml), see www.gotdotnet.com/userfiles/XMLDom/extendDOM.zip.</span></span>  
  
## <a name="node-event-handler"></a><span data-ttu-id="63eae-131">Program obsługi zdarzeń węzła</span><span class="sxs-lookup"><span data-stu-id="63eae-131">Node Event Handler</span></span>  
 <span data-ttu-id="63eae-132">Wdrożenia programu .NET Framework w modelu DOM obejmuje również system zdarzeń, umożliwiająca otrzymywanie i obsługę zdarzeń zmiany węzły w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="63eae-132">The .NET Framework implementation of the DOM also includes an event system that enables you to receive and handle events when nodes in an XML document change.</span></span> <span data-ttu-id="63eae-133">Przy użyciu <xref:System.Xml.XmlNodeChangedEventHandler> i <xref:System.Xml.XmlNodeChangedEventArgs> klas, można przechwytywać `NodeChanged`, `NodeChanging`, `NodeInserted`, `NodeInserting`, `NodeRemoved`, i `NodeRemoving` zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="63eae-133">Using the <xref:System.Xml.XmlNodeChangedEventHandler> and <xref:System.Xml.XmlNodeChangedEventArgs> classes, you can capture `NodeChanged`, `NodeChanging`, `NodeInserted`, `NodeInserting`, `NodeRemoved`, and `NodeRemoving` events.</span></span>  
  
 <span data-ttu-id="63eae-134">Proces obsługi zdarzeń działa tak samo w klasach pochodnych, tak jak w oryginalnym klasy modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="63eae-134">The event-handling process works exactly the same in derived classes as it would in the original DOM classes.</span></span>  
  
 <span data-ttu-id="63eae-135">Aby uzyskać więcej informacji na temat obsługi zdarzeń węzła zobacz [zdarzenia](../../../../docs/standard/events/index.md) i <xref:System.Xml.XmlNodeChangedEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="63eae-135">For more information regarding node event handling, see [Events](../../../../docs/standard/events/index.md) and <xref:System.Xml.XmlNodeChangedEventHandler>.</span></span>  
  
## <a name="default-attributes-and-the-createelement-method"></a><span data-ttu-id="63eae-136">Domyślne atrybuty i sposób funkcji CreateElement</span><span class="sxs-lookup"><span data-stu-id="63eae-136">Default Attributes and the CreateElement Method</span></span>  
 <span data-ttu-id="63eae-137">Jeśli są zastępowanie <xref:System.Xml.XmlDocument.CreateElement%2A> metody w klasie pochodnej domyślne atrybuty nie są dodawane podczas tworzenia nowych elementów podczas edytowania dokumentu.</span><span class="sxs-lookup"><span data-stu-id="63eae-137">If you are overriding the <xref:System.Xml.XmlDocument.CreateElement%2A> method in a derived class, default attributes are not added when you are creating new elements while editing the document.</span></span> <span data-ttu-id="63eae-138">Ten problem występuje tylko podczas edytowania.</span><span class="sxs-lookup"><span data-stu-id="63eae-138">This is only an issue while editing.</span></span> <span data-ttu-id="63eae-139">Ponieważ <xref:System.Xml.XmlDocument.CreateElement%2A> metoda jest odpowiedzialna za dodanie atrybutów domyślnych do <xref:System.Xml.XmlDocument>, musi kodu tę funkcję w <xref:System.Xml.XmlDocument.CreateElement%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="63eae-139">Because the <xref:System.Xml.XmlDocument.CreateElement%2A> method is responsible for adding default attributes to an <xref:System.Xml.XmlDocument>, you must code this functionality in the <xref:System.Xml.XmlDocument.CreateElement%2A> method.</span></span> <span data-ttu-id="63eae-140">Gdy ładowany <xref:System.Xml.XmlDocument> zawierającą domyślne atrybuty, będą one poprawnie obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="63eae-140">If you are loading an <xref:System.Xml.XmlDocument> that includes default attributes, they will be handled correctly.</span></span> <span data-ttu-id="63eae-141">Aby uzyskać więcej informacji dotyczących atrybutów domyślnych, zobacz [tworzenie nowych atrybutów elementów w modelu DOM](../../../../docs/standard/data/xml/creating-new-attributes-for-elements-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="63eae-141">For more information on default attributes, see [Creating New Attributes for Elements in the DOM](../../../../docs/standard/data/xml/creating-new-attributes-for-elements-in-the-dom.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63eae-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="63eae-142">See Also</span></span>  
 [<span data-ttu-id="63eae-143">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="63eae-143">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
