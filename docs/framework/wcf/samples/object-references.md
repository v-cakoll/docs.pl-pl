---
title: Odwołania do obiektów
ms.date: 03/30/2017
ms.assetid: 7a93d260-91c3-4448-8f7a-a66fb562fc23
ms.openlocfilehash: bc9c318fc0e05f384a00df7cd1436a138315d880
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714681"
---
# <a name="object-references"></a>Odwołania do obiektów
Ten przykład ilustruje sposób przekazywania obiektów przez odwołania między serwerem a klientem. Przykład używa symulowanych *sieci społecznościowych*. Sieć społecznościowa składa się z klasy `Person`, która zawiera listę znajomych, w których każdy zaprzyjaźniony jest wystąpieniem klasy `Person`, z własną listą znajomych. Spowoduje to utworzenie grafu obiektów. Usługa ujawnia operacje w tych sieciach społecznościowych.  
  
 W tym przykładzie usługa jest hostowana przez Internet Information Services (IIS), a klient jest aplikacją konsolową (. exe).  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
## <a name="service"></a>NDES  
 Klasa `Person` ma zastosowany atrybut <xref:System.Runtime.Serialization.DataContractAttribute> z <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> polem ustawionym na `true`, aby zadeklarować go jako typ referencyjny. Wszystkie właściwości mają zastosowany atrybut <xref:System.Runtime.Serialization.DataMemberAttribute>.  
  
```csharp
[DataContract(IsReference=true)]  
public class Person  
{  
    string name;  
    string location;  
    string gender;  
    int age;  
    List<Person> friends;  
    [DataMember()]  
    public string Name  
    {  
        get { return name; }  
        set { name = value; }  
    }  
    [DataMember()]  
    public string Location  
    {  
        get { return location; }  
        set { location = value; }  
    }  
    [DataMember()]  
    public string Gender  
    {  
        get { return gender; }  
        set { gender = value; }  
    }  
…  
}  
```  
  
 Operacja `GetPeopleInNetwork` przyjmuje parametr typu `Person` i zwraca wszystkie osoby w sieci; oznacza to, że wszystkie osoby znajdujące się na liście `friends`, znajomych przyjaciela i tak dalej, bez duplikatów.  
  
```csharp
public List<Person> GetPeopleInNetwork(Person p)  
{  
    List<Person> people = new List<Person>();  
    ListPeopleInNetwork(p, people);  
    return people;  
  
}  
```  
  
 Operacja `GetMutualFriends` przyjmuje parametr typu `Person` i zwraca wszystkich znajomych z listy, którzy posiadają również tę osobę na liście `friends`.  
  
```csharp
public List<Person> GetMutualFriends(Person p)  
{  
    List<Person> mutual = new List<Person>();  
    foreach (Person friend in p.Friends)  
    {  
        if (friend.Friends.Contains(p))  
            mutual.Add(friend);  
    }  
    return mutual;  
}  
```  
  
 Operacja `GetCommonFriends` pobiera listę `Person`typu. Lista powinna zawierać dwa `Person` obiektów. Operacja zwraca listę obiektów `Person`, które znajdują się na listach `friends` obu `Person` obiektów na liście wejściowej.  
  
```csharp
public List<Person> GetCommonFriends(List<Person> people)  
{  
    List<Person> common = new List<Person>();  
    foreach (Person friend in people[0].Friends)  
        if (people[1].Friends.Contains(friend))  
            common.Add(friend);  
    return common;  
}  
```  
  
## <a name="client"></a>Klient  
 Serwer proxy klienta jest tworzony przy użyciu funkcji **Dodaj odwołanie do usługi** programu Visual Studio.  
  
 Zostanie utworzona sieć społecznościowa, która składa się z pięciu `Person` obiektów. Klient wywołuje każdą z trzech metod w usłudze.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\ObjectReferences`  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>
- [Odwołania do obiektów międzyoperacyjnych](../../../../docs/framework/wcf/feature-details/interoperable-object-references.md)
