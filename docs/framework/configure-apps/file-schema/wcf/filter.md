---
title: <filter>
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: 6e78275aaeb202405e327302455d56fa431d7f27
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855255"
---
# <a name="filter"></a><span data-ttu-id="8cfbc-101">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="8cfbc-101">\<filter></span></span>

<span data-ttu-id="8cfbc-102">Definiuje filtr routingu, który określa typ Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> , który ma być używany podczas oceniania wiadomości przychodzących, a także wszelkie dane pomocnicze lub parametry wymagane przez filtr.</span><span class="sxs-lookup"><span data-stu-id="8cfbc-102">Defines a routing filter, which determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well any supporting data or parameters required by the filter.</span></span>

<span data-ttu-id="8cfbc-103">[ **\<system.serviceModel>** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="8cfbc-103">[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="8cfbc-104">&nbsp;&nbsp;[ **\<> routingu**](routing.md)</span><span class="sxs-lookup"><span data-stu-id="8cfbc-104">&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="8cfbc-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Filtry >** ](filters-of-routing.md)</span><span class="sxs-lookup"><span data-stu-id="8cfbc-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<filters>**](filters-of-routing.md)</span></span>\
<span data-ttu-id="8cfbc-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Filtr >**</span><span class="sxs-lookup"><span data-stu-id="8cfbc-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cfbc-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="8cfbc-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8cfbc-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8cfbc-108">Attributes and elements</span></span>

<span data-ttu-id="8cfbc-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8cfbc-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="8cfbc-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8cfbc-110">Attributes</span></span>

| <span data-ttu-id="8cfbc-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8cfbc-111">Attribute</span></span>  | <span data-ttu-id="8cfbc-112">Opis</span><span class="sxs-lookup"><span data-stu-id="8cfbc-112">Description</span></span> |
| ---------- | ----------- |
| <span data-ttu-id="8cfbc-113">customType</span><span class="sxs-lookup"><span data-stu-id="8cfbc-113">customType</span></span> | <span data-ttu-id="8cfbc-114">Ciąg zawierający w pełni kwalifikowaną nazwę typu typu niestandardowego, który ma być używany jako filtr.</span><span class="sxs-lookup"><span data-stu-id="8cfbc-114">A string containing the fully qualified type name of the custom type to be used as a filter.</span></span> <span data-ttu-id="8cfbc-115">Jeśli `filterType` jest ustawiona na `custom`, ten atrybut zawiera w pełni kwalifikowaną nazwę typu klasy do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="8cfbc-115">If `filterType` is set to `custom`, this attribute contains the fully qualified type name of the class to create.</span></span>  <span data-ttu-id="8cfbc-116">`filterData`może również zawierać wartości, które mają być używane podczas oceny niestandardowego filtru typów.</span><span class="sxs-lookup"><span data-stu-id="8cfbc-116">`filterData` may also contain values to be used during evaluation of the custom type filter.</span></span> |
| <span data-ttu-id="8cfbc-117">filterData</span><span class="sxs-lookup"><span data-stu-id="8cfbc-117">filterData</span></span> | <span data-ttu-id="8cfbc-118">Ciąg zawierający dane filtru.</span><span class="sxs-lookup"><span data-stu-id="8cfbc-118">A string containing the filter data.</span></span> <span data-ttu-id="8cfbc-119">Aby uzyskać więcej informacji na temat sposobu określania tego atrybutu, <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>Zobacz.</span><span class="sxs-lookup"><span data-stu-id="8cfbc-119">For more information on how to specify this attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="8cfbc-120">filterType</span><span class="sxs-lookup"><span data-stu-id="8cfbc-120">filterType</span></span> | <span data-ttu-id="8cfbc-121">Ciąg zawierający typ filtru.</span><span class="sxs-lookup"><span data-stu-id="8cfbc-121">A string containing the filter type.</span></span> <span data-ttu-id="8cfbc-122">Ten atrybut jest <xref:System.ServiceModel.Routing.Configuration.FilterType> typu.</span><span class="sxs-lookup"><span data-stu-id="8cfbc-122">This attribute is of <xref:System.ServiceModel.Routing.Configuration.FilterType> type.</span></span>  <span data-ttu-id="8cfbc-123">Aby uzyskać więcej informacji na temat tego, jak `filterData` to działa z <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>atrybutem, zobacz.</span><span class="sxs-lookup"><span data-stu-id="8cfbc-123">For more information on how this works with the `filterData` attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="8cfbc-124">nazwa</span><span class="sxs-lookup"><span data-stu-id="8cfbc-124">name</span></span>       | <span data-ttu-id="8cfbc-125">Ciąg zawierający unikatową nazwę tego elementu filtru.</span><span class="sxs-lookup"><span data-stu-id="8cfbc-125">A string containing the unique name of this filter element.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="8cfbc-126">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8cfbc-126">Child elements</span></span>

<span data-ttu-id="8cfbc-127">Brak.</span><span class="sxs-lookup"><span data-stu-id="8cfbc-127">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8cfbc-128">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8cfbc-128">Parent elements</span></span>

| <span data-ttu-id="8cfbc-129">Element</span><span class="sxs-lookup"><span data-stu-id="8cfbc-129">Element</span></span> | <span data-ttu-id="8cfbc-130">Opis</span><span class="sxs-lookup"><span data-stu-id="8cfbc-130">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="8cfbc-131">\<> routingu</span><span class="sxs-lookup"><span data-stu-id="8cfbc-131">\<routing></span></span>](routing.md) | <span data-ttu-id="8cfbc-132">Sekcja konfiguracji służąca do definiowania zestawu filtrów routingu, które określają typ Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> , który ma być używany podczas oceniania wiadomości przychodzących.</span><span class="sxs-lookup"><span data-stu-id="8cfbc-132">A configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span> |

## <a name="see-also"></a><span data-ttu-id="8cfbc-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8cfbc-133">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>
