---
title: <filter>
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: 6e78275aaeb202405e327302455d56fa431d7f27
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855255"
---
# \<filter>

<span data-ttu-id="d28e5-101">Definiuje filtr routingu, który określa typ Windows Communication Foundation (WCF), który <xref:System.ServiceModel.Dispatcher.MessageFilter> ma być używany podczas oceniania wiadomości przychodzących, a także wszelkie dane pomocnicze lub parametry wymagane przez filtr.</span><span class="sxs-lookup"><span data-stu-id="d28e5-101">Defines a routing filter, which determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well any supporting data or parameters required by the filter.</span></span>

[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<filters>**](filters-of-routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**  
  
## <a name="syntax"></a><span data-ttu-id="d28e5-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="d28e5-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d28e5-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d28e5-103">Attributes and elements</span></span>

<span data-ttu-id="d28e5-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d28e5-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="d28e5-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d28e5-105">Attributes</span></span>

| <span data-ttu-id="d28e5-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d28e5-106">Attribute</span></span>  | <span data-ttu-id="d28e5-107">Opis</span><span class="sxs-lookup"><span data-stu-id="d28e5-107">Description</span></span> |
| ---------- | ----------- |
| <span data-ttu-id="d28e5-108">CustomType</span><span class="sxs-lookup"><span data-stu-id="d28e5-108">customType</span></span> | <span data-ttu-id="d28e5-109">Ciąg zawierający w pełni kwalifikowaną nazwę typu typu niestandardowego, który ma być używany jako filtr.</span><span class="sxs-lookup"><span data-stu-id="d28e5-109">A string containing the fully qualified type name of the custom type to be used as a filter.</span></span> <span data-ttu-id="d28e5-110">Jeśli `filterType` jest ustawiona na `custom` , ten atrybut zawiera w pełni kwalifikowaną nazwę typu klasy do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="d28e5-110">If `filterType` is set to `custom`, this attribute contains the fully qualified type name of the class to create.</span></span>  <span data-ttu-id="d28e5-111">`filterData`może również zawierać wartości, które mają być używane podczas oceny niestandardowego filtru typów.</span><span class="sxs-lookup"><span data-stu-id="d28e5-111">`filterData` may also contain values to be used during evaluation of the custom type filter.</span></span> |
| <span data-ttu-id="d28e5-112">Danych filtru</span><span class="sxs-lookup"><span data-stu-id="d28e5-112">filterData</span></span> | <span data-ttu-id="d28e5-113">Ciąg zawierający dane filtru.</span><span class="sxs-lookup"><span data-stu-id="d28e5-113">A string containing the filter data.</span></span> <span data-ttu-id="d28e5-114">Aby uzyskać więcej informacji na temat sposobu określania tego atrybutu, zobacz <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A> .</span><span class="sxs-lookup"><span data-stu-id="d28e5-114">For more information on how to specify this attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="d28e5-115">filterType</span><span class="sxs-lookup"><span data-stu-id="d28e5-115">filterType</span></span> | <span data-ttu-id="d28e5-116">Ciąg zawierający typ filtru.</span><span class="sxs-lookup"><span data-stu-id="d28e5-116">A string containing the filter type.</span></span> <span data-ttu-id="d28e5-117">Ten atrybut jest <xref:System.ServiceModel.Routing.Configuration.FilterType> typu.</span><span class="sxs-lookup"><span data-stu-id="d28e5-117">This attribute is of <xref:System.ServiceModel.Routing.Configuration.FilterType> type.</span></span>  <span data-ttu-id="d28e5-118">Aby uzyskać więcej informacji na temat tego, jak to działa z `filterData` atrybutem, zobacz <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A> .</span><span class="sxs-lookup"><span data-stu-id="d28e5-118">For more information on how this works with the `filterData` attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="d28e5-119">name</span><span class="sxs-lookup"><span data-stu-id="d28e5-119">name</span></span>       | <span data-ttu-id="d28e5-120">Ciąg zawierający unikatową nazwę tego elementu filtru.</span><span class="sxs-lookup"><span data-stu-id="d28e5-120">A string containing the unique name of this filter element.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="d28e5-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d28e5-121">Child elements</span></span>

<span data-ttu-id="d28e5-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="d28e5-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d28e5-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d28e5-123">Parent elements</span></span>

| <span data-ttu-id="d28e5-124">Element</span><span class="sxs-lookup"><span data-stu-id="d28e5-124">Element</span></span> | <span data-ttu-id="d28e5-125">Opis</span><span class="sxs-lookup"><span data-stu-id="d28e5-125">Description</span></span> |
| ------- | ----------- |
| [\<routing>](routing.md) | <span data-ttu-id="d28e5-126">Sekcja konfiguracji służąca do definiowania zestawu filtrów routingu, które określają typ Windows Communication Foundation (WCF), który <xref:System.ServiceModel.Dispatcher.MessageFilter> ma być używany podczas oceniania wiadomości przychodzących.</span><span class="sxs-lookup"><span data-stu-id="d28e5-126">A configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span> |

## <a name="see-also"></a><span data-ttu-id="d28e5-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d28e5-127">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>
