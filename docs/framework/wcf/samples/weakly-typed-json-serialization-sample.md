---
title: Przykład serializacji kodu JSON ze słabą kontrolą typów
ms.date: 03/30/2017
ms.assetid: 0b30e501-4ef5-474d-9fad-a9d559cf9c52
ms.openlocfilehash: b0e9617ad5d616e8921fbf142085f2758f3e0cd4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59303690"
---
# <a name="weakly-typed-json-serialization-sample"></a>Przykład serializacji kodu JSON ze słabą kontrolą typów
Podczas serializacji typu zdefiniowanego przez użytkownika, do danego formatu, lub deserializację formatu do typu zdefiniowanego przez użytkownika, to danego typu zdefiniowane przez użytkownika muszą być dostępne zarówno usługi, jak i klienta. Zazwyczaj można to osiągnąć, <xref:System.Runtime.Serialization.DataContractAttribute> atrybut jest stosowany do tych typów zdefiniowanych przez użytkownika i <xref:System.Runtime.Serialization.DataMemberAttribute> atrybut jest stosowany do ich elementów członkowskich. Ten mechanizm również stosowana, gdy praca z obiektami JavaScript Object Notation (JSON), zgodnie z opisem w temacie [jak: Serializowanie i Deserializowanie danych JSON](../../../../docs/framework/wcf/feature-details/how-to-serialize-and-deserialize-json-data.md).  
  
 W niektórych scenariuszach usługi Windows Communication Foundation (WCF) lub klienta musi uzyskać dostęp do obiektów JSON generowanych przez usługi lub klienta, który jest poza kontrolą dewelopera. Zgodnie z większej liczby usług sieci Web uwidoczniają publicznie interfejsy API w formacie JSON, może stać się niepraktyczne dla deweloperów usługi WCF do konstruowania lokalnego typy zdefiniowane przez użytkownika, w którym należy wykonać deserializacji dowolne obiekty JSON. W tym przykładzie zapewnia mechanizm, który umożliwia deweloperom WCF do pracy z obiektami JSON po deserializacji, dowolnego bez tworzenia typów zdefiniowanych przez użytkownika. Jest to nazywane *ze słabą kontrolą typów serializacji* obiektów JSON, ponieważ typ, do którego deserializuje obiekt JSON nie jest znany w czasie kompilacji.  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 Na przykład z publicznego interfejsu API usługi sieci Web zwraca następujący obiekt JSON opisano niektóre informacje o użytkowniku usługi.  
  
```json  
{"personal": {"name": "Paul", "age": 23, "height": 1.7, "isSingle": true, "luckyNumbers": [5,17,21]}, "favoriteBands": ["Band ABC", "Band XYZ"]}  
```  
  
 Do deserializacji tego obiektu, klienta programu WCF musi implementować następujących typów zdefiniowanych przez użytkownika.  
  
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
  
 Może to być skomplikowane, zwłaszcza w przypadku, gdy klient musi obsługiwać więcej niż jednego typu obiektu JSON.  
  
 `JsonObject` Typu zawartym w tym przykładzie przedstawiono reprezentację zdeserializowany obiekt JSON ze słabą kontrolą typów. `JsonObject` opiera się na fizyczną mapowanie między obiektami JSON i [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] słowniki i mapowanie między tablice notacji JSON i [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tablic. Poniższy kod przedstawia `JsonObject` typu.  
  
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
  
 Należy pamiętać, że użytkownik może "Przeglądaj" obiekty JSON i tablice bez konieczności zadeklarować ich typem w czasie kompilacji. Wyjaśnienie potrzebę najwyższego poziomu `["root"]` obiektu, zobacz temat [mapowanie między formatami JSON i XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).  
  
> [!NOTE]
>  `JsonObject` Klasy jest dostarczana jako tylko przykładem. Nie została dokładnie przetestowana i nie powinny być używane w środowiskach produkcyjnych. Oczywiste domniemanie serializacja kodu JSON ze słabą kontrolą typów jest brak bezpieczeństwo typów podczas pracy z `JsonObject`.  
  
 Aby użyć `JsonObject` typu, należy użyć kontrakt operacji klienta <xref:System.ServiceModel.Channels.Message> jako jego typem zwracanym.  
  
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
  
 `JsonObject` Konstruktor przyjmuje <xref:System.Xml.XmlDictionaryReader>, jest uzyskiwany za pośrednictwem <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> metody. Czytnik zawiera reprezentację XML komunikat JSON odebranych przez klienta. Aby uzyskać więcej informacji, zobacz temat [mapowanie między formatami JSON i XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).  
  
 Program generuje następujące wyniki:  
  
```  
Service listening at http://localhost:8000/.  
To view the JSON output from the sample, navigate to http://localhost:8000/GetMemberProfile  
This is Paul's page. I am 23 years old and I am 1.7 meters tall.  
I am single.  
My lucky numbers are 5, 17, and 21.  
My favorite bands are Band ABC and Band XYZ.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1. Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Skompiluj rozwiązanie WeaklyTypedJson.sln, zgodnie z opisem w [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Uruchom rozwiązanie.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Ajax\WeaklyTypedJson`  
