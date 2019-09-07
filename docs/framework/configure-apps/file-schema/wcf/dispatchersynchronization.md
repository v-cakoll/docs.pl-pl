---
title: <dispatcherSynchronization>
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: b95f25217c2a3558846cc7a0ef43e21aacd2ee2a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398001"
---
# <a name="dispatchersynchronization"></a><span data-ttu-id="a2eac-101">\<dispatcherSynchronization></span><span class="sxs-lookup"><span data-stu-id="a2eac-101">\<dispatcherSynchronization></span></span>
  
<span data-ttu-id="a2eac-102">Określa zachowanie punktu końcowego, które umożliwia usłudze wysyłanie odpowiedzi asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="a2eac-102">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>  
  
<span data-ttu-id="a2eac-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a2eac-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a2eac-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a2eac-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a2eac-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a2eac-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="a2eac-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a2eac-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="a2eac-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a2eac-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="a2eac-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<dispatcherSynchronization >**</span><span class="sxs-lookup"><span data-stu-id="a2eac-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dispatcherSynchronization>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2eac-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="a2eac-109">Syntax</span></span>  
  
```xml  
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean"
                                   maxPendingReceives="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="a2eac-110">Typ</span><span class="sxs-lookup"><span data-stu-id="a2eac-110">Type</span></span>  
  
`Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a2eac-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a2eac-111">Attributes and elements</span></span>  
  
<span data-ttu-id="a2eac-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a2eac-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a2eac-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a2eac-113">Attributes</span></span>

| <span data-ttu-id="a2eac-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a2eac-114">Attribute</span></span>               | <span data-ttu-id="a2eac-115">Opis</span><span class="sxs-lookup"><span data-stu-id="a2eac-115">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="a2eac-116">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="a2eac-116">asynchronousSendEnabled</span></span> | <span data-ttu-id="a2eac-117">Wartość logiczna określająca, czy jest włączone asynchroniczne wysyłanie.</span><span class="sxs-lookup"><span data-stu-id="a2eac-117">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="a2eac-118">Liczba całkowita określająca liczbę współbieżnych odbiorów, które mogą być wystawiane w kanale.</span><span class="sxs-lookup"><span data-stu-id="a2eac-118">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="a2eac-119">Ta wartość powinna być skonfigurowana tylko po poprawnym skonfigurowaniu zachowania ograniczania usługi.</span><span class="sxs-lookup"><span data-stu-id="a2eac-119">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="a2eac-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a2eac-120">Child elements</span></span>

<span data-ttu-id="a2eac-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="a2eac-121">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a2eac-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a2eac-122">Parent elements</span></span>

| <span data-ttu-id="a2eac-123">Element</span><span class="sxs-lookup"><span data-stu-id="a2eac-123">Element</span></span> | <span data-ttu-id="a2eac-124">Opis</span><span class="sxs-lookup"><span data-stu-id="a2eac-124">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="a2eac-125">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="a2eac-125">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="a2eac-126">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="a2eac-126">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="a2eac-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a2eac-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement>
- <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>
