---
title: "Używanie mechanizmu rozpoznawania kontraktów danych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e68a16c-36f0-4df4-b763-32021bff2b89
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: dc28086e0e4489df5594c4b1ce5ec16cea9b1e61
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="using-a-data-contract-resolver"></a><span data-ttu-id="6630a-102">Używanie mechanizmu rozpoznawania kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="6630a-102">Using a Data Contract Resolver</span></span>
<span data-ttu-id="6630a-103">Mechanizmu rozpoznawania kontraktów danych umożliwia konfigurowanie znane typy dynamicznie.</span><span class="sxs-lookup"><span data-stu-id="6630a-103">A data contract resolver allows you to configure known types dynamically.</span></span> <span data-ttu-id="6630a-104">Znane typy są wymagane w przypadku serializacji lub deserializacji typu nie jest oczekiwany przez kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="6630a-104">Known types are required when serializing or deserializing a type not expected by a data contract.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="6630a-105">znane typy, zobacz [znane typy kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="6630a-105"> known types, see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span> <span data-ttu-id="6630a-106">Statycznie zwykle są określone znane typy.</span><span class="sxs-lookup"><span data-stu-id="6630a-106">Known types are normally specified statically.</span></span> <span data-ttu-id="6630a-107">Oznacza to, czy trzeba znać wszystkie możliwe typy operacji może pojawić się podczas wykonania operacji.</span><span class="sxs-lookup"><span data-stu-id="6630a-107">This means you would have to know all the possible types an operation may receive while implementing the operation.</span></span> <span data-ttu-id="6630a-108">Brak scenariuszy, w których nie dotyczy ważne jest możliwość dynamicznie Określ znanych typów.</span><span class="sxs-lookup"><span data-stu-id="6630a-108">There are scenarios in which this is not true and being able to specify known types dynamically is important.</span></span>  
  
## <a name="creating-a-data-contract-resolver"></a><span data-ttu-id="6630a-109">Tworzenie mechanizmu rozpoznawania kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="6630a-109">Creating a Data Contract Resolver</span></span>  
 <span data-ttu-id="6630a-110">Tworzenie mechanizmu rozpoznawania kontraktów danych wymaga wykonania dwóch metod <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> i <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A>.</span><span class="sxs-lookup"><span data-stu-id="6630a-110">Creating a data contract resolver involves implementing two methods, <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> and <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A>.</span></span> <span data-ttu-id="6630a-111">Te dwie metody wdrożenia wywołania zwrotne, które są używane podczas serializacji i deserializacji, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="6630a-111">These two methods implement callbacks that are used during serialization and deserialization, respectively.</span></span> <span data-ttu-id="6630a-112"><xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> Metoda jest wywoływana podczas serializacji i pobiera typu kontraktu danych i go do mapy `xsi:type` nazwę i przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="6630a-112">The <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> method is invoked during serialization and takes a data contract type and maps it to an `xsi:type` name and namespace.</span></span> <span data-ttu-id="6630a-113"><xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> Metoda jest wywoływana podczas deserializacji i przyjmuje `xsi:type` nazwę i przestrzeń nazw i jest rozpoznawany jako typ kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="6630a-113">The <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> method is invoked during deserialization and takes an `xsi:type` name and namespace and resolves it to a data contract type.</span></span> <span data-ttu-id="6630a-114">Obie te metody mają `knownTypeResolver` parametr, który może służyć do korzysta z domyślnego znany typ programu rozpoznawania nazw w implementacji.</span><span class="sxs-lookup"><span data-stu-id="6630a-114">Both of these methods have a `knownTypeResolver` parameter that can be used to use the default known type resolver in your implementation.</span></span>  
  
 <span data-ttu-id="6630a-115">Poniższy przykład przedstawia sposób wykonania <xref:System.Runtime.Serialization.DataContractResolver> do mapowania do i z typu kontraktu danych o nazwie `Customer` pochodzi od typu kontraktu danych `Person`.</span><span class="sxs-lookup"><span data-stu-id="6630a-115">The following example shows how to implement a <xref:System.Runtime.Serialization.DataContractResolver> to map to and from a data contract type named `Customer` derived from a data contract type `Person`.</span></span>  
  
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
  
 <span data-ttu-id="6630a-116">Po zdefiniowaniu <xref:System.Runtime.Serialization.DataContractResolver> służy przez przekazanie jej <xref:System.Runtime.Serialization.DataContractSerializer> konstruktora, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="6630a-116">Once you have defined a <xref:System.Runtime.Serialization.DataContractResolver> you can use it by passing it to the <xref:System.Runtime.Serialization.DataContractSerializer> constructor as shown in the following example.</span></span>  
  
```  
XmlObjectSerializer serializer = new DataContractSerializer(typeof(Customer), null, Int32.MaxValue, false, false, null, new MyCustomerResolver());  
```  
  
 <span data-ttu-id="6630a-117">Można określić <xref:System.Runtime.Serialization.DataContractSerializer> w wywołaniu <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A> lub <xref:System.Runtime.Serialization.DataContractSerializer.WriteObject%2A> metod, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="6630a-117">You can specify a <xref:System.Runtime.Serialization.DataContractSerializer> in a call to the <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A> or <xref:System.Runtime.Serialization.DataContractSerializer.WriteObject%2A> methods, as shown in the following example.</span></span>  
  
```  
MemoryStream ms = new MemoryStream();  
DataContractSerializer serializer = new DataContractSerializer(typeof(Customer));  
XmlDictionaryWriter writer = XmlDictionaryWriter.CreateDictionaryWriter(XmlWriter.Create(ms));  
serializer.WriteObject(writer, new Customer(), new MyCustomerResolver());  
writer.Flush();  
ms.Position = 0;  
Console.WriteLine(((Customer)serializer.ReadObject(XmlDictionaryReader.CreateDictionaryReader(XmlReader.Create(ms)), false, new MyCustomerResolver()));  
```  
  
 <span data-ttu-id="6630a-118">Lub ustaw ją na <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="6630a-118">Or you can set it on the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> as shown in the following example.</span></span>  
  
```  
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
  
 <span data-ttu-id="6630a-119">Mechanizmu rozpoznawania kontraktów danych można określić deklaratywnie zaimplementowanie atrybut, który może odnosić się do usługi.</span><span class="sxs-lookup"><span data-stu-id="6630a-119">You can declaratively specify a data contract resolver by implementing an attribute that can be applied to a service.</span></span>  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="6630a-120">[KnownAssemblyAttribute](../../../../docs/framework/wcf/samples/knownassemblyattribute.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="6630a-120"> the [KnownAssemblyAttribute](../../../../docs/framework/wcf/samples/knownassemblyattribute.md) sample.</span></span> <span data-ttu-id="6630a-121">W tym przykładzie implementuje atrybutu o nazwie "KnownAssembly" dodaje program rozpoznawania nazw kontraktu danych niestandardowych do zachowania usługi.</span><span class="sxs-lookup"><span data-stu-id="6630a-121">This sample implements an attribute called "KnownAssembly" that adds a custom data contract resolver to the service’s behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6630a-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6630a-122">See Also</span></span>  
 [<span data-ttu-id="6630a-123">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="6630a-123">Data Contract Known Types</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="6630a-124">Przykład elementu DataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="6630a-124">DataContractSerializer Sample</span></span>](../../../../docs/framework/wcf/samples/datacontractserializer-sample.md)  
 [<span data-ttu-id="6630a-125">KnownAssemblyAttribute</span><span class="sxs-lookup"><span data-stu-id="6630a-125">KnownAssemblyAttribute</span></span>](../../../../docs/framework/wcf/samples/knownassemblyattribute.md)
