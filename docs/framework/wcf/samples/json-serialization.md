---
title: DataContractJsonSerializer próbki
ms.date: 03/30/2017
ms.assetid: 3c2c4747-7510-4bdf-b4fe-64f98428ef4a
ms.openlocfilehash: d3456582d73640f1802c17d7f29f4931a6f920b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144633"
---
# <a name="datacontractjsonserializer-sample"></a>DataContractJsonSerializer próbki

> [!NOTE]
> Ten przykład <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>jest dla . W przypadku większości scenariuszy, które obejmują serializację i deserializację JSON, zalecamy interfejsy API w [obszarze nazw System.Text.Json](../../../standard/serialization/system-text-json-overview.md).

<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>obsługuje te same <xref:System.Runtime.Serialization.DataContractSerializer>typy co . Format danych JSON jest szczególnie przydatny podczas pisania asynchronicznych aplikacji sieci Web w stylu JavaScript i XML (AJAX). Obsługa ajax w programie Windows Communication Foundation (WCF) jest zoptymalizowana do użytku z ASP.NET AJAX za pośrednictwem formantu ScriptManager. Przykłady używania programu Windows Communication Foundation (WCF) z ASP.NET AJAX można znaleźć w [przykładzie próbek ajax](ajax.md).  
  
Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
W przykładzie `Person` użyto umowy danych do wykazania serializacji i deserializacji.  

```csharp
[DataContract]
class Person
{
    [DataMember]
    internal string name;

    [DataMember]
    internal int age;
}
```

 Aby serializować wystąpienie `Person` typu do JSON, utwórz <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> pierwszy i użyj metody do zapisu `WriteObject` danych JSON do strumienia.  

```csharp
Person p = new Person();
//Set up Person object...
MemoryStream stream1 = new MemoryStream();
DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));
ser.WriteObject(stream1, p);
```

 Strumień pamięci zawiera prawidłowe dane JSON.
  
```json  
{"age":42,"name":"John"}  
```  
  
 Przykład demonstruje deserializacji z danych JSON do obiektu. Następnie przewiń strumień `ReadObject`i zadzwoń .  

```csharp
Person p2 = (Person)ser.ReadObject(stream1);
```

 Badanie `p2` obiektu ujawnia, że dane JSON został poprawnie zdesializowany.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Zbuduj rozwiązanie JsonSerialization.sln zgodnie z opisem w [tworzenie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Uruchom wynikową aplikację konsoli.  
