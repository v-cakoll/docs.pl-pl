---
title: "Przykład serializacji kodu JSON ze słabą kontrolą typów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b30e501-4ef5-474d-9fad-a9d559cf9c52
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3b804064a2b7a7bb0f587ae1dc2014769ca6e058
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="weakly-typed-json-serialization-sample"></a>Przykład serializacji kodu JSON ze słabą kontrolą typów
Podczas serializowania typu zdefiniowane przez użytkownika format podanego podczas transmisji lub deserializacji formacie łańcuchowym do typu zdefiniowanego przez użytkownika, danego typu zdefiniowane przez użytkownika muszą być dostępne zarówno usługi, jak i na kliencie. Zwykle w tym celu, <xref:System.Runtime.Serialization.DataContractAttribute> atrybut jest stosowany do tych typów zdefiniowanych przez użytkownika i <xref:System.Runtime.Serialization.DataMemberAttribute> atrybut jest stosowany do ich elementy członkowskie. Ten mechanizm ma również zastosowanie podczas pracy z obiektami JavaScript Object Notation (JSON), zgodnie z opisem w temacie [porady: serializacji i deserializacji danych JSON](../../../../docs/framework/wcf/feature-details/how-to-serialize-and-deserialize-json-data.md).  
  
 W niektórych scenariuszach [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługi lub klienta muszą uzyskać dostęp do obiektów JSON generowanych przez usługi lub klienta, który jest poza kontrolą dewelopera. Jak większej liczby usług sieci Web publicznie uwidacznia interfejsów API JSON, może być niepraktyczne dla [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] developer do utworzenia lokalnego typy zdefiniowane przez użytkownika do którego deserializować dowolnego obiektów JSON. W tym przykładzie zapewnia mechanizm umożliwiający [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] deweloperom zdeserializowany, dowolnego obiektów JSON bez tworzenia typy danych zdefiniowane przez użytkownika. Jest to nazywane *szeregowanie słabą kontrolą* obiektów JSON, ponieważ typ, do którego deserializuje obiekt JSON nie jest znany w czasie kompilacji.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Na przykład publiczny interfejs API usługi sieci Web zwraca następujący obiekt JSON opisano niektóre informacje o użytkowniku usługi.  
  
```json  
{"personal": {"name": "Paul", "age": 23, "height": 1.7, "isSingle": true, "luckyNumbers": [5,17,21]}, "favoriteBands": ["Band ABC", "Band XYZ"]}  
```  
  
 Do deserializacji tego obiektu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta musi implementować następujące typy zdefiniowane przez użytkownika.  
  
```  
[DataContract]  
 public class MemberProfile  
 {  
     [DataMember]  
     public PersonalInfo personal;  
  
     [DataMember]  
     public string[] favoriteBands;  
 }  
  
 [DataContract]  
 public class PersonalInfo  
 {  
     [DataMember]  
     public string name;  
  
     [DataMember]  
     public int age;  
  
     [DataMember]  
     public double height;  
  
     [DataMember]  
     public bool isSingle;  
  
     [DataMember]  
     public int[] luckyNumbers;  
 }  
```  
  
 Może to być skomplikowane, szczególnie w przypadku, gdy klient musi obsługiwać więcej niż jeden typ obiektów JSON.  
  
 `JsonObject` Typem dostarczonym w tym przykładzie przedstawiono słabą kontrolą reprezentacja zdeserializowany obiekt JSON. `JsonObject`polega na fizyczne mapowanie między obiektami JSON i [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] słowniki i mapowanie pomiędzy tablicami JSON i [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tablic. Poniższy kod przedstawia `JsonObject` typu.  
  
```  
// Instantiation of JsonObject json omitted  
  
string name = json["root"]["personal"]["name"];  
int age = json["root"]["personal"]["age"];  
double height = json["root"]["personal"]["height"];  
bool isSingle = json["root"]["personal"]["isSingle"];  
int[] luckyNumbers = {  
                                     json["root"]["personal"]["luckyNumbers"][0],  
                                     json["root"]["personal"]["luckyNumbers"][1],  
                                     json["root"]["personal"]["luckyNumbers"][2]   
                                 };  
string[] favoriteBands = {  
                                        json["root"]["favoriteBands"][0],  
                                        json["root"]["favoriteBands"][1]  
                                    };  
```  
  
 Należy pamiętać, że użytkownik może "Przeglądaj" JSON obiekty i tablice bez konieczności deklarować typu ich w czasie kompilacji. Aby uzyskać informacje o wymogu najwyższego poziomu `["root"]` obiektów, zobacz temat [mapowanie między formatami JSON i XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).  
  
> [!NOTE]
>  `JsonObject` Klasa stanowi tylko przykładem. Nie została dokładnie przetestowana i nie powinna być używana w środowisku produkcyjnym. Oczywistym możliwa słabą kontrolą serializacji JSON jest Brak typu bezpieczeństwa podczas pracy z `JsonObject`.  
  
 Aby użyć `JsonObject` typu, należy użyć kontrakt operacji klienta <xref:System.ServiceModel.Channels.Message> jako jej typu zwracanego.  
  
```  
[ServiceContract]  
    interface IClientSideProfileService  
    {  
        // There is no need to write a DataContract for the complex type returned by the service.  
        // The client will use a JsonObject to browse the JSON in the received message.  
  
        [OperationContract]  
        [WebGet(ResponseFormat = WebMessageFormat.Json)]  
        Message GetMemberProfile();  
    }  
```  
  
 `JsonObject` Następnie zostanie uruchomiony, jak pokazano w poniższym kodzie.  
  
```  
// Code to instantiate IClientSideProfileService channel omitted…  
  
// Make a request to the service and obtain the Json response  
XmlDictionaryReader reader = channel.GetMemberProfile().GetReaderAtBodyContents();  
  
// Go through the Json as though it is a dictionary. There is no need to map it to a .NET CLR type.  
JsonObject json = new JsonObject(reader);  
```  
  
 `JsonObject` Konstruktor pobiera <xref:System.Xml.XmlDictionaryReader>, jest uzyskiwany za pośrednictwem <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> metody. Czytnik zawiera reprezentację XML JSON komunikat przez klienta. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]temat [mapowanie między formatami JSON i XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).  
  
 Program tworzy następujące dane wyjściowe:  
  
```  
Service listening at http://localhost:8000/.  
To view the JSON output from the sample, navigate to http://localhost:8000/GetMemberProfile  
This is Paul's page. I am 23 years old and I am 1.7 meters tall.  
I am single.  
My lucky numbers are 5, 17, and 21.  
My favorite bands are Band ABC and Band XYZ.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Skompiluj rozwiązanie WeaklyTypedJson.sln zgodnie z opisem w [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Uruchom rozwiązania.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Ajax\WeaklyTypedJson`  
  
## <a name="see-also"></a>Zobacz też
