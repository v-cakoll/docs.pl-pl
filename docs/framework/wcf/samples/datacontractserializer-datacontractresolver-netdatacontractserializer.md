---
title: Używanie elementów DataContractSerializer i DataContractResolver do udostępniania funkcji elementu NetDataContractSerializer
ms.date: 03/30/2017
ms.assetid: 1376658f-f695-45f7-a7e0-94664e9619ff
ms.openlocfilehash: 455ffe936373525f574d4401412c099d41d45f66
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59167222"
---
# <a name="using-datacontractserializer-and-datacontractresolver-to-provide-the-functionality-of-netdatacontractserializer"></a>Używanie elementów DataContractSerializer i DataContractResolver do udostępniania funkcji elementu NetDataContractSerializer
W tym przykładzie przedstawiono sposób użycia <xref:System.Runtime.Serialization.DataContractSerializer> odpowiednimi <xref:System.Runtime.Serialization.DataContractResolver> zapewnia taką samą funkcjonalność jak <xref:System.Runtime.Serialization.NetDataContractSerializer>. W tym przykładzie przedstawiono sposób tworzenia odpowiednie <xref:System.Runtime.Serialization.DataContractResolver> oraz jak je dodać <xref:System.Runtime.Serialization.DataContractSerializer>.

## <a name="sample-details"></a>Przykład szczegółów
 <xref:System.Runtime.Serialization.NetDataContractSerializer> różni się od <xref:System.Runtime.Serialization.DataContractSerializer> w jednym ze sposobów ważne: <xref:System.Runtime.Serialization.NetDataContractSerializer> zawiera informacje o typie CLR w serializacji XML, a <xref:System.Runtime.Serialization.DataContractSerializer> nie. W związku z tym <xref:System.Runtime.Serialization.NetDataContractSerializer> mogą służyć tylko wtedy, gdy zarówno serializacji i deserializacji kończy się udostępniać te same typy CLR. Jednak zaleca się używanie <xref:System.Runtime.Serialization.DataContractSerializer> ponieważ jego wydajność, większą niż <xref:System.Runtime.Serialization.NetDataContractSerializer>. Można zmienić informacje, które jest serializowana we <xref:System.Runtime.Serialization.DataContractSerializer> , dodając <xref:System.Runtime.Serialization.DataContractResolver> do niego.

 Ten przykład obejmuje dwa projekty. Używa pierwszego projektu <xref:System.Runtime.Serialization.NetDataContractSerializer> do serializacji obiektu. Drugi projekt używa <xref:System.Runtime.Serialization.DataContractSerializer> z <xref:System.Runtime.Serialization.DataContractResolver> zapewnienie taką samą funkcjonalność jak pierwszy projekt.

 Poniższy przykład kodu pokazuje implementację niestandardowej <xref:System.Runtime.Serialization.DataContractResolver> o nazwie `MyDataContractResolver` który został dodany do <xref:System.Runtime.Serialization.DataContractSerializer> w projekcie DCSwithDCR.

```csharp
class MyDataContractResolver : DataContractResolver
{
    private XmlDictionary dictionary = new XmlDictionary();

    public MyDataContractResolver()
    {
    }

    // Used at deserialization
    // Allows users to map xsi:type name to any Type
    public override Type ResolveName(string typeName, string typeNamespace, DataContractResolver knownTypeResolver)
    {
        Type type = knownTypeResolver.ResolveName(typeName, typeNamespace, null);
        if (type == null)
        {
            type = Type.GetType(typeName + ", " + typeNamespace);
        }
        return type;
    }

    // Used at serialization
    // Maps any Type to a new xsi:type representation
    public override void ResolveType(Type dataContractType, DataContractResolver knownTypeResolver, out XmlDictionaryString typeName, out XmlDictionaryString typeNamespace)
    {
        knownTypeResolver.ResolveType(dataContractType, null, out typeName, out typeNamespace);
        if (typeName == null || typeNamespace == null)
        {
            XmlDictionary dictionary = new XmlDictionary();
            typeName = dictionary.Add(dataContractType.FullName);
            typeNamespace = dictionary.Add(dataContractType.Assembly.FullName);
        }
    }
}
```

#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu

1.  Za pomocą programu Visual Studio 2012, otwórz plik rozwiązania DCRSample.sln.

2.  Kliknij prawym przyciskiem myszy plik rozwiązania, a następnie wybierz **właściwości**.

3.  W **strony właściwości rozwiązania** okna dialogowego, w obszarze **wspólne właściwości**, **projekt startowy**, wybierz opcję **wiele projektów startowych:**.

4.  Obok pozycji **DCSwithDCR** projektu, wybierz opcję **Start** z **akcji** listy rozwijanej.

5.  Obok pozycji **NetDCS** projektu, wybierz opcję **Start** z **akcji** listy rozwijanej.

6.  Kliknij przycisk **OK** aby zamknąć okno dialogowe.

7.  Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.

8.  Aby uruchomić rozwiązanie, naciśnij kombinację klawiszy CTRL + F5.

> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\NetDcSasDcSwithDCR`  
