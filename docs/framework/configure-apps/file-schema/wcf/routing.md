---
title: '&lt;Routing&gt;'
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: 1771d8a2603a8f61af6ba6e2acf6243d2fd073f7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747729"
---
# <a name="ltroutinggt"></a><span data-ttu-id="fbdf9-102">&lt;Routing&gt;</span><span class="sxs-lookup"><span data-stu-id="fbdf9-102">&lt;routing&gt;</span></span>

<span data-ttu-id="fbdf9-103">Reprezentuje sekcję konfiguracji określającą zestaw filtrów routingu, które określają typ obiektu Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> używanego podczas oceniania wiadomości przychodzących, jak również routingu tabel docelowych punktów końcowych, aby zdefiniować wysyłanie komunikatów do gdy kryteria filtru.</span><span class="sxs-lookup"><span data-stu-id="fbdf9-103">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>

<span data-ttu-id="fbdf9-104">[**\<system.serviceModel >**](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="fbdf9-104">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="fbdf9-105">&nbsp;&nbsp;**\<Routing >**</span><span class="sxs-lookup"><span data-stu-id="fbdf9-105">&nbsp;&nbsp;**\<routing>**</span></span>

## <a name="syntax"></a><span data-ttu-id="fbdf9-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="fbdf9-106">Syntax</span></span>

```xml
<system.serviceModel>
  <routing>
    <filters>
      <filter customType="String" 
              filterData="String" 
              filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath" 
              name="String" />
    </filters>
    <routingTables>
      <table name="String">
        <entries>
          <add endpoint="String" 
               filterName="String" 
               priority="Integer" />
        </entries>
      </table>
    </routingTables>
  </routing>
</system.serviceModel>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fbdf9-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fbdf9-107">Attributes and elements</span></span>

<span data-ttu-id="fbdf9-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fbdf9-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="fbdf9-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fbdf9-109">Attributes</span></span>

<span data-ttu-id="fbdf9-110">Brak</span><span class="sxs-lookup"><span data-stu-id="fbdf9-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="fbdf9-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fbdf9-111">Child elements</span></span>

|     | <span data-ttu-id="fbdf9-112">Opis</span><span class="sxs-lookup"><span data-stu-id="fbdf9-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="fbdf9-113">**\<Filtry >**</span><span class="sxs-lookup"><span data-stu-id="fbdf9-113">**\<filters>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md) | <span data-ttu-id="fbdf9-114">Zawiera zestaw filtrów routingu, które określają, że typ MessageFilter Windows Communication Foundation (WCF) będą używane podczas oceniania wiadomości przychodzących.</span><span class="sxs-lookup"><span data-stu-id="fbdf9-114">Contains a set of routing filters that determine the type of Windows Communication Foundation (WCF) MessageFilter will be used when evaluating incoming messages.</span></span> |
| [<span data-ttu-id="fbdf9-115">**\<filterTables >**</span><span class="sxs-lookup"><span data-stu-id="fbdf9-115">**\<filterTables>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) | <span data-ttu-id="fbdf9-116">Zawiera mapowania między filtrami i docelowymi punktami końcowymi, aby określić, który punkt końcowy do użycia podczas kryteria filtru są spełnione.</span><span class="sxs-lookup"><span data-stu-id="fbdf9-116">Contains mappings between the routing filters and the target endpoints to specify which endpoint to use when the filter matches.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="fbdf9-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fbdf9-117">Parent elements</span></span>

|     | <span data-ttu-id="fbdf9-118">Opis</span><span class="sxs-lookup"><span data-stu-id="fbdf9-118">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="fbdf9-119">**\<System. ServiceModel >**</span><span class="sxs-lookup"><span data-stu-id="fbdf9-119">**\<system.ServiceModel>**</span></span> | <span data-ttu-id="fbdf9-120">Element główny wszystkich elementów konfiguracji usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="fbdf9-120">The root element of all WCF configuration elements.</span></span> |

## <a name="see-also"></a><span data-ttu-id="fbdf9-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fbdf9-121">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
