---
title: Odwołania do obiektów
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7a93d260-91c3-4448-8f7a-a66fb562fc23
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fcb34efeb7eed28f85774dc5489b3e56aeac4e6c
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="object-references"></a>Odwołania do obiektów
W tym przykładzie pokazano, jak obiekty jest przekazywany za pomocą odwołania między serwerem a klientem. Używa próbki symulowane *sieci społecznościowych*. Sieci społecznościowych składa się z `Person` klasę, która zawiera listę znajomych, w których każdy friend jest wystąpieniem `Person` klasy, z listy znajomych. Spowoduje to utworzenie wykresu obiektów. Usługa udostępnia operacje w tych sieciach społecznościowych.  
  
 W tym przykładzie usługa jest obsługiwana przez Internet Information Services (IIS) i klient jest aplikacji konsoli (.exe).  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
## <a name="service"></a>Usługa  
 `Person` Klasa ma <xref:System.Runtime.Serialization.DataContractAttribute> atrybut zastosowany, z <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> pole `true` Aby zadeklarować go jako typu referencyjnego. Wszystkie właściwości mają <xref:System.Runtime.Serialization.DataMemberAttribute> atrybut zastosowany.  
  
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
  
 `GetPeopleInNetwork` Operacji przyjmuje parametr typu `Person` i zwraca wszystkie osoby w sieci; oznacza to, że wszystkie osoby w `friends` listy, znajomych friend i tak dalej, bez duplikaty.  
  
```  
public List<Person> GetPeopleInNetwork(Person p)  
{  
    List<Person> people = new List<Person>();  
    ListPeopleInNetwork(p, people);  
    return people;  
  
}  
```  
  
 `GetMutualFriends` Operacji przyjmuje parametr typu `Person` i zwraca wszystkie znajomych na liście mających tej osoby w ich `friends` listy.  
  
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
  
 `GetCommonFriends` Operacji przyjmuje listę typu `Person`. Listy powinien mieć dwa `Person` obiektów w nim. Operacja zwraca listę `Person` obiektów, które znajdują się w `friends` list obu `Person` obiekty na liście wejściowej.  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\ObjectReferences`  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>  
 [Odwołania do obiektów międzyoperacyjnych](../../../../docs/framework/wcf/feature-details/interoperable-object-references.md)
