---
title: DataContractResolver
ms.date: 03/30/2017
ms.assetid: 6c200c02-bc14-4b8d-bbab-9da31185b805
ms.openlocfilehash: 101c33ca197be9dff52a73c844dd0b006e62b2ac
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716590"
---
# <a name="datacontractresolver"></a><span data-ttu-id="4085e-102">DataContractResolver</span><span class="sxs-lookup"><span data-stu-id="4085e-102">DataContractResolver</span></span>
<span data-ttu-id="4085e-103">Ten przykład pokazuje, jak można dostosowywać procesy serializacji i deserializacji za pomocą klasy <xref:System.Runtime.Serialization.DataContractResolver>.</span><span class="sxs-lookup"><span data-stu-id="4085e-103">This sample demonstrates how the serialization and deserialization processes can be customized by using the <xref:System.Runtime.Serialization.DataContractResolver> class.</span></span> <span data-ttu-id="4085e-104">Ten przykład pokazuje, jak używać obiektu DataContractResolver do mapowania typów CLR do i z reprezentacji xsi: Type podczas serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="4085e-104">This sample shows how to use a DataContractResolver to map CLR types to and from an xsi:type representation during serialization and deserialization.</span></span>

## <a name="sample-details"></a><span data-ttu-id="4085e-105">Przykładowe szczegóły</span><span class="sxs-lookup"><span data-stu-id="4085e-105">Sample Details</span></span>
 <span data-ttu-id="4085e-106">Przykład definiuje następujące typy CLR.</span><span class="sxs-lookup"><span data-stu-id="4085e-106">The sample defines the following CLR types.</span></span>

```csharp
using System;
using System.Runtime.Serialization;

namespace Types
{
    [DataContract]
    public class Customer
    {
        [DataMember]
        public string Name { get; set; }
    }

    [DataContract]
    public class VIPCustomer : Customer
    {
        [DataMember]
        public string VipInfo { get; set; }
    }

    [DataContract]
    public class RegularCustomer : Customer
    {
    }

    [DataContract]
    public class PreferredVIPCustomer : VIPCustomer
    {
    }
}
```

 <span data-ttu-id="4085e-107">Przykład ładuje zestaw, wyodrębnia każdy z tych typów, a następnie serializować i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="4085e-107">The sample loads the assembly, extracts each of these types, and then serializes and deserializes them.</span></span> <span data-ttu-id="4085e-108"><xref:System.Runtime.Serialization.DataContractResolver> jest podłączony do procesu serializacji przez przekazanie wystąpienia klasy pochodnej <xref:System.Runtime.Serialization.DataContractResolver>do konstruktora <xref:System.Runtime.Serialization.DataContractSerializer>, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="4085e-108">The <xref:System.Runtime.Serialization.DataContractResolver> is plugged into the serialization process by passing an instance of the <xref:System.Runtime.Serialization.DataContractResolver>-derived class to the <xref:System.Runtime.Serialization.DataContractSerializer> constructor, as shown in the following example.</span></span>

```csharp
this.serializer = new DataContractSerializer(typeof(Object), null, int.MaxValue, false, true, null, new MyDataContractResolver(assembly));
```

 <span data-ttu-id="4085e-109">Następnie próbka serializować typy CLR, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="4085e-109">The sample then serializes the CLR types as shown in the following code example.</span></span>

```csharp
Assembly assembly = Assembly.Load(new AssemblyName("Types"));

public void serialize(Type type)
{
    Object instance = Activator.CreateInstance(type);

    Console.WriteLine("----------------------------------------");
    Console.WriteLine();
    Console.WriteLine("Serializing type: {0}", type.Name);
    Console.WriteLine();
    this.buffer = new StringBuilder();
    using (XmlWriter xmlWriter = XmlWriter.Create(this.buffer))
    {
        try
        {
            this.serializer.WriteObject(xmlWriter, instance);
        }
        catch (SerializationException error)
        {
            Console.WriteLine(error.ToString());
        }
    }
    Console.WriteLine(this.buffer.ToString());
}
```

 <span data-ttu-id="4085e-110">Następnie próbka deserializacji xsi: Types, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="4085e-110">The sample then deserializes the xsi:types as shown in the following code example.</span></span>

```csharp
public void deserialize(Type type)
{
    Console.WriteLine();
    Console.WriteLine("Deserializing type: {0}", type.Name);
    Console.WriteLine();
    using (XmlReader xmlReader = XmlReader.Create(new StringReader(this.buffer.ToString())))
    {
        Object obj = this.serializer.ReadObject(xmlReader);
    }
}
```

 <span data-ttu-id="4085e-111">Ponieważ <xref:System.Runtime.Serialization.DataContractResolver> niestandardowe jest przenoszona do konstruktora <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> jest wywoływana podczas serializacji w celu mapowania typu CLR na odpowiedni `xsi:type`.</span><span class="sxs-lookup"><span data-stu-id="4085e-111">Since the custom <xref:System.Runtime.Serialization.DataContractResolver> is passed in to the <xref:System.Runtime.Serialization.DataContractSerializer> constructor, the <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> is called during serialization to map a CLR type to an equivalent `xsi:type`.</span></span> <span data-ttu-id="4085e-112">Podobnie <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> jest wywoływana podczas deserializacji, aby zmapować `xsi:type` do równoważnego typu CLR.</span><span class="sxs-lookup"><span data-stu-id="4085e-112">Similarly the <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> is called during deserialization to map the `xsi:type` to an equivalent CLR type.</span></span> <span data-ttu-id="4085e-113">W tym przykładzie <xref:System.Runtime.Serialization.DataContractResolver> jest zdefiniowana, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="4085e-113">In this sample, the <xref:System.Runtime.Serialization.DataContractResolver> is defined as shown in the following example.</span></span>

 <span data-ttu-id="4085e-114">Poniższy przykład kodu jest klasą pochodną <xref:System.Runtime.Serialization.DataContractResolver>.</span><span class="sxs-lookup"><span data-stu-id="4085e-114">The following code example is a class deriving from <xref:System.Runtime.Serialization.DataContractResolver>.</span></span>

```csharp
class MyDataContractResolver : DataContractResolver
{
    private Dictionary<string, XmlDictionaryString> dictionary = new Dictionary<string, XmlDictionaryString>();
    Assembly assembly;

    public MyDataContractResolver(Assembly assembly)
    {
        this.assembly = assembly;
    }

    // Used at deserialization
    // Allows users to map xsi:type name to any Type
    public override Type ResolveName(string typeName, string typeNamespace, DataContractResolver knownTypeResolver)
    {
        XmlDictionaryString tName;
        XmlDictionaryString tNamespace;
        if (dictionary.TryGetValue(typeName, out tName) && dictionary.TryGetValue(typeNamespace, out tNamespace))
        {
            return this.assembly.GetType(tNamespace.Value + "." + tName.Value);
        }
        else
        {
            return null;
        }
    }

    // Used at serialization
    // Maps any Type to a new xsi:type representation
    public override void ResolveType(Type dataContractType, DataContractResolver knownTypeResolver, out XmlDictionaryString typeName, out XmlDictionaryString typeNamespace)
    {
        string name = dataContractType.Name;
        string namesp = dataContractType.Namespace;
        typeName = new XmlDictionaryString(XmlDictionary.Empty, name, 0);
        typeNamespace = new XmlDictionaryString(XmlDictionary.Empty, namesp, 0);
        if (!dictionary.ContainsKey(dataContractType.Name))
        {
            dictionary.Add(name, typeName);
        }
        if (!dictionary.ContainsKey(dataContractType.Namespace))
        {
            dictionary.Add(namesp, typeNamespace);
        }
    }
}
```

 <span data-ttu-id="4085e-115">W ramach próbki projekt typów generuje zestaw ze wszystkimi typami, które są używane w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="4085e-115">As part of the sample, the Types project generates the assembly with all the types that are used in this sample.</span></span> <span data-ttu-id="4085e-116">Ten projekt służy do dodawania, usuwania lub modyfikowania typów, które będą serializowane.</span><span class="sxs-lookup"><span data-stu-id="4085e-116">Use this project to add, remove or modify the types that will be serialized.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="4085e-117">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="4085e-117">To use this sample</span></span>

1. <span data-ttu-id="4085e-118">Za pomocą programu Visual Studio 2012 Otwórz plik rozwiązania DCRSample. sln.</span><span class="sxs-lookup"><span data-stu-id="4085e-118">Using Visual Studio 2012, open the DCRSample.sln solution file.</span></span>

2. <span data-ttu-id="4085e-119">Aby uruchomić rozwiązanie, naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="4085e-119">To run the solution, press F5</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4085e-120">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="4085e-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4085e-121">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="4085e-121">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="4085e-122">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4085e-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4085e-123">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="4085e-123">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractResolver`  
  
## <a name="see-also"></a><span data-ttu-id="4085e-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4085e-124">See also</span></span>

- [<span data-ttu-id="4085e-125">Używanie mechanizmu rozpoznawania kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="4085e-125">Using a Data Contract Resolver</span></span>](../../../../docs/framework/wcf/feature-details/using-a-data-contract-resolver.md)
