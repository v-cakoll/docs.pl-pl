---
title: Jak serializować przy użyciu obiektu DataContractSerializerC#()
ms.date: 07/20/2015
ms.assetid: 3320ecbf-cdbe-480e-979c-2c14bbef9988
ms.openlocfilehash: c75455ce7c7943194ab43ac0150f5b9392f92e16
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347406"
---
# <a name="how-to-serialize-using-datacontractserializer-c"></a><span data-ttu-id="bca8e-102">Jak serializować przy użyciu obiektu DataContractSerializerC#()</span><span class="sxs-lookup"><span data-stu-id="bca8e-102">How to serialize using DataContractSerializer (C#)</span></span>
<span data-ttu-id="bca8e-103">W tym temacie przedstawiono przykład serializacji i deserializacji przy użyciu <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="bca8e-103">This topic shows an example that serializes and deserializes using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bca8e-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="bca8e-104">Example</span></span>  
 <span data-ttu-id="bca8e-105">Poniższy przykład tworzy wiele obiektów, które zawierają obiekty <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="bca8e-105">The following example creates a number of objects that contain <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="bca8e-106">Następnie serializować je do plików tekstowych, a następnie deserializacji ich z plików tekstowych.</span><span class="sxs-lookup"><span data-stu-id="bca8e-106">It then serializes them to text files, and then deserializes them from the text files.</span></span>  
  
```csharp  
using System;  
using System.Xml;  
using System.Xml.Linq;  
using System.IO;  
using System.Runtime.Serialization;  
  
public class XLinqTest  
{  
    public static void Main()  
    {  
        Test<XElement>(CreateXElement());  
        Test<XElementContainer>(new XElementContainer());  
        Test<XElementNullContainer>(new XElementNullContainer());  
    }  
  
    public static void Test<T>(T obj)  
    {  
        DataContractSerializer s = new DataContractSerializer(typeof(T));  
        using (FileStream fs = File.Open("test" + typeof(T).Name + ".xml", FileMode.Create))  
        {  
            Console.WriteLine("Testing for type: {0}", typeof(T));   
            s.WriteObject(fs, obj);  
        }  
        using (FileStream fs = File.Open("test" + typeof(T).Name + ".xml", FileMode.Open))  
        {  
            object s2 = s.ReadObject(fs);  
            if (s2 == null)  
                Console.WriteLine("  Deserialized object is null (Nothing in VB)");  
            else  
                Console.WriteLine("  Deserialized type: {0}", s2.GetType());  
        }  
    }  
  
    public static XElement CreateXElement()  
    {  
        return new XElement(XName.Get("NameInNamespace", "http://www.adventure-works.org"));  
    }  
}  
  
[DataContract]  
public class XElementContainer  
{  
    [DataMember]  
    public XElement member;  
  
    public XElementContainer()  
    {  
        member = XLinqTest.CreateXElement();  
    }  
}  
  
[DataContract]  
public class XElementNullContainer  
{  
    [DataMember]  
    public XElement member;  
  
    public XElementNullContainer()  
    {  
        member = null;  
    }  
}  
```  
  
 <span data-ttu-id="bca8e-107">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="bca8e-107">This example produces the following output:</span></span>  
  
```output  
Testing for type: System.Xml.Linq.XElement  
  Deserialized type: System.Xml.Linq.XElement  
Testing for type: XElementContainer  
  Deserialized type: XElementContainer  
Testing for type: XElementNullContainer  
  Deserialized type: XElementNullContainer  
```  
