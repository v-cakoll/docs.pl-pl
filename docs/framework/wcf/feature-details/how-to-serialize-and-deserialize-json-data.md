---
title: 'Instrukcje: Serializowanie i deserializowanie danych JSON'
ms.date: 03/30/2017
ms.assetid: 88abc1fb-8196-4ee3-a23b-c6934144d1dd
ms.openlocfilehash: f51ffb180adfc8310c91ff3c1ec7b7725f6b8b15
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492593"
---
# <a name="how-to-serialize-and-deserialize-json-data"></a><span data-ttu-id="51d2e-102">Instrukcje: Serializowanie i deserializowanie danych JSON</span><span class="sxs-lookup"><span data-stu-id="51d2e-102">How to: Serialize and Deserialize JSON Data</span></span>
<span data-ttu-id="51d2e-103">JSON (JavaScript Object Notation) jest format kodowania danych wydajne umożliwiający szybkie wymianę niewielkich ilości danych między przeglądarki klienta i usługi sieci Web obsługujących technologię AJAX.</span><span class="sxs-lookup"><span data-stu-id="51d2e-103">JSON (JavaScript Object Notation) is an efficient data encoding format that enables fast exchanges of small amounts of data between client browsers and AJAX-enabled Web services.</span></span>  
  
 <span data-ttu-id="51d2e-104">W tym temacie przedstawiono sposób serializacji obiektów typu .NET na dane zakodowane w formacie JSON, a następnie do deserializacji dane w formacie JSON do wystąpień typów .NET przy użyciu <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="51d2e-104">This topic demonstrates how to serialize .NET type objects into JSON-encoded data and then deserialize data in the JSON format back into instances of .NET types using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span> <span data-ttu-id="51d2e-105">W tym przykładzie użyto kontraktu danych, aby zademonstrować serializacji i deserializacji zdefiniowane przez użytkownika `Person` typu.</span><span class="sxs-lookup"><span data-stu-id="51d2e-105">This example uses a data contract to demonstrate serialization and deserialization of a user-defined `Person` type.</span></span>  
  
 <span data-ttu-id="51d2e-106">Zwykle JSON serializacji i deserializacji odbywa się automatycznie przez Windows Communication Foundation (WCF) przy użyciu typy kontraktu danych w operacji usługi, które są dostępne za pośrednictwem punktów końcowych z włączoną obsługą technologii AJAX.</span><span class="sxs-lookup"><span data-stu-id="51d2e-106">Normally, JSON serialization and deserialization is handled automatically by Windows Communication Foundation (WCF) when you use data contract types in service operations that are exposed over AJAX-enabled endpoints.</span></span> <span data-ttu-id="51d2e-107">Jednak w niektórych przypadkach może być konieczne do pracy z danymi JSON bezpośrednio — jest scenariusz, który w tym temacie przedstawiono.</span><span class="sxs-lookup"><span data-stu-id="51d2e-107">However, in some cases you may need to work with JSON data directly - this is the scenario that this topic demonstrates.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51d2e-108">Jeśli wystąpi błąd podczas serializacji odpowiedzi wychodzących na serwerze lub operacji odpowiedzi zgłasza wyjątek innego powodu, może nie pobrać zwróceniem klientowi jako błąd.</span><span class="sxs-lookup"><span data-stu-id="51d2e-108">If an error occurs during serialization of an outgoing reply on the server or the reply operation throws an exception for some other reason, it may not get returned to the client as a fault.</span></span>  
  
 <span data-ttu-id="51d2e-109">W tym temacie jest oparta na [serializacji JSON](../../../../docs/framework/wcf/samples/json-serialization.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="51d2e-109">This topic is based on the [JSON Serialization](../../../../docs/framework/wcf/samples/json-serialization.md) sample.</span></span>  
  
### <a name="to-define-the-data-contract-for-a-person"></a><span data-ttu-id="51d2e-110">Aby zdefiniować kontrakt danych osoby</span><span class="sxs-lookup"><span data-stu-id="51d2e-110">To define the data contract for a Person</span></span>  
  
1.  <span data-ttu-id="51d2e-111">Definiowanie kontraktu danych dla `Person` dołączając <xref:System.Runtime.Serialization.DataContractAttribute> do klasy i <xref:System.Runtime.Serialization.DataMemberAttribute> atrybut do elementów członkowskich mają do serializacji.</span><span class="sxs-lookup"><span data-stu-id="51d2e-111">Define the data contract for `Person` by attaching the <xref:System.Runtime.Serialization.DataContractAttribute> to the class and <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the members you want to serialize.</span></span> <span data-ttu-id="51d2e-112">Aby uzyskać więcej informacji na temat kontraktów danych, zobacz [projektowanie kontraktów usług](../../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="51d2e-112">For more information about data contracts, see [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
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
  
### <a name="to-serialize-an-instance-of-type-person-to-json"></a><span data-ttu-id="51d2e-113">Do serializacji wystąpienia typu osoby do ciągu JSON</span><span class="sxs-lookup"><span data-stu-id="51d2e-113">To serialize an instance of type Person to JSON</span></span>  
  
1.  <span data-ttu-id="51d2e-114">Utwórz wystąpienie `Person` typu.</span><span class="sxs-lookup"><span data-stu-id="51d2e-114">Create an instance of the `Person` type.</span></span>  
  
    ```csharp  
    Person p = new Person();  
    p.name = "John";  
    p.age = 42;  
    ```  
  
2.  <span data-ttu-id="51d2e-115">Serializować `Person` obiektu strumienia pamięci przy użyciu <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="51d2e-115">Serialize the `Person` object to a memory stream using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
    ```csharp  
    MemoryStream stream1 = new MemoryStream();  
    DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));  
    ```  
  
3.  <span data-ttu-id="51d2e-116">Użyj <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> metodę, aby zapisać dane JSON do strumienia.</span><span class="sxs-lookup"><span data-stu-id="51d2e-116">Use the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> method to write JSON data to the stream.</span></span>  
  
    ```csharp  
    ser.WriteObject(stream1, p);  
    ```  
  
4.  <span data-ttu-id="51d2e-117">Pokaż dane wyjściowe JSON.</span><span class="sxs-lookup"><span data-stu-id="51d2e-117">Show the JSON output.</span></span>  
  
    ```csharp  
    stream1.Position = 0;  
    StreamReader sr = new StreamReader(stream1);  
    Console.Write("JSON form of Person object: ");  
    Console.WriteLine(sr.ReadToEnd());  
    ```  
  
### <a name="to-deserialize-an-instance-of-type-person-from-json"></a><span data-ttu-id="51d2e-118">Zdeserializować wystąpienia typu osoby z formatu JSON</span><span class="sxs-lookup"><span data-stu-id="51d2e-118">To deserialize an instance of type Person from JSON</span></span>  
  
1.  <span data-ttu-id="51d2e-119">Deserializuje dane zakodowane w formacie JSON na nowe wystąpienie klasy `Person` za pomocą <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> metody <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="51d2e-119">Deserialize the JSON-encoded data into a new instance of `Person` by using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> method of the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
    ```csharp  
    stream1.Position = 0;  
    Person p2 = (Person)ser.ReadObject(stream1);  
    ```  
  
2.  <span data-ttu-id="51d2e-120">Pokaż wyniki.</span><span class="sxs-lookup"><span data-stu-id="51d2e-120">Show the results.</span></span>  
  
    ```csharp  
    Console.WriteLine($"Deserialized back, got name={p2.name}, age={p2.age}");  
    ```  
  
## <a name="example"></a><span data-ttu-id="51d2e-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="51d2e-121">Example</span></span>  
  
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
>  <span data-ttu-id="51d2e-122">Serializator JSON zgłasza wyjątek serializacji dla kontraktów danych, które mają wielu członków o tej samej nazwie, jak pokazano w poniższym kodzie próbki.</span><span class="sxs-lookup"><span data-stu-id="51d2e-122">The JSON serializer throws a serialization exception for data contracts that have multiple members with the same name, as shown in the following sample code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="51d2e-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="51d2e-123">See Also</span></span>  
 [<span data-ttu-id="51d2e-124">Autonomiczna serializacja kodu JSON</span><span class="sxs-lookup"><span data-stu-id="51d2e-124">Stand-Alone JSON Serialization</span></span>](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)  
 [<span data-ttu-id="51d2e-125">Obsługa formatu JSON i innych formatów transferowania danych</span><span class="sxs-lookup"><span data-stu-id="51d2e-125">Support for JSON and Other Data Transfer Formats</span></span>](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)
