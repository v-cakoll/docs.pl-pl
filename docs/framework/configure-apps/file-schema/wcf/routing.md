---
title: <routing>
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: fcf2d4eec93fd7127c6f800e1c739ad1fac49203
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399971"
---
# <a name="routing"></a><span data-ttu-id="f470d-101">\<> routingu</span><span class="sxs-lookup"><span data-stu-id="f470d-101">\<routing></span></span>

<span data-ttu-id="f470d-102">Reprezentuje sekcję konfiguracji określającą zestaw filtrów routingu, które określają typ Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> , który ma być używany podczas oceniania wiadomości przychodzących, a także tabele routingu, które definiują docelowe punkty końcowe Wysyłaj komunikaty do, gdy filtr jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="f470d-102">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>

<span data-ttu-id="f470d-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f470d-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f470d-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="f470d-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f470d-105">&nbsp;&nbsp;&nbsp;&nbsp; **\<> routingu**</span><span class="sxs-lookup"><span data-stu-id="f470d-105">&nbsp;&nbsp;&nbsp;&nbsp;**\<routing>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="f470d-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="f470d-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f470d-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f470d-107">Attributes and elements</span></span>

<span data-ttu-id="f470d-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f470d-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="f470d-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f470d-109">Attributes</span></span>

<span data-ttu-id="f470d-110">Brak</span><span class="sxs-lookup"><span data-stu-id="f470d-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="f470d-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f470d-111">Child elements</span></span>

|     | <span data-ttu-id="f470d-112">Opis</span><span class="sxs-lookup"><span data-stu-id="f470d-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="f470d-113"> **\<Filtry >** </span><span class="sxs-lookup"><span data-stu-id="f470d-113">**\<filters>**</span></span>](filters-of-routing.md) | <span data-ttu-id="f470d-114">Zawiera zestaw filtrów routingu, które określają typ Windows Communication Foundation (WCF), który będzie używany podczas oceniania wiadomości przychodzących.</span><span class="sxs-lookup"><span data-stu-id="f470d-114">Contains a set of routing filters that determine the type of Windows Communication Foundation (WCF) MessageFilter will be used when evaluating incoming messages.</span></span> |
| [<span data-ttu-id="f470d-115"> **\<filterTables>** </span><span class="sxs-lookup"><span data-stu-id="f470d-115">**\<filterTables>**</span></span>](filtertables.md) | <span data-ttu-id="f470d-116">Zawiera mapowania między filtrami routingu i docelowymi punktami końcowymi, aby określić, który punkt końcowy ma być używany, gdy filtr jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="f470d-116">Contains mappings between the routing filters and the target endpoints to specify which endpoint to use when the filter matches.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="f470d-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f470d-117">Parent elements</span></span>

|     | <span data-ttu-id="f470d-118">Opis</span><span class="sxs-lookup"><span data-stu-id="f470d-118">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="f470d-119">**\<system.ServiceModel>**</span><span class="sxs-lookup"><span data-stu-id="f470d-119">**\<system.ServiceModel>**</span></span> | <span data-ttu-id="f470d-120">Element główny wszystkich elementów konfiguracji WCF.</span><span class="sxs-lookup"><span data-stu-id="f470d-120">The root element of all WCF configuration elements.</span></span> |

## <a name="see-also"></a><span data-ttu-id="f470d-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f470d-121">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
