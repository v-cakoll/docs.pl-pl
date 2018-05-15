---
title: Odwołania do obiektów
ms.date: 03/30/2017
ms.assetid: 7a93d260-91c3-4448-8f7a-a66fb562fc23
ms.openlocfilehash: 366030cfcbdaa633a1c2f5eb3c9d80bdd7d31ae3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="object-references"></a><span data-ttu-id="1741f-102">Odwołania do obiektów</span><span class="sxs-lookup"><span data-stu-id="1741f-102">Object References</span></span>
<span data-ttu-id="1741f-103">W tym przykładzie pokazano, jak obiekty jest przekazywany za pomocą odwołania między serwerem a klientem.</span><span class="sxs-lookup"><span data-stu-id="1741f-103">This sample demonstrates how to pass objects by references between server and client.</span></span> <span data-ttu-id="1741f-104">Używa próbki symulowane *sieci społecznościowych*.</span><span class="sxs-lookup"><span data-stu-id="1741f-104">The sample uses simulated *social networks*.</span></span> <span data-ttu-id="1741f-105">Sieci społecznościowych składa się z `Person` klasę, która zawiera listę znajomych, w których każdy friend jest wystąpieniem `Person` klasy, z listy znajomych.</span><span class="sxs-lookup"><span data-stu-id="1741f-105">A social network consists of a `Person` class that contains a list of friends in which each friend is an instance of the `Person` class, with its own list of friends.</span></span> <span data-ttu-id="1741f-106">Spowoduje to utworzenie wykresu obiektów.</span><span class="sxs-lookup"><span data-stu-id="1741f-106">This creates a graph of objects.</span></span> <span data-ttu-id="1741f-107">Usługa udostępnia operacje w tych sieciach społecznościowych.</span><span class="sxs-lookup"><span data-stu-id="1741f-107">The service exposes operations on these social networks.</span></span>  
  
 <span data-ttu-id="1741f-108">W tym przykładzie usługa jest obsługiwana przez Internet Information Services (IIS) i klient jest aplikacji konsoli (.exe).</span><span class="sxs-lookup"><span data-stu-id="1741f-108">In this sample, the service is hosted by Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1741f-109">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="1741f-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="service"></a><span data-ttu-id="1741f-110">Usługa</span><span class="sxs-lookup"><span data-stu-id="1741f-110">Service</span></span>  
 <span data-ttu-id="1741f-111">`Person` Klasa ma <xref:System.Runtime.Serialization.DataContractAttribute> atrybut zastosowany, z <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> pole `true` Aby zadeklarować go jako typu referencyjnego.</span><span class="sxs-lookup"><span data-stu-id="1741f-111">The `Person` class has the <xref:System.Runtime.Serialization.DataContractAttribute> attribute applied, with the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> field set to `true` to declare it as a reference type.</span></span> <span data-ttu-id="1741f-112">Wszystkie właściwości mają <xref:System.Runtime.Serialization.DataMemberAttribute> atrybut zastosowany.</span><span class="sxs-lookup"><span data-stu-id="1741f-112">All properties have the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute applied.</span></span>  
  
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
  
 <span data-ttu-id="1741f-113">`GetPeopleInNetwork` Operacji przyjmuje parametr typu `Person` i zwraca wszystkie osoby w sieci; oznacza to, że wszystkie osoby w `friends` listy, znajomych friend i tak dalej, bez duplikaty.</span><span class="sxs-lookup"><span data-stu-id="1741f-113">The `GetPeopleInNetwork` operation takes a parameter of type `Person` and returns all the people in the network; that is, all the people in the `friends` list, the friend's friends, and so on, without duplicates.</span></span>  
  
```  
public List<Person> GetPeopleInNetwork(Person p)  
{  
    List<Person> people = new List<Person>();  
    ListPeopleInNetwork(p, people);  
    return people;  
  
}  
```  
  
 <span data-ttu-id="1741f-114">`GetMutualFriends` Operacji przyjmuje parametr typu `Person` i zwraca wszystkie znajomych na liście mających tej osoby w ich `friends` listy.</span><span class="sxs-lookup"><span data-stu-id="1741f-114">The `GetMutualFriends` operation takes a parameter of type `Person` and returns all the friends in the list who also have this person in their `friends` list.</span></span>  
  
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
  
 <span data-ttu-id="1741f-115">`GetCommonFriends` Operacji przyjmuje listę typu `Person`.</span><span class="sxs-lookup"><span data-stu-id="1741f-115">The `GetCommonFriends` operation takes a list of type `Person`.</span></span> <span data-ttu-id="1741f-116">Listy powinien mieć dwa `Person` obiektów w nim.</span><span class="sxs-lookup"><span data-stu-id="1741f-116">The list is expected to have two `Person` objects in it.</span></span> <span data-ttu-id="1741f-117">Operacja zwraca listę `Person` obiektów, które znajdują się w `friends` list obu `Person` obiekty na liście wejściowej.</span><span class="sxs-lookup"><span data-stu-id="1741f-117">The operation returns a list of `Person` objects that are in the `friends` lists of both `Person` objects in the input list.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="1741f-118">Klient</span><span class="sxs-lookup"><span data-stu-id="1741f-118">Client</span></span>  
 <span data-ttu-id="1741f-119">Serwer proxy klienta jest tworzony przy użyciu **Dodaj odwołanie do usługi** funkcji programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1741f-119">The client proxy is created using the **Add Service Reference** feature of Visual Studio.</span></span>  
  
 <span data-ttu-id="1741f-120">Sieci społecznościowych, która składa się z pięciu `Person` obiekty są tworzone.</span><span class="sxs-lookup"><span data-stu-id="1741f-120">A social network that consists of five `Person` objects is created.</span></span> <span data-ttu-id="1741f-121">Klient wywołuje każdą z trzech metod w usłudze.</span><span class="sxs-lookup"><span data-stu-id="1741f-121">The client calls each of the three methods in the service.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1741f-122">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="1741f-122">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="1741f-123">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1741f-123">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="1741f-124">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1741f-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="1741f-125">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1741f-125">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1741f-126">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="1741f-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1741f-127">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="1741f-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1741f-128">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="1741f-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1741f-129">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="1741f-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\ObjectReferences`  
  
## <a name="see-also"></a><span data-ttu-id="1741f-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1741f-130">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>  
 [<span data-ttu-id="1741f-131">Odwołania do obiektów międzyoperacyjnych</span><span class="sxs-lookup"><span data-stu-id="1741f-131">Interoperable Object References</span></span>](../../../../docs/framework/wcf/feature-details/interoperable-object-references.md)
