---
title: 'Instrukcje: Serializowanie i deserializowanie danych JSON'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 88abc1fb-8196-4ee3-a23b-c6934144d1dd
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 994ccb677d1376eff5b889a0a4ddfe072557bdea
ms.sourcegitcommit: 2142a4732bb4ff519b9817db4c24a237b9810d4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2018
---
# <a name="how-to-serialize-and-deserialize-json-data"></a>Instrukcje: Serializowanie i deserializowanie danych JSON
JSON (JavaScript Object Notation) jest format kodowania danych wydajne umożliwiający szybkie wymianę niewielkich ilości danych między przeglądarki klienta i usługi sieci Web obsługujących technologię AJAX.  
  
 W tym temacie przedstawiono sposób serializacji obiektów typu .NET na dane zakodowane w formacie JSON, a następnie do deserializacji dane w formacie JSON do wystąpień typów .NET przy użyciu <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>. W tym przykładzie użyto kontraktu danych, aby zademonstrować serializacji i deserializacji zdefiniowane przez użytkownika `Person` typu.  
  
 Zwykle JSON serializacji i deserializacji odbywa się automatycznie przez [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Jeśli używasz typy kontraktu danych operacji usługi, które są dostępne za pośrednictwem punktów końcowych z włączoną obsługą technologii AJAX. Jednak w niektórych przypadkach może być konieczne do pracy z danymi JSON bezpośrednio — jest scenariusz, który w tym temacie przedstawiono.  
  
> [!NOTE]
>  Jeśli wystąpi błąd podczas serializacji odpowiedzi wychodzących na serwerze lub operacji odpowiedzi zgłasza wyjątek innego powodu, może nie pobrać zwróceniem klientowi jako błąd.  
  
 W tym temacie jest oparta na [serializacji JSON](../../../../docs/framework/wcf/samples/json-serialization.md) próbki.  
  
### <a name="to-define-the-data-contract-for-a-person"></a>Aby zdefiniować kontrakt danych osoby  
  
1.  Definiowanie kontraktu danych dla `Person` dołączając <xref:System.Runtime.Serialization.DataContractAttribute> do klasy i <xref:System.Runtime.Serialization.DataMemberAttribute> atrybut do elementów członkowskich mają do serializacji. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]kontrakty danych, zobacz [projektowanie kontraktów usług](../../../../docs/framework/wcf/designing-service-contracts.md).  
  
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
  
### <a name="to-serialize-an-instance-of-type-person-to-json"></a>Do serializacji wystąpienia typu osoby do ciągu JSON  
  
1.  Utwórz wystąpienie `Person` typu.  
  
    ```csharp  
    Person p = new Person();  
    p.name = "John";  
    p.age = 42;  
    ```  
  
2.  Serializować `Person` obiektu strumienia pamięci przy użyciu <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
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
  
### <a name="to-deserialize-an-instance-of-type-person-from-json"></a>Zdeserializować wystąpienia typu osoby z formatu JSON  
  
1.  Deserializuje dane zakodowane w formacie JSON na nowe wystąpienie klasy `Person` za pomocą <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> metody <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
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
>  Serializator JSON zgłasza wyjątek serializacji dla kontraktów danych, które mają wielu członków o tej samej nazwie, jak pokazano w poniższym kodzie próbki.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Autonomiczna serializacja kodu JSON](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)  
 [Obsługa formatu JSON i innych formatów transferowania danych](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)
