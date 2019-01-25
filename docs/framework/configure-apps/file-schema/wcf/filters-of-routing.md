---
title: '&lt;filters&gt; w &lt;routing&gt;'
ms.date: 03/30/2017
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
ms.openlocfilehash: 468c10bc06b60f80ce93cf413c02582fe3861f70
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54704436"
---
# <a name="ltfiltersgt-of-ltroutinggt"></a><span data-ttu-id="3b680-102">&lt;filters&gt; w &lt;routing&gt;</span><span class="sxs-lookup"><span data-stu-id="3b680-102">&lt;filters&gt; of &lt;routing&gt;</span></span>

<span data-ttu-id="3b680-103">Reprezentuje sekcję konfiguracji określającą zestaw filtrów routingu, które określają typ obiektu programu Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> używanego podczas oceniania wiadomości przychodzących.</span><span class="sxs-lookup"><span data-stu-id="3b680-103">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span>

<span data-ttu-id="3b680-104">[**\<system.serviceModel>**](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="3b680-104">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="3b680-105">&nbsp;&nbsp;[**\<routing>**](routing.md) </span><span class="sxs-lookup"><span data-stu-id="3b680-105">&nbsp;&nbsp;[**\<routing>**](routing.md) </span></span>  
<span data-ttu-id="3b680-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Filtry >**</span><span class="sxs-lookup"><span data-stu-id="3b680-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<filters>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="3b680-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="3b680-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3b680-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3b680-108">Attributes and elements</span></span>

<span data-ttu-id="3b680-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3b680-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="3b680-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3b680-110">Attributes</span></span>

<span data-ttu-id="3b680-111">Brak</span><span class="sxs-lookup"><span data-stu-id="3b680-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="3b680-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3b680-112">Child elements</span></span>

|     | <span data-ttu-id="3b680-113">Opis</span><span class="sxs-lookup"><span data-stu-id="3b680-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="3b680-114">**\<filter>**</span><span class="sxs-lookup"><span data-stu-id="3b680-114">**\<filter>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | <span data-ttu-id="3b680-115">Zawiera filtr routingu, który określa typ programu Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> będą używane podczas oceniania wiadomości przychodzących.</span><span class="sxs-lookup"><span data-stu-id="3b680-115">Contains a routing filter that determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> will be used when evaluating incoming messages.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="3b680-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3b680-116">Parent elements</span></span>

|     | <span data-ttu-id="3b680-117">Opis</span><span class="sxs-lookup"><span data-stu-id="3b680-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="3b680-118">**\<routing>**</span><span class="sxs-lookup"><span data-stu-id="3b680-118">**\<routing>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="3b680-119">Reprezentuje sekcję konfiguracji określającą zestaw filtrów routingu, które określają typ obiektu programu Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> używanego podczas oceniania wiadomości przychodzących, jak również routingu definiujące miejsce docelowe punktów końcowych do tabel wysyłanie komunikatów do gdy kryteria filtru.</span><span class="sxs-lookup"><span data-stu-id="3b680-119">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="3b680-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3b680-120">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
