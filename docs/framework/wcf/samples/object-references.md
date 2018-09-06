---
title: Odwołania do obiektów
ms.date: 03/30/2017
ms.assetid: 7a93d260-91c3-4448-8f7a-a66fb562fc23
ms.openlocfilehash: 1aa8b1c9d135186dba9e4da75f0c7cb9297d8e5c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43724412"
---
# <a name="object-references"></a><span data-ttu-id="f6f94-102">Odwołania do obiektów</span><span class="sxs-lookup"><span data-stu-id="f6f94-102">Object References</span></span>
<span data-ttu-id="f6f94-103">W tym przykładzie przedstawiono sposób przekazywania obiektów według odwołania między serwerem a klientem.</span><span class="sxs-lookup"><span data-stu-id="f6f94-103">This sample demonstrates how to pass objects by references between server and client.</span></span> <span data-ttu-id="f6f94-104">Zastosowań przykładowe symulowane *sieci społecznościowych*.</span><span class="sxs-lookup"><span data-stu-id="f6f94-104">The sample uses simulated *social networks*.</span></span> <span data-ttu-id="f6f94-105">Sieci społecznościowej składa się z `Person` klasę, która zawiera listy znajomych, w których każdy friend jest wystąpieniem `Person` klasy z listy znajomych.</span><span class="sxs-lookup"><span data-stu-id="f6f94-105">A social network consists of a `Person` class that contains a list of friends in which each friend is an instance of the `Person` class, with its own list of friends.</span></span> <span data-ttu-id="f6f94-106">Spowoduje to utworzenie grafu obiektów.</span><span class="sxs-lookup"><span data-stu-id="f6f94-106">This creates a graph of objects.</span></span> <span data-ttu-id="f6f94-107">Usługa udostępnia operacje w tych sieciach społecznościowych.</span><span class="sxs-lookup"><span data-stu-id="f6f94-107">The service exposes operations on these social networks.</span></span>  
  
 <span data-ttu-id="f6f94-108">W tym przykładzie usługa jest hostowana przez Internetowe usługi informacyjne (IIS), a klient to aplikacja konsoli (.exe).</span><span class="sxs-lookup"><span data-stu-id="f6f94-108">In this sample, the service is hosted by Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f6f94-109">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="f6f94-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="service"></a><span data-ttu-id="f6f94-110">Usługa</span><span class="sxs-lookup"><span data-stu-id="f6f94-110">Service</span></span>  
 <span data-ttu-id="f6f94-111">`Person` Klasa ma <xref:System.Runtime.Serialization.DataContractAttribute> zastosowany, za pomocą <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> pola `true` do deklarowania go jako typu odwołania.</span><span class="sxs-lookup"><span data-stu-id="f6f94-111">The `Person` class has the <xref:System.Runtime.Serialization.DataContractAttribute> attribute applied, with the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> field set to `true` to declare it as a reference type.</span></span> <span data-ttu-id="f6f94-112">Wszystkie właściwości mają <xref:System.Runtime.Serialization.DataMemberAttribute> zastosowany.</span><span class="sxs-lookup"><span data-stu-id="f6f94-112">All properties have the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute applied.</span></span>  
  
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
  
 <span data-ttu-id="f6f94-113">`GetPeopleInNetwork` Operacja przyjmuje parametr typu `Person` i zwraca wszystkie osoby w sieci; oznacza to, że wszystkie osoby w `friends` listy, przyjazne znajomych i tak dalej, bez duplikatów.</span><span class="sxs-lookup"><span data-stu-id="f6f94-113">The `GetPeopleInNetwork` operation takes a parameter of type `Person` and returns all the people in the network; that is, all the people in the `friends` list, the friend's friends, and so on, without duplicates.</span></span>  
  
```  
public List<Person> GetPeopleInNetwork(Person p)  
{  
    List<Person> people = new List<Person>();  
    ListPeopleInNetwork(p, people);  
    return people;  
  
}  
```  
  
 <span data-ttu-id="f6f94-114">`GetMutualFriends` Operacja przyjmuje parametr typu `Person` i zwraca wszystkich znajomych na liście, mających tę osobę w ich `friends` listy.</span><span class="sxs-lookup"><span data-stu-id="f6f94-114">The `GetMutualFriends` operation takes a parameter of type `Person` and returns all the friends in the list who also have this person in their `friends` list.</span></span>  
  
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
  
 <span data-ttu-id="f6f94-115">`GetCommonFriends` Operacja pobiera listę typów `Person`.</span><span class="sxs-lookup"><span data-stu-id="f6f94-115">The `GetCommonFriends` operation takes a list of type `Person`.</span></span> <span data-ttu-id="f6f94-116">Lista powinna mieć dwie `Person` obiektów w nim.</span><span class="sxs-lookup"><span data-stu-id="f6f94-116">The list is expected to have two `Person` objects in it.</span></span> <span data-ttu-id="f6f94-117">Operacja zwraca listę `Person` obiekty, które znajdują się w `friends` wykaz obu `Person` obiekty na liście wejściowej.</span><span class="sxs-lookup"><span data-stu-id="f6f94-117">The operation returns a list of `Person` objects that are in the `friends` lists of both `Person` objects in the input list.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="f6f94-118">Klient</span><span class="sxs-lookup"><span data-stu-id="f6f94-118">Client</span></span>  
 <span data-ttu-id="f6f94-119">Serwer proxy klienta jest tworzony przy użyciu **Dodaj odwołanie do usługi** funkcji programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f6f94-119">The client proxy is created using the **Add Service Reference** feature of Visual Studio.</span></span>  
  
 <span data-ttu-id="f6f94-120">Sieci społecznościowych, która składa się z pięciu `Person` obiekty są tworzone.</span><span class="sxs-lookup"><span data-stu-id="f6f94-120">A social network that consists of five `Person` objects is created.</span></span> <span data-ttu-id="f6f94-121">Klient wywołuje każdą z trzech metod w usłudze.</span><span class="sxs-lookup"><span data-stu-id="f6f94-121">The client calls each of the three methods in the service.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f6f94-122">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="f6f94-122">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="f6f94-123">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f6f94-123">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="f6f94-124">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f6f94-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="f6f94-125">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f6f94-125">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f6f94-126">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="f6f94-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f6f94-127">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="f6f94-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f6f94-128">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="f6f94-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f6f94-129">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="f6f94-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\ObjectReferences`  
  
## <a name="see-also"></a><span data-ttu-id="f6f94-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f6f94-130">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>  
 [<span data-ttu-id="f6f94-131">Odwołania do obiektów międzyoperacyjnych</span><span class="sxs-lookup"><span data-stu-id="f6f94-131">Interoperable Object References</span></span>](../../../../docs/framework/wcf/feature-details/interoperable-object-references.md)
