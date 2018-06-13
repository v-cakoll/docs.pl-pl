---
title: 'Porady: deserializacji obiektu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- deserializing objects
- objects, deserializing steps
ms.assetid: 287129c8-035a-4fea-b7b3-4790057ca076
ms.openlocfilehash: 957c332b3456e2b27aca36ef2bcabbc36b4e94e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33581485"
---
# <a name="how-to-deserialize-an-object"></a><span data-ttu-id="2ea0a-102">Porady: deserializacji obiektu</span><span class="sxs-lookup"><span data-stu-id="2ea0a-102">How to: Deserialize an Object</span></span>
<span data-ttu-id="2ea0a-103">Podczas deserializacji obiektu, format transportu Określa, czy zostanie utworzony obiekt PLiku lub strumienia.</span><span class="sxs-lookup"><span data-stu-id="2ea0a-103">When you deserialize an object, the transport format determines whether you will create a stream or file object.</span></span> <span data-ttu-id="2ea0a-104">Po transport format jest określony, można wywołać <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> lub <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> metod, zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="2ea0a-104">After the transport format is determined, you can call the <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> or <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> methods, as required.</span></span>  
  
### <a name="to-deserialize-an-object"></a><span data-ttu-id="2ea0a-105">Do deserializacji obiektu</span><span class="sxs-lookup"><span data-stu-id="2ea0a-105">To deserialize an object</span></span>  
  
1.  <span data-ttu-id="2ea0a-106">Budowy <xref:System.Xml.Serialization.XmlSerializer> przy użyciu typu obiektu do deserializacji.</span><span class="sxs-lookup"><span data-stu-id="2ea0a-106">Construct a <xref:System.Xml.Serialization.XmlSerializer> using the type of the object to deserialize.</span></span>  
  
2.  <span data-ttu-id="2ea0a-107">Wywołanie <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> metodę tworzenia repliki obiektu.</span><span class="sxs-lookup"><span data-stu-id="2ea0a-107">Call the <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> method to produce a replica of the object.</span></span> <span data-ttu-id="2ea0a-108">Podczas deserializacji, należy rzutować zwróconego obiektu na typ pierwotny, jak pokazano w poniższym przykładzie deserializuje obiekt do pliku (mimo że można go również zostać przeprowadzona deserializacja strumień).</span><span class="sxs-lookup"><span data-stu-id="2ea0a-108">When deserializing, you must cast the returned object to the type of the original, as shown in the following example, which deserializes the object into a file (although it could also be deserialized into a stream).</span></span>  
  
    ```vb  
    Dim myObject As MySerializableClass  
    ' Construct an instance of the XmlSerializer with the type  
    ' of object that is being deserialized.  
    Dim mySerializer As XmlSerializer = New XmlSerializer(GetType(MySerializableClass))  
    ' To read the file, create a FileStream.  
    Dim myFileStream As FileStream = _  
    New FileStream("myFileName.xml", FileMode.Open)  
    ' Call the Deserialize method and cast to the object type.  
    myObject = CType( _  
    mySerializer.Deserialize(myFileStream), MySerializableClass)  
    ```  
  
    ```csharp  
    MySerializableClass myObject;  
    // Construct an instance of the XmlSerializer with the type  
    // of object that is being deserialized.  
    XmlSerializer mySerializer =   
    new XmlSerializer(typeof(MySerializableClass));  
    // To read the file, create a FileStream.  
    FileStream myFileStream =   
    new FileStream("myFileName.xml", FileMode.Open);  
    // Call the Deserialize method and cast to the object type.  
    myObject = (MySerializableClass)   
    mySerializer.Deserialize(myFileStream)  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2ea0a-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2ea0a-109">See Also</span></span>  
 [<span data-ttu-id="2ea0a-110">Wprowadzenie do serializacji XML</span><span class="sxs-lookup"><span data-stu-id="2ea0a-110">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [<span data-ttu-id="2ea0a-111">Instrukcje: Serializacja obiektu</span><span class="sxs-lookup"><span data-stu-id="2ea0a-111">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)
