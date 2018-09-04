---
title: Serializacja JSON
ms.date: 03/30/2017
ms.assetid: 3c2c4747-7510-4bdf-b4fe-64f98428ef4a
ms.openlocfilehash: 02e81fe8d75ae7b752641d1f9a650fcfe5873141
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43510070"
---
# <a name="json-serialization"></a>Serializacja JSON
W tym przykładzie przedstawiono sposób użycia <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> do serializacji i deserializacji danych w formacie JavaScript Object Notation (JSON). Ten mechanizm serializacji konwertuje dane JSON do wystąpień [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typów i z powrotem na dane JSON. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> obsługuje te same typy jako <xref:System.Runtime.Serialization.DataContractSerializer>. Format danych JSON jest szczególnie przydatne podczas pisania asynchronicznego języka JavaScript i XML (technologia AJAX)-stylów aplikacji sieci Web. Obsługa technologii AJAX w Windows Communication Foundation (WCF) została zoptymalizowana do użytku przy użyciu rozszerzeń ASP.NET AJAX, za pomocą formantu ScriptManager. Przykłady dotyczące używania usługi Windows Communication Foundation (WCF) przy użyciu rozszerzeń ASP.NET AJAX, zobacz [przykłady AJAX](https://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące konfiguracji dla tego przykładu znajdują się na końcu tego tematu.  
  
 W przykładzie użyto `Person` kontraktu danych zademonstrować serializacji i deserializacji.  

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

 Do serializacji wystąpienia `Person` wpisz do formatu JSON, Utwórz <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> pierwszy i użyj `WriteObject` metodę, aby zapisać dane JSON do strumienia.  

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
  
 W przykładzie pokazano deserializacją z danymi w formacie JSON na obiekt. Następnie przewiń strumienia i wywołanie `ReadObject`.  

```csharp
Person p2 = (Person)ser.ReadObject(stream1);
```

 Badanie `p2` obiektu wykazuje, że dane JSON została przeprowadzona prawidłowo.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Skompiluj rozwiązanie JsonSerialization.sln, zgodnie z opisem w [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Uruchamianie wynikłej aplikacji konsoli.  
  
## <a name="see-also"></a>Zobacz też
