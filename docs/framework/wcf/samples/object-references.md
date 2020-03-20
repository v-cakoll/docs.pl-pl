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
# <a name="object-references"></a><span data-ttu-id="e08ff-102">Odwołania do obiektów</span><span class="sxs-lookup"><span data-stu-id="e08ff-102">Object References</span></span>
<span data-ttu-id="e08ff-103">W tym przykładzie pokazano, jak przekazać obiekty przez odwołania między serwerem a klientem.</span><span class="sxs-lookup"><span data-stu-id="e08ff-103">This sample demonstrates how to pass objects by references between server and client.</span></span> <span data-ttu-id="e08ff-104">W przykładzie użyto symulowanych *sieci społecznościowych.*</span><span class="sxs-lookup"><span data-stu-id="e08ff-104">The sample uses simulated *social networks*.</span></span> <span data-ttu-id="e08ff-105">Sieć społecznościowa `Person` składa się z klasy, która zawiera listę znajomych, w których każdy przyjaciel jest wystąpieniem `Person` klasy, z własną listą znajomych.</span><span class="sxs-lookup"><span data-stu-id="e08ff-105">A social network consists of a `Person` class that contains a list of friends in which each friend is an instance of the `Person` class, with its own list of friends.</span></span> <span data-ttu-id="e08ff-106">Spowoduje to utworzenie wykresu obiektów.</span><span class="sxs-lookup"><span data-stu-id="e08ff-106">This creates a graph of objects.</span></span> <span data-ttu-id="e08ff-107">Usługa udostępnia operacje w tych sieciach społecznościowych.</span><span class="sxs-lookup"><span data-stu-id="e08ff-107">The service exposes operations on these social networks.</span></span>  
  
 <span data-ttu-id="e08ff-108">W tym przykładzie usługa jest obsługiwana przez internetowe usługi informacyjne (IIS), a klient jest aplikacją konsoli (.exe).</span><span class="sxs-lookup"><span data-stu-id="e08ff-108">In this sample, the service is hosted by Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e08ff-109">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="e08ff-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="service"></a><span data-ttu-id="e08ff-110">Usługa</span><span class="sxs-lookup"><span data-stu-id="e08ff-110">Service</span></span>  
 <span data-ttu-id="e08ff-111">Klasa `Person` ma <xref:System.Runtime.Serialization.DataContractAttribute> zastosowany atrybut, <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> z polem ustawionym na zadeklarowanie `true` go jako typu odwołania.</span><span class="sxs-lookup"><span data-stu-id="e08ff-111">The `Person` class has the <xref:System.Runtime.Serialization.DataContractAttribute> attribute applied, with the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> field set to `true` to declare it as a reference type.</span></span> <span data-ttu-id="e08ff-112">Wszystkie właściwości mają <xref:System.Runtime.Serialization.DataMemberAttribute> zastosowany atrybut.</span><span class="sxs-lookup"><span data-stu-id="e08ff-112">All properties have the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute applied.</span></span>  
  
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
  
 <span data-ttu-id="e08ff-113">Operacja `GetPeopleInNetwork` przyjmuje parametr typu `Person` i zwraca wszystkie osoby w sieci; oznacza to, że wszyscy `friends` ludzie na liście, przyjaciele przyjaciela i tak dalej, bez duplikatów.</span><span class="sxs-lookup"><span data-stu-id="e08ff-113">The `GetPeopleInNetwork` operation takes a parameter of type `Person` and returns all the people in the network; that is, all the people in the `friends` list, the friend's friends, and so on, without duplicates.</span></span>  
  
```csharp
public List<Person> GetPeopleInNetwork(Person p)  
{  
    List<Person> people = new List<Person>();  
    ListPeopleInNetwork(p, people);  
    return people;  
  
}  
```  
  
 <span data-ttu-id="e08ff-114">Operacja `GetMutualFriends` przyjmuje parametr typu `Person` i zwraca wszystkich znajomych na liście, `friends` którzy również mają tę osobę na swojej liście.</span><span class="sxs-lookup"><span data-stu-id="e08ff-114">The `GetMutualFriends` operation takes a parameter of type `Person` and returns all the friends in the list who also have this person in their `friends` list.</span></span>  
  
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
  
 <span data-ttu-id="e08ff-115">Operacja `GetCommonFriends` przyjmuje listę typu `Person`.</span><span class="sxs-lookup"><span data-stu-id="e08ff-115">The `GetCommonFriends` operation takes a list of type `Person`.</span></span> <span data-ttu-id="e08ff-116">Oczekuje się, że `Person` lista będzie miała dwa obiekty.</span><span class="sxs-lookup"><span data-stu-id="e08ff-116">The list is expected to have two `Person` objects in it.</span></span> <span data-ttu-id="e08ff-117">Operacja zwraca listę `Person` obiektów, które `friends` znajdują się `Person` na listach obu obiektów na liście wejściowej.</span><span class="sxs-lookup"><span data-stu-id="e08ff-117">The operation returns a list of `Person` objects that are in the `friends` lists of both `Person` objects in the input list.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="e08ff-118">Klient</span><span class="sxs-lookup"><span data-stu-id="e08ff-118">Client</span></span>  
 <span data-ttu-id="e08ff-119">Serwer proxy klienta jest tworzony przy użyciu funkcji **Dodaj odwołanie do usługi** programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e08ff-119">The client proxy is created using the **Add Service Reference** feature of Visual Studio.</span></span>  
  
 <span data-ttu-id="e08ff-120">Tworzona jest sieć `Person` społecznościowa, która składa się z pięciu obiektów.</span><span class="sxs-lookup"><span data-stu-id="e08ff-120">A social network that consists of five `Person` objects is created.</span></span> <span data-ttu-id="e08ff-121">Klient wywołuje każdą z trzech metod w usłudze.</span><span class="sxs-lookup"><span data-stu-id="e08ff-121">The client calls each of the three methods in the service.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e08ff-122">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="e08ff-122">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e08ff-123">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e08ff-123">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="e08ff-124">Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e08ff-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="e08ff-125">Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e08ff-125">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e08ff-126">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="e08ff-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e08ff-127">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="e08ff-127">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="e08ff-128">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="e08ff-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e08ff-129">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="e08ff-129">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\ObjectReferences`  
  
## <a name="see-also"></a><span data-ttu-id="e08ff-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e08ff-130">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>
- [<span data-ttu-id="e08ff-131">Odwołania do obiektów międzyoperacyjnych</span><span class="sxs-lookup"><span data-stu-id="e08ff-131">Interoperable Object References</span></span>](../../../../docs/framework/wcf/feature-details/interoperable-object-references.md)
