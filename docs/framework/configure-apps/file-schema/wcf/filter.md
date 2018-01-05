---
title: '&lt;Filtr&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 186c511cd8a69cef5e30e369641628a10a0972d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltfiltergt"></a><span data-ttu-id="fc044-102">&lt;Filtr&gt;</span><span class="sxs-lookup"><span data-stu-id="fc044-102">&lt;filter&gt;</span></span>

<span data-ttu-id="fc044-103">Określa filtr routingu, która określa typ [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> używanego podczas oceniania wiadomości przychodzących, jak również obsługujących danych lub parametrów wymaganych przez filtr.</span><span class="sxs-lookup"><span data-stu-id="fc044-103">Defines a routing filter, which determines the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well any supporting data or parameters required by the filter.</span></span>

<span data-ttu-id="fc044-104">\<system.serviceModel > \<routingu > \<Filtry > \<filtru ></span><span class="sxs-lookup"><span data-stu-id="fc044-104">\<system.serviceModel> \<routing> \<filters> \<filter></span></span>

## <a name="syntax"></a><span data-ttu-id="fc044-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="fc044-105">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="fc044-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fc044-106">Attributes and elements</span></span>

<span data-ttu-id="fc044-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fc044-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="fc044-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fc044-108">Attributes</span></span>

| <span data-ttu-id="fc044-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="fc044-109">Attribute</span></span>  | <span data-ttu-id="fc044-110">Opis</span><span class="sxs-lookup"><span data-stu-id="fc044-110">Description</span></span> |
| ---------- | ----------- |
| <span data-ttu-id="fc044-111">customtype —</span><span class="sxs-lookup"><span data-stu-id="fc044-111">customType</span></span> | <span data-ttu-id="fc044-112">Ciąg zawierający nazwę FQDN typu niestandardowego typu ma być używany jako filtr.</span><span class="sxs-lookup"><span data-stu-id="fc044-112">A string containing the fully qualified type name of the custom type to be used as a filter.</span></span> <span data-ttu-id="fc044-113">Jeśli `filterType` ma ustawioną wartość `custom`, ten atrybut zawiera typu w pełni kwalifikowaną nazwę klasy w celu utworzenia.</span><span class="sxs-lookup"><span data-stu-id="fc044-113">If `filterType` is set to `custom`, this attribute contains the fully qualified type name of the class to create.</span></span>  <span data-ttu-id="fc044-114">`filterData`może również zawierać wartości, które mają być użyte podczas obliczania filtru typu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="fc044-114">`filterData` may also contain values to be used during evaluation of the custom type filter.</span></span> |
| <span data-ttu-id="fc044-115">danych filtru</span><span class="sxs-lookup"><span data-stu-id="fc044-115">filterData</span></span> | <span data-ttu-id="fc044-116">Ciąg zawierający dane filtru.</span><span class="sxs-lookup"><span data-stu-id="fc044-116">A string containing the filter data.</span></span> <span data-ttu-id="fc044-117">Aby uzyskać więcej informacji dotyczących sposobu określania tego atrybutu, zobacz <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span><span class="sxs-lookup"><span data-stu-id="fc044-117">For more information on how to specify this attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="fc044-118">filterType</span><span class="sxs-lookup"><span data-stu-id="fc044-118">filterType</span></span> | <span data-ttu-id="fc044-119">Ciąg zawierający typ filtru.</span><span class="sxs-lookup"><span data-stu-id="fc044-119">A string containing the filter type.</span></span> <span data-ttu-id="fc044-120">Ten atrybut jest <xref:System.ServiceModel.Routing.Configuration.FilterType> typu.</span><span class="sxs-lookup"><span data-stu-id="fc044-120">This attribute is of <xref:System.ServiceModel.Routing.Configuration.FilterType> type.</span></span>  <span data-ttu-id="fc044-121">Aby uzyskać więcej informacji na temat sposobu wykonywania z `filterData` atrybutów, zobacz <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span><span class="sxs-lookup"><span data-stu-id="fc044-121">For more information on how this works with the `filterData` attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="fc044-122">nazwa</span><span class="sxs-lookup"><span data-stu-id="fc044-122">name</span></span>       | <span data-ttu-id="fc044-123">Ciąg zawierający unikatową nazwę tego elementu filtru.</span><span class="sxs-lookup"><span data-stu-id="fc044-123">A string containing the unique name of this filter element.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="fc044-124">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fc044-124">Child elements</span></span>

<span data-ttu-id="fc044-125">Brak.</span><span class="sxs-lookup"><span data-stu-id="fc044-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fc044-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fc044-126">Parent elements</span></span>

| <span data-ttu-id="fc044-127">Element</span><span class="sxs-lookup"><span data-stu-id="fc044-127">Element</span></span> | <span data-ttu-id="fc044-128">Opis</span><span class="sxs-lookup"><span data-stu-id="fc044-128">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="fc044-129">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="fc044-129">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="fc044-130">Sekcję konfiguracji określającą zestaw filtrów routingu, które określają typ [!INCLUDE[ indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> używanego podczas oceniania wiadomości przychodzących.</span><span class="sxs-lookup"><span data-stu-id="fc044-130">A configuration section for defining a set of routing filters, which determine the type of [!INCLUDE[ indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span> |

## <a name="see-also"></a><span data-ttu-id="fc044-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fc044-131">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>    
<xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>   
<xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>   
