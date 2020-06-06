---
title: <routing>
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: fcf2d4eec93fd7127c6f800e1c739ad1fac49203
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399971"
---
# \<routing>

<span data-ttu-id="9de9a-101">Reprezentuje sekcję konfiguracji określającą zestaw filtrów routingu, które określają typ Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> , który ma być używany podczas oceniania wiadomości przychodzących, a także tabele routingu, które definiują docelowe punkty końcowe do wysyłania komunikatów, gdy filtr jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="9de9a-101">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<routing>**
  
## <a name="syntax"></a><span data-ttu-id="9de9a-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="9de9a-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9de9a-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9de9a-103">Attributes and elements</span></span>

<span data-ttu-id="9de9a-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9de9a-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="9de9a-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9de9a-105">Attributes</span></span>

<span data-ttu-id="9de9a-106">Brak</span><span class="sxs-lookup"><span data-stu-id="9de9a-106">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="9de9a-107">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9de9a-107">Child elements</span></span>

|     | <span data-ttu-id="9de9a-108">Opis</span><span class="sxs-lookup"><span data-stu-id="9de9a-108">Description</span></span> |
| --- | ----------- |
| [**\<filters>**](filters-of-routing.md) | <span data-ttu-id="9de9a-109">Zawiera zestaw filtrów routingu, które określają typ Windows Communication Foundation (WCF), który będzie używany podczas oceniania wiadomości przychodzących.</span><span class="sxs-lookup"><span data-stu-id="9de9a-109">Contains a set of routing filters that determine the type of Windows Communication Foundation (WCF) MessageFilter will be used when evaluating incoming messages.</span></span> |
| [**\<filterTables>**](filtertables.md) | <span data-ttu-id="9de9a-110">Zawiera mapowania między filtrami routingu i docelowymi punktami końcowymi, aby określić, który punkt końcowy ma być używany, gdy filtr jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="9de9a-110">Contains mappings between the routing filters and the target endpoints to specify which endpoint to use when the filter matches.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="9de9a-111">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9de9a-111">Parent elements</span></span>

|     | <span data-ttu-id="9de9a-112">Opis</span><span class="sxs-lookup"><span data-stu-id="9de9a-112">Description</span></span> |
| --- | ----------- |
| **\<system.ServiceModel>** | <span data-ttu-id="9de9a-113">Element główny wszystkich elementów konfiguracji WCF.</span><span class="sxs-lookup"><span data-stu-id="9de9a-113">The root element of all WCF configuration elements.</span></span> |

## <a name="see-also"></a><span data-ttu-id="9de9a-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9de9a-114">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
