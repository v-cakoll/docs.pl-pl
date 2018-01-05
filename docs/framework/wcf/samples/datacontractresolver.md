---
title: DataContractResolver
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6c200c02-bc14-4b8d-bbab-9da31185b805
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e360bed1cbdd11920d983c08cd7f3955b7432a96
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="datacontractresolver"></a>DataContractResolver
W tym przykładzie pokazano, jak można dostosować procesy serializacji i deserializacji za pomocą <xref:System.Runtime.Serialization.DataContractResolver> klasy. Ten przykład przedstawia użycie obiektu DataContractResolver do mapowania typów CLR do i z reprezentacji xsi: type podczas serializacji i deserializacji.  
  
## <a name="sample-details"></a>Szczegóły próbki  
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
  
 Próbki ładuje zestaw, wyodrębnia każdego z tych typów, a następnie serializuje i deserializuje je. <xref:System.Runtime.Serialization.DataContractResolver> Jest podłączony do procesu serializacji przez przekazanie wystąpienia <xref:System.Runtime.Serialization.DataContractResolver>-klasy do <xref:System.Runtime.Serialization.DataContractSerializer> konstruktora, jak pokazano w poniższym przykładzie.  
  
```csharp  
this.serializer = new DataContractSerializer(typeof(Object), null, int.MaxValue, false, true, null, new MyDataContractResolver(assembly));  
```  
  
 Przykład następnie serializuje typy CLR, jak pokazano w poniższym przykładzie kodu.  
  
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
  
 Ponieważ niestandardowego <xref:System.Runtime.Serialization.DataContractResolver> jest przekazywany do <xref:System.Runtime.Serialization.DataContractSerializer> konstruktora, <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> jest wywoływana podczas serializacji w celu mapowania typu CLR na równoważne `xsi:type`. Podobnie <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> jest wywoływana podczas deserializacji w celu mapowania `xsi:type` odpowiednik typu CLR. W tym przykładzie <xref:System.Runtime.Serialization.DataContractResolver> jest zdefiniowany, jak pokazano w poniższym przykładzie.  
  
 Poniższy przykładowy kod jest klasy wywodzące się z <xref:System.Runtime.Serialization.DataContractResolver>.  
  
```  
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
  
 W ramach przykładu projektu typy generuje zestawu ze wszystkimi typami, które są używane w tym przykładzie. Aby dodać, usunąć lub zmodyfikować typy, które będą serializowane korzystać z tego projektu.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Przy użyciu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz plik rozwiązania DCRSample.sln.  
  
2.  Aby uruchomić rozwiązanie, naciśnij klawisz F5  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractResolver`  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie mechanizmu rozpoznawania kontraktów danych](../../../../docs/framework/wcf/feature-details/using-a-data-contract-resolver.md)
