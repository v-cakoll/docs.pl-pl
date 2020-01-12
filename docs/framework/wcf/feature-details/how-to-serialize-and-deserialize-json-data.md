---
title: 'Instrukcje: korzystanie z Klasa DataContractJsonSerializer'
ms.date: 03/25/2019
ms.assetid: 88abc1fb-8196-4ee3-a23b-c6934144d1dd
ms.openlocfilehash: 3cf8cc52587a64e7273ab9e0de0b1751d00827cf
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901214"
---
# <a name="how-to-use-datacontractjsonserializer"></a><span data-ttu-id="62a5b-102">Jak używać Klasa DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="62a5b-102">How to use DataContractJsonSerializer</span></span>

> [!NOTE]
> <span data-ttu-id="62a5b-103">Ten artykuł dotyczy <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="62a5b-103">This article is about <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span> <span data-ttu-id="62a5b-104">W przypadku większości scenariuszy obejmujących serializację i deserializacja kodu JSON zalecamy używanie interfejsów API w [przestrzeni nazw System. Text. JSON](../../../standard/serialization/system-text-json-overview.md).</span><span class="sxs-lookup"><span data-stu-id="62a5b-104">For most scenarios that involve serializing and deserializing JSON, we recommend the APIs in the [System.Text.Json namespace](../../../standard/serialization/system-text-json-overview.md).</span></span>

<span data-ttu-id="62a5b-105">JSON (JavaScript Object Notation) to wydajny format kodowania danych, który umożliwia szybką wymianę małych ilości danych między przeglądarkami klienta i usługami sieci Web obsługującymi technologię AJAX.</span><span class="sxs-lookup"><span data-stu-id="62a5b-105">JSON (JavaScript Object Notation) is an efficient data encoding format that enables fast exchanges of small amounts of data between client browsers and AJAX-enabled Web services.</span></span>

<span data-ttu-id="62a5b-106">W tym artykule pokazano, jak serializować obiekty typu .NET do danych zakodowanych w formacie JSON, a następnie deserializować dane z powrotem do wystąpień typów .NET.</span><span class="sxs-lookup"><span data-stu-id="62a5b-106">This article demonstrates how to serialize .NET type objects into JSON-encoded data and then deserialize data in the JSON format back into instances of .NET types.</span></span> <span data-ttu-id="62a5b-107">Ten przykład używa kontraktu danych do zademonstrowania serializacji i deserializacji typu `Person` zdefiniowanego przez użytkownika i używa <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="62a5b-107">This example uses a data contract to demonstrate serialization and deserialization of a user-defined `Person` type and uses <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>

<span data-ttu-id="62a5b-108">Zazwyczaj Serializacja i deserializacja JSON są obsługiwane automatycznie przez Windows Communication Foundation (WCF), gdy używasz typów kontraktu danych w operacjach usługi, które są udostępniane za pośrednictwem punktów końcowych z obsługą technologii AJAX.</span><span class="sxs-lookup"><span data-stu-id="62a5b-108">Normally, JSON serialization and deserialization are handled automatically by Windows Communication Foundation (WCF) when you use data contract types in service operations that are exposed over AJAX-enabled endpoints.</span></span> <span data-ttu-id="62a5b-109">Jednak w niektórych przypadkach może zajść potrzeba bezpośredniej pracy z danymi JSON.</span><span class="sxs-lookup"><span data-stu-id="62a5b-109">However, in some cases you may need to work with JSON data directly.</span></span>

<span data-ttu-id="62a5b-110">Ten artykuł jest oparty na [przykładu Klasa DataContractJsonSerializer](../samples/json-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="62a5b-110">This article is based on the [DataContractJsonSerializer sample](../samples/json-serialization.md).</span></span>

## <a name="to-define-the-data-contract-for-a-person-type"></a><span data-ttu-id="62a5b-111">Aby zdefiniować kontrakt danych dla typu osoby</span><span class="sxs-lookup"><span data-stu-id="62a5b-111">To define the data contract for a Person type</span></span>

1. <span data-ttu-id="62a5b-112">Zdefiniuj kontrakt danych dla `Person`, dołączając <xref:System.Runtime.Serialization.DataContractAttribute> do klasy i atrybutu <xref:System.Runtime.Serialization.DataMemberAttribute> do elementów członkowskich, które chcesz serializować.</span><span class="sxs-lookup"><span data-stu-id="62a5b-112">Define the data contract for `Person` by attaching the <xref:System.Runtime.Serialization.DataContractAttribute> to the class and <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the members you want to serialize.</span></span> <span data-ttu-id="62a5b-113">Aby uzyskać więcej informacji na temat umów dotyczących danych, zobacz [Projektowanie kontraktów usług](../designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="62a5b-113">For more information about data contracts, see [Designing service contracts](../designing-service-contracts.md).</span></span>

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

## <a name="to-serialize-an-instance-of-type-person-to-json"></a><span data-ttu-id="62a5b-114">Aby serializować wystąpienie typu Person do JSON</span><span class="sxs-lookup"><span data-stu-id="62a5b-114">To serialize an instance of type Person to JSON</span></span>

> [!NOTE]
> <span data-ttu-id="62a5b-115">Jeśli wystąpi błąd podczas serializacji odpowiedzi wychodzącej na serwerze lub z innego powodu, może to nie zostać zwrócone do klienta jako błąd.</span><span class="sxs-lookup"><span data-stu-id="62a5b-115">If an error occurs during serialization of an outgoing reply on the server or for some other reason, it may not get returned to the client as a fault.</span></span>

1. <span data-ttu-id="62a5b-116">Utwórz wystąpienie typu `Person`.</span><span class="sxs-lookup"><span data-stu-id="62a5b-116">Create an instance of the `Person` type.</span></span>

    ```csharp
    var p = new Person();
    p.name = "John";
    p.age = 42;
    ```

2. <span data-ttu-id="62a5b-117">Serializacja obiektu `Person` do strumienia pamięci przy użyciu <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="62a5b-117">Serialize the `Person` object to a memory stream by using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>

    ```csharp
    var stream1 = new MemoryStream();
    var ser = new DataContractJsonSerializer(typeof(Person));
    ```

3. <span data-ttu-id="62a5b-118">Użyj metody <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>, aby zapisać dane JSON w strumieniu.</span><span class="sxs-lookup"><span data-stu-id="62a5b-118">Use the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> method to write JSON data to the stream.</span></span>

    ```csharp
    ser.WriteObject(stream1, p);
    ```

4. <span data-ttu-id="62a5b-119">Pokaż dane wyjściowe JSON.</span><span class="sxs-lookup"><span data-stu-id="62a5b-119">Show the JSON output.</span></span>

    ```csharp
    stream1.Position = 0;
    var sr = new StreamReader(stream1);
    Console.Write("JSON form of Person object: ");
    Console.WriteLine(sr.ReadToEnd());
    ```

## <a name="to-deserialize-an-instance-of-type-person-from-json"></a><span data-ttu-id="62a5b-120">Aby zdeserializować wystąpienie typu Person z JSON</span><span class="sxs-lookup"><span data-stu-id="62a5b-120">To deserialize an instance of type Person from JSON</span></span>

1. <span data-ttu-id="62a5b-121">Deserializacja danych zakodowanych w formacie JSON do nowego wystąpienia `Person` przy użyciu metody <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="62a5b-121">Deserialize the JSON-encoded data into a new instance of `Person` by using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> method of the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>

    ```csharp
    stream1.Position = 0;
    var p2 = (Person)ser.ReadObject(stream1);
    ```

2. <span data-ttu-id="62a5b-122">Pokaż wyniki.</span><span class="sxs-lookup"><span data-stu-id="62a5b-122">Show the results.</span></span>

    ```csharp
    Console.WriteLine($"Deserialized back, got name={p2.name}, age={p2.age}");
    ```

## <a name="example"></a><span data-ttu-id="62a5b-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="62a5b-123">Example</span></span>

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
> <span data-ttu-id="62a5b-124">Serializator JSON zgłasza wyjątek serializacji dla kontraktów danych, które mają wiele składowych o tej samej nazwie, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="62a5b-124">The JSON serializer throws a serialization exception for data contracts that have multiple members with the same name, as shown in the following sample code.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="62a5b-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="62a5b-125">See also</span></span>

- [<span data-ttu-id="62a5b-126">Serializacja kodu JSON w programie .NET</span><span class="sxs-lookup"><span data-stu-id="62a5b-126">JSON serialization in .NET</span></span>](../../../standard/serialization/system-text-json-overview.md)
