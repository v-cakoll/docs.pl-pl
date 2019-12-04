---
title: Używanie elementów DataContractSerializer i DataContractResolver do udostępniania funkcji elementu NetDataContractSerializer
ms.date: 03/30/2017
ms.assetid: 1376658f-f695-45f7-a7e0-94664e9619ff
ms.openlocfilehash: 3a0f88310caf9865756d9c04011b709dd4c4c2eb
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716907"
---
# <a name="using-datacontractserializer-and-datacontractresolver-to-provide-the-functionality-of-netdatacontractserializer"></a>Używanie elementów DataContractSerializer i DataContractResolver do udostępniania funkcji elementu NetDataContractSerializer
W tym przykładzie pokazano, jak korzystanie z <xref:System.Runtime.Serialization.DataContractSerializer> z odpowiednimi <xref:System.Runtime.Serialization.DataContractResolver> zapewnia te same funkcje co <xref:System.Runtime.Serialization.NetDataContractSerializer>. Ten przykład pokazuje, jak utworzyć odpowiednie <xref:System.Runtime.Serialization.DataContractResolver> i sposób dodawania go do <xref:System.Runtime.Serialization.DataContractSerializer>.

## <a name="sample-details"></a>Przykładowe szczegóły
 <xref:System.Runtime.Serialization.NetDataContractSerializer> różni się od <xref:System.Runtime.Serialization.DataContractSerializer> w jeden ważny sposób: <xref:System.Runtime.Serialization.NetDataContractSerializer> zawiera informacje o typie CLR w serializowanym kodzie XML, natomiast <xref:System.Runtime.Serialization.DataContractSerializer> nie. W związku z tym, <xref:System.Runtime.Serialization.NetDataContractSerializer> mogą być używane tylko wtedy, gdy obie operacje serializacji i deserializacji współużytkują te same typy CLR. Zaleca się jednak używanie <xref:System.Runtime.Serialization.DataContractSerializer>, ponieważ jego wydajność jest lepsza niż <xref:System.Runtime.Serialization.NetDataContractSerializer>. Można zmienić informacje, które są serializowane w <xref:System.Runtime.Serialization.DataContractSerializer> przez dodanie <xref:System.Runtime.Serialization.DataContractResolver> do niego.

 Ten przykład składa się z dwóch projektów. Pierwszy projekt używa <xref:System.Runtime.Serialization.NetDataContractSerializer> do serializacji obiektu. Drugi projekt używa <xref:System.Runtime.Serialization.DataContractSerializer> z <xref:System.Runtime.Serialization.DataContractResolver>, aby zapewnić te same funkcje co pierwszy projekt.

 Poniższy przykład kodu pokazuje implementację niestandardowego <xref:System.Runtime.Serialization.DataContractResolver> o nazwie `MyDataContractResolver`, która jest dodawana do <xref:System.Runtime.Serialization.DataContractSerializer> w projekcie DCSwithDCR.

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
        type ??= Type.GetType(typeName + ", " + typeNamespace);
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

1. Za pomocą programu Visual Studio 2012 Otwórz plik rozwiązania DCRSample. sln.

2. Kliknij prawym przyciskiem myszy plik rozwiązania i wybierz polecenie **Właściwości**.

3. W oknie dialogowym **strony właściwości rozwiązania** w obszarze **wspólne właściwości**, **projekt startowy**wybierz **wiele projektów startowych:** .

4. Obok projektu **DCSwithDCR** wybierz pozycję **Rozpocznij** z listy rozwijanej **Akcja** .

5. Obok projektu **NetDCS** wybierz pozycję **Rozpocznij** z listy rozwijanej **Akcja** .

6. Kliknij przycisk **OK** , aby zamknąć okno dialogowe.

7. Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.

8. Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\NetDcSasDcSwithDCR`  
