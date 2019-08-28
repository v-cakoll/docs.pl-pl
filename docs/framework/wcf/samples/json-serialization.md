---
title: Serializacja JSON
ms.date: 03/30/2017
ms.assetid: 3c2c4747-7510-4bdf-b4fe-64f98428ef4a
ms.openlocfilehash: 364c5935dbbe087b413d28a033e0b5b569b02c9a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045547"
---
# <a name="json-serialization"></a>Serializacja JSON
Ten przykład pokazuje, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> jak używać do serializacji i deserializacji danych w formacie JavaScript Object Notation (JSON). Ten aparat serializacji konwertuje dane JSON na wystąpienia typów .NET Framework i z powrotem do danych JSON. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>obsługuje te same typy co <xref:System.Runtime.Serialization.DataContractSerializer>. Format danych JSON jest szczególnie przydatny podczas pisania asynchronicznych aplikacji sieci Web w stylu JavaScript i XML (AJAX). Obsługa technologii AJAX w programie Windows Communication Foundation (WCF) jest zoptymalizowana pod kątem użycia z ASP.NET AJAX przez kontrolkę ScriptManager. Przykłady użycia Windows Communication Foundation (WCF) z ASP.NET AJAX można znaleźć w przykładach [AJAX](ajax.md).  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Przykład używa `Person` kontraktu danych w celu przedstawienia serializacji i deserializacji.  

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

 Aby serializować wystąpienie `Person` typu do formatu JSON, należy <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> utworzyć pierwszy i użyć `WriteObject` metody do zapisania danych JSON w strumieniu.  

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
  
 Przykład demonstruje deserializacji z danych JSON do obiektu. Następnie przewiń strumień i Wywołaj `ReadObject`.  

```csharp
Person p2 = (Person)ser.ReadObject(stream1);
```

 `p2` Badanie obiektu informuje o poprawnym deserializacji danych JSON.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Skompiluj rozwiązanie JsonSerialization. sln zgodnie z opisem w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Uruchom utworzoną aplikację konsolową.  
