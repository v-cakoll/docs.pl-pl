---
title: Używanie mechanizmu rozpoznawania kontraktów danych
ms.date: 03/30/2017
ms.assetid: 2e68a16c-36f0-4df4-b763-32021bff2b89
ms.openlocfilehash: d9082d2979cf9bd0837635af567d69ef34c2e312
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975971"
---
# <a name="using-a-data-contract-resolver"></a><span data-ttu-id="86156-102">Używanie mechanizmu rozpoznawania kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="86156-102">Using a Data Contract Resolver</span></span>
<span data-ttu-id="86156-103">Program rozpoznawania kontraktów danych umożliwia dynamiczne Konfigurowanie znanych typów.</span><span class="sxs-lookup"><span data-stu-id="86156-103">A data contract resolver allows you to configure known types dynamically.</span></span> <span data-ttu-id="86156-104">Znane typy są wymagane podczas serializacji lub deserializacji typu nieoczekiwanego przez kontrakt danych.</span><span class="sxs-lookup"><span data-stu-id="86156-104">Known types are required when serializing or deserializing a type not expected by a data contract.</span></span> <span data-ttu-id="86156-105">Aby uzyskać więcej informacji na temat znanych typów, zobacz [znane typy kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="86156-105">For more information about known types, see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span> <span data-ttu-id="86156-106">Znane typy są zwykle określane statycznie.</span><span class="sxs-lookup"><span data-stu-id="86156-106">Known types are normally specified statically.</span></span> <span data-ttu-id="86156-107">Oznacza to, że trzeba znać wszystkie możliwe typy, które operacja może otrzymać podczas implementowania operacji.</span><span class="sxs-lookup"><span data-stu-id="86156-107">This means you would have to know all the possible types an operation may receive while implementing the operation.</span></span> <span data-ttu-id="86156-108">Istnieją scenariusze, w których ta wartość nie jest prawdziwa i możliwość dynamicznego określania znanych typów jest ważna.</span><span class="sxs-lookup"><span data-stu-id="86156-108">There are scenarios in which this is not true and being able to specify known types dynamically is important.</span></span>  
  
## <a name="creating-a-data-contract-resolver"></a><span data-ttu-id="86156-109">Tworzenie programu rozpoznawania kontraktu danych</span><span class="sxs-lookup"><span data-stu-id="86156-109">Creating a Data Contract Resolver</span></span>  
 <span data-ttu-id="86156-110">Tworzenie programu rozpoznawania kontraktu danych wymaga zastosowania dwóch metod, <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> i <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A>.</span><span class="sxs-lookup"><span data-stu-id="86156-110">Creating a data contract resolver involves implementing two methods, <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> and <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A>.</span></span> <span data-ttu-id="86156-111">Te dwie metody implementują wywołania zwrotne, które są używane podczas serializacji i deserializacji odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="86156-111">These two methods implement callbacks that are used during serialization and deserialization, respectively.</span></span> <span data-ttu-id="86156-112">Metoda <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> jest wywoływana podczas serializacji i pobiera typ kontraktu danych i mapuje go na nazwę `xsi:type` i przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="86156-112">The <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> method is invoked during serialization and takes a data contract type and maps it to an `xsi:type` name and namespace.</span></span> <span data-ttu-id="86156-113">Metoda <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> jest wywoływana podczas deserializacji i przyjmuje `xsi:type` nazwę i przestrzeń nazw i rozwiązuje ją do typu kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="86156-113">The <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> method is invoked during deserialization and takes an `xsi:type` name and namespace and resolves it to a data contract type.</span></span> <span data-ttu-id="86156-114">Obie te metody mają parametr `knownTypeResolver`, którego można użyć do użycia domyślnego programu rozpoznawania znanego typu w implementacji.</span><span class="sxs-lookup"><span data-stu-id="86156-114">Both of these methods have a `knownTypeResolver` parameter that can be used to use the default known type resolver in your implementation.</span></span>  
  
 <span data-ttu-id="86156-115">Poniższy przykład pokazuje, jak zaimplementować <xref:System.Runtime.Serialization.DataContractResolver>, aby mapować do i z typu kontraktu danych o nazwie `Customer` pochodzącego od typu kontraktu danych `Person`.</span><span class="sxs-lookup"><span data-stu-id="86156-115">The following example shows how to implement a <xref:System.Runtime.Serialization.DataContractResolver> to map to and from a data contract type named `Customer` derived from a data contract type `Person`.</span></span>  
  
```csharp  
public class MyCustomerResolver : DataContractResolver  
{  
    public override bool TryResolveType(Type dataContractType, Type declaredType, DataContractResolver knownTypeResolver, out XmlDictionaryString typeName, out XmlDictionaryString typeNamespace)  
    {  
        if (dataContractType == typeof(Customer))  
        {  
            XmlDictionary dictionary = new XmlDictionary();  
            typeName = dictionary.Add("SomeCustomer");  
            typeNamespace = dictionary.Add("http://tempuri.com");  
            return true;  
        }  
        else  
        {  
            return knownTypeResolver.TryResolveType(dataContractType, declaredType, null, out typeName, out typeNamespace);  
        }  
    }  
  
    public override Type ResolveName(string typeName, string typeNamespace, DataContractResolver knownTypeResolver)  
    {  
        if (typeName == "SomeCustomer" && typeNamespace == "http://tempuri.com")  
        {  
            return typeof(Customer);  
        }  
        else  
        {  
            return knownTypeResolver.ResolveName(typeName, typeNamespace, null);  
        }  
    }  
}  
```  
  
 <span data-ttu-id="86156-116">Po zdefiniowaniu <xref:System.Runtime.Serialization.DataContractResolver> można go użyć przez przekazanie go do konstruktora <xref:System.Runtime.Serialization.DataContractSerializer>, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="86156-116">Once you have defined a <xref:System.Runtime.Serialization.DataContractResolver> you can use it by passing it to the <xref:System.Runtime.Serialization.DataContractSerializer> constructor as shown in the following example.</span></span>  
  
```csharp
XmlObjectSerializer serializer = new DataContractSerializer(typeof(Customer), null, Int32.MaxValue, false, false, null, new MyCustomerResolver());  
```  
  
 <span data-ttu-id="86156-117">Można określić <xref:System.Runtime.Serialization.DataContractResolver> w wywołaniu metody <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A?displayProperty=nameWithType> lub <xref:System.Runtime.Serialization.DataContractSerializer.WriteObject%2A?displayProperty=nameWithType>, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="86156-117">You can specify a <xref:System.Runtime.Serialization.DataContractResolver> in a call to the <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A?displayProperty=nameWithType> or <xref:System.Runtime.Serialization.DataContractSerializer.WriteObject%2A?displayProperty=nameWithType> methods, as shown in the following example.</span></span>  
  
```csharp
MemoryStream ms = new MemoryStream();  
DataContractSerializer serializer = new DataContractSerializer(typeof(Customer));  
XmlDictionaryWriter writer = XmlDictionaryWriter.CreateDictionaryWriter(XmlWriter.Create(ms));  
serializer.WriteObject(writer, new Customer(), new MyCustomerResolver());  
writer.Flush();  
ms.Position = 0;  
Console.WriteLine(((Customer)serializer.ReadObject(XmlDictionaryReader.CreateDictionaryReader(XmlReader.Create(ms)), false, new MyCustomerResolver()));  
```  
  
 <span data-ttu-id="86156-118">Lub można ją ustawić na <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="86156-118">Or you can set it on the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> as shown in the following example.</span></span>  
  
```csharp
ServiceHost host = new ServiceHost(typeof(MyService));  
  
ContractDescription cd = host.Description.Endpoints[0].Contract;  
OperationDescription myOperationDescription = cd.Operations.Find("Echo");  
  
DataContractSerializerOperationBehavior serializerBehavior = myOperationDescription.Behaviors.Find<DataContractSerializerOperationBehavior>();  
if (serializerBehavior == null)  
{  
    serializerBehavior = new DataContractSerializerOperationBehavior(myOperationDescription);  
    myOperationDescription.Behaviors.Add(serializerBehavior);  
}  
  
SerializerBehavior.DataContractResolver = new MyCustomerResolver();  
```  
  
 <span data-ttu-id="86156-119">Można deklaratywnie określić program rozpoznawania kontraktu danych przez implementację atrybutu, który można zastosować do usługi.</span><span class="sxs-lookup"><span data-stu-id="86156-119">You can declaratively specify a data contract resolver by implementing an attribute that can be applied to a service.</span></span>  <span data-ttu-id="86156-120">Aby uzyskać więcej informacji, zobacz przykład [KnownAssemblyAttribute](../../../../docs/framework/wcf/samples/knownassemblyattribute.md) .</span><span class="sxs-lookup"><span data-stu-id="86156-120">For more information, see the [KnownAssemblyAttribute](../../../../docs/framework/wcf/samples/knownassemblyattribute.md) sample.</span></span> <span data-ttu-id="86156-121">Ten przykład implementuje atrybut o nazwie "KnownAssembly", który dodaje niestandardowy program rozpoznawania kontraktu danych do zachowania usługi.</span><span class="sxs-lookup"><span data-stu-id="86156-121">This sample implements an attribute called "KnownAssembly" that adds a custom data contract resolver to the service’s behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86156-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86156-122">See also</span></span>

- [<span data-ttu-id="86156-123">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="86156-123">Data Contract Known Types</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="86156-124">Przykład elementu DataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="86156-124">DataContractSerializer Sample</span></span>](../../../../docs/framework/wcf/samples/datacontractserializer-sample.md)
- [<span data-ttu-id="86156-125">KnownAssemblyAttribute</span><span class="sxs-lookup"><span data-stu-id="86156-125">KnownAssemblyAttribute</span></span>](../../../../docs/framework/wcf/samples/knownassemblyattribute.md)
