---
title: 'Instrukcje: Serializacja obiektu'
description: W tym artykule przedstawiono sposób serializacji obiektu. Wybierz format transportu, w którym jest przechowywany strumień XML, albo jako strumień, albo jako plik.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
ms.assetid: a1207d05-32b2-4953-8582-959607991227
ms.openlocfilehash: 63446df3fa2c931c839eda91c648cee961715f93
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83377556"
---
# <a name="how-to-serialize-an-object"></a><span data-ttu-id="7c27c-104">Instrukcje: Serializacja obiektu</span><span class="sxs-lookup"><span data-stu-id="7c27c-104">How to: Serialize an Object</span></span>
<span data-ttu-id="7c27c-105">Do serializacji obiektu, należy najpierw utworzyć obiekt, który ma być serializowany i ustaw jego właściwości publiczne oraz pól.</span><span class="sxs-lookup"><span data-stu-id="7c27c-105">To serialize an object, first create the object that is to be serialized and set its public properties and fields.</span></span> <span data-ttu-id="7c27c-106">W tym celu należy określić transportu format, w którym strumień XML mają być przechowywane jako strumień lub jako PLik.</span><span class="sxs-lookup"><span data-stu-id="7c27c-106">To do this, you must determine the transport format in which the XML stream is to be stored, either as a stream or as a file.</span></span> <span data-ttu-id="7c27c-107">Na przykład, jeśli strumień XML musi być zapisany w postaci trwałej, Utwórz <xref:System.IO.FileStream> obiekt.</span><span class="sxs-lookup"><span data-stu-id="7c27c-107">For example, if the XML stream must be saved in a permanent form, create a <xref:System.IO.FileStream> object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7c27c-108">Aby uzyskać więcej przykładów serializacji XML, zobacz [przykłady serializacji XML](../../../docs/standard/serialization/examples-of-xml-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="7c27c-108">For more examples of XML serialization, see [Examples of XML Serialization](../../../docs/standard/serialization/examples-of-xml-serialization.md).</span></span>  
  
### <a name="to-serialize-an-object"></a><span data-ttu-id="7c27c-109">Do serializacji obiektu</span><span class="sxs-lookup"><span data-stu-id="7c27c-109">To serialize an object</span></span>  
  
1. <span data-ttu-id="7c27c-110">Utworzenie obiektu i ustaw jego publiczny pola i właściwości.</span><span class="sxs-lookup"><span data-stu-id="7c27c-110">Create the object and set its public fields and properties.</span></span>  
  
2. <span data-ttu-id="7c27c-111">Budowy <xref:System.Xml.Serialization.XmlSerializer> za pomocą typu obiektu.</span><span class="sxs-lookup"><span data-stu-id="7c27c-111">Construct a <xref:System.Xml.Serialization.XmlSerializer> using the type of the object.</span></span> <span data-ttu-id="7c27c-112">Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Serialization.XmlSerializer> klasy konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="7c27c-112">For more information, see the <xref:System.Xml.Serialization.XmlSerializer> class constructors.</span></span>  
  
3. <span data-ttu-id="7c27c-113">Wywołanie <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> metodę w celu wygenerowania strumień XML lub PLik reprezentacja właściwości publiczne i pola obiektu.</span><span class="sxs-lookup"><span data-stu-id="7c27c-113">Call the <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> method to generate either an XML stream or a file representation of the object's public properties and fields.</span></span> <span data-ttu-id="7c27c-114">Poniższy przykład tworzy plik.</span><span class="sxs-lookup"><span data-stu-id="7c27c-114">The following example creates a file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7c27c-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7c27c-115">See also</span></span>

- [<span data-ttu-id="7c27c-116">Wprowadzenie do serializacji XML</span><span class="sxs-lookup"><span data-stu-id="7c27c-116">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="7c27c-117">Instrukcje: Deserializacja obiektu</span><span class="sxs-lookup"><span data-stu-id="7c27c-117">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
