---
title: Jak zdeserializować obiekt za pomocą elementu XmlSerializer
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- deserializing objects
- objects, deserializing steps
ms.assetid: 287129c8-035a-4fea-b7b3-4790057ca076
ms.openlocfilehash: c24ba466a208fe5abdbf565169c41c4ee3f47482
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559901"
---
# <a name="how-to-deserialize-an-object-using-xmlserializer"></a>Jak zdeserializować obiekt za pomocą elementu XmlSerializer

Podczas deserializacji obiektu, format transportu Określa, czy zostanie utworzony obiekt PLiku lub strumienia. Po transport format jest określony, można wywołać <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> lub <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> metod, zgodnie z potrzebami.

## <a name="to-deserialize-an-object"></a>Do deserializacji obiektu

1. Budowy <xref:System.Xml.Serialization.XmlSerializer> przy użyciu typu obiektu do deserializacji.

1. Wywołaj metodę <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A>, aby utworzyć replikę obiektu. Podczas deserializacji należy rzutować zwracany obiekt na typ oryginału, jak pokazano w poniższym przykładzie, który deserializacji obiekt z pliku (mimo że można go również zdeserializować ze strumienia).

    ```vb
    ' Construct an instance of the XmlSerializer with the type
    ' of object that is being deserialized.
    Dim mySerializer As New XmlSerializer(GetType(MySerializableClass))
    ' To read the file, create a FileStream.
    Dim myFileStream As New FileStream("myFileName.xml", FileMode.Open)
    ' Call the Deserialize method and cast to the object type.
    Dim myObject = CType( _
    mySerializer.Deserialize(myFileStream), MySerializableClass)
    ```

    ```csharp
    // Construct an instance of the XmlSerializer with the type
    // of object that is being deserialized.
    var mySerializer = new XmlSerializer(typeof(MySerializableClass));
    // To read the file, create a FileStream.
    var myFileStream = new FileStream("myFileName.xml", FileMode.Open);
    // Call the Deserialize method and cast to the object type.
    var myObject = (MySerializableClass) mySerializer.Deserialize(myFileStream)
    ```

## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do serializacji XML](introducing-xml-serialization.md)
- [Instrukcje: Serializacja obiektu](how-to-serialize-an-object.md)
