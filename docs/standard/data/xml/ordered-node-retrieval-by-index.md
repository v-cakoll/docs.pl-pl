---
title: Uporządkowane pobierania węzła według indeksu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 5412c90f-2703-4aa8-a9c4-1b8a35183c37
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c3cfa371394e76aab832c3dd4b065eb811413322
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568628"
---
# <a name="ordered-node-retrieval-by-index"></a><span data-ttu-id="d00c9-102">Uporządkowane pobierania węzła według indeksu</span><span class="sxs-lookup"><span data-stu-id="d00c9-102">Ordered Node Retrieval by Index</span></span>
<span data-ttu-id="d00c9-103">Sieci World Wide Web konsorcjum W3C XML modelu DOM (Document Object) opisano również wstawienia, który ma możliwość obsługi uporządkowaną listę węzłów, w przeciwieństwie do zestawu nieuporządkowaną obsługiwane przez **XmlNamedNodeMap**.</span><span class="sxs-lookup"><span data-stu-id="d00c9-103">The World Wide Web Consortium (W3C) XML Document Object Model (DOM) also describes a NodeList, which has the ability to handle an ordered list of nodes, as opposed to the unordered set handled by the **XmlNamedNodeMap**.</span></span> <span data-ttu-id="d00c9-104">Wstawienia programu Microsoft .NET Framework jest nazywany **XmlNodeList**.</span><span class="sxs-lookup"><span data-stu-id="d00c9-104">The NodeList in the Microsoft .NET Framework is called **XmlNodeList**.</span></span> <span data-ttu-id="d00c9-105">Metody i właściwości, które zwracają **XmlNodeList** są:</span><span class="sxs-lookup"><span data-stu-id="d00c9-105">Methods and properties that return an **XmlNodeList** are:</span></span>  
  
-   <span data-ttu-id="d00c9-106">XmlNode.ChildNodes</span><span class="sxs-lookup"><span data-stu-id="d00c9-106">XmlNode.ChildNodes</span></span>  
  
-   <span data-ttu-id="d00c9-107">XmlDocument.GetElementsByTagName</span><span class="sxs-lookup"><span data-stu-id="d00c9-107">XmlDocument.GetElementsByTagName</span></span>  
  
-   <span data-ttu-id="d00c9-108">XmlElement.GetElementsByTagName</span><span class="sxs-lookup"><span data-stu-id="d00c9-108">XmlElement.GetElementsByTagName</span></span>  
  
-   <span data-ttu-id="d00c9-109">XmlNode.SelectNodes</span><span class="sxs-lookup"><span data-stu-id="d00c9-109">XmlNode.SelectNodes</span></span>  
  
 <span data-ttu-id="d00c9-110">**XmlNodeList** ma **liczba** właściwość, która może być użyty do zapisu pętli w celu wykonania iteracji w węzłach **XmlNodeList**, jak pokazano w poniższym przykładzie kodu:</span><span class="sxs-lookup"><span data-stu-id="d00c9-110">The **XmlNodeList** has a **Count** property that can be used to write loops to iterate over the nodes in the **XmlNodeList**, as shown in the following code sample:</span></span>  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
   doc.Load("books.xml")  
  
    ' Retrieve all book titles.  
    Dim root as XmlElement = doc.DocumentElement  
    Dim elemList as XmlNodeList = root.GetElementsByTagName("title")  
    Dim i as integer  
    for i=0  to elemList.Count-1  
        ' Display all book titles in the Node List.  
        Console.WriteLine(elemList.ItemOf(i).InnerXml)  
    next  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.Load("books.xml");  
// Retrieve all book titles.  
XmlElement root = doc.DocumentElement;  
XmlNodeList elemList = root.GetElementsByTagName("title");  
for (int i=0; i < elemList.Count; i++)  
{     
   // Display all book titles in the Node List.  
   Console.WriteLine(elemList[i].InnerXml);  
}   
```  
  
 <span data-ttu-id="d00c9-111">Oprócz **liczba** właściwości, istnieje **GetEnumerator** metoda zapewniająca, `foreach` styl iteracji w kolekcji węzły w **XmlNodeList**.</span><span class="sxs-lookup"><span data-stu-id="d00c9-111">In addition to the **Count** property, there is a **GetEnumerator** method that provides a, `foreach` style iteration over the collection of nodes in the **XmlNodeList**.</span></span> <span data-ttu-id="d00c9-112">W poniższym przykładzie pokazano sposób użycia `foreach` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="d00c9-112">The following code example shows the use of the `foreach` statement.</span></span>  
  
```vb  
Dim doc As New XmlDocument()  
doc.Load("books.xml")  
  
' Get book titles.  
Dim root As XmlElement = doc.DocumentElement  
Dim elemList As XmlNodeList = root.GetElementsByTagName("title")  
Dim ienum As IEnumerator = elemList.GetEnumerator()  
' Loop over the XmlNodeList using the enumerator ienum          
While ienum.MoveNext()  
    ' Display the book title.  
    Dim title As XmlNode = CType(ienum.Current, XmlNode)  
    Console.WriteLine(title.InnerText)  
End While  
```  
  
```csharp  
{  
     XmlDocument doc = new XmlDocument();  
     doc.Load("books.xml");  
  
     // Get book titles.  
     XmlElement root = doc.DocumentElement;  
     XmlNodeList elemList = root.GetElementsByTagName("title");  
     IEnumerator ienum = elemList.GetEnumerator();    
     // Loop over the XmlNodeList using the enumerator ienum          
     while (ienum.MoveNext())  
     {  
          // Display the book title.  
           XmlNode title = (XmlNode) ienum.Current;  
           Console.WriteLine(title.InnerText);  
     }  
  }  
```  
  
 <span data-ttu-id="d00c9-113">Aby uzyskać więcej informacji na temat metod i właściwości dostępnych na **XmlNodeList**, zobacz <xref:System.Xml.XmlNodeList>.</span><span class="sxs-lookup"><span data-stu-id="d00c9-113">For more information on the methods and properties available on the **XmlNodeList**, see <xref:System.Xml.XmlNodeList>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d00c9-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d00c9-114">See Also</span></span>  
 [<span data-ttu-id="d00c9-115">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="d00c9-115">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
