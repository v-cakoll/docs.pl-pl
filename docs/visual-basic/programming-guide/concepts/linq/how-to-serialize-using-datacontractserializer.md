---
title: 'Instrukcje: serializowanie przy użyciu elementu DataContractSerializer'
ms.date: 07/20/2015
ms.assetid: ecaea518-8a0f-4249-b4e5-9b3fb0cdd8ad
ms.openlocfilehash: ef3a1d7f4b4ce5705411053303d23b3ecfad81e8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397781"
---
# <a name="how-to-serialize-using-datacontractserializer-visual-basic"></a><span data-ttu-id="fad9f-102">Instrukcje: Serializowanie przy użyciu obiektu DataContractSerializer (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fad9f-102">How to: Serialize Using DataContractSerializer (Visual Basic)</span></span>
<span data-ttu-id="fad9f-103">W tym temacie przedstawiono przykład serializacji i deserializacji przy użyciu <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="fad9f-103">This topic shows an example that serializes and deserializes using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fad9f-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="fad9f-104">Example</span></span>  
 <span data-ttu-id="fad9f-105">Poniższy przykład tworzy wiele obiektów, które zawierają <xref:System.Xml.Linq.XElement> obiekty.</span><span class="sxs-lookup"><span data-stu-id="fad9f-105">The following example creates a number of objects that contain <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="fad9f-106">Następnie serializować je do plików tekstowych, a następnie deserializacji ich z plików tekstowych.</span><span class="sxs-lookup"><span data-stu-id="fad9f-106">It then serializes them to text files, and then deserializes them from the text files.</span></span>  
  
```vb  
Imports System  
Imports System.Xml  
Imports System.Xml.Linq  
Imports System.IO  
Imports System.Runtime.Serialization  
  
Public Class XLinqTest  
    Shared Sub Main()  
        Test(Of XElement)(CreateXElement())  
        Test(Of XElementContainer)(New XElementContainer())  
        Test(Of XElementNullContainer)(New XElementNullContainer())  
    End Sub  
  
    Public Shared Sub Test(Of T)(ByRef obj)  
        Dim s As DataContractSerializer = New DataContractSerializer(GetType(T))  
        Using fs As FileStream = File.Open("test" & GetType(T).Name & ".xml", FileMode.Create)  
            Console.WriteLine("Testing for type: {0}", GetType(T))  
            s.WriteObject(fs, obj)  
        End Using  
  
        Using fs As FileStream = File.Open("test" & GetType(T).Name & ".xml", FileMode.Open)  
            Dim s2 As Object = s.ReadObject(fs)  
            If s2 Is Nothing Then  
                Console.WriteLine("  Deserialized object is null (Nothing in VB)")  
            Else  
                Console.WriteLine("  Deserialized type: {0}", s2.GetType())  
            End If  
        End Using  
    End Sub  
  
    Public Shared Function CreateXElement() As XElement  
        Return New XElement(XName.Get("NameInNamespace", "http://www.adventure-works.org"))  
    End Function  
End Class  
  
<DataContract()> _  
Public Class XElementContainer  
    <DataMember()> _  
    Public member As XElement  
  
    Public Sub XElementContainer()  
        member = XLinqTest.CreateXElement()  
    End Sub  
End Class  
  
<DataContract()> _  
Public Class XElementNullContainer  
    <DataMember()> _  
    Public member As XElement  
  
    Public Sub XElementNullContainer()  
        member = Nothing  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="fad9f-107">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="fad9f-107">This example produces the following output:</span></span>  
  
```console  
Testing for type: System.Xml.Linq.XElement  
  Deserialized type: System.Xml.Linq.XElement  
Testing for type: XElementContainer  
  Deserialized type: XElementContainer  
Testing for type: XElementNullContainer  
  Deserialized type: XElementNullContainer  
```  
  
## <a name="see-also"></a><span data-ttu-id="fad9f-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fad9f-108">See also</span></span>

- [<span data-ttu-id="fad9f-109">Serializacja grafów obiektów, które zawierają obiekty XElement (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fad9f-109">Serializing Object Graphs that Contain XElement Objects (Visual Basic)</span></span>](serializing-object-graphs-that-contain-xelement-objects.md)
