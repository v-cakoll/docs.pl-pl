---
title: 'Instrukcje: serializowanie i deserializowanie danych JSON'
ms.date: 03/25/2019
ms.assetid: 88abc1fb-8196-4ee3-a23b-c6934144d1dd
ms.openlocfilehash: 7edce66a23021fa03a6f98b3b847a5b671c17124
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59336957"
---
# <a name="how-to-serialize-and-deserialize-json-data"></a><span data-ttu-id="91c3e-102">Instrukcje: Serializowanie i deserializowanie danych JSON</span><span class="sxs-lookup"><span data-stu-id="91c3e-102">How to: Serialize and deserialize JSON data</span></span>
<span data-ttu-id="91c3e-103">JSON (JavaScript Object Notation) jest formatem kodowania wydajne danych, umożliwiająca szybkie wymiany małe ilości danych między przeglądarkami klienckimi i usług sieci Web z włączoną obsługą technologii AJAX.</span><span class="sxs-lookup"><span data-stu-id="91c3e-103">JSON (JavaScript Object Notation) is an efficient data encoding format that enables fast exchanges of small amounts of data between client browsers and AJAX-enabled Web services.</span></span>  
  
 <span data-ttu-id="91c3e-104">W tym artykule pokazano, jak do serializacji obiektów typu .NET na dane zakodowane w formacie JSON, a następnie zdeserializowanie danych w formacie JSON do wystąpień typów .NET.</span><span class="sxs-lookup"><span data-stu-id="91c3e-104">This article demonstrates how to serialize .NET type objects into JSON-encoded data and then deserialize data in the JSON format back into instances of .NET types.</span></span> <span data-ttu-id="91c3e-105">W tym przykładzie użyto kontraktu danych, aby zademonstrować serializacji i deserializacji obiektu zdefiniowany przez użytkownika `Person` typu i używa <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="91c3e-105">This example uses a data contract to demonstrate serialization and deserialization of a user-defined `Person` type and uses <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
 <span data-ttu-id="91c3e-106">Zwykle JSON serializacji i deserializacji są obsługiwane automatycznie przez Windows Communication Foundation (WCF) przy użyciu typy kontraktu danych w operacji usługi, które są dostępne za pośrednictwem punktów końcowych z włączoną obsługą technologii AJAX.</span><span class="sxs-lookup"><span data-stu-id="91c3e-106">Normally, JSON serialization and deserialization are handled automatically by Windows Communication Foundation (WCF) when you use data contract types in service operations that are exposed over AJAX-enabled endpoints.</span></span> <span data-ttu-id="91c3e-107">W niektórych przypadkach może być konieczne do pracy z danymi w formacie JSON bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="91c3e-107">However, in some cases you may need to work with JSON data directly.</span></span>   
  
> [!NOTE]
>  <span data-ttu-id="91c3e-108">Jeśli wystąpi błąd podczas serializacji wychodzące odpowiedzi, na serwerze lub z innego powodu, jego mogą nie zwrócona do klienta jako błąd.</span><span class="sxs-lookup"><span data-stu-id="91c3e-108">If an error occurs during serialization of an outgoing reply on the server or for some other reason, it may not get returned to the client as a fault.</span></span>  
  
 <span data-ttu-id="91c3e-109">Ten artykuł jest oparty na [serializacji JSON](../samples/json-serialization.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="91c3e-109">This article is based on the [JSON serialization](../samples/json-serialization.md) sample.</span></span>  
  
## <a name="to-define-the-data-contract-for-a-person-type"></a><span data-ttu-id="91c3e-110">Aby zdefiniować kontraktu danych dla typu osoby</span><span class="sxs-lookup"><span data-stu-id="91c3e-110">To define the data contract for a Person type</span></span> 
  
1. <span data-ttu-id="91c3e-111">Definiowanie kontraktu danych dla `Person` , dołączając <xref:System.Runtime.Serialization.DataContractAttribute> do klasy i <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutów do elementów członkowskich mają serializacji.</span><span class="sxs-lookup"><span data-stu-id="91c3e-111">Define the data contract for `Person` by attaching the <xref:System.Runtime.Serialization.DataContractAttribute> to the class and <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the members you want to serialize.</span></span> <span data-ttu-id="91c3e-112">Aby uzyskać więcej informacji na temat kontraktów danych zobacz [projektowanie kontraktów usług](../designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="91c3e-112">For more information about data contracts, see [Designing service contracts](../designing-service-contracts.md).</span></span>  
  
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
  
## <a name="to-serialize-an-instance-of-type-person-to-json"></a><span data-ttu-id="91c3e-113">Do serializacji wystąpienia typu osoby do formatu JSON</span><span class="sxs-lookup"><span data-stu-id="91c3e-113">To serialize an instance of type Person to JSON</span></span>  
  
1. <span data-ttu-id="91c3e-114">Utwórz wystąpienie obiektu `Person` typu.</span><span class="sxs-lookup"><span data-stu-id="91c3e-114">Create an instance of the `Person` type.</span></span>  
  
    ```csharp  
    Person p = new Person();  
    p.name = "John";  
    p.age = 42;  
    ```  
  
2. <span data-ttu-id="91c3e-115">Serializowanie `Person` obiektu w strumieniu pamięci za pomocą <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="91c3e-115">Serialize the `Person` object to a memory stream by using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
    ```csharp  
    MemoryStream stream1 = new MemoryStream();  
    DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));  
    ```  
  
3. <span data-ttu-id="91c3e-116">Użyj <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> metodę, aby zapisać dane JSON do strumienia.</span><span class="sxs-lookup"><span data-stu-id="91c3e-116">Use the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> method to write JSON data to the stream.</span></span>  
  
    ```csharp  
    ser.WriteObject(stream1, p);  
    ```  
  
4. <span data-ttu-id="91c3e-117">Pokaż dane wyjściowe JSON.</span><span class="sxs-lookup"><span data-stu-id="91c3e-117">Show the JSON output.</span></span>  
  
    ```csharp  
    stream1.Position = 0;  
    StreamReader sr = new StreamReader(stream1);  
    Console.Write("JSON form of Person object: ");  
    Console.WriteLine(sr.ReadToEnd());  
    ```  
  
## <a name="to-deserialize-an-instance-of-type-person-from-json"></a><span data-ttu-id="91c3e-118">Do deserializacji wystąpienia typu osoby z formatu JSON</span><span class="sxs-lookup"><span data-stu-id="91c3e-118">To deserialize an instance of type Person from JSON</span></span>  
  
1. <span data-ttu-id="91c3e-119">Deserializuje dane zakodowane w formacie JSON na nowe wystąpienie klasy `Person` przy użyciu <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> metody <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="91c3e-119">Deserialize the JSON-encoded data into a new instance of `Person` by using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> method of the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
    ```csharp  
    stream1.Position = 0;  
    Person p2 = (Person)ser.ReadObject(stream1);  
    ```  
  
2. <span data-ttu-id="91c3e-120">Pokaż wyniki.</span><span class="sxs-lookup"><span data-stu-id="91c3e-120">Show the results.</span></span>  
  
    ```csharp  
    Console.WriteLine($"Deserialized back, got name={p2.name}, age={p2.age}");  
    ```  
  
## <a name="example"></a><span data-ttu-id="91c3e-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="91c3e-121">Example</span></span>  
  
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
>  <span data-ttu-id="91c3e-122">Serializator JSON zgłasza wyjątek serializacji dla kontraktów danych, które mają wiele składowych o tej samej nazwie, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="91c3e-122">The JSON serializer throws a serialization exception for data contracts that have multiple members with the same name, as shown in the following sample code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="91c3e-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="91c3e-123">See also</span></span>

- [<span data-ttu-id="91c3e-124">Autonomiczna serializacja kodu JSON</span><span class="sxs-lookup"><span data-stu-id="91c3e-124">Stand-alone JSON serialization</span></span>](stand-alone-json-serialization.md)
- [<span data-ttu-id="91c3e-125">Pomoc techniczna dla formatu JSON i inne dane transferu formatów</span><span class="sxs-lookup"><span data-stu-id="91c3e-125">Support for JSON and other data transfer formats</span></span>](support-for-json-and-other-data-transfer-formats.md)
