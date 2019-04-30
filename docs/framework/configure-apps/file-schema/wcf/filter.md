---
title: <filter>
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: bff19f106d86c73dea80b8b57bb73442eaa2cf9f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704040"
---
# <a name="filter"></a><span data-ttu-id="d1dad-101">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="d1dad-101">\<filter></span></span>

<span data-ttu-id="d1dad-102">Określa filtr routingu, który określa typ programu Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> używanego podczas oceniania wiadomości przychodzących, jak również obsługujących danych lub parametrów wymaganych przez filtr.</span><span class="sxs-lookup"><span data-stu-id="d1dad-102">Defines a routing filter, which determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well any supporting data or parameters required by the filter.</span></span>

<span data-ttu-id="d1dad-103">\<system.serviceModel> \<routing> \<filters> \<filter></span><span class="sxs-lookup"><span data-stu-id="d1dad-103">\<system.serviceModel> \<routing> \<filters> \<filter></span></span>
  
## <a name="syntax"></a><span data-ttu-id="d1dad-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d1dad-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d1dad-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d1dad-105">Attributes and elements</span></span>

<span data-ttu-id="d1dad-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d1dad-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="d1dad-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d1dad-107">Attributes</span></span>

| <span data-ttu-id="d1dad-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d1dad-108">Attribute</span></span>  | <span data-ttu-id="d1dad-109">Opis</span><span class="sxs-lookup"><span data-stu-id="d1dad-109">Description</span></span> |
| ---------- | ----------- |
| <span data-ttu-id="d1dad-110">customType</span><span class="sxs-lookup"><span data-stu-id="d1dad-110">customType</span></span> | <span data-ttu-id="d1dad-111">Ciąg zawierający w pełni kwalifikowana nazwa typu niestandardowego typu ma być używany jako filtr.</span><span class="sxs-lookup"><span data-stu-id="d1dad-111">A string containing the fully qualified type name of the custom type to be used as a filter.</span></span> <span data-ttu-id="d1dad-112">Jeśli `filterType` ustawiono `custom`, ten atrybut zawiera w pełni kwalifikowana nazwa typu klasy, aby utworzyć.</span><span class="sxs-lookup"><span data-stu-id="d1dad-112">If `filterType` is set to `custom`, this attribute contains the fully qualified type name of the class to create.</span></span>  <span data-ttu-id="d1dad-113">`filterData` może również zawierać wartości, które mają być używane podczas obliczania wartości filtru typu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="d1dad-113">`filterData` may also contain values to be used during evaluation of the custom type filter.</span></span> |
| <span data-ttu-id="d1dad-114">filterData</span><span class="sxs-lookup"><span data-stu-id="d1dad-114">filterData</span></span> | <span data-ttu-id="d1dad-115">Ciąg zawierający dane filtru.</span><span class="sxs-lookup"><span data-stu-id="d1dad-115">A string containing the filter data.</span></span> <span data-ttu-id="d1dad-116">Aby uzyskać więcej informacji na temat sposobu określania tego atrybutu, zobacz <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span><span class="sxs-lookup"><span data-stu-id="d1dad-116">For more information on how to specify this attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="d1dad-117">filterType</span><span class="sxs-lookup"><span data-stu-id="d1dad-117">filterType</span></span> | <span data-ttu-id="d1dad-118">Ciąg zawierający typ filtru.</span><span class="sxs-lookup"><span data-stu-id="d1dad-118">A string containing the filter type.</span></span> <span data-ttu-id="d1dad-119">Ten atrybut jest <xref:System.ServiceModel.Routing.Configuration.FilterType> typu.</span><span class="sxs-lookup"><span data-stu-id="d1dad-119">This attribute is of <xref:System.ServiceModel.Routing.Configuration.FilterType> type.</span></span>  <span data-ttu-id="d1dad-120">Aby uzyskać więcej informacji na temat działania z `filterData` atrybutów, zobacz <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span><span class="sxs-lookup"><span data-stu-id="d1dad-120">For more information on how this works with the `filterData` attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="d1dad-121">nazwa</span><span class="sxs-lookup"><span data-stu-id="d1dad-121">name</span></span>       | <span data-ttu-id="d1dad-122">Ciąg zawierający unikatową nazwę tego elementu filtru.</span><span class="sxs-lookup"><span data-stu-id="d1dad-122">A string containing the unique name of this filter element.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="d1dad-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d1dad-123">Child elements</span></span>

<span data-ttu-id="d1dad-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="d1dad-124">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d1dad-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d1dad-125">Parent elements</span></span>

| <span data-ttu-id="d1dad-126">Element</span><span class="sxs-lookup"><span data-stu-id="d1dad-126">Element</span></span> | <span data-ttu-id="d1dad-127">Opis</span><span class="sxs-lookup"><span data-stu-id="d1dad-127">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="d1dad-128">\<routing></span><span class="sxs-lookup"><span data-stu-id="d1dad-128">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="d1dad-129">Sekcję konfiguracji określającą zestaw filtrów routingu, które określają typ obiektu programu Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> używanego podczas oceniania wiadomości przychodzących.</span><span class="sxs-lookup"><span data-stu-id="d1dad-129">A configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span> |

## <a name="see-also"></a><span data-ttu-id="d1dad-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d1dad-130">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>
