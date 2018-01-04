---
title: '&lt;dispatcherSynchronization&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 57477ea60337e5032b80bd9ae8da850099dd08f7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltdispatchersynchronizationgt"></a><span data-ttu-id="166e4-102">&lt;dispatcherSynchronization&gt;</span><span class="sxs-lookup"><span data-stu-id="166e4-102">&lt;dispatcherSynchronization&gt;</span></span>

<span data-ttu-id="166e4-103">Określa zachowanie punktu końcowego, który włącza usługę Aby wysłać odpowiedzi asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="166e4-103">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>

<span data-ttu-id="166e4-104">\<system.serviceModel > \<zachowania > \<endpointBehaviors > \<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="166e4-104">\<system.serviceModel> \<behaviors> \<endpointBehaviors> \<behavior></span></span>

## <a name="syntax"></a><span data-ttu-id="166e4-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="166e4-105">Syntax</span></span>

```xml
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean" 
                                   maxPendingReceives="Integer" />
```

## <a name="type"></a><span data-ttu-id="166e4-106">Typ</span><span class="sxs-lookup"><span data-stu-id="166e4-106">Type</span></span>

`Type`

## <a name="attributes-and-elements"></a><span data-ttu-id="166e4-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="166e4-107">Attributes and elements</span></span>

<span data-ttu-id="166e4-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="166e4-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="166e4-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="166e4-109">Attributes</span></span>

| <span data-ttu-id="166e4-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="166e4-110">Attribute</span></span>               | <span data-ttu-id="166e4-111">Opis</span><span class="sxs-lookup"><span data-stu-id="166e4-111">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="166e4-112">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="166e4-112">asynchronousSendEnabled</span></span> | <span data-ttu-id="166e4-113">Wartość logiczna określająca czy zachowanie przesyłu asynchronicznego jest włączone.</span><span class="sxs-lookup"><span data-stu-id="166e4-113">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="166e4-114">Liczba całkowita, która określa, że liczba równoczesnych pobrań, które mogą być wystawiane w kanale.</span><span class="sxs-lookup"><span data-stu-id="166e4-114">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="166e4-115">Ta wartość musi być skonfigurowany tylko wtedy, gdy zostały poprawnie skonfigurowane zachowanie ograniczenia przepustowości usługi.</span><span class="sxs-lookup"><span data-stu-id="166e4-115">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="166e4-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="166e4-116">Child elements</span></span>

<span data-ttu-id="166e4-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="166e4-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="166e4-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="166e4-118">Parent elements</span></span>

| <span data-ttu-id="166e4-119">Element</span><span class="sxs-lookup"><span data-stu-id="166e4-119">Element</span></span> | <span data-ttu-id="166e4-120">Opis</span><span class="sxs-lookup"><span data-stu-id="166e4-120">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="166e4-121">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="166e4-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="166e4-122">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="166e4-122">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="166e4-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="166e4-123">See also</span></span>

 <span data-ttu-id="166e4-124"><xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement><xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior></span><span class="sxs-lookup"><span data-stu-id="166e4-124"><xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement> <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior></span></span>
