---
title: Filtry niestandardowe
ms.date: 03/30/2017
ms.assetid: 97cf247d-be0a-4057-bba9-3be5c45029d5
ms.openlocfilehash: 9ef94d95737fb743af56f411bcc0f39ceea679a0
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2019
ms.locfileid: "64912688"
---
# <a name="custom-filters"></a><span data-ttu-id="791f6-102">Filtry niestandardowe</span><span class="sxs-lookup"><span data-stu-id="791f6-102">Custom Filters</span></span>
<span data-ttu-id="791f6-103">Filtry niestandardowe umożliwiają zdefiniowanie pasującego logiki, która nie da się osiągnąć przy użyciu filtrów dostarczane przez system komunikatu.</span><span class="sxs-lookup"><span data-stu-id="791f6-103">Custom filters allow you to define matching logic that cannot be accomplished using the system-provided message filters.</span></span> <span data-ttu-id="791f6-104">Na przykład utworzyć filtr niestandardowy, który wyznacza wartość skrótu elementu określoną wiadomość, a następnie sprawdza, czy wartość do określenia, czy filtr ma zwracać wartość PRAWDA lub FAŁSZ.</span><span class="sxs-lookup"><span data-stu-id="791f6-104">For example, you might create a custom filter that hashes a particular message element and then examines the value to determine whether the filter should return true or false.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="791f6-105">Implementacja</span><span class="sxs-lookup"><span data-stu-id="791f6-105">Implementation</span></span>  
 <span data-ttu-id="791f6-106">Filtr niestandardowy jest implementacją <xref:System.ServiceModel.Dispatcher.MessageFilter> abstrakcyjna klasa bazowa.</span><span class="sxs-lookup"><span data-stu-id="791f6-106">A custom filter is an implementation of the <xref:System.ServiceModel.Dispatcher.MessageFilter> abstract base class.</span></span> <span data-ttu-id="791f6-107">Podczas implementowania niestandardowego filtru, Konstruktor opcjonalnie może akceptować jeden ciąg znaków.</span><span class="sxs-lookup"><span data-stu-id="791f6-107">When implementing your custom filter, the constructor can optionally accept a single string parameter.</span></span> <span data-ttu-id="791f6-108">Ten parametr zawiera informacje o konfiguracji, który jest przekazywany do konstruktora MessageFilter w celu zapewnienia, że odpowiada wartości lub konfigurację filtru musi mieć w czasie wykonywania w celu wykonania.</span><span class="sxs-lookup"><span data-stu-id="791f6-108">This parameter contains the configuration information that is passed to the MessageFilter constructor in order to provide any values or configuration that the filter needs at runtime in order to perform matches.</span></span> <span data-ttu-id="791f6-109">Na przykład to może służyć do Podaj wartość filtru szuka wiadomości oceniane.</span><span class="sxs-lookup"><span data-stu-id="791f6-109">For example, this might be used to provide a value that the filter looks for within the message being evaluated.</span></span> <span data-ttu-id="791f6-110">Poniższy przykład pokazuje podstawową implementację filtr niestandardowy komunikat, który przyjmuje parametr ciąg:</span><span class="sxs-lookup"><span data-stu-id="791f6-110">The following example demonstrates a basic implementation of a custom message filter that accepts a string parameter:</span></span>  
  
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
>  <span data-ttu-id="791f6-111">W rzeczywistej implementacji metody dopasowania zawiera logikę, która zbada komunikatu, aby określić, jeśli ten filtr komunikatu powinna zwrócić **true** lub **false**.</span><span class="sxs-lookup"><span data-stu-id="791f6-111">In an actual implementation, the Match method(s) contains logic that will examine the message to determine if this message filter should return **true** or **false**.</span></span>  
  
### <a name="performance"></a><span data-ttu-id="791f6-112">Wydajność</span><span class="sxs-lookup"><span data-stu-id="791f6-112">Performance</span></span>  
 <span data-ttu-id="791f6-113">Podczas implementowania niestandardowego filtru, należy wziąć pod uwagę maksymalnego czasu wymaganego do filtru w celu oceny wiadomości.</span><span class="sxs-lookup"><span data-stu-id="791f6-113">When implementing a custom filter, it is important to take into consideration the maximum length of time required for the filter to complete the evaluation of a message.</span></span> <span data-ttu-id="791f6-114">Ponieważ komunikat może zostać obliczone dla wielu filtrów, zanim zostanie znalezione dopasowanie, jest ważne, aby upewnić się, że żądanie klienta nie podlega limitowi czasu zanim wszystkie filtry, które mogą być obliczane.</span><span class="sxs-lookup"><span data-stu-id="791f6-114">Since a message may be evaluated against multiple filters before a match is found, it is important to ensure that the client request does not time out before all filters can be evaluated.</span></span> <span data-ttu-id="791f6-115">W związku z tym filtr niestandardowy może zawierać tylko kod niezbędnych do oceny zawartości lub atrybutów wiadomości w celu ustalenia, jeśli jest on zgodny kryteria filtrowania.</span><span class="sxs-lookup"><span data-stu-id="791f6-115">Therefore a custom filter should contain only the code necessary to evaluate the contents or attributes of a message in order to determine if it matches the filter criteria.</span></span>  
  
 <span data-ttu-id="791f6-116">Ogólnie rzecz biorąc należy unikać następujące podczas implementowania niestandardowego filtru:</span><span class="sxs-lookup"><span data-stu-id="791f6-116">In general, you should avoid the following when implementing a custom filter:</span></span>  
  
- <span data-ttu-id="791f6-117">We/Wy, takich jak zapisywanie danych na dysku lub z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="791f6-117">IO, such as saving data to disk or to a database.</span></span>  
  
- <span data-ttu-id="791f6-118">Niepotrzebna przetwarzania, takich jak odtwarzanie w pętli za pośrednictwem wielu rekordów w dokumencie.</span><span class="sxs-lookup"><span data-stu-id="791f6-118">Unnecessary processing, such as looping over multiple records in a document.</span></span>  
  
- <span data-ttu-id="791f6-119">Blokowanie operacji, takich jak wywołania, które obejmują uzyskania blokady ze współużytkowanych zasobów lub przeprowadzania wyszukiwań względem bazy danych.</span><span class="sxs-lookup"><span data-stu-id="791f6-119">Blocking operations, such as calls that involve obtaining a lock on shared resources or performing lookups against a database.</span></span>  
  
 <span data-ttu-id="791f6-120">Przed użyciem niestandardowego filtru w środowisku produkcyjnym, należy uruchomić testy wydajności w celu ustalenia średnia długość czasu, przez jaki filtr potrzebuje do oceny wiadomość.</span><span class="sxs-lookup"><span data-stu-id="791f6-120">Before using a custom filter in a production environment, you should run performance tests to determine the average length of time that the filter takes to evaluate a message.</span></span> <span data-ttu-id="791f6-121">W połączeniu z Średni czas przetwarzania filtrów, używane w tabeli filtru, temu będzie można dokładnie określić maksymalną wartość limitu czasu, który powinien być określony przez aplikację klienta.</span><span class="sxs-lookup"><span data-stu-id="791f6-121">When combined with the average processing time of the other filters used in the filter table, this will allow you to accurately determine the maximum timeout value that should be specified by the client application.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="791f6-122">Użycie</span><span class="sxs-lookup"><span data-stu-id="791f6-122">Usage</span></span>  
 <span data-ttu-id="791f6-123">Aby można było używać niestandardowego filtru z usługą routingu, należy dodać go do tabeli filtru, określając nowy wpis filtru typu niestandardowego"," w pełni kwalifikowana nazwa typu filtru komunikatów i nazwy zestawu.</span><span class="sxs-lookup"><span data-stu-id="791f6-123">In order to use your custom filter with the Routing Service, you must add it to the filter table by specifying a new filter entry of type "Custom," the fully qualified type name of the message filter, and the name of your assembly.</span></span>  <span data-ttu-id="791f6-124">Podobnie jak w przypadku innych MessageFilters można określić danych parametrów filtru, który zostanie przekazany do konstruktora niestandardowego filtru.</span><span class="sxs-lookup"><span data-stu-id="791f6-124">As with other MessageFilters, you can specify the string filterData that will be passed to your custom filter’s constructor.</span></span>  
  
 <span data-ttu-id="791f6-125">W poniższych przykładach pokazano, przy użyciu niestandardowego filtru z usługą routingu:</span><span class="sxs-lookup"><span data-stu-id="791f6-125">The following examples demonstrate using a custom filter with the Routing Service:</span></span>  
  
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
