---
title: <filter>
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: 68de255b9f11dc4377159d1cc3efa575633db316
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918895"
---
# <a name="filter"></a><span data-ttu-id="4eda4-101">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="4eda4-101">\<filter></span></span>

<span data-ttu-id="4eda4-102">Definiuje filtr routingu, który określa typ Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> , który ma być używany podczas oceniania wiadomości przychodzących, a także wszelkie dane pomocnicze lub parametry wymagane przez filtr.</span><span class="sxs-lookup"><span data-stu-id="4eda4-102">Defines a routing filter, which determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well any supporting data or parameters required by the filter.</span></span>

<span data-ttu-id="4eda4-103">\<system.serviceModel> \<routing> \<filters> \<filter></span><span class="sxs-lookup"><span data-stu-id="4eda4-103">\<system.serviceModel> \<routing> \<filters> \<filter></span></span>
  
## <a name="syntax"></a><span data-ttu-id="4eda4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4eda4-104">Syntax</span></span>  
  
```xml  
<routing>
  <filters>
    <filter customType="String"
            filterData="String"
            filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath"
            name="String" />
  </filters>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4eda4-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4eda4-105">Attributes and elements</span></span>

<span data-ttu-id="4eda4-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4eda4-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="4eda4-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4eda4-107">Attributes</span></span>

| <span data-ttu-id="4eda4-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4eda4-108">Attribute</span></span>  | <span data-ttu-id="4eda4-109">Opis</span><span class="sxs-lookup"><span data-stu-id="4eda4-109">Description</span></span> |
| ---------- | ----------- |
| <span data-ttu-id="4eda4-110">customType</span><span class="sxs-lookup"><span data-stu-id="4eda4-110">customType</span></span> | <span data-ttu-id="4eda4-111">Ciąg zawierający w pełni kwalifikowaną nazwę typu typu niestandardowego, który ma być używany jako filtr.</span><span class="sxs-lookup"><span data-stu-id="4eda4-111">A string containing the fully qualified type name of the custom type to be used as a filter.</span></span> <span data-ttu-id="4eda4-112">Jeśli `filterType` jest ustawiona na `custom`, ten atrybut zawiera w pełni kwalifikowaną nazwę typu klasy do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="4eda4-112">If `filterType` is set to `custom`, this attribute contains the fully qualified type name of the class to create.</span></span>  <span data-ttu-id="4eda4-113">`filterData`może również zawierać wartości, które mają być używane podczas oceny niestandardowego filtru typów.</span><span class="sxs-lookup"><span data-stu-id="4eda4-113">`filterData` may also contain values to be used during evaluation of the custom type filter.</span></span> |
| <span data-ttu-id="4eda4-114">filterData</span><span class="sxs-lookup"><span data-stu-id="4eda4-114">filterData</span></span> | <span data-ttu-id="4eda4-115">Ciąg zawierający dane filtru.</span><span class="sxs-lookup"><span data-stu-id="4eda4-115">A string containing the filter data.</span></span> <span data-ttu-id="4eda4-116">Aby uzyskać więcej informacji na temat sposobu określania tego atrybutu, <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>Zobacz.</span><span class="sxs-lookup"><span data-stu-id="4eda4-116">For more information on how to specify this attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="4eda4-117">filterType</span><span class="sxs-lookup"><span data-stu-id="4eda4-117">filterType</span></span> | <span data-ttu-id="4eda4-118">Ciąg zawierający typ filtru.</span><span class="sxs-lookup"><span data-stu-id="4eda4-118">A string containing the filter type.</span></span> <span data-ttu-id="4eda4-119">Ten atrybut jest <xref:System.ServiceModel.Routing.Configuration.FilterType> typu.</span><span class="sxs-lookup"><span data-stu-id="4eda4-119">This attribute is of <xref:System.ServiceModel.Routing.Configuration.FilterType> type.</span></span>  <span data-ttu-id="4eda4-120">Aby uzyskać więcej informacji na temat tego, jak `filterData` to działa z <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>atrybutem, zobacz.</span><span class="sxs-lookup"><span data-stu-id="4eda4-120">For more information on how this works with the `filterData` attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="4eda4-121">nazwa</span><span class="sxs-lookup"><span data-stu-id="4eda4-121">name</span></span>       | <span data-ttu-id="4eda4-122">Ciąg zawierający unikatową nazwę tego elementu filtru.</span><span class="sxs-lookup"><span data-stu-id="4eda4-122">A string containing the unique name of this filter element.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="4eda4-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4eda4-123">Child elements</span></span>

<span data-ttu-id="4eda4-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="4eda4-124">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4eda4-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4eda4-125">Parent elements</span></span>

| <span data-ttu-id="4eda4-126">Element</span><span class="sxs-lookup"><span data-stu-id="4eda4-126">Element</span></span> | <span data-ttu-id="4eda4-127">Opis</span><span class="sxs-lookup"><span data-stu-id="4eda4-127">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="4eda4-128">\<> routingu</span><span class="sxs-lookup"><span data-stu-id="4eda4-128">\<routing></span></span>](routing.md) | <span data-ttu-id="4eda4-129">Sekcja konfiguracji służąca do definiowania zestawu filtrów routingu, które określają typ Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> , który ma być używany podczas oceniania wiadomości przychodzących.</span><span class="sxs-lookup"><span data-stu-id="4eda4-129">A configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span> |

## <a name="see-also"></a><span data-ttu-id="4eda4-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4eda4-130">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>
