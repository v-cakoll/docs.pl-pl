---
title: <dispatcherSynchronization>
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: 7336c9f7d8a117f9a9bfd338e47941eeb648fa51
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925846"
---
# <a name="dispatchersynchronization"></a><span data-ttu-id="2fd80-101">\<dispatcherSynchronization></span><span class="sxs-lookup"><span data-stu-id="2fd80-101">\<dispatcherSynchronization></span></span>
  
<span data-ttu-id="2fd80-102">Określa zachowanie punktu końcowego, które umożliwia usłudze wysyłanie odpowiedzi asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="2fd80-102">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>  
  
<span data-ttu-id="2fd80-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="2fd80-103">\<system.serviceModel></span></span>  
<span data-ttu-id="2fd80-104">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="2fd80-104">\<behaviors></span></span>  
<span data-ttu-id="2fd80-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="2fd80-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="2fd80-106">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="2fd80-106">\<behavior></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fd80-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="2fd80-107">Syntax</span></span>  
  
```xml  
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean"
                                   maxPendingReceives="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="2fd80-108">Typ</span><span class="sxs-lookup"><span data-stu-id="2fd80-108">Type</span></span>  
  
`Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2fd80-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2fd80-109">Attributes and elements</span></span>  
  
<span data-ttu-id="2fd80-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2fd80-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2fd80-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2fd80-111">Attributes</span></span>

| <span data-ttu-id="2fd80-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2fd80-112">Attribute</span></span>               | <span data-ttu-id="2fd80-113">Opis</span><span class="sxs-lookup"><span data-stu-id="2fd80-113">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="2fd80-114">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="2fd80-114">asynchronousSendEnabled</span></span> | <span data-ttu-id="2fd80-115">Wartość logiczna określająca, czy jest włączone asynchroniczne wysyłanie.</span><span class="sxs-lookup"><span data-stu-id="2fd80-115">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="2fd80-116">Liczba całkowita określająca liczbę współbieżnych odbiorów, które mogą być wystawiane w kanale.</span><span class="sxs-lookup"><span data-stu-id="2fd80-116">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="2fd80-117">Ta wartość powinna być skonfigurowana tylko po poprawnym skonfigurowaniu zachowania ograniczania usługi.</span><span class="sxs-lookup"><span data-stu-id="2fd80-117">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="2fd80-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2fd80-118">Child elements</span></span>

<span data-ttu-id="2fd80-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="2fd80-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2fd80-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2fd80-120">Parent elements</span></span>

| <span data-ttu-id="2fd80-121">Element</span><span class="sxs-lookup"><span data-stu-id="2fd80-121">Element</span></span> | <span data-ttu-id="2fd80-122">Opis</span><span class="sxs-lookup"><span data-stu-id="2fd80-122">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="2fd80-123">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="2fd80-123">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="2fd80-124">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="2fd80-124">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="2fd80-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2fd80-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement>
- <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>
