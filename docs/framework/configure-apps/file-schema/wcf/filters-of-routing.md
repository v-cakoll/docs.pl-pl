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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9dddd9f9ba5f4c2cea7e92c666e8d224ccf21cee
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltfiltersgt-of-ltroutinggt"></a><span data-ttu-id="e79e0-102">&lt;filters&gt; w &lt;routing&gt;</span><span class="sxs-lookup"><span data-stu-id="e79e0-102">&lt;filters&gt; of &lt;routing&gt;</span></span>

<span data-ttu-id="e79e0-103">Reprezentuje sekcję konfiguracji określającą zestaw filtrów routingu, które określają typ [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> używanego podczas oceniania wiadomości przychodzących.</span><span class="sxs-lookup"><span data-stu-id="e79e0-103">Represents a configuration section for defining a set of routing filters, which determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span>

<span data-ttu-id="e79e0-104">[**\<system.serviceModel >**](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="e79e0-104">[**\<system.serviceModel>**](system-servicemodel.md) </span></span>  
<span data-ttu-id="e79e0-105">&nbsp;&nbsp;[**\<Routing >**](routing.md) </span><span class="sxs-lookup"><span data-stu-id="e79e0-105">&nbsp;&nbsp;[**\<routing>**](routing.md) </span></span>  
<span data-ttu-id="e79e0-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Filtry >**</span><span class="sxs-lookup"><span data-stu-id="e79e0-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<filters>**</span></span>

## <a name="syntax"></a><span data-ttu-id="e79e0-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="e79e0-107">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="e79e0-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e79e0-108">Attributes and elements</span></span>

<span data-ttu-id="e79e0-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e79e0-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="e79e0-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e79e0-110">Attributes</span></span>

<span data-ttu-id="e79e0-111">Brak</span><span class="sxs-lookup"><span data-stu-id="e79e0-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="e79e0-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e79e0-112">Child elements</span></span>

|     | <span data-ttu-id="e79e0-113">Opis</span><span class="sxs-lookup"><span data-stu-id="e79e0-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="e79e0-114">**\<Filtr >**</span><span class="sxs-lookup"><span data-stu-id="e79e0-114">**\<filter>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | <span data-ttu-id="e79e0-115">Zawiera filtr routingu, która określa typ [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> będą używane podczas oceniania wiadomości przychodzących.</span><span class="sxs-lookup"><span data-stu-id="e79e0-115">Contains a routing filter that determines the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> will be used when evaluating incoming messages.</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="e79e0-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e79e0-116">Parent elements</span></span>

|     | <span data-ttu-id="e79e0-117">Opis</span><span class="sxs-lookup"><span data-stu-id="e79e0-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="e79e0-118">**\<Routing >**</span><span class="sxs-lookup"><span data-stu-id="e79e0-118">**\<routing>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="e79e0-119">Reprezentuje sekcję konfiguracji określającą zestaw filtrów routingu, które określają typ [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> używanego podczas oceniania wiadomości przychodzących, jak również routingu tabel docelowych punktów końcowych do wysyłania komunikatów do podczas definiowania kryteria filtru.</span><span class="sxs-lookup"><span data-stu-id="e79e0-119">Represents a configuration section for defining a set of routing filters, which determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span> |

## <a name="see-also"></a><span data-ttu-id="e79e0-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e79e0-120">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
