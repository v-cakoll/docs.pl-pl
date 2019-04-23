---
title: Używanie mechanizmu rozpoznawania kontraktów danych
ms.date: 03/30/2017
ms.assetid: 2e68a16c-36f0-4df4-b763-32021bff2b89
ms.openlocfilehash: b1c545d84db68f4b13925dd9088cc9d81050b5e7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59222448"
---
# <a name="using-a-data-contract-resolver"></a>Używanie mechanizmu rozpoznawania kontraktów danych
Mechanizmu rozpoznawania kontraktów danych umożliwia dynamicznie konfigurować znane typy. Znane typy są wymagane, gdy serializacji lub deserializacji typu nie jest oczekiwany przez kontraktu danych. Aby uzyskać więcej informacji na temat znanych typów, zobacz [znane typy kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md). Statycznie zwykle są określone znane typy. Oznacza to, czy trzeba znać możliwych typów operacji może pojawić się podczas wykonywania operacji. Istnieją scenariusze, w których nie jest to prawdą, i możliwość dynamicznie określić znanych typów jest ważne.  
  
## <a name="creating-a-data-contract-resolver"></a>Tworzenie mechanizmu rozpoznawania kontraktów danych  
 Tworzenie mechanizmu rozpoznawania kontraktów danych wymaga implementacji dwóch metod <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> i <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A>. Te dwie metody wdrożenia wywołania zwrotne, które są używane podczas serializacji i deserializacji, odpowiednio. <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> Metoda jest wywoływana podczas serializacji i przyjmuje typ kontraktu danych i mapowany do `xsi:type` nazwy i przestrzeni nazw. <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> Metoda jest wywoływana podczas deserializacji i przyjmuje `xsi:type` nazwy i przestrzeni nazw i jest rozpoznawana jako typ kontraktu danych. Obie te metody mają `knownTypeResolver` parametr, który może służyć do Użyj domyślnej znany typ programu rozpoznawania nazw w danej implementacji.  
  
 Poniższy przykład pokazuje, jak zaimplementować <xref:System.Runtime.Serialization.DataContractResolver> do mapowania do i z typu kontraktu danych o nazwie `Customer` pochodzi od typu kontraktu danych `Person`.  
  
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
  
 Po zdefiniowaniu <xref:System.Runtime.Serialization.DataContractResolver> służy przez przekazanie jej do <xref:System.Runtime.Serialization.DataContractSerializer> konstruktora, jak pokazano w poniższym przykładzie.  
  
```  
XmlObjectSerializer serializer = new DataContractSerializer(typeof(Customer), null, Int32.MaxValue, false, false, null, new MyCustomerResolver());  
```  
  
 Można określić <xref:System.Runtime.Serialization.DataContractResolver> w wywołaniu <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A?displayProperty=nameWithType> lub <xref:System.Runtime.Serialization.DataContractSerializer.WriteObject%2A?displayProperty=nameWithType> metody, jak pokazano w poniższym przykładzie.  
  
```  
MemoryStream ms = new MemoryStream();  
DataContractSerializer serializer = new DataContractSerializer(typeof(Customer));  
XmlDictionaryWriter writer = XmlDictionaryWriter.CreateDictionaryWriter(XmlWriter.Create(ms));  
serializer.WriteObject(writer, new Customer(), new MyCustomerResolver());  
writer.Flush();  
ms.Position = 0;  
Console.WriteLine(((Customer)serializer.ReadObject(XmlDictionaryReader.CreateDictionaryReader(XmlReader.Create(ms)), false, new MyCustomerResolver()));  
```  
  
 Lub ustaw go na <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> jak pokazano w poniższym przykładzie.  
  
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
  
 Mechanizmu rozpoznawania kontraktów danych można określić sposób deklaratywny implementując atrybut, który można zastosować do usługi.  Aby uzyskać więcej informacji, zobacz [KnownAssemblyAttribute](../../../../docs/framework/wcf/samples/knownassemblyattribute.md) próbki. W tym przykładzie implementuje atrybutu o nazwie "KnownAssembly" dodająca mechanizmu rozpoznawania kontraktów danych niestandardowych do zachowania usługi.  
  
## <a name="see-also"></a>Zobacz także

- [Znane typy kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [Przykład elementu DataContractSerializer](../../../../docs/framework/wcf/samples/datacontractserializer-sample.md)
- [KnownAssemblyAttribute](../../../../docs/framework/wcf/samples/knownassemblyattribute.md)
