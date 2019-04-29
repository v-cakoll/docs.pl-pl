---
title: DataContractResolver
ms.date: 03/30/2017
ms.assetid: 6c200c02-bc14-4b8d-bbab-9da31185b805
ms.openlocfilehash: 981b70011979e1e0fbd8fc6b22ba54774c824342
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61608466"
---
# <a name="datacontractresolver"></a>DataContractResolver
Niniejszy przykład pokazuje, jak można dostosować procesy serializacji i deserializacji za pomocą <xref:System.Runtime.Serialization.DataContractResolver> klasy. W tym przykładzie pokazano, jak używać obiektu DataContractResolver do mapowania typów CLR, do i z reprezentacji xsi: type podczas serializacji i deserializacji.

## <a name="sample-details"></a>Przykład szczegółów
 Przykładowa aplikacja definiuje następujące typy CLR.

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

 Przykład ładuje zestaw, wyodrębnia z każdego z tych typów serializuje i deserializuje z nich. <xref:System.Runtime.Serialization.DataContractResolver> Jest podłączony do procesu serializacji przez przekazanie wystąpienia <xref:System.Runtime.Serialization.DataContractResolver>-klasy pochodnej <xref:System.Runtime.Serialization.DataContractSerializer> konstruktora, jak pokazano w poniższym przykładzie.

```csharp
this.serializer = new DataContractSerializer(typeof(Object), null, int.MaxValue, false, true, null, new MyDataContractResolver(assembly));
```

 Przykład szereguje typy CLR, jak pokazano w poniższym przykładzie kodu.

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

 Przykład następnie deserializuje xsi:types, jak pokazano w poniższym przykładzie kodu.

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

 Od niestandardowej <xref:System.Runtime.Serialization.DataContractResolver> jest przekazywany do <xref:System.Runtime.Serialization.DataContractSerializer> konstruktora, <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> jest wywoływana podczas serializacji w celu mapowania typu CLR na równoważne `xsi:type`. Podobnie <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> jest wywoływana podczas deserializacji, aby zamapować `xsi:type` na równoważne typ CLR. W tym przykładzie <xref:System.Runtime.Serialization.DataContractResolver> jest zdefiniowany jak pokazano w poniższym przykładzie.

 Poniższy przykład kodu jest Klasa pochodząca od <xref:System.Runtime.Serialization.DataContractResolver>.

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

 Jako części przykładu projekt typów generuje zestaw ze wszystkimi typami, które są używane w tym przykładzie. Użyj tego projektu, aby dodać, usunąć lub zmodyfikować typy, które będą serializowane.

#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu

1. Za pomocą programu Visual Studio 2012, otwórz plik rozwiązania DCRSample.sln.

2. Aby uruchomić rozwiązanie, naciśnij klawisz F5

> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractResolver`  
  
## <a name="see-also"></a>Zobacz także

- [Używanie mechanizmu rozpoznawania kontraktów danych](../../../../docs/framework/wcf/feature-details/using-a-data-contract-resolver.md)
