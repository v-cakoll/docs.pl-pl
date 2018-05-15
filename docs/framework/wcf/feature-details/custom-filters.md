---
title: Filtry niestandardowe
ms.date: 03/30/2017
ms.assetid: 97cf247d-be0a-4057-bba9-3be5c45029d5
ms.openlocfilehash: 4140a944ed195e1defc1a0677d8e26ff4ff85beb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="custom-filters"></a><span data-ttu-id="c1753-102">Filtry niestandardowe</span><span class="sxs-lookup"><span data-stu-id="c1753-102">Custom Filters</span></span>
<span data-ttu-id="c1753-103">Filtry niestandardowe umożliwiają definiowanie pasującego logikę, która nie może być wykonywane przy użyciu filtrów dostarczane przez system komunikatu.</span><span class="sxs-lookup"><span data-stu-id="c1753-103">Custom filters allow you to define matching logic that cannot be accomplished using the system-provided message filters.</span></span> <span data-ttu-id="c1753-104">Na przykład możesz utworzyć niestandardowy filtr, który tworzy skrót elementu określonego komunikatu, a następnie sprawdza, czy wartość, aby ustalić, czy filtr powinien zwrócić wartość true lub false.</span><span class="sxs-lookup"><span data-stu-id="c1753-104">For example, you might create a custom filter that hashes a particular message element and then examines the value to determine whether the filter should return true or false.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="c1753-105">Implementacja</span><span class="sxs-lookup"><span data-stu-id="c1753-105">Implementation</span></span>  
 <span data-ttu-id="c1753-106">Filtr niestandardowy jest implementacją <xref:System.ServiceModel.Dispatcher.MessageFilter> abstrakcyjnej klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="c1753-106">A custom filter is an implementation of the <xref:System.ServiceModel.Dispatcher.MessageFilter> abstract base class.</span></span> <span data-ttu-id="c1753-107">Podczas implementowania niestandardowych filtru, konstruktora opcjonalnie może akceptować parametr będący pojedynczym ciągiem.</span><span class="sxs-lookup"><span data-stu-id="c1753-107">When implementing your custom filter, the constructor can optionally accept a single string parameter.</span></span> <span data-ttu-id="c1753-108">Ten parametr zawiera informacje o konfiguracji, który jest przekazany do konstruktora MessageFilter w celu zapewnienia wszystkie wartości lub konfiguracji, który wymaga filtr w czasie wykonywania, aby wykonać jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="c1753-108">This parameter contains the configuration information that is passed to the MessageFilter constructor in order to provide any values or configuration that the filter needs at runtime in order to perform matches.</span></span> <span data-ttu-id="c1753-109">Na przykład to może służyć do zapewnienia wartość filtru wyszukuje w komunikacie oceniane.</span><span class="sxs-lookup"><span data-stu-id="c1753-109">For example, this might be used to provide a value that the filter looks for within the message being evaluated.</span></span> <span data-ttu-id="c1753-110">W poniższym przykładzie pokazano Podstawowa implementacja filtr niestandardowy komunikat, który akceptuje parametr typu string:</span><span class="sxs-lookup"><span data-stu-id="c1753-110">The following example demonstrates a basic implementation of a custom message filter that accepts a string parameter:</span></span>  
  
```csharp  
public class MyMessageFilter: MessageFilter  
{  
    string filterData;  
    public MyMessageFilter(string filterData)  
    {  
        if(string.IsNullOrEmpty(filterData)  
            throw new ArgumentNullException("filterData");  
        this.filterData=filterData;  
    }  
    public override bool Match(System.ServiceModel.Channels.Message message)  
    {  
        ...  
        return retValue;  
    }  
    public override bool Match(System.ServiceModel.Channels.MessageBuffer buffer)  
    {  
        ...  
        return retValue;  
    }  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="c1753-111">W rzeczywistych implementacji metody dopasowania zawiera logikę, która zbada komunikatu, aby określić, czy ten filtr komunikatu powinien zwrócić **true** lub **false**.</span><span class="sxs-lookup"><span data-stu-id="c1753-111">In an actual implementation, the Match method(s) contains logic that will examine the message to determine if this message filter should return **true** or **false**.</span></span>  
  
### <a name="performance"></a><span data-ttu-id="c1753-112">Wydajność</span><span class="sxs-lookup"><span data-stu-id="c1753-112">Performance</span></span>  
 <span data-ttu-id="c1753-113">Podczas implementowania niestandardowego filtru, należy wziąć pod uwagę maksymalnego czasu wymaganego do filtr, aby ukończyć obliczania komunikatu.</span><span class="sxs-lookup"><span data-stu-id="c1753-113">When implementing a custom filter, it is important to take into consideration the maximum length of time required for the filter to complete the evaluation of a message.</span></span> <span data-ttu-id="c1753-114">Ponieważ komunikat może zostać oceniona pod kątem wielu filtrów, zanim zostanie znaleziony odpowiednik, jest ważne upewnić się, czy żądanie klienta jest nie upłynął limit czasu, zanim wszystkie filtry, które może przyjąć.</span><span class="sxs-lookup"><span data-stu-id="c1753-114">Since a message may be evaluated against multiple filters before a match is found, it is important to ensure that the client request does not time out before all filters can be evaluated.</span></span> <span data-ttu-id="c1753-115">W związku z tym niestandardowego filtru powinien zawierać tylko kod niezbędnych do oceny zawartości lub atrybutów komunikatu w celu określenia, czy jego kryteria filtru.</span><span class="sxs-lookup"><span data-stu-id="c1753-115">Therefore a custom filter should contain only the code necessary to evaluate the contents or attributes of a message in order to determine if it matches the filter criteria.</span></span>  
  
 <span data-ttu-id="c1753-116">Ogólnie rzecz biorąc należy unikać następujące podczas implementowania niestandardowego filtru:</span><span class="sxs-lookup"><span data-stu-id="c1753-116">In general, you should avoid the following when implementing a custom filter:</span></span>  
  
-   <span data-ttu-id="c1753-117">We/Wy, takich jak zapisywania danych na dysku lub z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="c1753-117">IO, such as saving data to disk or to a database.</span></span>  
  
-   <span data-ttu-id="c1753-118">Niepotrzebny przetwarzania, takich jak pętli wielu rekordów w dokumencie.</span><span class="sxs-lookup"><span data-stu-id="c1753-118">Unnecessary processing, such as looping over multiple records in a document.</span></span>  
  
-   <span data-ttu-id="c1753-119">Blokowanie operacji, takich jak wywołania, które wymagają uzyskania blokady na udostępnionych zasobów lub wykonywania wyszukiwania w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="c1753-119">Blocking operations, such as calls that involve obtaining a lock on shared resources or performing lookups against a database.</span></span>  
  
 <span data-ttu-id="c1753-120">Aby można było używać niestandardowego filtru w środowisku produkcyjnym, należy uruchomić testy wydajności w celu ustalenia średnią długość czasu, który przyjmuje filtr do oceny wiadomości.</span><span class="sxs-lookup"><span data-stu-id="c1753-120">Before using a custom filter in a production environment, you should run performance tests to determine the average length of time that the filter takes to evaluate a message.</span></span> <span data-ttu-id="c1753-121">W połączeniu z Średni czas przetwarzania inne filtry w tabeli filtrów, to umożliwi dokładnie określić wartości maksymalny limit czasu, który powinien być określony przez aplikację klienta.</span><span class="sxs-lookup"><span data-stu-id="c1753-121">When combined with the average processing time of the other filters used in the filter table, this will allow you to accurately determine the maximum timeout value that should be specified by the client application.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="c1753-122">Użycie</span><span class="sxs-lookup"><span data-stu-id="c1753-122">Usage</span></span>  
 <span data-ttu-id="c1753-123">Aby można było używać niestandardowego filtru z usługą routingu, należy dodać go do tabeli filtrów, określając nowy wpis filtru typu "Niestandardowy" pełni kwalifikowana nazwa typu filtru komunikatów, a nazwa z zestawu.</span><span class="sxs-lookup"><span data-stu-id="c1753-123">In order to use your custom filter with the Routing Service, you must add it to the filter table by specifying a new filter entry of type "Custom," the fully qualified type name of the message filter, and the name of your assembly.</span></span>  <span data-ttu-id="c1753-124">Podobnie jak w przypadku innych MessageFilters można określić danych ciąg filtru, który zostanie przekazany do konstruktora filtru niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="c1753-124">As with other MessageFilters, you can specify the string filterData that will be passed to your custom filter’s constructor.</span></span>  
  
 <span data-ttu-id="c1753-125">W poniższych przykładach pokazano, w usłudze Routing przy użyciu niestandardowego filtru:</span><span class="sxs-lookup"><span data-stu-id="c1753-125">The following examples demonstrate using a custom filter with the Routing Service:</span></span>  
  
```xml  
<!--ROUTING SECTION -->  
<routing>  
  <filters>  
    <filter name="CustomFilter1" filterType="Custom"   
            customType="CustomAssembly.MyMessageFilter,   
            CustomAssembly" filterData="custom data" />  
  </filters>  
  <filterTables>  
    <table name="routingTable1">  
      <filters>  
        <add filterName="CustomFilter1" endpointName="CalculatorService" />  
      </filters>  
    </table>  
  </filterTables>  
</routing>  
```  
  
```csharp  
RoutingConfiguration rc = new RoutingConfiguration();  
List<ServiceEndpoint> endpointList = new List<ServiceEndpoint>();  
endpointList.Add(client);  
rc.FilterTable.Add(new MyMessageFilter("CustomData"), endpointList);  
```
