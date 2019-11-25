---
title: Przykład Klasa DataContractJsonSerializer
ms.date: 03/30/2017
ms.assetid: 3c2c4747-7510-4bdf-b4fe-64f98428ef4a
ms.openlocfilehash: 509f80812bb815e4fa56fa3ebdc9236ac0622ace
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141823"
---
# <a name="datacontractjsonserializer-sample"></a>Przykład Klasa DataContractJsonSerializer

> [!NOTE]
> Ten przykład jest przeznaczony dla <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>. W przypadku większości scenariuszy, które obejmują Serializowanie i deserializacja kodu JSON, zalecamy korzystanie z narzędzi w [przestrzeni nazw System. Text. JSON](../../../standard/serialization/system-text-json-overview.md). 

<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> obsługuje te same typy co <xref:System.Runtime.Serialization.DataContractSerializer>. Format danych JSON jest szczególnie przydatny podczas pisania asynchronicznych aplikacji sieci Web w stylu JavaScript i XML (AJAX). Obsługa technologii AJAX w programie Windows Communication Foundation (WCF) jest zoptymalizowana pod kątem użycia z ASP.NET AJAX przez kontrolkę ScriptManager. Przykłady użycia Windows Communication Foundation (WCF) z ASP.NET AJAX można znaleźć w przykładach [AJAX](ajax.md).  
  
Procedura konfiguracji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
Przykład używa kontraktu danych `Person` do zademonstrowania serializacji i deserializacji.  

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

 Aby serializować wystąpienie typu `Person` do formatu JSON, najpierw utwórz <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> i użyj metody `WriteObject` do zapisania danych JSON w strumieniu.  

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

 Badanie obiektu `p2` informuje o poprawnym deserializacji danych JSON.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Skompiluj rozwiązanie JsonSerialization. sln zgodnie z opisem w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Uruchom utworzoną aplikację konsolową.  
