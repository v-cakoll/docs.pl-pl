---
title: 'Instrukcje: Serializowanie i deserializowanie danych JSON'
ms.date: 03/30/2017
ms.assetid: 88abc1fb-8196-4ee3-a23b-c6934144d1dd
ms.openlocfilehash: 797b29fd7ddecd3e3ed85f8cb3a6df93044942ef
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54704345"
---
# <a name="how-to-serialize-and-deserialize-json-data"></a>Instrukcje: Serializowanie i deserializowanie danych JSON
JSON (JavaScript Object Notation) jest formatem kodowania wydajne danych, umożliwiająca szybkie wymiany małe ilości danych między przeglądarkami klienckimi i usług sieci Web z włączoną obsługą technologii AJAX.  
  
 W tym temacie pokazano, jak do serializacji obiektów typu .NET na dane zakodowane w formacie JSON, a następnie zdeserializowanie danych w formacie JSON do wystąpień typów .NET przy użyciu <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>. W tym przykładzie użyto kontraktu danych, aby zademonstrować serializacji i deserializacji obiektu zdefiniowany przez użytkownika `Person` typu.  
  
 Zwykle JSON serializacji i deserializacji odbywa się automatycznie przez Windows Communication Foundation (WCF) przy użyciu typy kontraktu danych w operacji usługi, które są dostępne za pośrednictwem punktów końcowych z włączoną obsługą technologii AJAX. Jednak w niektórych przypadkach może być konieczne do pracy z danymi w formacie JSON bezpośrednio — to jest scenariusz, który pokazuje, w tym temacie.  
  
> [!NOTE]
>  Jeśli wystąpi błąd podczas serializacji wychodzące odpowiedzi na serwerze lub operacji odpowiedzi zgłasza wyjątek, innego powodu, jego mogą nie zwrócona do klienta jako błąd.  
  
 Ten temat opiera się na [serializacji JSON](../../../../docs/framework/wcf/samples/json-serialization.md) próbki.  
  
### <a name="to-define-the-data-contract-for-a-person"></a>Aby zdefiniować kontraktu danych dla danej osoby  
  
1.  Definiowanie kontraktu danych dla `Person` , dołączając <xref:System.Runtime.Serialization.DataContractAttribute> do klasy i <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutów do elementów członkowskich mają serializacji. Aby uzyskać więcej informacji na temat kontraktów danych zobacz [projektowanie kontraktów usług](../../../../docs/framework/wcf/designing-service-contracts.md).  
  
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
  
### <a name="to-serialize-an-instance-of-type-person-to-json"></a>Do serializacji wystąpienia typu osoby do formatu JSON  
  
1.  Utwórz wystąpienie obiektu `Person` typu.  
  
    ```csharp  
    Person p = new Person();  
    p.name = "John";  
    p.age = 42;  
    ```  
  
2.  Serializowanie `Person` obiektu do strumienia pamięci za pomocą <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
    ```csharp  
    MemoryStream stream1 = new MemoryStream();  
    DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));  
    ```  
  
3.  Użyj <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> metodę, aby zapisać dane JSON do strumienia.  
  
    ```csharp  
    ser.WriteObject(stream1, p);  
    ```  
  
4.  Pokaż dane wyjściowe JSON.  
  
    ```csharp  
    stream1.Position = 0;  
    StreamReader sr = new StreamReader(stream1);  
    Console.Write("JSON form of Person object: ");  
    Console.WriteLine(sr.ReadToEnd());  
    ```  
  
### <a name="to-deserialize-an-instance-of-type-person-from-json"></a>Do deserializacji wystąpienia typu osoby z formatu JSON  
  
1.  Deserializuje dane zakodowane w formacie JSON na nowe wystąpienie klasy `Person` przy użyciu <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> metody <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
    ```csharp  
    stream1.Position = 0;  
    Person p2 = (Person)ser.ReadObject(stream1);  
    ```  
  
2.  Pokaż wyniki.  
  
    ```csharp  
    Console.WriteLine($"Deserialized back, got name={p2.name}, age={p2.age}");  
    ```  
  
## <a name="example"></a>Przykład  
  
```csharp  
// Create a User object and serialize it to a JSON stream.  
public static string WriteFromObject()  
{  
    //Create User object.  
    User user = new User("Bob", 42);  
  
    //Create a stream to serialize the object to.  
    MemoryStream ms = new MemoryStream();  
  
    // Serializer the User object to the stream.  
    DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(User));  
    ser.WriteObject(ms, user);  
    byte[] json = ms.ToArray();  
    ms.Close();  
    return Encoding.UTF8.GetString(json, 0, json.Length);  
}  
  
// Deserialize a JSON stream to a User object.  
public static User ReadToObject(string json)  
{  
    User deserializedUser = new User();  
    MemoryStream ms = new MemoryStream(Encoding.UTF8.GetBytes(json));  
    DataContractJsonSerializer ser = new DataContractJsonSerializer(deserializedUser.GetType());  
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
- [Autonomiczna serializacja kodu JSON](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)
- [Obsługa formatu JSON i innych formatów transferowania danych](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)
