---
title: <filters> dla <routing>
ms.date: 03/30/2017
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
ms.openlocfilehash: ba60958ad33b46b40285f3f70001273bb3af3a63
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925618"
---
# <a name="filters-of-routing"></a><span data-ttu-id="9d451-102">\<Filtry > \<routingu ></span><span class="sxs-lookup"><span data-stu-id="9d451-102">\<filters> of \<routing></span></span>

<span data-ttu-id="9d451-103">Reprezentuje sekcję konfiguracji określającą zestaw filtrów routingu, które określają typ Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> , który ma być używany podczas oceniania wiadomości przychodzących.</span><span class="sxs-lookup"><span data-stu-id="9d451-103">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span>

<span data-ttu-id="9d451-104">[ **\<system.serviceModel>** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="9d451-104">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="9d451-105">&nbsp;&nbsp;[ **\<> routingu**](routing.md) </span><span class="sxs-lookup"><span data-stu-id="9d451-105">&nbsp;&nbsp;[**\<routing>**](routing.md) </span></span>  
<span data-ttu-id="9d451-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<Filtry >**</span><span class="sxs-lookup"><span data-stu-id="9d451-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<filters>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="9d451-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="9d451-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <routing>
    <filters>
      <filter customType="String"
              filterData="String"
              filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath"
              name="String" />
    </filters>
  </routing>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9d451-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9d451-108">Attributes and elements</span></span>

<span data-ttu-id="9d451-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9d451-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="9d451-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9d451-110">Attributes</span></span>

<span data-ttu-id="9d451-111">Brak</span><span class="sxs-lookup"><span data-stu-id="9d451-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="9d451-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9d451-112">Child elements</span></span>

|     | <span data-ttu-id="9d451-113">Opis</span><span class="sxs-lookup"><span data-stu-id="9d451-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="9d451-114"> **\<Filtr >** </span><span class="sxs-lookup"><span data-stu-id="9d451-114">**\<filter>**</span></span>](filter.md) | <span data-ttu-id="9d451-115">Zawiera filtr routingu, który określa typ Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> , który będzie używany podczas oceniania wiadomości przychodzących.</span><span class="sxs-lookup"><span data-stu-id="9d451-115">Contains a routing filter that determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> will be used when evaluating incoming messages.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="9d451-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9d451-116">Parent elements</span></span>

|     | <span data-ttu-id="9d451-117">Opis</span><span class="sxs-lookup"><span data-stu-id="9d451-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="9d451-118"> **\<> routingu**</span><span class="sxs-lookup"><span data-stu-id="9d451-118">**\<routing>**</span></span>](routing.md) | <span data-ttu-id="9d451-119">Reprezentuje sekcję konfiguracji określającą zestaw filtrów routingu, które określają typ Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> , który ma być używany podczas oceniania wiadomości przychodzących, a także tabele routingu, które definiują docelowe punkty końcowe Wysyłaj komunikaty do, gdy filtr jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="9d451-119">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="9d451-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9d451-120">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
