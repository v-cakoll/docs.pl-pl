---
title: 'Instrukcje: serializowanie obiektu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
ms.assetid: a1207d05-32b2-4953-8582-959607991227
ms.openlocfilehash: a587a132446a5f5d74b2d534b1ca3b93ccca1480
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928992"
---
# <a name="how-to-serialize-an-object"></a><span data-ttu-id="6351e-102">Instrukcje: serializowanie obiektu</span><span class="sxs-lookup"><span data-stu-id="6351e-102">How to: Serialize an Object</span></span>
<span data-ttu-id="6351e-103">Do serializacji obiektu, należy najpierw utworzyć obiekt, który ma być serializowany i ustaw jego właściwości publiczne oraz pól.</span><span class="sxs-lookup"><span data-stu-id="6351e-103">To serialize an object, first create the object that is to be serialized and set its public properties and fields.</span></span> <span data-ttu-id="6351e-104">W tym celu należy określić transportu format, w którym strumień XML mają być przechowywane jako strumień lub jako PLik.</span><span class="sxs-lookup"><span data-stu-id="6351e-104">To do this, you must determine the transport format in which the XML stream is to be stored, either as a stream or as a file.</span></span> <span data-ttu-id="6351e-105">Na przykład, jeśli strumień XML musi być zapisany w postaci trwałej, Utwórz <xref:System.IO.FileStream> obiekt.</span><span class="sxs-lookup"><span data-stu-id="6351e-105">For example, if the XML stream must be saved in a permanent form, create a <xref:System.IO.FileStream> object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6351e-106">Aby uzyskać więcej przykładów serializacji XML, zobacz [przykłady serializacji XML](../../../docs/standard/serialization/examples-of-xml-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="6351e-106">For more examples of XML serialization, see [Examples of XML Serialization](../../../docs/standard/serialization/examples-of-xml-serialization.md).</span></span>  
  
### <a name="to-serialize-an-object"></a><span data-ttu-id="6351e-107">Do serializacji obiektu</span><span class="sxs-lookup"><span data-stu-id="6351e-107">To serialize an object</span></span>  
  
1. <span data-ttu-id="6351e-108">Utworzenie obiektu i ustaw jego publiczny pola i właściwości.</span><span class="sxs-lookup"><span data-stu-id="6351e-108">Create the object and set its public fields and properties.</span></span>  
  
2. <span data-ttu-id="6351e-109">Budowy <xref:System.Xml.Serialization.XmlSerializer> za pomocą typu obiektu.</span><span class="sxs-lookup"><span data-stu-id="6351e-109">Construct a <xref:System.Xml.Serialization.XmlSerializer> using the type of the object.</span></span> <span data-ttu-id="6351e-110">Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Serialization.XmlSerializer> klasy konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="6351e-110">For more information, see the <xref:System.Xml.Serialization.XmlSerializer> class constructors.</span></span>  
  
3. <span data-ttu-id="6351e-111">Wywołanie <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> metodę w celu wygenerowania strumień XML lub PLik reprezentacja właściwości publiczne i pola obiektu.</span><span class="sxs-lookup"><span data-stu-id="6351e-111">Call the <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> method to generate either an XML stream or a file representation of the object's public properties and fields.</span></span> <span data-ttu-id="6351e-112">Poniższy przykład tworzy plik.</span><span class="sxs-lookup"><span data-stu-id="6351e-112">The following example creates a file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6351e-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6351e-113">See also</span></span>

- [<span data-ttu-id="6351e-114">Wprowadzenie do serializacji XML</span><span class="sxs-lookup"><span data-stu-id="6351e-114">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="6351e-115">Instrukcje: Deserializacja obiektu</span><span class="sxs-lookup"><span data-stu-id="6351e-115">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
