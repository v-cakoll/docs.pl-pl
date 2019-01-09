---
title: '&lt;Routing&gt;'
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: 220c18ab8ea6222fcf7d9fb8a93950281c9de796
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145149"
---
# <a name="ltroutinggt"></a><span data-ttu-id="1be58-102">&lt;Routing&gt;</span><span class="sxs-lookup"><span data-stu-id="1be58-102">&lt;routing&gt;</span></span>

<span data-ttu-id="1be58-103">Reprezentuje sekcję konfiguracji określającą zestaw filtrów routingu, które określają typ obiektu programu Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> używanego podczas oceniania wiadomości przychodzących, jak również routingu definiujące miejsce docelowe punktów końcowych do tabel wysyłanie komunikatów do gdy kryteria filtru.</span><span class="sxs-lookup"><span data-stu-id="1be58-103">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>

<span data-ttu-id="1be58-104">[**\<system.serviceModel >**](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="1be58-104">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="1be58-105">&nbsp;&nbsp;**\<Routing >**</span><span class="sxs-lookup"><span data-stu-id="1be58-105">&nbsp;&nbsp;**\<routing>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="1be58-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="1be58-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1be58-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1be58-107">Attributes and elements</span></span>

<span data-ttu-id="1be58-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1be58-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="1be58-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1be58-109">Attributes</span></span>

<span data-ttu-id="1be58-110">Brak</span><span class="sxs-lookup"><span data-stu-id="1be58-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="1be58-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1be58-111">Child elements</span></span>

|     | <span data-ttu-id="1be58-112">Opis</span><span class="sxs-lookup"><span data-stu-id="1be58-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="1be58-113">**\<Filtry >**</span><span class="sxs-lookup"><span data-stu-id="1be58-113">**\<filters>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md) | <span data-ttu-id="1be58-114">Zawiera zestaw filtrów routingu, które określają typ MessageFilter Windows Communication Foundation (WCF), będzie ono używane podczas oceniania wiadomości przychodzących.</span><span class="sxs-lookup"><span data-stu-id="1be58-114">Contains a set of routing filters that determine the type of Windows Communication Foundation (WCF) MessageFilter will be used when evaluating incoming messages.</span></span> |
| [<span data-ttu-id="1be58-115">**\<filterTables >**</span><span class="sxs-lookup"><span data-stu-id="1be58-115">**\<filterTables>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) | <span data-ttu-id="1be58-116">Zawiera mapowania między filtrami i docelowymi punktami końcowymi, aby określić, który punkt końcowy do użycia podczas filtr dopasowuje wartość.</span><span class="sxs-lookup"><span data-stu-id="1be58-116">Contains mappings between the routing filters and the target endpoints to specify which endpoint to use when the filter matches.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="1be58-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1be58-117">Parent elements</span></span>

|     | <span data-ttu-id="1be58-118">Opis</span><span class="sxs-lookup"><span data-stu-id="1be58-118">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="1be58-119">**\<System. ServiceModel >**</span><span class="sxs-lookup"><span data-stu-id="1be58-119">**\<system.ServiceModel>**</span></span> | <span data-ttu-id="1be58-120">Element główny wszystkich elementów konfiguracji programu WCF.</span><span class="sxs-lookup"><span data-stu-id="1be58-120">The root element of all WCF configuration elements.</span></span> |

## <a name="see-also"></a><span data-ttu-id="1be58-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1be58-121">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
