---
title: 'Instrukcje: serializowanie i deserializowanie danych JSON'
ms.date: 03/25/2019
ms.assetid: 88abc1fb-8196-4ee3-a23b-c6934144d1dd
ms.openlocfilehash: 0c56b298737dc9b9902f13c586edffb3d05257f8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783012"
---
# <a name="how-to-serialize-and-deserialize-json-data"></a>Instrukcje: Serializowanie i deserializowanie danych JSON
JSON (JavaScript Object Notation) jest formatem kodowania wydajne danych, umożliwiająca szybkie wymiany małe ilości danych między przeglądarkami klienckimi i usług sieci Web z włączoną obsługą technologii AJAX.  
  
 W tym artykule pokazano, jak do serializacji obiektów typu .NET na dane zakodowane w formacie JSON, a następnie zdeserializowanie danych w formacie JSON do wystąpień typów .NET. W tym przykładzie użyto kontraktu danych, aby zademonstrować serializacji i deserializacji obiektu zdefiniowany przez użytkownika `Person` typu i używa <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
 Zwykle JSON serializacji i deserializacji są obsługiwane automatycznie przez Windows Communication Foundation (WCF) przy użyciu typy kontraktu danych w operacji usługi, które są dostępne za pośrednictwem punktów końcowych z włączoną obsługą technologii AJAX. W niektórych przypadkach może być konieczne do pracy z danymi w formacie JSON bezpośrednio.   
  
> [!NOTE]
>  Jeśli wystąpi błąd podczas serializacji wychodzące odpowiedzi, na serwerze lub z innego powodu, jego mogą nie zwrócona do klienta jako błąd.  
  
 Ten artykuł jest oparty na [serializacji JSON](../samples/json-serialization.md) próbki.  
  
## <a name="to-define-the-data-contract-for-a-person-type"></a>Aby zdefiniować kontraktu danych dla typu osoby 
  
1. Definiowanie kontraktu danych dla `Person` , dołączając <xref:System.Runtime.Serialization.DataContractAttribute> do klasy i <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutów do elementów członkowskich mają serializacji. Aby uzyskać więcej informacji na temat kontraktów danych zobacz [projektowanie kontraktów usług](../designing-service-contracts.md).  
  
    ```csharp  
    [DataContract]  
    internal class Person  
    {  
        [DataMember]  
        internal string name;  
  
        [DataMember]  
        internal int age;  
    }  
    ```  
  
## <a name="to-serialize-an-instance-of-type-person-to-json"></a>Do serializacji wystąpienia typu osoby do formatu JSON  
  
1. Utwórz wystąpienie obiektu `Person` typu.  
  
    ```csharp  
    var p = new Person();  
    p.name = "John";  
    p.age = 42;  
    ```  
  
2. Serializowanie `Person` obiektu w strumieniu pamięci za pomocą <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
    ```csharp  
    var stream1 = new MemoryStream();  
    var ser = new DataContractJsonSerializer(typeof(Person));  
    ```  
  
3. Użyj <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> metodę, aby zapisać dane JSON do strumienia.  
  
    ```csharp  
    ser.WriteObject(stream1, p);  
    ```  
  
4. Pokaż dane wyjściowe JSON.  
  
    ```csharp  
    stream1.Position = 0;  
    var sr = new StreamReader(stream1);  
    Console.Write("JSON form of Person object: ");  
    Console.WriteLine(sr.ReadToEnd());  
    ```  
  
## <a name="to-deserialize-an-instance-of-type-person-from-json"></a>Do deserializacji wystąpienia typu osoby z formatu JSON  
  
1. Deserializuje dane zakodowane w formacie JSON na nowe wystąpienie klasy `Person` przy użyciu <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> metody <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
    ```csharp  
    stream1.Position = 0;  
    var p2 = (Person)ser.ReadObject(stream1);  
    ```  
  
2. Pokaż wyniki.  
  
    ```csharp  
    Console.WriteLine($"Deserialized back, got name={p2.name}, age={p2.age}");  
    ```  
  
## <a name="example"></a>Przykład  
  
```csharp  
// Create a User object and serialize it to a JSON stream.  
public static string WriteFromObject()  
{  
    // Create User object.  
    var user = new User("Bob", 42);  
  
    // Create a stream to serialize the object to.  
    var ms = new MemoryStream();  
  
    // Serializer the User object to the stream.  
    var ser = new DataContractJsonSerializer(typeof(User));  
    ser.WriteObject(ms, user);  
    byte[] json = ms.ToArray();  
    ms.Close();  
    return Encoding.UTF8.GetString(json, 0, json.Length);  
}  
  
// Deserialize a JSON stream to a User object.  
public static User ReadToObject(string json)  
{  
    var deserializedUser = new User();  
    var ms = new MemoryStream(Encoding.UTF8.GetBytes(json));  
    var ser = new DataContractJsonSerializer(deserializedUser.GetType());  
    deserializedUser = ser.ReadObject(ms) as User;  
    ms.Close();  
    return deserializedUser;  
}  
```  
  
> [!NOTE]
>  Serializator JSON zgłasza wyjątek serializacji dla kontraktów danych, które mają wiele składowych o tej samej nazwie, jak pokazano w poniższym przykładowym kodzie.  
  
```csharp  
[DataContract]  
public class TestDuplicateDataBase  
{  
    [DataMember]  
    public int field1 = 123;  
}

[DataContract]  
public class TestDuplicateDataDerived : TestDuplicateDataBase  
{  
    [DataMember]  
    public new int field1 = 999;  
}  
```  
  
## <a name="see-also"></a>Zobacz także

- [Autonomiczna serializacja kodu JSON](stand-alone-json-serialization.md)
- [Pomoc techniczna dla formatu JSON i inne dane transferu formatów](support-for-json-and-other-data-transfer-formats.md)
