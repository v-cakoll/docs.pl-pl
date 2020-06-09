---
title: Odwołania do obiektów
ms.date: 03/30/2017
ms.assetid: 7a93d260-91c3-4448-8f7a-a66fb562fc23
ms.openlocfilehash: ba4ee3fd0cc16130f66570891ecc295b2d2c50aa
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599987"
---
# <a name="object-references"></a>Odwołania do obiektów
Ten przykład ilustruje sposób przekazywania obiektów przez odwołania między serwerem a klientem. Przykład używa symulowanych *sieci społecznościowych*. Sieć społecznościowa składa się z `Person` klasy, która zawiera listę znajomych, w których każdy zaprzyjaźniony jest wystąpieniem `Person` klasy, z własną listą znajomych. Spowoduje to utworzenie grafu obiektów. Usługa ujawnia operacje w tych sieciach społecznościowych.  
  
 W tym przykładzie usługa jest hostowana przez Internet Information Services (IIS), a klient jest aplikacją konsolową (. exe).  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
## <a name="service"></a>Usługa  
 `Person`Klasa ma <xref:System.Runtime.Serialization.DataContractAttribute> zastosowany atrybut, z <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> polem ustawionym na `true` Zadeklaruj go jako typ referencyjny. Wszystkie właściwości mają <xref:System.Runtime.Serialization.DataMemberAttribute> zastosowany atrybut.  
  
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
  
 `GetPeopleInNetwork`Operacja przyjmuje parametr typu `Person` i zwraca wszystkie osoby w sieci, czyli wszystkie osoby znajdujące się na `friends` liście, znajomych zaprzyjaźnionych i tak dalej, bez duplikatów.  
  
```csharp
public List<Person> GetPeopleInNetwork(Person p)  
{  
    List<Person> people = new List<Person>();  
    ListPeopleInNetwork(p, people);  
    return people;  
  
}  
```  
  
 `GetMutualFriends`Operacja przyjmuje parametr typu `Person` i zwraca wszystkich znajomych z listy, którzy posiadają również tę osobę na `friends` liście.  
  
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
  
 `GetCommonFriends`Operacja przyjmuje listę typu `Person` . Lista powinna zawierać dwa `Person` obiekty. Operacja zwraca listę `Person` obiektów, które znajdują się na `friends` listach `Person` obiektów na liście wejściowej.  
  
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
  
 Zostanie utworzona sieć społecznościowa składająca się z pięciu `Person` obiektów. Klient wywołuje każdą z trzech metod w usłudze.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).  
  
3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\ObjectReferences`  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>
- [Odwołania do obiektów międzyoperacyjnych](../feature-details/interoperable-object-references.md)
