---
title: DataContractResolver
ms.date: 03/30/2017
ms.assetid: 6c200c02-bc14-4b8d-bbab-9da31185b805
ms.openlocfilehash: c2a2afaa450e9abe17b62f6be07a2dc41459ca20
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600026"
---
# <a name="datacontractresolver"></a>DataContractResolver
Ten przykład pokazuje, jak procesy serializacji i deserializacji można dostosować za pomocą <xref:System.Runtime.Serialization.DataContractResolver> klasy. Ten przykład pokazuje, jak używać obiektu DataContractResolver do mapowania typów CLR do i z reprezentacji xsi: Type podczas serializacji i deserializacji.

## <a name="sample-details"></a>Przykładowe szczegóły
 Przykład definiuje następujące typy CLR.

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

 Przykład ładuje zestaw, wyodrębnia każdy z tych typów, a następnie serializować i deserializacji. <xref:System.Runtime.Serialization.DataContractResolver>Program jest podłączony do procesu serializacji przez przekazanie wystąpienia <xref:System.Runtime.Serialization.DataContractResolver> klasy pochodnej do <xref:System.Runtime.Serialization.DataContractSerializer> konstruktora, jak pokazano w poniższym przykładzie.

```csharp
this.serializer = new DataContractSerializer(typeof(Object), null, int.MaxValue, false, true, null, new MyDataContractResolver(assembly));
```

 Następnie próbka serializować typy CLR, jak pokazano w poniższym przykładzie kodu.

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

 Następnie próbka deserializacji xsi: Types, jak pokazano w poniższym przykładzie kodu.

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

 Ponieważ element niestandardowy <xref:System.Runtime.Serialization.DataContractResolver> jest przekazywać do <xref:System.Runtime.Serialization.DataContractSerializer> konstruktora, <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> jest wywoływany podczas serializacji w celu mapowania typu CLR na odpowiednik `xsi:type` . Podobnie <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> jest wywoływana podczas deserializacji w celu mapowania `xsi:type` do równoważnego typu CLR. W tym przykładzie <xref:System.Runtime.Serialization.DataContractResolver> jest zdefiniowana, tak jak pokazano w poniższym przykładzie.

 Poniższy przykład kodu jest klasą pochodną <xref:System.Runtime.Serialization.DataContractResolver> .

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

 W ramach próbki projekt typów generuje zestaw ze wszystkimi typami, które są używane w tym przykładzie. Ten projekt służy do dodawania, usuwania lub modyfikowania typów, które będą serializowane.

#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu

1. Za pomocą programu Visual Studio 2012 Otwórz plik rozwiązania DCRSample. sln.

2. Aby uruchomić rozwiązanie, naciśnij klawisz F5.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractResolver`  
  
## <a name="see-also"></a>Zobacz też

- [Używanie mechanizmu rozpoznawania kontraktów danych](../feature-details/using-a-data-contract-resolver.md)
