---
title: '&lt;dispatcherSynchronization&gt;'
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: 34c12a05ee363df6b6cfc9ff3809bab50ee8d522
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltdispatchersynchronizationgt"></a><span data-ttu-id="b527d-102">&lt;dispatcherSynchronization&gt;</span><span class="sxs-lookup"><span data-stu-id="b527d-102">&lt;dispatcherSynchronization&gt;</span></span>

<span data-ttu-id="b527d-103">Określa zachowanie punktu końcowego, który włącza usługę Aby wysłać odpowiedzi asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="b527d-103">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>

<span data-ttu-id="b527d-104">\<system.serviceModel > \<zachowania > \<endpointBehaviors > \<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="b527d-104">\<system.serviceModel> \<behaviors> \<endpointBehaviors> \<behavior></span></span>

## <a name="syntax"></a><span data-ttu-id="b527d-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b527d-105">Syntax</span></span>

```xml
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean" 
                                   maxPendingReceives="Integer" />
```

## <a name="type"></a><span data-ttu-id="b527d-106">Typ</span><span class="sxs-lookup"><span data-stu-id="b527d-106">Type</span></span>

`Type`

## <a name="attributes-and-elements"></a><span data-ttu-id="b527d-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b527d-107">Attributes and elements</span></span>

<span data-ttu-id="b527d-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b527d-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="b527d-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b527d-109">Attributes</span></span>

| <span data-ttu-id="b527d-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b527d-110">Attribute</span></span>               | <span data-ttu-id="b527d-111">Opis</span><span class="sxs-lookup"><span data-stu-id="b527d-111">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="b527d-112">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="b527d-112">asynchronousSendEnabled</span></span> | <span data-ttu-id="b527d-113">Wartość logiczna określająca czy zachowanie przesyłu asynchronicznego jest włączone.</span><span class="sxs-lookup"><span data-stu-id="b527d-113">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="b527d-114">Liczba całkowita, która określa, że liczba równoczesnych pobrań, które mogą być wystawiane w kanale.</span><span class="sxs-lookup"><span data-stu-id="b527d-114">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="b527d-115">Ta wartość musi być skonfigurowany tylko wtedy, gdy zostały poprawnie skonfigurowane zachowanie ograniczenia przepustowości usługi.</span><span class="sxs-lookup"><span data-stu-id="b527d-115">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="b527d-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b527d-116">Child elements</span></span>

<span data-ttu-id="b527d-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="b527d-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b527d-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b527d-118">Parent elements</span></span>

| <span data-ttu-id="b527d-119">Element</span><span class="sxs-lookup"><span data-stu-id="b527d-119">Element</span></span> | <span data-ttu-id="b527d-120">Opis</span><span class="sxs-lookup"><span data-stu-id="b527d-120">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="b527d-121">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="b527d-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="b527d-122">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="b527d-122">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="b527d-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b527d-123">See also</span></span>

 <span data-ttu-id="b527d-124"><xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement><xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior></span><span class="sxs-lookup"><span data-stu-id="b527d-124"><xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement> <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior></span></span>
