---
title: 'Instrukcje: deserializowanie obiektu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- deserializing objects
- objects, deserializing steps
ms.assetid: 287129c8-035a-4fea-b7b3-4790057ca076
ms.openlocfilehash: e1a960d39319beee1c3c257fcd3ade207de11010
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881142"
---
# <a name="how-to-deserialize-an-object"></a>Instrukcje: deserializowanie obiektu
Podczas deserializacji obiektu, format transportu Określa, czy zostanie utworzony obiekt PLiku lub strumienia. Po transport format jest określony, można wywołać <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> lub <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> metod, zgodnie z potrzebami.  
  
### <a name="to-deserialize-an-object"></a>Do deserializacji obiektu  
  
1. Budowy <xref:System.Xml.Serialization.XmlSerializer> przy użyciu typu obiektu do deserializacji.  
  
2. Wywołaj <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> metodę tworzenia repliki obiektu. Podczas deserializacji, należy rzutować zwracany obiekt na typ pierwotny, jak pokazano w następującym przykładzie deserializuje obiekt z pliku (chociaż może on również zostać przeprowadzona ze strumienia).  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do serializacji XML](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [Instrukcje: Serializacja obiektu](../../../docs/standard/serialization/how-to-serialize-an-object.md)
