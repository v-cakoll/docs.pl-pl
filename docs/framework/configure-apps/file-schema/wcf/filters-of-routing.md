---
title: '&lt;filters&gt; w &lt;routing&gt;'
ms.date: 03/30/2017
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
ms.openlocfilehash: 4a6a079264c54ac481c3a8996b74ac924c33bdc7
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150893"
---
# <a name="ltfiltersgt-of-ltroutinggt"></a><span data-ttu-id="31841-102">&lt;filters&gt; w &lt;routing&gt;</span><span class="sxs-lookup"><span data-stu-id="31841-102">&lt;filters&gt; of &lt;routing&gt;</span></span>

<span data-ttu-id="31841-103">Reprezentuje sekcję konfiguracji określającą zestaw filtrów routingu, które określają typ obiektu programu Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> używanego podczas oceniania wiadomości przychodzących.</span><span class="sxs-lookup"><span data-stu-id="31841-103">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span>

<span data-ttu-id="31841-104">[**\<system.serviceModel >**](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="31841-104">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="31841-105">&nbsp;&nbsp;[**\<Routing >**](routing.md) </span><span class="sxs-lookup"><span data-stu-id="31841-105">&nbsp;&nbsp;[**\<routing>**](routing.md) </span></span>  
<span data-ttu-id="31841-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Filtry >**</span><span class="sxs-lookup"><span data-stu-id="31841-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<filters>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="31841-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="31841-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="31841-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="31841-108">Attributes and elements</span></span>

<span data-ttu-id="31841-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="31841-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="31841-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="31841-110">Attributes</span></span>

<span data-ttu-id="31841-111">Brak</span><span class="sxs-lookup"><span data-stu-id="31841-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="31841-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="31841-112">Child elements</span></span>

|     | <span data-ttu-id="31841-113">Opis</span><span class="sxs-lookup"><span data-stu-id="31841-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="31841-114">**\<Filtr >**</span><span class="sxs-lookup"><span data-stu-id="31841-114">**\<filter>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | <span data-ttu-id="31841-115">Zawiera filtr routingu, który określa typ programu Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> będą używane podczas oceniania wiadomości przychodzących.</span><span class="sxs-lookup"><span data-stu-id="31841-115">Contains a routing filter that determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> will be used when evaluating incoming messages.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="31841-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="31841-116">Parent elements</span></span>

|     | <span data-ttu-id="31841-117">Opis</span><span class="sxs-lookup"><span data-stu-id="31841-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="31841-118">**\<Routing >**</span><span class="sxs-lookup"><span data-stu-id="31841-118">**\<routing>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="31841-119">Reprezentuje sekcję konfiguracji określającą zestaw filtrów routingu, które określają typ obiektu programu Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> używanego podczas oceniania wiadomości przychodzących, jak również routingu definiujące miejsce docelowe punktów końcowych do tabel wysyłanie komunikatów do gdy kryteria filtru.</span><span class="sxs-lookup"><span data-stu-id="31841-119">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="31841-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="31841-120">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
