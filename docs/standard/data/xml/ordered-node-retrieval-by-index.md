---
title: Pobieranie uporządkowanych węzłów na podstawie indeksu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 5412c90f-2703-4aa8-a9c4-1b8a35183c37
ms.openlocfilehash: 8ff02a81ab579cc0041074990a76166fcafe6eb5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288722"
---
# <a name="ordered-node-retrieval-by-index"></a>Pobieranie uporządkowanych węzłów na podstawie indeksu
Organizacja World Wide Web Consortium (W3C) XML Document Object Model (DOM) również opisuje powstanie, który ma możliwość obsługi uporządkowanej listy węzłów, w przeciwieństwie do zestawu nieuporządkowanego obsługiwanego przez **XmlNamedNodeMap**. Powstanie w strukturze Microsoft .NET jest nazywana **XmlNodeList**. Metody i właściwości, które zwracają **XmlNodeList** są następujące:  
  
- XmlNode. ChildNodes  
  
- XmlDocument. GetElementsByTagName  
  
- XmlElement. GetElementsByTagName  
  
- XmlNode. SelectNodes  
  
 **XmlNodeList** ma właściwość **Count** , która może służyć do pisania pętli do iteracji na węzłach w **XmlNodeList**, jak pokazano w następującym przykładzie kodu:  
  
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
  
 Oprócz właściwości **Count** istnieje metoda **GetEnumerator** , która udostępnia `foreach` iterację stylu w kolekcji węzłów w **XmlNodeList**. Poniższy przykład kodu pokazuje użycie `foreach` instrukcji.  
  
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
  
 Aby uzyskać więcej informacji na temat metod i właściwości dostępnych w **XmlNodeList**, zobacz <xref:System.Xml.XmlNodeList> .  
  
## <a name="see-also"></a>Zobacz także

- [XML Document Object Model (DOM)](xml-document-object-model-dom.md)
