---
title: Odwołania do obiektów
ms.date: 03/30/2017
ms.assetid: 7a93d260-91c3-4448-8f7a-a66fb562fc23
ms.openlocfilehash: 1aa8b1c9d135186dba9e4da75f0c7cb9297d8e5c
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46000245"
---
# <a name="object-references"></a>Odwołania do obiektów
W tym przykładzie przedstawiono sposób przekazywania obiektów według odwołania między serwerem a klientem. Zastosowań przykładowe symulowane *sieci społecznościowych*. Sieci społecznościowej składa się z `Person` klasę, która zawiera listy znajomych, w których każdy friend jest wystąpieniem `Person` klasy z listy znajomych. Spowoduje to utworzenie grafu obiektów. Usługa udostępnia operacje w tych sieciach społecznościowych.  
  
 W tym przykładzie usługa jest hostowana przez Internetowe usługi informacyjne (IIS), a klient to aplikacja konsoli (.exe).  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
## <a name="service"></a>Usługa  
 `Person` Klasa ma <xref:System.Runtime.Serialization.DataContractAttribute> zastosowany, za pomocą <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> pola `true` do deklarowania go jako typu odwołania. Wszystkie właściwości mają <xref:System.Runtime.Serialization.DataMemberAttribute> zastosowany.  
  
```  
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
  
 `GetPeopleInNetwork` Operacja przyjmuje parametr typu `Person` i zwraca wszystkie osoby w sieci; oznacza to, że wszystkie osoby w `friends` listy, przyjazne znajomych i tak dalej, bez duplikatów.  
  
```  
public List<Person> GetPeopleInNetwork(Person p)  
{  
    List<Person> people = new List<Person>();  
    ListPeopleInNetwork(p, people);  
    return people;  
  
}  
```  
  
 `GetMutualFriends` Operacja przyjmuje parametr typu `Person` i zwraca wszystkich znajomych na liście, mających tę osobę w ich `friends` listy.  
  
```  
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
  
 `GetCommonFriends` Operacja pobiera listę typów `Person`. Lista powinna mieć dwie `Person` obiektów w nim. Operacja zwraca listę `Person` obiekty, które znajdują się w `friends` wykaz obu `Person` obiekty na liście wejściowej.  
  
```  
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
 Serwer proxy klienta jest tworzony przy użyciu **Dodaj odwołanie do usługi** funkcji programu Visual Studio.  
  
 Sieci społecznościowych, która składa się z pięciu `Person` obiekty są tworzone. Klient wywołuje każdą z trzech metod w usłudze.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\ObjectReferences`  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>  
 [Odwołania do obiektów międzyoperacyjnych](../../../../docs/framework/wcf/feature-details/interoperable-object-references.md)
