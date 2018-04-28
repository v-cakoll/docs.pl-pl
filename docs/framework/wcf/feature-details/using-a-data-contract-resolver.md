---
title: Używanie mechanizmu rozpoznawania kontraktów danych
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2e68a16c-36f0-4df4-b763-32021bff2b89
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 20ef713c67ee21aa8f7a92975bc6e6ce8798a087
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="using-a-data-contract-resolver"></a>Używanie mechanizmu rozpoznawania kontraktów danych
Mechanizmu rozpoznawania kontraktów danych umożliwia konfigurowanie znane typy dynamicznie. Znane typy są wymagane w przypadku serializacji lub deserializacji typu nie jest oczekiwany przez kontraktu danych. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] znane typy, zobacz [znane typy kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md). Statycznie zwykle są określone znane typy. Oznacza to, czy trzeba znać wszystkie możliwe typy operacji może pojawić się podczas wykonania operacji. Brak scenariuszy, w których nie dotyczy ważne jest możliwość dynamicznie Określ znanych typów.  
  
## <a name="creating-a-data-contract-resolver"></a>Tworzenie mechanizmu rozpoznawania kontraktów danych  
 Tworzenie mechanizmu rozpoznawania kontraktów danych wymaga wykonania dwóch metod <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> i <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A>. Te dwie metody wdrożenia wywołania zwrotne, które są używane podczas serializacji i deserializacji, odpowiednio. <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> Metoda jest wywoływana podczas serializacji i pobiera typu kontraktu danych i go do mapy `xsi:type` nazwę i przestrzeń nazw. <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> Metoda jest wywoływana podczas deserializacji i przyjmuje `xsi:type` nazwę i przestrzeń nazw i jest rozpoznawany jako typ kontraktu danych. Obie te metody mają `knownTypeResolver` parametr, który może służyć do korzysta z domyślnego znany typ programu rozpoznawania nazw w implementacji.  
  
 Poniższy przykład przedstawia sposób wykonania <xref:System.Runtime.Serialization.DataContractResolver> do mapowania do i z typu kontraktu danych o nazwie `Customer` pochodzi od typu kontraktu danych `Person`.  
  
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
  
 Po zdefiniowaniu <xref:System.Runtime.Serialization.DataContractResolver> służy przez przekazanie jej <xref:System.Runtime.Serialization.DataContractSerializer> konstruktora, jak pokazano w poniższym przykładzie.  
  
```  
XmlObjectSerializer serializer = new DataContractSerializer(typeof(Customer), null, Int32.MaxValue, false, false, null, new MyCustomerResolver());  
```  
  
 Można określić <xref:System.Runtime.Serialization.DataContractSerializer> w wywołaniu <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A> lub <xref:System.Runtime.Serialization.DataContractSerializer.WriteObject%2A> metod, jak pokazano w poniższym przykładzie.  
  
```  
MemoryStream ms = new MemoryStream();  
DataContractSerializer serializer = new DataContractSerializer(typeof(Customer));  
XmlDictionaryWriter writer = XmlDictionaryWriter.CreateDictionaryWriter(XmlWriter.Create(ms));  
serializer.WriteObject(writer, new Customer(), new MyCustomerResolver());  
writer.Flush();  
ms.Position = 0;  
Console.WriteLine(((Customer)serializer.ReadObject(XmlDictionaryReader.CreateDictionaryReader(XmlReader.Create(ms)), false, new MyCustomerResolver()));  
```  
  
 Lub ustaw ją na <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> jak pokazano w poniższym przykładzie.  
  
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
  
 Mechanizmu rozpoznawania kontraktów danych można określić deklaratywnie zaimplementowanie atrybut, który może odnosić się do usługi.  Aby uzyskać więcej informacji, zobacz [KnownAssemblyAttribute](../../../../docs/framework/wcf/samples/knownassemblyattribute.md) próbki. W tym przykładzie implementuje atrybutu o nazwie "KnownAssembly" dodaje program rozpoznawania nazw kontraktu danych niestandardowych do zachowania usługi.  
  
## <a name="see-also"></a>Zobacz też  
 [Znane typy kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [Przykład elementu DataContractSerializer](../../../../docs/framework/wcf/samples/datacontractserializer-sample.md)  
 [KnownAssemblyAttribute](../../../../docs/framework/wcf/samples/knownassemblyattribute.md)
