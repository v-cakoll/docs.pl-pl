---
title: Filtry niestandardowe
ms.date: 03/30/2017
ms.assetid: 97cf247d-be0a-4057-bba9-3be5c45029d5
ms.openlocfilehash: ade387524c9ca6c8ef337ccf6a5b3453b7df976b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945378"
---
# <a name="custom-filters"></a><span data-ttu-id="db94c-102">Filtry niestandardowe</span><span class="sxs-lookup"><span data-stu-id="db94c-102">Custom Filters</span></span>
<span data-ttu-id="db94c-103">Filtry niestandardowe umożliwiają zdefiniowanie dopasowania logiki, której nie można wykonać za pomocą filtrów komunikatów dostarczonych przez system.</span><span class="sxs-lookup"><span data-stu-id="db94c-103">Custom filters allow you to define matching logic that cannot be accomplished using the system-provided message filters.</span></span> <span data-ttu-id="db94c-104">Na przykład można utworzyć filtr niestandardowy, który miesza określony element komunikatu, a następnie analizuje wartość, aby określić, czy filtr powinien zwrócić wartość true lub false.</span><span class="sxs-lookup"><span data-stu-id="db94c-104">For example, you might create a custom filter that hashes a particular message element and then examines the value to determine whether the filter should return true or false.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="db94c-105">Implementacja</span><span class="sxs-lookup"><span data-stu-id="db94c-105">Implementation</span></span>  
 <span data-ttu-id="db94c-106">Filtr niestandardowy jest implementacją <xref:System.ServiceModel.Dispatcher.MessageFilter> abstrakcyjnej klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="db94c-106">A custom filter is an implementation of the <xref:System.ServiceModel.Dispatcher.MessageFilter> abstract base class.</span></span> <span data-ttu-id="db94c-107">Podczas implementowania niestandardowego filtru Konstruktor może opcjonalnie zaakceptować pojedynczy parametr ciągu.</span><span class="sxs-lookup"><span data-stu-id="db94c-107">When implementing your custom filter, the constructor can optionally accept a single string parameter.</span></span> <span data-ttu-id="db94c-108">Ten parametr zawiera informacje o konfiguracji, które są przesyłane do konstruktora MessageFilter w celu zapewnienia dowolnych wartości lub konfiguracji wymaganych przez filtr w czasie wykonywania w celu wykonania dopasowań.</span><span class="sxs-lookup"><span data-stu-id="db94c-108">This parameter contains the configuration information that is passed to the MessageFilter constructor in order to provide any values or configuration that the filter needs at runtime in order to perform matches.</span></span> <span data-ttu-id="db94c-109">Na przykład może to służyć do podania wartości, która będzie wyglądała w filtrze w analizowanym komunikacie.</span><span class="sxs-lookup"><span data-stu-id="db94c-109">For example, this might be used to provide a value that the filter looks for within the message being evaluated.</span></span> <span data-ttu-id="db94c-110">Poniższy przykład ilustruje podstawową implementację niestandardowego filtru komunikatów, który akceptuje parametr ciągu:</span><span class="sxs-lookup"><span data-stu-id="db94c-110">The following example demonstrates a basic implementation of a custom message filter that accepts a string parameter:</span></span>  
  
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
> <span data-ttu-id="db94c-111">W rzeczywistej implementacji metody dopasowania zawierają logikę, która będzie analizować komunikat, aby określić, czy ten filtr komunikatów powinien zwrócić **wartość true** lub **false**.</span><span class="sxs-lookup"><span data-stu-id="db94c-111">In an actual implementation, the Match method(s) contains logic that will examine the message to determine if this message filter should return **true** or **false**.</span></span>  
  
### <a name="performance"></a><span data-ttu-id="db94c-112">Wydajność</span><span class="sxs-lookup"><span data-stu-id="db94c-112">Performance</span></span>  
 <span data-ttu-id="db94c-113">Podczas implementowania filtru niestandardowego należy wziąć pod uwagę maksymalny czas wymagany do przeprowadzenia obliczeń przez filtr.</span><span class="sxs-lookup"><span data-stu-id="db94c-113">When implementing a custom filter, it is important to take into consideration the maximum length of time required for the filter to complete the evaluation of a message.</span></span> <span data-ttu-id="db94c-114">Ponieważ komunikat można ocenić względem wielu filtrów przed znalezieniem dopasowania, należy się upewnić, że żądanie klienta nie przekroczy limitu czasu, zanim będzie można ocenić wszystkie filtry.</span><span class="sxs-lookup"><span data-stu-id="db94c-114">Since a message may be evaluated against multiple filters before a match is found, it is important to ensure that the client request does not time out before all filters can be evaluated.</span></span> <span data-ttu-id="db94c-115">W związku z tym filtr niestandardowy powinien zawierać tylko kod niezbędny do oszacowania zawartości lub atrybutów komunikatu w celu ustalenia, czy pasuje do kryteriów filtrowania.</span><span class="sxs-lookup"><span data-stu-id="db94c-115">Therefore a custom filter should contain only the code necessary to evaluate the contents or attributes of a message in order to determine if it matches the filter criteria.</span></span>  
  
 <span data-ttu-id="db94c-116">Ogólnie rzecz biorąc, podczas implementowania filtra niestandardowego należy unikać następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="db94c-116">In general, you should avoid the following when implementing a custom filter:</span></span>  
  
- <span data-ttu-id="db94c-117">We/wy, takie jak zapisywanie danych na dysku lub w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="db94c-117">IO, such as saving data to disk or to a database.</span></span>  
  
- <span data-ttu-id="db94c-118">Niepotrzebne przetwarzanie, takie jak pętla dla wielu rekordów w dokumencie.</span><span class="sxs-lookup"><span data-stu-id="db94c-118">Unnecessary processing, such as looping over multiple records in a document.</span></span>  
  
- <span data-ttu-id="db94c-119">Operacje blokowania, takie jak wywołania, które wymagają uzyskania blokady zasobów udostępnionych lub wykonywania wyszukiwania względem bazy danych.</span><span class="sxs-lookup"><span data-stu-id="db94c-119">Blocking operations, such as calls that involve obtaining a lock on shared resources or performing lookups against a database.</span></span>  
  
 <span data-ttu-id="db94c-120">Przed użyciem filtru niestandardowego w środowisku produkcyjnym należy uruchomić testy wydajnościowe, aby określić średni czas wymagany przez filtr w celu oceny komunikatu.</span><span class="sxs-lookup"><span data-stu-id="db94c-120">Before using a custom filter in a production environment, you should run performance tests to determine the average length of time that the filter takes to evaluate a message.</span></span> <span data-ttu-id="db94c-121">W połączeniu z średnim czasem przetwarzania innych filtrów używanych w tabeli filtrów umożliwi to dokładne określenie maksymalnej wartości limitu czasu, która powinna być określona przez aplikację kliencką.</span><span class="sxs-lookup"><span data-stu-id="db94c-121">When combined with the average processing time of the other filters used in the filter table, this will allow you to accurately determine the maximum timeout value that should be specified by the client application.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="db94c-122">Użycie</span><span class="sxs-lookup"><span data-stu-id="db94c-122">Usage</span></span>  
 <span data-ttu-id="db94c-123">Aby można było użyć niestandardowego filtru z usługą routingu, należy dodać go do tabeli filtrów przez określenie nowego wpisu filtru typu "Custom", w pełni kwalifikowanej nazwy typu filtru komunikatów i nazwy zestawu.</span><span class="sxs-lookup"><span data-stu-id="db94c-123">In order to use your custom filter with the Routing Service, you must add it to the filter table by specifying a new filter entry of type "Custom," the fully qualified type name of the message filter, and the name of your assembly.</span></span>  <span data-ttu-id="db94c-124">Podobnie jak w przypadku innych MessageFilters można określić ciąg danych filtru, który zostanie przesłany do konstruktora filtru niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="db94c-124">As with other MessageFilters, you can specify the string filterData that will be passed to your custom filter’s constructor.</span></span>  
  
 <span data-ttu-id="db94c-125">W poniższych przykładach pokazano, jak za pomocą filtru niestandardowego korzystać z usługi routingu:</span><span class="sxs-lookup"><span data-stu-id="db94c-125">The following examples demonstrate using a custom filter with the Routing Service:</span></span>  
  
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
