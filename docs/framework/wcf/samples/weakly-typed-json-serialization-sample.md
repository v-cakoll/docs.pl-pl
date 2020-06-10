---
title: Przykład serializacji kodu JSON ze słabą kontrolą typów
ms.date: 03/30/2017
ms.assetid: 0b30e501-4ef5-474d-9fad-a9d559cf9c52
ms.openlocfilehash: a503878f1cbb60090b648da8dfec741edbf02d1b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602326"
---
# <a name="weakly-typed-json-serialization-sample"></a>Przykład serializacji kodu JSON ze słabą kontrolą typów
Podczas serializowania typu zdefiniowanego przez użytkownika do określonego formatu sieci lub deserializacji formatu sieci z powrotem do typu zdefiniowanego przez użytkownika, dany typ zdefiniowany przez użytkownika musi być dostępny zarówno dla usługi, jak i dla klienta. Zwykle w tym celu <xref:System.Runtime.Serialization.DataContractAttribute> atrybut jest stosowany do tych typów zdefiniowanych przez użytkownika, a <xref:System.Runtime.Serialization.DataMemberAttribute> atrybut jest stosowany do ich członków. Ten mechanizm stosuje się również podczas pracy z obiektami JavaScript Object Notation (JSON), zgodnie z opisem w temacie [How to: deserializacji i deserializacji danych JSON](../feature-details/how-to-serialize-and-deserialize-json-data.md).  
  
 W niektórych scenariuszach usługa Windows Communication Foundation (WCF) lub klient musi mieć dostęp do obiektów JSON generowanych przez usługę lub klienta poza kontrolą dewelopera. Ponieważ więcej usług sieci Web publicznie uwidacznia interfejsy API JSON, może być niepraktyczne, aby deweloper programu WCF konstruuje lokalne typy zdefiniowane przez użytkownika, w którym można deserializować dowolne obiekty JSON. Ten przykład zapewnia mechanizm, który umożliwia deweloperom WCF współpracę z deserializowanymi, dowolnymi obiektami JSON bez tworzenia typów zdefiniowanych przez użytkownika. Nazywa się to *słabo wpisaną Serializacja* obiektów JSON, ponieważ typ, do którego deserializacji obiektu JSON nie jest znany w czasie kompilacji.  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Na przykład publiczny interfejs API usługi sieci Web zwraca następujący obiekt JSON, który opisuje niektóre informacje o użytkowniku usługi.  
  
```json  
{"personal": {"name": "Paul", "age": 23, "height": 1.7, "isSingle": true, "luckyNumbers": [5,17,21]}, "favoriteBands": ["Band ABC", "Band XYZ"]}  
```  
  
 Aby deserializować ten obiekt, klient WCF musi zaimplementować następujące typy zdefiniowane przez użytkownika.  
  
```csharp  
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
  
 Może to być uciążliwe, szczególnie jeśli klient musi obsługiwać więcej niż jeden typ obiektu JSON.  
  
 `JsonObject`Typ dostarczony przez ten przykład wprowadza nieprawidłową reprezentację deserializowanego obiektu JSON. `JsonObject`opiera się na naturalnym mapowaniu między obiektami JSON i słownikami .NET Framework, a mapowanie między tablicami JSON i tablicami .NET Framework. Poniższy kod przedstawia `JsonObject` Typ.  
  
```csharp  
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
  
 Należy pamiętać, że można "przeglądać" obiekty JSON i tablice bez potrzeby deklarowania ich typu w czasie kompilacji. Aby uzyskać wyjaśnienie wymagania dotyczącego obiektu najwyższego poziomu `["root"]` , zobacz [Mapowanie tematu między danymi JSON i XML](../feature-details/mapping-between-json-and-xml.md).  
  
> [!NOTE]
> `JsonObject`Klasa jest dostępna tylko jako przykład. Nie została dokładnie przetestowana i nie powinna być używana w środowiskach produkcyjnych. Oczywiste implikacje serializacji JSON o słabo określonym typie to brak bezpieczeństwa typu podczas pracy z `JsonObject` .  
  
 Aby użyć tego `JsonObject` typu, kontrakt operacji klienta musi używać <xref:System.ServiceModel.Channels.Message> jako jego typu zwracanego.  
  
```csharp  
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
  
 `JsonObject`Następnie zostanie utworzone wystąpienie, jak pokazano w poniższym kodzie.  
  
```csharp  
// Code to instantiate IClientSideProfileService channel omitted…  
  
// Make a request to the service and obtain the Json response  
XmlDictionaryReader reader = channel.GetMemberProfile().GetReaderAtBodyContents();  
  
// Go through the Json as though it is a dictionary. There is no need to map it to a .NET CLR type.  
JsonObject json = new JsonObject(reader);  
```  
  
 `JsonObject`Konstruktor przyjmuje <xref:System.Xml.XmlDictionaryReader> , który jest uzyskiwany za pomocą <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> metody. Czytnik zawiera reprezentację XML wiadomości JSON otrzymanej przez klienta. Aby uzyskać więcej informacji, zobacz [Mapowanie tematu między danymi JSON i XML](../feature-details/mapping-between-json-and-xml.md).  
  
 Program tworzy następujące dane wyjściowe:  
  
```console  
Service listening at http://localhost:8000/.  
To view the JSON output from the sample, navigate to http://localhost:8000/GetMemberProfile  
This is Paul's page. I am 23 years old and I am 1.7 meters tall.  
I am single.  
My lucky numbers are 5, 17, and 21.  
My favorite bands are Band ABC and Band XYZ.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Skompiluj rozwiązanie WeaklyTypedJson. sln zgodnie z opisem w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).  
  
3. Uruchom rozwiązanie.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Ajax\WeaklyTypedJson`  
