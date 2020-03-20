---
title: Odwołania do obiektów
ms.date: 03/30/2017
ms.assetid: 7a93d260-91c3-4448-8f7a-a66fb562fc23
ms.openlocfilehash: 5eb842e1bff9ba60074379fde5ef3d0597f2184e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183459"
---
# <a name="object-references"></a>Odwołania do obiektów
W tym przykładzie pokazano, jak przekazać obiekty przez odwołania między serwerem a klientem. W przykładzie użyto symulowanych *sieci społecznościowych.* Sieć społecznościowa `Person` składa się z klasy, która zawiera listę znajomych, w których każdy przyjaciel jest wystąpieniem `Person` klasy, z własną listą znajomych. Spowoduje to utworzenie wykresu obiektów. Usługa udostępnia operacje w tych sieciach społecznościowych.  
  
 W tym przykładzie usługa jest obsługiwana przez internetowe usługi informacyjne (IIS), a klient jest aplikacją konsoli (.exe).  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
## <a name="service"></a>Usługa  
 Klasa `Person` ma <xref:System.Runtime.Serialization.DataContractAttribute> zastosowany atrybut, <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> z polem ustawionym na zadeklarowanie `true` go jako typu odwołania. Wszystkie właściwości mają <xref:System.Runtime.Serialization.DataMemberAttribute> zastosowany atrybut.  
  
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
  
 Operacja `GetPeopleInNetwork` przyjmuje parametr typu `Person` i zwraca wszystkie osoby w sieci; oznacza to, że wszyscy `friends` ludzie na liście, przyjaciele przyjaciela i tak dalej, bez duplikatów.  
  
```csharp
public List<Person> GetPeopleInNetwork(Person p)  
{  
    List<Person> people = new List<Person>();  
    ListPeopleInNetwork(p, people);  
    return people;  
  
}  
```  
  
 Operacja `GetMutualFriends` przyjmuje parametr typu `Person` i zwraca wszystkich znajomych na liście, `friends` którzy również mają tę osobę na swojej liście.  
  
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
  
 Operacja `GetCommonFriends` przyjmuje listę typu `Person`. Oczekuje się, że `Person` lista będzie miała dwa obiekty. Operacja zwraca listę `Person` obiektów, które `friends` znajdują się `Person` na listach obu obiektów na liście wejściowej.  
  
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
  
 Tworzona jest sieć `Person` społecznościowa, która składa się z pięciu obiektów. Klient wywołuje każdą z trzech metod w usłudze.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\ObjectReferences`  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>
- [Odwołania do obiektów międzyoperacyjnych](../../../../docs/framework/wcf/feature-details/interoperable-object-references.md)
