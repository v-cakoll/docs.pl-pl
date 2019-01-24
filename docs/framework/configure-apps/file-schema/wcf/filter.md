---
title: '&lt;Filtr&gt;'
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: 9fae9a599299fdd8cf1e996593514fc0ef38b6ce
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645512"
---
# <a name="ltfiltergt"></a><span data-ttu-id="44daf-102">&lt;Filtr&gt;</span><span class="sxs-lookup"><span data-stu-id="44daf-102">&lt;filter&gt;</span></span>

<span data-ttu-id="44daf-103">Określa filtr routingu, który określa typ programu Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> używanego podczas oceniania wiadomości przychodzących, jak również obsługujących danych lub parametrów wymaganych przez filtr.</span><span class="sxs-lookup"><span data-stu-id="44daf-103">Defines a routing filter, which determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well any supporting data or parameters required by the filter.</span></span>

<span data-ttu-id="44daf-104">\<system.serviceModel> \<routing> \<filters> \<filter></span><span class="sxs-lookup"><span data-stu-id="44daf-104">\<system.serviceModel> \<routing> \<filters> \<filter></span></span>
  
## <a name="syntax"></a><span data-ttu-id="44daf-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="44daf-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44daf-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="44daf-106">Attributes and elements</span></span>

<span data-ttu-id="44daf-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="44daf-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="44daf-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="44daf-108">Attributes</span></span>

| <span data-ttu-id="44daf-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="44daf-109">Attribute</span></span>  | <span data-ttu-id="44daf-110">Opis</span><span class="sxs-lookup"><span data-stu-id="44daf-110">Description</span></span> |
| ---------- | ----------- |
| <span data-ttu-id="44daf-111">customType</span><span class="sxs-lookup"><span data-stu-id="44daf-111">customType</span></span> | <span data-ttu-id="44daf-112">Ciąg zawierający w pełni kwalifikowana nazwa typu niestandardowego typu ma być używany jako filtr.</span><span class="sxs-lookup"><span data-stu-id="44daf-112">A string containing the fully qualified type name of the custom type to be used as a filter.</span></span> <span data-ttu-id="44daf-113">Jeśli `filterType` ustawiono `custom`, ten atrybut zawiera w pełni kwalifikowana nazwa typu klasy, aby utworzyć.</span><span class="sxs-lookup"><span data-stu-id="44daf-113">If `filterType` is set to `custom`, this attribute contains the fully qualified type name of the class to create.</span></span>  <span data-ttu-id="44daf-114">`filterData` może również zawierać wartości, które mają być używane podczas obliczania wartości filtru typu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="44daf-114">`filterData` may also contain values to be used during evaluation of the custom type filter.</span></span> |
| <span data-ttu-id="44daf-115">filterData</span><span class="sxs-lookup"><span data-stu-id="44daf-115">filterData</span></span> | <span data-ttu-id="44daf-116">Ciąg zawierający dane filtru.</span><span class="sxs-lookup"><span data-stu-id="44daf-116">A string containing the filter data.</span></span> <span data-ttu-id="44daf-117">Aby uzyskać więcej informacji na temat sposobu określania tego atrybutu, zobacz <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span><span class="sxs-lookup"><span data-stu-id="44daf-117">For more information on how to specify this attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="44daf-118">filterType</span><span class="sxs-lookup"><span data-stu-id="44daf-118">filterType</span></span> | <span data-ttu-id="44daf-119">Ciąg zawierający typ filtru.</span><span class="sxs-lookup"><span data-stu-id="44daf-119">A string containing the filter type.</span></span> <span data-ttu-id="44daf-120">Ten atrybut jest <xref:System.ServiceModel.Routing.Configuration.FilterType> typu.</span><span class="sxs-lookup"><span data-stu-id="44daf-120">This attribute is of <xref:System.ServiceModel.Routing.Configuration.FilterType> type.</span></span>  <span data-ttu-id="44daf-121">Aby uzyskać więcej informacji na temat działania z `filterData` atrybutów, zobacz <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span><span class="sxs-lookup"><span data-stu-id="44daf-121">For more information on how this works with the `filterData` attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="44daf-122">nazwa</span><span class="sxs-lookup"><span data-stu-id="44daf-122">name</span></span>       | <span data-ttu-id="44daf-123">Ciąg zawierający unikatową nazwę tego elementu filtru.</span><span class="sxs-lookup"><span data-stu-id="44daf-123">A string containing the unique name of this filter element.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="44daf-124">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="44daf-124">Child elements</span></span>

<span data-ttu-id="44daf-125">Brak.</span><span class="sxs-lookup"><span data-stu-id="44daf-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="44daf-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="44daf-126">Parent elements</span></span>

| <span data-ttu-id="44daf-127">Element</span><span class="sxs-lookup"><span data-stu-id="44daf-127">Element</span></span> | <span data-ttu-id="44daf-128">Opis</span><span class="sxs-lookup"><span data-stu-id="44daf-128">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="44daf-129">\<routing></span><span class="sxs-lookup"><span data-stu-id="44daf-129">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="44daf-130">Sekcję konfiguracji określającą zestaw filtrów routingu, które określają typ obiektu programu Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> używanego podczas oceniania wiadomości przychodzących.</span><span class="sxs-lookup"><span data-stu-id="44daf-130">A configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span> |

## <a name="see-also"></a><span data-ttu-id="44daf-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="44daf-131">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>
