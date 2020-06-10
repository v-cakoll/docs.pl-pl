---
title: Używanie mechanizmu rozpoznawania kontraktów danych
ms.date: 03/30/2017
ms.assetid: 2e68a16c-36f0-4df4-b763-32021bff2b89
ms.openlocfilehash: 20abd4d928fc51eb359949ecbb216615e9659b7f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595027"
---
# <a name="using-a-data-contract-resolver"></a>Używanie mechanizmu rozpoznawania kontraktów danych
Program rozpoznawania kontraktów danych umożliwia dynamiczne Konfigurowanie znanych typów. Znane typy są wymagane podczas serializacji lub deserializacji typu nieoczekiwanego przez kontrakt danych. Aby uzyskać więcej informacji na temat znanych typów, zobacz [znane typy kontraktu danych](data-contract-known-types.md). Znane typy są zwykle określane statycznie. Oznacza to, że trzeba znać wszystkie możliwe typy, które operacja może otrzymać podczas implementowania operacji. Istnieją scenariusze, w których ta wartość nie jest prawdziwa i możliwość dynamicznego określania znanych typów jest ważna.  
  
## <a name="creating-a-data-contract-resolver"></a>Tworzenie programu rozpoznawania kontraktu danych  
 Tworzenie programu rozpoznawania kontraktu danych wymaga zastosowania dwóch metod <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> i <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> . Te dwie metody implementują wywołania zwrotne, które są używane podczas serializacji i deserializacji odpowiednio. <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A>Metoda jest wywoływana podczas serializacji i pobiera typ kontraktu danych i mapuje go na `xsi:type` nazwę i przestrzeń nazw. <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A>Metoda jest wywoływana podczas deserializacji i przyjmuje `xsi:type` nazwę i przestrzeń nazw i rozwiązuje ją do typu kontraktu danych. Obie te metody mają `knownTypeResolver` parametr, którego można użyć do użycia domyślnego programu rozpoznawania znanego typu w implementacji.  
  
 Poniższy przykład pokazuje, jak zaimplementować metodę <xref:System.Runtime.Serialization.DataContractResolver> w celu mapowania do i z typu kontraktu danych o nazwie `Customer` pochodnej z typu kontraktu danych `Person` .  
  
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
  
 Po zdefiniowaniu można <xref:System.Runtime.Serialization.DataContractResolver> użyć go przez przekazanie go do <xref:System.Runtime.Serialization.DataContractSerializer> konstruktora, jak pokazano w poniższym przykładzie.  
  
```csharp
XmlObjectSerializer serializer = new DataContractSerializer(typeof(Customer), null, Int32.MaxValue, false, false, null, new MyCustomerResolver());  
```  
  
 Można określić <xref:System.Runtime.Serialization.DataContractResolver> w wywołaniu <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A?displayProperty=nameWithType> <xref:System.Runtime.Serialization.DataContractSerializer.WriteObject%2A?displayProperty=nameWithType> metody lub, jak pokazano w poniższym przykładzie.  
  
```csharp
MemoryStream ms = new MemoryStream();  
DataContractSerializer serializer = new DataContractSerializer(typeof(Customer));  
XmlDictionaryWriter writer = XmlDictionaryWriter.CreateDictionaryWriter(XmlWriter.Create(ms));  
serializer.WriteObject(writer, new Customer(), new MyCustomerResolver());  
writer.Flush();  
ms.Position = 0;  
Console.WriteLine(((Customer)serializer.ReadObject(XmlDictionaryReader.CreateDictionaryReader(XmlReader.Create(ms)), false, new MyCustomerResolver()));  
```  
  
 Można też ustawić ją na tak, <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> jak pokazano w poniższym przykładzie.  
  
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
  
 Można deklaratywnie określić program rozpoznawania kontraktu danych przez implementację atrybutu, który można zastosować do usługi.  Aby uzyskać więcej informacji, zobacz przykład [KnownAssemblyAttribute](../samples/knownassemblyattribute.md) . Ten przykład implementuje atrybut o nazwie "KnownAssembly", który dodaje niestandardowy program rozpoznawania kontraktu danych do zachowania usługi.  
  
## <a name="see-also"></a>Zobacz też

- [Znane typy kontraktów danych](data-contract-known-types.md)
- [Przykład elementu DataContractSerializer](../samples/datacontractserializer-sample.md)
- [KnownAssemblyAttribute](../samples/knownassemblyattribute.md)
