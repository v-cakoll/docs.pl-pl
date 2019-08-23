---
title: 'Instrukcje: serializowanie i deserializowanie danych JSON'
ms.date: 03/25/2019
ms.assetid: 88abc1fb-8196-4ee3-a23b-c6934144d1dd
ms.openlocfilehash: 0bebdbb3d74d58db093c4ec1e0e88138c7080335
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947899"
---
# <a name="how-to-serialize-and-deserialize-json-data"></a><span data-ttu-id="44ba0-102">Instrukcje: Serializowanie i deserializacja danych JSON</span><span class="sxs-lookup"><span data-stu-id="44ba0-102">How to: Serialize and deserialize JSON data</span></span>
<span data-ttu-id="44ba0-103">JSON (JavaScript Object Notation) to wydajny format kodowania danych, który umożliwia szybką wymianę małych ilości danych między przeglądarkami klienta i usługami sieci Web obsługującymi technologię AJAX.</span><span class="sxs-lookup"><span data-stu-id="44ba0-103">JSON (JavaScript Object Notation) is an efficient data encoding format that enables fast exchanges of small amounts of data between client browsers and AJAX-enabled Web services.</span></span>  
  
 <span data-ttu-id="44ba0-104">W tym artykule pokazano, jak serializować obiekty typu .NET do danych zakodowanych w formacie JSON, a następnie deserializować dane z powrotem do wystąpień typów .NET.</span><span class="sxs-lookup"><span data-stu-id="44ba0-104">This article demonstrates how to serialize .NET type objects into JSON-encoded data and then deserialize data in the JSON format back into instances of .NET types.</span></span> <span data-ttu-id="44ba0-105">Ten przykład używa kontraktu danych do zademonstrowania serializacji i deserializacji typu zdefiniowanego przez `Person` użytkownika i użycia. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer></span><span class="sxs-lookup"><span data-stu-id="44ba0-105">This example uses a data contract to demonstrate serialization and deserialization of a user-defined `Person` type and uses <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
 <span data-ttu-id="44ba0-106">Zazwyczaj Serializacja i deserializacja JSON są obsługiwane automatycznie przez Windows Communication Foundation (WCF), gdy używasz typów kontraktu danych w operacjach usługi, które są udostępniane za pośrednictwem punktów końcowych z obsługą technologii AJAX.</span><span class="sxs-lookup"><span data-stu-id="44ba0-106">Normally, JSON serialization and deserialization are handled automatically by Windows Communication Foundation (WCF) when you use data contract types in service operations that are exposed over AJAX-enabled endpoints.</span></span> <span data-ttu-id="44ba0-107">Jednak w niektórych przypadkach może zajść potrzeba bezpośredniej pracy z danymi JSON.</span><span class="sxs-lookup"><span data-stu-id="44ba0-107">However, in some cases you may need to work with JSON data directly.</span></span>   
  
> [!NOTE]
> <span data-ttu-id="44ba0-108">Jeśli wystąpi błąd podczas serializacji odpowiedzi wychodzącej na serwerze lub z innego powodu, może to nie zostać zwrócone do klienta jako błąd.</span><span class="sxs-lookup"><span data-stu-id="44ba0-108">If an error occurs during serialization of an outgoing reply on the server or for some other reason, it may not get returned to the client as a fault.</span></span>  
  
 <span data-ttu-id="44ba0-109">Ten artykuł jest oparty na przykład [serializacji JSON](../samples/json-serialization.md) .</span><span class="sxs-lookup"><span data-stu-id="44ba0-109">This article is based on the [JSON serialization](../samples/json-serialization.md) sample.</span></span>  
  
## <a name="to-define-the-data-contract-for-a-person-type"></a><span data-ttu-id="44ba0-110">Aby zdefiniować kontrakt danych dla typu osoby</span><span class="sxs-lookup"><span data-stu-id="44ba0-110">To define the data contract for a Person type</span></span> 
  
1. <span data-ttu-id="44ba0-111">Zdefiniuj kontrakt danych dla `Person` przez <xref:System.Runtime.Serialization.DataContractAttribute> dołączenie do klasy i <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutu do elementów członkowskich, które chcesz serializować.</span><span class="sxs-lookup"><span data-stu-id="44ba0-111">Define the data contract for `Person` by attaching the <xref:System.Runtime.Serialization.DataContractAttribute> to the class and <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the members you want to serialize.</span></span> <span data-ttu-id="44ba0-112">Aby uzyskać więcej informacji na temat umów dotyczących danych, zobacz [Projektowanie kontraktów usług](../designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="44ba0-112">For more information about data contracts, see [Designing service contracts](../designing-service-contracts.md).</span></span>  
  
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
  
## <a name="to-serialize-an-instance-of-type-person-to-json"></a><span data-ttu-id="44ba0-113">Aby serializować wystąpienie typu Person do JSON</span><span class="sxs-lookup"><span data-stu-id="44ba0-113">To serialize an instance of type Person to JSON</span></span>  
  
1. <span data-ttu-id="44ba0-114">Utwórz wystąpienie `Person` typu.</span><span class="sxs-lookup"><span data-stu-id="44ba0-114">Create an instance of the `Person` type.</span></span>  
  
    ```csharp  
    var p = new Person();  
    p.name = "John";  
    p.age = 42;  
    ```  
  
2. <span data-ttu-id="44ba0-115">Serializacja obiektu do strumienia pamięci za <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>pomocą. `Person`</span><span class="sxs-lookup"><span data-stu-id="44ba0-115">Serialize the `Person` object to a memory stream by using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
    ```csharp  
    var stream1 = new MemoryStream();  
    var ser = new DataContractJsonSerializer(typeof(Person));  
    ```  
  
3. <span data-ttu-id="44ba0-116">Użyj metody <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> , aby zapisać dane JSON w strumieniu.</span><span class="sxs-lookup"><span data-stu-id="44ba0-116">Use the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> method to write JSON data to the stream.</span></span>  
  
    ```csharp  
    ser.WriteObject(stream1, p);  
    ```  
  
4. <span data-ttu-id="44ba0-117">Pokaż dane wyjściowe JSON.</span><span class="sxs-lookup"><span data-stu-id="44ba0-117">Show the JSON output.</span></span>  
  
    ```csharp  
    stream1.Position = 0;  
    var sr = new StreamReader(stream1);  
    Console.Write("JSON form of Person object: ");  
    Console.WriteLine(sr.ReadToEnd());  
    ```  
  
## <a name="to-deserialize-an-instance-of-type-person-from-json"></a><span data-ttu-id="44ba0-118">Aby zdeserializować wystąpienie typu Person z JSON</span><span class="sxs-lookup"><span data-stu-id="44ba0-118">To deserialize an instance of type Person from JSON</span></span>  
  
1. <span data-ttu-id="44ba0-119">Deserializacja danych zakodowanych w formacie JSON do nowego wystąpienia `Person` przy <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> użyciu metody <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="44ba0-119">Deserialize the JSON-encoded data into a new instance of `Person` by using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> method of the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
    ```csharp  
    stream1.Position = 0;  
    var p2 = (Person)ser.ReadObject(stream1);  
    ```  
  
2. <span data-ttu-id="44ba0-120">Pokaż wyniki.</span><span class="sxs-lookup"><span data-stu-id="44ba0-120">Show the results.</span></span>  
  
    ```csharp  
    Console.WriteLine($"Deserialized back, got name={p2.name}, age={p2.age}");  
    ```  
  
## <a name="example"></a><span data-ttu-id="44ba0-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="44ba0-121">Example</span></span>  
  
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
> <span data-ttu-id="44ba0-122">Serializator JSON zgłasza wyjątek serializacji dla kontraktów danych, które mają wiele składowych o tej samej nazwie, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="44ba0-122">The JSON serializer throws a serialization exception for data contracts that have multiple members with the same name, as shown in the following sample code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="44ba0-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="44ba0-123">See also</span></span>

- [<span data-ttu-id="44ba0-124">Autonomiczna Serializacja kodu JSON</span><span class="sxs-lookup"><span data-stu-id="44ba0-124">Stand-alone JSON serialization</span></span>](stand-alone-json-serialization.md)
- [<span data-ttu-id="44ba0-125">Obsługa formatu JSON i innych formatów transferu danych</span><span class="sxs-lookup"><span data-stu-id="44ba0-125">Support for JSON and other data transfer formats</span></span>](support-for-json-and-other-data-transfer-formats.md)
