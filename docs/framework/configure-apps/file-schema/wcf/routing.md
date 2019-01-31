---
title: <routing>
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: cc7c1a64f9481a7ab41cf35241ade04bd690dae0
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55275577"
---
# <a name="routing"></a><span data-ttu-id="9607b-101">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="9607b-101">\<routing></span></span>

<span data-ttu-id="9607b-102">Reprezentuje sekcję konfiguracji określającą zestaw filtrów routingu, które określają typ obiektu programu Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> używanego podczas oceniania wiadomości przychodzących, jak również routingu definiujące miejsce docelowe punktów końcowych do tabel wysyłanie komunikatów do gdy kryteria filtru.</span><span class="sxs-lookup"><span data-stu-id="9607b-102">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>

<span data-ttu-id="9607b-103">[**\<system.serviceModel>**](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="9607b-103">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="9607b-104">&nbsp;&nbsp;**\<routing>**</span><span class="sxs-lookup"><span data-stu-id="9607b-104">&nbsp;&nbsp;**\<routing>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="9607b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="9607b-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9607b-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9607b-106">Attributes and elements</span></span>

<span data-ttu-id="9607b-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9607b-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="9607b-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9607b-108">Attributes</span></span>

<span data-ttu-id="9607b-109">Brak</span><span class="sxs-lookup"><span data-stu-id="9607b-109">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="9607b-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9607b-110">Child elements</span></span>

|     | <span data-ttu-id="9607b-111">Opis</span><span class="sxs-lookup"><span data-stu-id="9607b-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="9607b-112">**\<filters>**</span><span class="sxs-lookup"><span data-stu-id="9607b-112">**\<filters>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md) | <span data-ttu-id="9607b-113">Zawiera zestaw filtrów routingu, które określają typ MessageFilter Windows Communication Foundation (WCF), będzie ono używane podczas oceniania wiadomości przychodzących.</span><span class="sxs-lookup"><span data-stu-id="9607b-113">Contains a set of routing filters that determine the type of Windows Communication Foundation (WCF) MessageFilter will be used when evaluating incoming messages.</span></span> |
| [<span data-ttu-id="9607b-114">**\<filterTables>**</span><span class="sxs-lookup"><span data-stu-id="9607b-114">**\<filterTables>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) | <span data-ttu-id="9607b-115">Zawiera mapowania między filtrami i docelowymi punktami końcowymi, aby określić, który punkt końcowy do użycia podczas filtr dopasowuje wartość.</span><span class="sxs-lookup"><span data-stu-id="9607b-115">Contains mappings between the routing filters and the target endpoints to specify which endpoint to use when the filter matches.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="9607b-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9607b-116">Parent elements</span></span>

|     | <span data-ttu-id="9607b-117">Opis</span><span class="sxs-lookup"><span data-stu-id="9607b-117">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="9607b-118">**\<system.ServiceModel>**</span><span class="sxs-lookup"><span data-stu-id="9607b-118">**\<system.ServiceModel>**</span></span> | <span data-ttu-id="9607b-119">Element główny wszystkich elementów konfiguracji programu WCF.</span><span class="sxs-lookup"><span data-stu-id="9607b-119">The root element of all WCF configuration elements.</span></span> |

## <a name="see-also"></a><span data-ttu-id="9607b-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9607b-120">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
