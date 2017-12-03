---
title: '&lt;filters&gt; w &lt;routing&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c9dd9faf63ade725bb8bea12b40390fd30c91973
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltfiltersgt-of-ltroutinggt"></a><span data-ttu-id="504d5-102">&lt;filters&gt; w &lt;routing&gt;</span><span class="sxs-lookup"><span data-stu-id="504d5-102">&lt;filters&gt; of &lt;routing&gt;</span></span>

<span data-ttu-id="504d5-103">Reprezentuje sekcję konfiguracji określającą zestaw filtrów routingu, które określają typ [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> używanego podczas oceniania wiadomości przychodzących.</span><span class="sxs-lookup"><span data-stu-id="504d5-103">Represents a configuration section for defining a set of routing filters, which determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span>

<span data-ttu-id="504d5-104">[**\<system.serviceModel >**](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="504d5-104">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="504d5-105">&nbsp;&nbsp;[**\<Routing >**](routing.md) </span><span class="sxs-lookup"><span data-stu-id="504d5-105">&nbsp;&nbsp;[**\<routing>**](routing.md) </span></span>  
<span data-ttu-id="504d5-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Filtry >**</span><span class="sxs-lookup"><span data-stu-id="504d5-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<filters>**</span></span>

## <a name="syntax"></a><span data-ttu-id="504d5-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="504d5-107">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="504d5-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="504d5-108">Attributes and elements</span></span>

<span data-ttu-id="504d5-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="504d5-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="504d5-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="504d5-110">Attributes</span></span>

<span data-ttu-id="504d5-111">Brak</span><span class="sxs-lookup"><span data-stu-id="504d5-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="504d5-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="504d5-112">Child elements</span></span>

|     | <span data-ttu-id="504d5-113">Opis</span><span class="sxs-lookup"><span data-stu-id="504d5-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="504d5-114">**\<Filtr >**</span><span class="sxs-lookup"><span data-stu-id="504d5-114">**\<filter>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | <span data-ttu-id="504d5-115">Zawiera filtr routingu, która określa typ [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> będą używane podczas oceniania wiadomości przychodzących.</span><span class="sxs-lookup"><span data-stu-id="504d5-115">Contains a routing filter that determines the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> will be used when evaluating incoming messages.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="504d5-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="504d5-116">Parent elements</span></span>

|     | <span data-ttu-id="504d5-117">Opis</span><span class="sxs-lookup"><span data-stu-id="504d5-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="504d5-118">**\<Routing >**</span><span class="sxs-lookup"><span data-stu-id="504d5-118">**\<routing>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="504d5-119">Reprezentuje sekcję konfiguracji określającą zestaw filtrów routingu, które określają typ [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> używanego podczas oceniania wiadomości przychodzących, jak również routingu tabel docelowych punktów końcowych do wysyłania komunikatów do podczas definiowania kryteria filtru.</span><span class="sxs-lookup"><span data-stu-id="504d5-119">Represents a configuration section for defining a set of routing filters, which determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="504d5-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="504d5-120">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
