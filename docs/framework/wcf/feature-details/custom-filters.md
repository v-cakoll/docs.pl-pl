---
title: Filtry niestandardowe
ms.date: 03/30/2017
ms.assetid: 97cf247d-be0a-4057-bba9-3be5c45029d5
ms.openlocfilehash: ae020173544372c3ce097c8ac57e53f3fde37514
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185210"
---
# <a name="custom-filters"></a><span data-ttu-id="a7dd7-102">Filtry niestandardowe</span><span class="sxs-lookup"><span data-stu-id="a7dd7-102">Custom Filters</span></span>
<span data-ttu-id="a7dd7-103">Filtry niestandardowe umożliwiają definiowanie pasującej logiki, której nie można wykonać za pomocą filtrów wiadomości dostarczonych przez system.</span><span class="sxs-lookup"><span data-stu-id="a7dd7-103">Custom filters allow you to define matching logic that cannot be accomplished using the system-provided message filters.</span></span> <span data-ttu-id="a7dd7-104">Na przykład można utworzyć filtr niestandardowy, który skróty określonego elementu wiadomości, a następnie sprawdza wartość, aby ustalić, czy filtr powinien zwracać true lub false.</span><span class="sxs-lookup"><span data-stu-id="a7dd7-104">For example, you might create a custom filter that hashes a particular message element and then examines the value to determine whether the filter should return true or false.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="a7dd7-105">Wdrażanie</span><span class="sxs-lookup"><span data-stu-id="a7dd7-105">Implementation</span></span>  
 <span data-ttu-id="a7dd7-106">Filtr niestandardowy jest implementacją abstrakcyjnej <xref:System.ServiceModel.Dispatcher.MessageFilter> klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="a7dd7-106">A custom filter is an implementation of the <xref:System.ServiceModel.Dispatcher.MessageFilter> abstract base class.</span></span> <span data-ttu-id="a7dd7-107">Podczas implementowania filtru niestandardowego konstruktora można opcjonalnie zaakceptować parametr pojedynczego ciągu.</span><span class="sxs-lookup"><span data-stu-id="a7dd7-107">When implementing your custom filter, the constructor can optionally accept a single string parameter.</span></span> <span data-ttu-id="a7dd7-108">Ten parametr zawiera informacje o konfiguracji, który jest przekazywany do konstruktora MessageFilter w celu zapewnienia wszelkich wartości lub konfiguracji, które filtr potrzebuje w czasie wykonywania w celu wykonywania dopasowań.</span><span class="sxs-lookup"><span data-stu-id="a7dd7-108">This parameter contains the configuration information that is passed to the MessageFilter constructor in order to provide any values or configuration that the filter needs at runtime in order to perform matches.</span></span> <span data-ttu-id="a7dd7-109">Na przykład może to służyć do zapewnienia wartości, która szuka filtru w ramach wiadomości są oceniane.</span><span class="sxs-lookup"><span data-stu-id="a7dd7-109">For example, this might be used to provide a value that the filter looks for within the message being evaluated.</span></span> <span data-ttu-id="a7dd7-110">W poniższym przykładzie pokazano podstawową implementację niestandardowego filtru wiadomości, który akceptuje parametr ciągu:</span><span class="sxs-lookup"><span data-stu-id="a7dd7-110">The following example demonstrates a basic implementation of a custom message filter that accepts a string parameter:</span></span>  
  
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
> <span data-ttu-id="a7dd7-111">W rzeczywistej implementacji Match metody zawiera logikę, która zbada komunikat, aby ustalić, czy ten filtr wiadomości powinien zwracać **true** lub **false**.</span><span class="sxs-lookup"><span data-stu-id="a7dd7-111">In an actual implementation, the Match method(s) contains logic that will examine the message to determine if this message filter should return **true** or **false**.</span></span>  
  
### <a name="performance"></a><span data-ttu-id="a7dd7-112">Wydajność</span><span class="sxs-lookup"><span data-stu-id="a7dd7-112">Performance</span></span>  
 <span data-ttu-id="a7dd7-113">Podczas implementowania filtru niestandardowego, należy wziąć pod uwagę maksymalny czas wymagany dla filtru, aby zakończyć ocenę wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a7dd7-113">When implementing a custom filter, it is important to take into consideration the maximum length of time required for the filter to complete the evaluation of a message.</span></span> <span data-ttu-id="a7dd7-114">Ponieważ komunikat może być oceniany względem wielu filtrów przed znalezieniem dopasowania, ważne jest, aby upewnić się, że żądanie klienta nie limit czasu przed wszystkie filtry mogą być oceniane.</span><span class="sxs-lookup"><span data-stu-id="a7dd7-114">Since a message may be evaluated against multiple filters before a match is found, it is important to ensure that the client request does not time out before all filters can be evaluated.</span></span> <span data-ttu-id="a7dd7-115">W związku z tym filtr niestandardowy powinien zawierać tylko kod niezbędny do oceny zawartości lub atrybutów wiadomości w celu ustalenia, czy spełnia kryteria filtrowania.</span><span class="sxs-lookup"><span data-stu-id="a7dd7-115">Therefore a custom filter should contain only the code necessary to evaluate the contents or attributes of a message in order to determine if it matches the filter criteria.</span></span>  
  
 <span data-ttu-id="a7dd7-116">Ogólnie rzecz biorąc należy unikać następujących czynności podczas implementowania filtru niestandardowego:</span><span class="sxs-lookup"><span data-stu-id="a7dd7-116">In general, you should avoid the following when implementing a custom filter:</span></span>  
  
- <span data-ttu-id="a7dd7-117">We/Wy, takie jak zapisywanie danych na dysku lub w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="a7dd7-117">IO, such as saving data to disk or to a database.</span></span>  
  
- <span data-ttu-id="a7dd7-118">Niepotrzebne przetwarzanie, takie jak zapętlanie wielu rekordów w dokumencie.</span><span class="sxs-lookup"><span data-stu-id="a7dd7-118">Unnecessary processing, such as looping over multiple records in a document.</span></span>  
  
- <span data-ttu-id="a7dd7-119">Blokowanie operacji, takich jak wywołania, które obejmują uzyskanie blokady zasobów udostępnionych lub wykonywanie odnośeń w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="a7dd7-119">Blocking operations, such as calls that involve obtaining a lock on shared resources or performing lookups against a database.</span></span>  
  
 <span data-ttu-id="a7dd7-120">Przed użyciem filtru niestandardowego w środowisku produkcyjnym należy uruchomić testy wydajności, aby określić średni czas potrzebny filtrowi do oceny wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a7dd7-120">Before using a custom filter in a production environment, you should run performance tests to determine the average length of time that the filter takes to evaluate a message.</span></span> <span data-ttu-id="a7dd7-121">W połączeniu ze średnim czasem przetwarzania innych filtrów używanych w tabeli filtrów, pozwoli to dokładnie określić maksymalną wartość limitu czasu, który powinien być określony przez aplikację kliencką.</span><span class="sxs-lookup"><span data-stu-id="a7dd7-121">When combined with the average processing time of the other filters used in the filter table, this will allow you to accurately determine the maximum timeout value that should be specified by the client application.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="a7dd7-122">Sposób użycia</span><span class="sxs-lookup"><span data-stu-id="a7dd7-122">Usage</span></span>  
 <span data-ttu-id="a7dd7-123">Aby użyć filtru niestandardowego z usługą routingu, należy dodać go do tabeli filtrów, określając nowy wpis filtru typu "Niestandardowy", w pełni kwalifikowaną nazwę typu filtru wiadomości i nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="a7dd7-123">In order to use your custom filter with the Routing Service, you must add it to the filter table by specifying a new filter entry of type "Custom," the fully qualified type name of the message filter, and the name of your assembly.</span></span>  <span data-ttu-id="a7dd7-124">Podobnie jak w przypadku innych MessageFilters, można określić filterdata ciąg, który zostanie przekazany do konstruktora filtru niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="a7dd7-124">As with other MessageFilters, you can specify the string filterData that will be passed to your custom filter’s constructor.</span></span>  
  
 <span data-ttu-id="a7dd7-125">Poniższe przykłady demonstrują przy użyciu filtru niestandardowego z usługą routingu:</span><span class="sxs-lookup"><span data-stu-id="a7dd7-125">The following examples demonstrate using a custom filter with the Routing Service:</span></span>  
  
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
