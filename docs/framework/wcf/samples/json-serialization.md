---
title: Serializacja JSON
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3c2c4747-7510-4bdf-b4fe-64f98428ef4a
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d87dd0f22473015ba51d7be996106a57c4708a67
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="json-serialization"></a>Serializacja JSON
W tym przykładzie przedstawiono sposób użycia <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> do serializowania i deserializowania danych w formacie JavaScript Object Notation (JSON). Ten aparat serializacji konwertuje dane JSON na wystąpień [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typów i z powrotem na dane JSON. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>obsługuje te same typy jako <xref:System.Runtime.Serialization.DataContractSerializer>. Format danych JSON jest szczególnie przydatne podczas zapisywania asynchronicznego JavaScript i XML (AJAX) — styl aplikacji sieci Web. Obsługa interfejsu AJAX w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] jest zoptymalizowany do użycia z programem ASP.NET AJAX, za pomocą formantu ScriptManager. Przykłady dotyczące używania [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] z ASP.NET AJAX, zobacz [przykłady AJAX](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące konfiguracji dla tego przykładu znajdują się na końcu tego tematu.  
  
 W przykładzie użyto `Person` kontraktu danych zademonstrować serializacji i deserializacji.  
  
```  
[DataContract]  
    class Person  
    {  
        [DataMember]  
        internal string name;  
  
        [DataMember]  
        internal int age;  
    }  
```  
  
 Do serializacji wystąpienia `Person` typu do formatu JSON, Utwórz <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> pierwszy i użyj `WriteObject` metody do zapisu danych JSON strumienia.  
  
```  
Person p = new Person();  
//Set up Person object...  
MemoryStream stream1 = new MemoryStream();  
DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));  
ser.WriteObject(stream1, p);  
```  
  
 Strumienia pamięci zawiera poprawne dane JSON.  
  
```json  
{"age":42,"name":"John"}  
```  
  
 W przykładzie pokazano, podczas deserializacji danych JSON na obiekt. Następnie rewind strumienia i wywołania `ReadObject`.  
  
```  
Person p2 = (Person)ser.ReadObject(stream1);  
```  
  
 Badanie `p2` obiektu wykazuje, że dane JSON została prawidłowo zdeserializowana.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie próbki  
  
1.  Skompiluj rozwiązanie JsonSerialization.sln zgodnie z opisem w [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Uruchom wynikowej aplikacji konsoli.  
  
## <a name="see-also"></a>Zobacz też
