---
title: <filters> dla <routing>
ms.date: 03/30/2017
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
ms.openlocfilehash: c9bc3a2c379e14d8cf687676a3ec40702d150e1e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855238"
---
# <a name="filters-of-routing"></a><span data-ttu-id="9db60-102">\<filters> dla \<routing></span><span class="sxs-lookup"><span data-stu-id="9db60-102">\<filters> of \<routing></span></span>

<span data-ttu-id="9db60-103">Reprezentuje sekcję konfiguracji określającą zestaw filtrów routingu, które określają typ Windows Communication Foundation (WCF), który <xref:System.ServiceModel.Dispatcher.MessageFilter> ma być używany podczas oceniania wiadomości przychodzących.</span><span class="sxs-lookup"><span data-stu-id="9db60-103">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span>

[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<filters>**  
  
## <a name="syntax"></a><span data-ttu-id="9db60-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9db60-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9db60-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9db60-105">Attributes and elements</span></span>

<span data-ttu-id="9db60-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9db60-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="9db60-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9db60-107">Attributes</span></span>

<span data-ttu-id="9db60-108">Brak</span><span class="sxs-lookup"><span data-stu-id="9db60-108">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="9db60-109">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9db60-109">Child elements</span></span>

|     | <span data-ttu-id="9db60-110">Opis</span><span class="sxs-lookup"><span data-stu-id="9db60-110">Description</span></span> |
| --- | ----------- |
| [**\<filter>**](filter.md) | <span data-ttu-id="9db60-111">Zawiera filtr routingu, który określa typ Windows Communication Foundation (WCF), który <xref:System.ServiceModel.Dispatcher.MessageFilter> będzie używany podczas oceniania wiadomości przychodzących.</span><span class="sxs-lookup"><span data-stu-id="9db60-111">Contains a routing filter that determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> will be used when evaluating incoming messages.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="9db60-112">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9db60-112">Parent elements</span></span>

|     | <span data-ttu-id="9db60-113">Opis</span><span class="sxs-lookup"><span data-stu-id="9db60-113">Description</span></span> |
| --- | ----------- |
| [**\<routing>**](routing.md) | <span data-ttu-id="9db60-114">Reprezentuje sekcję konfiguracji określającą zestaw filtrów routingu, które określają typ Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> , który ma być używany podczas oceniania wiadomości przychodzących, a także tabele routingu, które definiują docelowe punkty końcowe do wysyłania komunikatów, gdy filtr jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="9db60-114">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="9db60-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9db60-115">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
