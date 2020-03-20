---
title: Przykład serializacji kodu JSON ze słabą kontrolą typów
ms.date: 03/30/2017
ms.assetid: 0b30e501-4ef5-474d-9fad-a9d559cf9c52
ms.openlocfilehash: bdeaffe31ba9bced28eebcfe294fc9944e5d05d0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143593"
---
# <a name="weakly-typed-json-serialization-sample"></a>Przykład serializacji kodu JSON ze słabą kontrolą typów
Podczas serializacji typu zdefiniowanego przez użytkownika do danego formatu przewodowego lub deserializacji formatu przewodowego z powrotem do typu zdefiniowanego przez użytkownika, dany typ zdefiniowany przez użytkownika musi być dostępny zarówno dla usługi, jak i klienta. Zwykle w tym <xref:System.Runtime.Serialization.DataContractAttribute> celu atrybut jest stosowany do tych typów <xref:System.Runtime.Serialization.DataMemberAttribute> zdefiniowanych przez użytkownika i atrybut jest stosowany do ich członków. Mechanizm ten ma również zastosowanie podczas pracy z obiektami Notacji obiektów JavaScript (JSON), zgodnie z opisem w temacie [Jak: Serialize i Deserialize JSON Data](../../../../docs/framework/wcf/feature-details/how-to-serialize-and-deserialize-json-data.md).  
  
 W niektórych scenariuszach usługi lub klienta Programu Windows Communication Foundation (WCF) musi uzyskiwać dostęp do obiektów JSON generowanych przez usługę lub klienta, który znajduje się poza kontrolą dewelopera. Ponieważ więcej usług sieci Web publicznie uwidaczniać interfejsy API JSON, może stać się niepraktyczne dla dewelopera WCF do konstruowania typów lokalnych zdefiniowanych przez użytkownika, do których do deserializacji dowolnych obiektów JSON. Ten przykład zawiera mechanizm, który umożliwia deweloperom WCF do pracy z deserializacji, dowolnych obiektów JSON, bez tworzenia typów zdefiniowanych przez użytkownika. Jest to znane jako *słabo typizowane serializacji* obiektów JSON, ponieważ typ, do którego obiekt JSON deserializes nie jest znany w czasie kompilacji.  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Na przykład publiczny interfejs API usługi sieci Web zwraca następujący obiekt JSON, który opisuje niektóre informacje o użytkowniku usługi.  
  
```json  
{"personal": {"name": "Paul", "age": 23, "height": 1.7, "isSingle": true, "luckyNumbers": [5,17,21]}, "favoriteBands": ["Band ABC", "Band XYZ"]}  
```  
  
 Aby zdesializować ten obiekt, klient WCF musi zaimplementować następujące typy zdefiniowane przez użytkownika.  
  
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
  
 Może to być uciążliwe, zwłaszcza jeśli klient ma do obsługi więcej niż jeden typ obiektu JSON.  
  
 Typ `JsonObject` dostarczony przez ten przykład wprowadza słabo typizowane reprezentacji deserialized JSON obiektu. `JsonObject`opiera się na mapowaniu naturalnym między obiektami JSON i słownikami .NET Framework oraz mapowaniem między tablicami JSON i tablicami .NET Framework. Poniższy kod `JsonObject` pokazuje typ.  
  
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
  
 Należy zauważyć, że można "przeglądać" JSON obiektów i tablic bez konieczności deklarowania ich typu w czasie kompilacji. Aby uzyskać wyjaśnienie wymagań dla obiektu `["root"]` najwyższego poziomu, zobacz temat [Mapowanie między JSON i XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).  
  
> [!NOTE]
> Klasa `JsonObject` jest podana tylko jako przykład. Nie został dokładnie przetestowany i nie powinien być stosowany w środowiskach produkcyjnych. Oczywistym implikacją słabo typizowanej serializacji JSON jest brak bezpieczeństwa typu podczas pracy z programem `JsonObject`.  
  
 Aby użyć `JsonObject` tego typu, kontrakt <xref:System.ServiceModel.Channels.Message> operacji klienta musi używać jako jego typu zwracania.  
  
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
  
 Następnie `JsonObject` jest tworzone, jak pokazano w poniższym kodzie.  
  
```csharp  
// Code to instantiate IClientSideProfileService channel omitted…  
  
// Make a request to the service and obtain the Json response  
XmlDictionaryReader reader = channel.GetMemberProfile().GetReaderAtBodyContents();  
  
// Go through the Json as though it is a dictionary. There is no need to map it to a .NET CLR type.  
JsonObject json = new JsonObject(reader);  
```  
  
 Konstruktor `JsonObject` przyjmuje <xref:System.Xml.XmlDictionaryReader>, który jest <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> uzyskiwany za pomocą metody. Czytnik zawiera reprezentację XML wiadomości JSON odebranej przez klienta. Aby uzyskać więcej informacji, zobacz temat [Mapowanie między JSON i XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).  
  
 Program generuje następujące dane wyjściowe:  
  
```console  
Service listening at http://localhost:8000/.  
To view the JSON output from the sample, navigate to http://localhost:8000/GetMemberProfile  
This is Paul's page. I am 23 years old and I am 1.7 meters tall.  
I am single.  
My lucky numbers are 5, 17, and 21.  
My favorite bands are Band ABC and Band XYZ.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Tworzenie rozwiązania WeaklyTypedJson.sln zgodnie z opisem w [tworzenie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Uruchom rozwiązanie.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Ajax\WeaklyTypedJson`  
