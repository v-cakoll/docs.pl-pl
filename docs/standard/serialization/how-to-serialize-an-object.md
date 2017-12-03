---
title: 'Porady: szeregowania obiektu'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
ms.assetid: a1207d05-32b2-4953-8582-959607991227
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 92f7d19d84f8146a5c7933119874f4223dc20b6b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-serialize-an-object"></a><span data-ttu-id="66fb8-102">Porady: szeregowania obiektu</span><span class="sxs-lookup"><span data-stu-id="66fb8-102">How to: Serialize an Object</span></span>
<span data-ttu-id="66fb8-103">Do serializacji obiektu, należy najpierw utworzyć obiekt, który ma być serializowany i ustaw jego właściwości publiczne oraz pól.</span><span class="sxs-lookup"><span data-stu-id="66fb8-103">To serialize an object, first create the object that is to be serialized and set its public properties and fields.</span></span> <span data-ttu-id="66fb8-104">W tym celu należy określić transportu format, w którym strumień XML mają być przechowywane jako strumień lub jako PLik.</span><span class="sxs-lookup"><span data-stu-id="66fb8-104">To do this, you must determine the transport format in which the XML stream is to be stored, either as a stream or as a file.</span></span> <span data-ttu-id="66fb8-105">Na przykład, jeśli strumień XML musi zostać zapisany w postaci stałe, Utwórz <xref:System.IO.FileStream> obiektu.</span><span class="sxs-lookup"><span data-stu-id="66fb8-105">For example, if the XML stream must be saved in a permanent form, create a <xref:System.IO.FileStream> object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="66fb8-106">Aby uzyskać więcej przykładów serializacji XML, zobacz [przykłady serializacji XML](../../../docs/standard/serialization/examples-of-xml-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="66fb8-106">For more examples of XML serialization, see [Examples of XML Serialization](../../../docs/standard/serialization/examples-of-xml-serialization.md).</span></span>  
  
### <a name="to-serialize-an-object"></a><span data-ttu-id="66fb8-107">Do serializacji obiektu</span><span class="sxs-lookup"><span data-stu-id="66fb8-107">To serialize an object</span></span>  
  
1.  <span data-ttu-id="66fb8-108">Utworzenie obiektu i ustaw jego publiczny pola i właściwości.</span><span class="sxs-lookup"><span data-stu-id="66fb8-108">Create the object and set its public fields and properties.</span></span>  
  
2.  <span data-ttu-id="66fb8-109">Budowy <xref:System.Xml.Serialization.XmlSerializer> za pomocą typu obiektu.</span><span class="sxs-lookup"><span data-stu-id="66fb8-109">Construct a <xref:System.Xml.Serialization.XmlSerializer> using the type of the object.</span></span> <span data-ttu-id="66fb8-110">Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Serialization.XmlSerializer> klasy konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="66fb8-110">For more information, see the <xref:System.Xml.Serialization.XmlSerializer> class constructors.</span></span>  
  
3.  <span data-ttu-id="66fb8-111">Wywołanie <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> metodę w celu wygenerowania strumień XML lub PLik reprezentacja właściwości publiczne i pola obiektu.</span><span class="sxs-lookup"><span data-stu-id="66fb8-111">Call the <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> method to generate either an XML stream or a file representation of the object's public properties and fields.</span></span> <span data-ttu-id="66fb8-112">Poniższy przykład tworzy plik.</span><span class="sxs-lookup"><span data-stu-id="66fb8-112">The following example creates a file.</span></span>  
  
    ```vb  
    Dim myObject As MySerializableClass = New MySerializableClass()  
    ' Insert code to set properties and fields of the object.  
    Dim mySerializer As XmlSerializer = New XmlSerializer(GetType(MySerializableClass))  
    ' To write to a file, create a StreamWriter object.  
    Dim myWriter As StreamWriter = New StreamWriter("myFileName.xml")  
    mySerializer.Serialize(myWriter, myObject)  
    myWriter.Close()  
    ```  
  
    ```csharp  
    MySerializableClass myObject = new MySerializableClass();  
    // Insert code to set properties and fields of the object.  
    XmlSerializer mySerializer = new   
    XmlSerializer(typeof(MySerializableClass));  
    // To write to a file, create a StreamWriter object.  
    StreamWriter myWriter = new StreamWriter("myFileName.xml");  
    mySerializer.Serialize(myWriter, myObject);  
    myWriter.Close();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="66fb8-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="66fb8-113">See Also</span></span>  
 [<span data-ttu-id="66fb8-114">Wprowadzenie do serializacji XML</span><span class="sxs-lookup"><span data-stu-id="66fb8-114">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [<span data-ttu-id="66fb8-115">Porady: deserializacji obiektu</span><span class="sxs-lookup"><span data-stu-id="66fb8-115">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
