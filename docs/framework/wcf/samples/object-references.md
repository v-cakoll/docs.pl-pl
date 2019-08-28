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
# <a name="object-references"></a><span data-ttu-id="549e1-102">Odwołania do obiektów</span><span class="sxs-lookup"><span data-stu-id="549e1-102">Object References</span></span>
<span data-ttu-id="549e1-103">Ten przykład ilustruje sposób przekazywania obiektów przez odwołania między serwerem a klientem.</span><span class="sxs-lookup"><span data-stu-id="549e1-103">This sample demonstrates how to pass objects by references between server and client.</span></span> <span data-ttu-id="549e1-104">Przykład używa symulowanych *sieci społecznościowych*.</span><span class="sxs-lookup"><span data-stu-id="549e1-104">The sample uses simulated *social networks*.</span></span> <span data-ttu-id="549e1-105">Sieć społecznościowa składa się `Person` z klasy, która zawiera listę znajomych, w których każdy zaprzyjaźniony jest wystąpieniem `Person` klasy, z własną listą znajomych.</span><span class="sxs-lookup"><span data-stu-id="549e1-105">A social network consists of a `Person` class that contains a list of friends in which each friend is an instance of the `Person` class, with its own list of friends.</span></span> <span data-ttu-id="549e1-106">Spowoduje to utworzenie grafu obiektów.</span><span class="sxs-lookup"><span data-stu-id="549e1-106">This creates a graph of objects.</span></span> <span data-ttu-id="549e1-107">Usługa ujawnia operacje w tych sieciach społecznościowych.</span><span class="sxs-lookup"><span data-stu-id="549e1-107">The service exposes operations on these social networks.</span></span>  
  
 <span data-ttu-id="549e1-108">W tym przykładzie usługa jest hostowana przez Internet Information Services (IIS), a klient jest aplikacją konsolową (. exe).</span><span class="sxs-lookup"><span data-stu-id="549e1-108">In this sample, the service is hosted by Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="549e1-109">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="549e1-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="service"></a><span data-ttu-id="549e1-110">Usługa</span><span class="sxs-lookup"><span data-stu-id="549e1-110">Service</span></span>  
 <span data-ttu-id="549e1-111">Klasa ma zastosowany<xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> atrybut ,`true` z polem ustawionym na Zadeklaruj go jako typ referencyjny. <xref:System.Runtime.Serialization.DataContractAttribute> `Person`</span><span class="sxs-lookup"><span data-stu-id="549e1-111">The `Person` class has the <xref:System.Runtime.Serialization.DataContractAttribute> attribute applied, with the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> field set to `true` to declare it as a reference type.</span></span> <span data-ttu-id="549e1-112">Wszystkie właściwości mają <xref:System.Runtime.Serialization.DataMemberAttribute> zastosowany atrybut.</span><span class="sxs-lookup"><span data-stu-id="549e1-112">All properties have the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute applied.</span></span>  
  
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
  
 <span data-ttu-id="549e1-113">Operacja przyjmuje parametr typu `Person` i zwraca wszystkie osoby w sieci, czyli `friends` wszystkie osoby znajdujące się na liście, znajomych zaprzyjaźnionych i tak dalej, bez duplikatów. `GetPeopleInNetwork`</span><span class="sxs-lookup"><span data-stu-id="549e1-113">The `GetPeopleInNetwork` operation takes a parameter of type `Person` and returns all the people in the network; that is, all the people in the `friends` list, the friend's friends, and so on, without duplicates.</span></span>  
  
```csharp
public List<Person> GetPeopleInNetwork(Person p)  
{  
    List<Person> people = new List<Person>();  
    ListPeopleInNetwork(p, people);  
    return people;  
  
}  
```  
  
 <span data-ttu-id="549e1-114">Operacja przyjmuje parametr typu `Person` i zwraca wszystkich znajomych z listy, którzy `friends` posiadają również tę osobę na liście. `GetMutualFriends`</span><span class="sxs-lookup"><span data-stu-id="549e1-114">The `GetMutualFriends` operation takes a parameter of type `Person` and returns all the friends in the list who also have this person in their `friends` list.</span></span>  
  
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
  
 <span data-ttu-id="549e1-115">Operacja przyjmuje listę typu `Person`. `GetCommonFriends`</span><span class="sxs-lookup"><span data-stu-id="549e1-115">The `GetCommonFriends` operation takes a list of type `Person`.</span></span> <span data-ttu-id="549e1-116">Lista powinna zawierać dwa `Person` obiekty.</span><span class="sxs-lookup"><span data-stu-id="549e1-116">The list is expected to have two `Person` objects in it.</span></span> <span data-ttu-id="549e1-117">Operacja zwraca listę `Person` obiektów, które znajdują się `friends` na listach `Person` obiektów na liście wejściowej.</span><span class="sxs-lookup"><span data-stu-id="549e1-117">The operation returns a list of `Person` objects that are in the `friends` lists of both `Person` objects in the input list.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="549e1-118">Klient</span><span class="sxs-lookup"><span data-stu-id="549e1-118">Client</span></span>  
 <span data-ttu-id="549e1-119">Serwer proxy klienta jest tworzony przy użyciu funkcji **Dodaj odwołanie do usługi** programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="549e1-119">The client proxy is created using the **Add Service Reference** feature of Visual Studio.</span></span>  
  
 <span data-ttu-id="549e1-120">Zostanie utworzona sieć społecznościowa składająca `Person` się z pięciu obiektów.</span><span class="sxs-lookup"><span data-stu-id="549e1-120">A social network that consists of five `Person` objects is created.</span></span> <span data-ttu-id="549e1-121">Klient wywołuje każdą z trzech metod w usłudze.</span><span class="sxs-lookup"><span data-stu-id="549e1-121">The client calls each of the three methods in the service.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="549e1-122">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="549e1-122">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="549e1-123">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="549e1-123">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="549e1-124">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="549e1-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="549e1-125">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="549e1-125">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="549e1-126">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="549e1-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="549e1-127">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="549e1-127">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="549e1-128">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="549e1-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="549e1-129">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="549e1-129">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\ObjectReferences`  
  
## <a name="see-also"></a><span data-ttu-id="549e1-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="549e1-130">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>
- [<span data-ttu-id="549e1-131">Odwołania do obiektów międzyoperacyjnych</span><span class="sxs-lookup"><span data-stu-id="549e1-131">Interoperable Object References</span></span>](../../../../docs/framework/wcf/feature-details/interoperable-object-references.md)
