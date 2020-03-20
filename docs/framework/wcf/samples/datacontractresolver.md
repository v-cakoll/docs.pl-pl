---
title: DataContractResolver
ms.date: 03/30/2017
ms.assetid: 6c200c02-bc14-4b8d-bbab-9da31185b805
ms.openlocfilehash: 716bcb2bb43656051beffb15da9c7a988942ecd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183795"
---
# <a name="datacontractresolver"></a>DataContractResolver
W tym przykładzie pokazano, jak procesy serializacji i <xref:System.Runtime.Serialization.DataContractResolver> deserializacji można dostosować przy użyciu klasy. W tym przykładzie pokazano, jak używać DataContractResolver do mapowania typów CLR do i z reprezentacji xsi:type podczas serializacji i deserializacji.

## <a name="sample-details"></a>Przykładowe szczegóły
 Próbka definiuje następujące typy CLR.

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

 Próbka ładuje zestaw, wyodrębnia każdy z tych typów, a następnie serializuje i deserializuje je. Jest <xref:System.Runtime.Serialization.DataContractResolver> podłączony do procesu serializacji, przekazując <xref:System.Runtime.Serialization.DataContractResolver>wystąpienie klasy pochodnej do konstruktora, <xref:System.Runtime.Serialization.DataContractSerializer> jak pokazano w poniższym przykładzie.

```csharp
this.serializer = new DataContractSerializer(typeof(Object), null, int.MaxValue, false, true, null, new MyDataContractResolver(assembly));
```

 Następnie w próbce serializuje typy CLR, jak pokazano w poniższym przykładzie kodu.

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

 Następnie deserializuje xsi:types, jak pokazano w poniższym przykładzie kodu.

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

 Ponieważ zwyczaj <xref:System.Runtime.Serialization.DataContractResolver> jest przekazywany do <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> konstruktora, jest wywoływana podczas serializacji do mapowania typu CLR do równoważnego `xsi:type`. Podobnie <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> jest wywoływana podczas deserializacji `xsi:type` do mapowania do równoważnego typu CLR. W tym przykładzie <xref:System.Runtime.Serialization.DataContractResolver> jest zdefiniowany, jak pokazano w poniższym przykładzie.

 Poniższy przykład kodu jest klasą wywodzącą się z <xref:System.Runtime.Serialization.DataContractResolver>.

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

 W ramach próbki Types projektu generuje zestaw ze wszystkimi typami, które są używane w tym przykładzie. Ten projekt służy do dodawania, usuwania lub modyfikowania typów, które będą serializowane.

#### <a name="to-use-this-sample"></a>Aby użyć tej próbki

1. Za pomocą programu Visual Studio 2012 otwórz plik rozwiązania DCRSample.sln.

2. Aby uruchomić rozwiązanie, naciśnij klawisz F5

> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractResolver`  
  
## <a name="see-also"></a>Zobacz też

- [Używanie mechanizmu rozpoznawania kontraktów danych](../../../../docs/framework/wcf/feature-details/using-a-data-contract-resolver.md)
