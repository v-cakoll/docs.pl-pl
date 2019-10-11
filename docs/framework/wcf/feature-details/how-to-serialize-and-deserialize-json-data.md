---
title: 'Instrukcje: korzystanie z Klasa DataContractJsonSerializer'
ms.date: 03/25/2019
ms.assetid: 88abc1fb-8196-4ee3-a23b-c6934144d1dd
ms.openlocfilehash: 5e521621dd3ec8e82a860590e66c1c4da95fd3b8
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2019
ms.locfileid: "72180221"
---
# <a name="how-to-use-datacontractjsonserializer"></a>Instrukcje: korzystanie z Klasa DataContractJsonSerializer
JSON (JavaScript Object Notation) to wydajny format kodowania danych, który umożliwia szybką wymianę małych ilości danych między przeglądarkami klienta i usługami sieci Web obsługującymi technologię AJAX.  
  
 W tym artykule pokazano, jak serializować obiekty typu .NET do danych zakodowanych w formacie JSON, a następnie deserializować dane z powrotem do wystąpień typów .NET. W tym przykładzie używa się kontraktu danych w celu przedstawienia serializacji i deserializacji zdefiniowanego przez użytkownika typu `Person` i używa <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
 Zazwyczaj Serializacja i deserializacja JSON są obsługiwane automatycznie przez Windows Communication Foundation (WCF), gdy używasz typów kontraktu danych w operacjach usługi, które są udostępniane za pośrednictwem punktów końcowych z obsługą technologii AJAX. Jednak w niektórych przypadkach może zajść potrzeba bezpośredniej pracy z danymi JSON.

> [!NOTE]
> W tym artykule opisano <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>. W przypadku większości scenariuszy, które obejmują Serializowanie i deserializacja kodu JSON, zalecamy korzystanie z narzędzi w [przestrzeni nazw System. Text. JSON](../../../standard/serialization/system-text-json-overview.md). 
  
 Ten artykuł jest oparty na [przykładu Klasa DataContractJsonSerializer](../samples/json-serialization.md).  
  
## <a name="to-define-the-data-contract-for-a-person-type"></a>Aby zdefiniować kontrakt danych dla typu osoby 
  
1. Zdefiniuj kontrakt danych dla `Person` przez dołączenie <xref:System.Runtime.Serialization.DataContractAttribute> do klasy i atrybutu <xref:System.Runtime.Serialization.DataMemberAttribute> do elementów członkowskich, które chcesz serializować. Aby uzyskać więcej informacji na temat umów dotyczących danych, zobacz [Projektowanie kontraktów usług](../designing-service-contracts.md).  
  
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
  
## <a name="to-serialize-an-instance-of-type-person-to-json"></a>Aby serializować wystąpienie typu Person do JSON  
  
> [!NOTE]
> Jeśli wystąpi błąd podczas serializacji odpowiedzi wychodzącej na serwerze lub z innego powodu, może to nie zostać zwrócone do klienta jako błąd.  

1. Utwórz wystąpienie typu `Person`.  
  
    ```csharp  
    var p = new Person();  
    p.name = "John";  
    p.age = 42;  
    ```  
  
2. Serializacja obiektu `Person` do strumienia pamięci przy użyciu <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
    ```csharp  
    var stream1 = new MemoryStream();  
    var ser = new DataContractJsonSerializer(typeof(Person));  
    ```  
  
3. Użyj metody <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> w celu zapisania danych JSON w strumieniu.  
  
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
  
## <a name="to-deserialize-an-instance-of-type-person-from-json"></a>Aby zdeserializować wystąpienie typu Person z JSON  
  
1. Deserializacja danych zakodowanych w formacie JSON do nowego wystąpienia `Person` przy użyciu metody <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
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
> Serializator JSON zgłasza wyjątek serializacji dla kontraktów danych, które mają wiele składowych o tej samej nazwie, jak pokazano w poniższym przykładowym kodzie.  
  
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

- [Serializacja kodu JSON w programie .NET](../../../standard/serialization/system-text-json-overview.md)

