---
title: Odwołania do obiektów
ms.date: 03/30/2017
ms.assetid: 7a93d260-91c3-4448-8f7a-a66fb562fc23
ms.openlocfilehash: f82ebe741c2deaccb3bd6593c7b4f53a646582dd
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039148"
---
# <a name="object-references"></a>Odwołania do obiektów
Ten przykład ilustruje sposób przekazywania obiektów przez odwołania między serwerem a klientem. Przykład używa symulowanych *sieci społecznościowych*. Sieć społecznościowa składa się `Person` z klasy, która zawiera listę znajomych, w których każdy zaprzyjaźniony jest wystąpieniem `Person` klasy, z własną listą znajomych. Spowoduje to utworzenie grafu obiektów. Usługa ujawnia operacje w tych sieciach społecznościowych.  
  
 W tym przykładzie usługa jest hostowana przez Internet Information Services (IIS), a klient jest aplikacją konsolową (. exe).  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
## <a name="service"></a>Usługa  
 Klasa ma zastosowany<xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> atrybut ,`true` z polem ustawionym na Zadeklaruj go jako typ referencyjny. <xref:System.Runtime.Serialization.DataContractAttribute> `Person` Wszystkie właściwości mają <xref:System.Runtime.Serialization.DataMemberAttribute> zastosowany atrybut.  
  
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
  
 Operacja przyjmuje parametr typu `Person` i zwraca wszystkie osoby w sieci, czyli `friends` wszystkie osoby znajdujące się na liście, znajomych zaprzyjaźnionych i tak dalej, bez duplikatów. `GetPeopleInNetwork`  
  
```csharp
public List<Person> GetPeopleInNetwork(Person p)  
{  
    List<Person> people = new List<Person>();  
    ListPeopleInNetwork(p, people);  
    return people;  
  
}  
```  
  
 Operacja przyjmuje parametr typu `Person` i zwraca wszystkich znajomych z listy, którzy `friends` posiadają również tę osobę na liście. `GetMutualFriends`  
  
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
  
 Operacja przyjmuje listę typu `Person`. `GetCommonFriends` Lista powinna zawierać dwa `Person` obiekty. Operacja zwraca listę `Person` obiektów, które znajdują się `friends` na listach `Person` obiektów na liście wejściowej.  
  
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
  
 Zostanie utworzona sieć społecznościowa składająca `Person` się z pięciu obiektów. Klient wywołuje każdą z trzech metod w usłudze.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\ObjectReferences`  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>
- [Odwołania do obiektów międzyoperacyjnych](../../../../docs/framework/wcf/feature-details/interoperable-object-references.md)
