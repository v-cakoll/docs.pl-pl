---
title: Używanie elementów DataContractSerializer i DataContractResolver do udostępniania funkcji elementu NetDataContractSerializer
ms.date: 03/30/2017
ms.assetid: 1376658f-f695-45f7-a7e0-94664e9619ff
ms.openlocfilehash: e7a4f0d754b444d8558b03e07d98788a2eee5971
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144985"
---
# <a name="using-datacontractserializer-and-datacontractresolver-to-provide-the-functionality-of-netdatacontractserializer"></a>Używanie elementów DataContractSerializer i DataContractResolver do udostępniania funkcji elementu NetDataContractSerializer
W tym przykładzie pokazano, w jaki sposób <xref:System.Runtime.Serialization.DataContractSerializer> użycie za pomocą odpowiedniego <xref:System.Runtime.Serialization.DataContractResolver> zapewnia taką samą funkcjonalność jak <xref:System.Runtime.Serialization.NetDataContractSerializer>. W tym przykładzie pokazano, jak utworzyć <xref:System.Runtime.Serialization.DataContractResolver> odpowiednie <xref:System.Runtime.Serialization.DataContractSerializer>i jak dodać go do .

## <a name="sample-details"></a>Przykładowe szczegóły
 <xref:System.Runtime.Serialization.NetDataContractSerializer>różni się <xref:System.Runtime.Serialization.DataContractSerializer> od w <xref:System.Runtime.Serialization.NetDataContractSerializer> jeden ważny sposób: zawiera informacje o typie CLR w serializowanym XML, podczas gdy <xref:System.Runtime.Serialization.DataContractSerializer> nie. W związku <xref:System.Runtime.Serialization.NetDataContractSerializer> z tym może służyć tylko wtedy, gdy zarówno serializacji i deserializacji kończy współużytkować te same typy CLR. Jednak zaleca się stosowanie, <xref:System.Runtime.Serialization.DataContractSerializer> ponieważ jego <xref:System.Runtime.Serialization.NetDataContractSerializer>wydajność jest lepsza niż . Można zmienić informacje, które <xref:System.Runtime.Serialization.DataContractSerializer> są serializowane, dodając <xref:System.Runtime.Serialization.DataContractResolver> do niego.

 Ten przykład składa się z dwóch projektów. Pierwszy projekt używa <xref:System.Runtime.Serialization.NetDataContractSerializer> do serializacji obiektu. Drugi projekt używa <xref:System.Runtime.Serialization.DataContractSerializer> z <xref:System.Runtime.Serialization.DataContractResolver> a, aby zapewnić taką samą funkcjonalność jak pierwszy projekt.

 Poniższy przykład kodu pokazuje implementację niestandardowej <xref:System.Runtime.Serialization.DataContractResolver> nazwie, `MyDataContractResolver` która jest dodawana <xref:System.Runtime.Serialization.DataContractSerializer> do projektu DCSwithDCR.

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

#### <a name="to-use-this-sample"></a>Aby użyć tej próbki

1. Za pomocą programu Visual Studio 2012 otwórz plik rozwiązania DCRSample.sln.

2. Kliknij prawym przyciskiem myszy plik rozwiązania i wybierz polecenie **Właściwości**.

3. W oknie dialogowym **Strony właściwości rozwiązania** w obszarze Wspólne **właściwości**, **Projekt uruchamiania**wybierz pozycję **Wiele projektów startowych:**.

4. Obok projektu **DCSwithDCR** wybierz pozycję **Start** z listy rozwijanej **Akcja.**

5. Obok projektu **NetDCS** wybierz pozycję **Start** z listy rozwijanej **Akcja.**

6. Kliknij **przycisk OK,** aby zamknąć okno dialogowe.

7. Aby utworzyć rozwiązanie, naciśnij klawisze CTRL+SHIFT+B.

8. Aby uruchomić rozwiązanie, naciśnij klawisze CTRL+F5.

> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\NetDcSasDcSwithDCR`  
