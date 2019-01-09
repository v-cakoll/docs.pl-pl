---
title: '&lt;dispatcherSynchronization&gt;'
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: 86660620113b162a9a5260b7026a64455284d184
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151465"
---
# <a name="ltdispatchersynchronizationgt"></a><span data-ttu-id="e2f3f-102">&lt;dispatcherSynchronization&gt;</span><span class="sxs-lookup"><span data-stu-id="e2f3f-102">&lt;dispatcherSynchronization&gt;</span></span>
  
<span data-ttu-id="e2f3f-103">Określa zachowanie punktu końcowego, które włącza usługę wysłać odpowiedzi asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="e2f3f-103">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>  
  
<span data-ttu-id="e2f3f-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e2f3f-104">\<system.serviceModel></span></span>  
<span data-ttu-id="e2f3f-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="e2f3f-105">\<behaviors></span></span>  
<span data-ttu-id="e2f3f-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="e2f3f-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="e2f3f-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="e2f3f-107">\<behavior></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2f3f-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="e2f3f-108">Syntax</span></span>  
  
```xml  
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean"
                                   maxPendingReceives="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="e2f3f-109">Typ</span><span class="sxs-lookup"><span data-stu-id="e2f3f-109">Type</span></span>  
  
`Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e2f3f-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e2f3f-110">Attributes and elements</span></span>  
  
<span data-ttu-id="e2f3f-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e2f3f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e2f3f-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e2f3f-112">Attributes</span></span>

| <span data-ttu-id="e2f3f-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e2f3f-113">Attribute</span></span>               | <span data-ttu-id="e2f3f-114">Opis</span><span class="sxs-lookup"><span data-stu-id="e2f3f-114">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="e2f3f-115">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="e2f3f-115">asynchronousSendEnabled</span></span> | <span data-ttu-id="e2f3f-116">Wartość logiczna określająca czy zachowanie przesyłu asynchronicznego jest włączone.</span><span class="sxs-lookup"><span data-stu-id="e2f3f-116">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="e2f3f-117">Liczba całkowita, która określa liczbę równoczesnych pobrań, które mogą być wystawiane na kanale.</span><span class="sxs-lookup"><span data-stu-id="e2f3f-117">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="e2f3f-118">Tę wartość należy skonfigurować tylko wtedy, gdy zachowanie ograniczania przepływności usługi zostało poprawnie skonfigurowane.</span><span class="sxs-lookup"><span data-stu-id="e2f3f-118">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="e2f3f-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e2f3f-119">Child elements</span></span>

<span data-ttu-id="e2f3f-120">Brak.</span><span class="sxs-lookup"><span data-stu-id="e2f3f-120">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e2f3f-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e2f3f-121">Parent elements</span></span>

| <span data-ttu-id="e2f3f-122">Element</span><span class="sxs-lookup"><span data-stu-id="e2f3f-122">Element</span></span> | <span data-ttu-id="e2f3f-123">Opis</span><span class="sxs-lookup"><span data-stu-id="e2f3f-123">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="e2f3f-124">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="e2f3f-124">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="e2f3f-125">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="e2f3f-125">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="e2f3f-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e2f3f-126">See also</span></span>

 <span data-ttu-id="e2f3f-127"><xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement><xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior></span><span class="sxs-lookup"><span data-stu-id="e2f3f-127"><xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement> <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior></span></span>
