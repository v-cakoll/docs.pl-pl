---
title: Pobieranie uporządkowanych węzłów na podstawie indeksu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 5412c90f-2703-4aa8-a9c4-1b8a35183c37
ms.openlocfilehash: 72e866e43b556d8534024a219d924b1f372ed073
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710521"
---
# <a name="ordered-node-retrieval-by-index"></a><span data-ttu-id="a4088-102">Pobieranie uporządkowanych węzłów na podstawie indeksu</span><span class="sxs-lookup"><span data-stu-id="a4088-102">Ordered Node Retrieval by Index</span></span>
<span data-ttu-id="a4088-103">Organizacja World Wide Web Consortium (W3C) XML Document Object Model (DOM) również opisuje powstanie, który ma możliwość obsługi uporządkowanej listy węzłów, w przeciwieństwie do zestawu nieuporządkowanego obsługiwanego przez **XmlNamedNodeMap**.</span><span class="sxs-lookup"><span data-stu-id="a4088-103">The World Wide Web Consortium (W3C) XML Document Object Model (DOM) also describes a NodeList, which has the ability to handle an ordered list of nodes, as opposed to the unordered set handled by the **XmlNamedNodeMap**.</span></span> <span data-ttu-id="a4088-104">Powstanie w strukturze Microsoft .NET jest nazywana **XmlNodeList**.</span><span class="sxs-lookup"><span data-stu-id="a4088-104">The NodeList in the Microsoft .NET Framework is called **XmlNodeList**.</span></span> <span data-ttu-id="a4088-105">Metody i właściwości, które zwracają **XmlNodeList** są następujące:</span><span class="sxs-lookup"><span data-stu-id="a4088-105">Methods and properties that return an **XmlNodeList** are:</span></span>  
  
- <span data-ttu-id="a4088-106">XmlNode.ChildNodes</span><span class="sxs-lookup"><span data-stu-id="a4088-106">XmlNode.ChildNodes</span></span>  
  
- <span data-ttu-id="a4088-107">XmlDocument.GetElementsByTagName</span><span class="sxs-lookup"><span data-stu-id="a4088-107">XmlDocument.GetElementsByTagName</span></span>  
  
- <span data-ttu-id="a4088-108">XmlElement.GetElementsByTagName</span><span class="sxs-lookup"><span data-stu-id="a4088-108">XmlElement.GetElementsByTagName</span></span>  
  
- <span data-ttu-id="a4088-109">XmlNode.SelectNodes</span><span class="sxs-lookup"><span data-stu-id="a4088-109">XmlNode.SelectNodes</span></span>  
  
 <span data-ttu-id="a4088-110">**XmlNodeList** ma właściwość **Count** , która może służyć do pisania pętli do iteracji na węzłach w **XmlNodeList**, jak pokazano w następującym przykładzie kodu:</span><span class="sxs-lookup"><span data-stu-id="a4088-110">The **XmlNodeList** has a **Count** property that can be used to write loops to iterate over the nodes in the **XmlNodeList**, as shown in the following code sample:</span></span>  
  
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
  
 <span data-ttu-id="a4088-111">Oprócz właściwości **Count** istnieje metoda **GetEnumerator** , która zapewnia, `foreach` iteracji stylu w kolekcji węzłów w **XmlNodeList**.</span><span class="sxs-lookup"><span data-stu-id="a4088-111">In addition to the **Count** property, there is a **GetEnumerator** method that provides a, `foreach` style iteration over the collection of nodes in the **XmlNodeList**.</span></span> <span data-ttu-id="a4088-112">Poniższy przykład kodu pokazuje użycie instrukcji `foreach`.</span><span class="sxs-lookup"><span data-stu-id="a4088-112">The following code example shows the use of the `foreach` statement.</span></span>  
  
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
  
 <span data-ttu-id="a4088-113">Aby uzyskać więcej informacji na temat metod i właściwości dostępnych w **XmlNodeList**, zobacz <xref:System.Xml.XmlNodeList>.</span><span class="sxs-lookup"><span data-stu-id="a4088-113">For more information on the methods and properties available on the **XmlNodeList**, see <xref:System.Xml.XmlNodeList>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4088-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a4088-114">See also</span></span>

- [<span data-ttu-id="a4088-115">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="a4088-115">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
