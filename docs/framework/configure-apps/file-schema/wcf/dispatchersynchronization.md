---
title: <dispatcherSynchronization>
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: 6be9752e8102a5d4db4fed31aae8ff6d56fdd24e
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55273335"
---
# <a name="dispatchersynchronization"></a><span data-ttu-id="bacce-101">\<dispatcherSynchronization></span><span class="sxs-lookup"><span data-stu-id="bacce-101">\<dispatcherSynchronization></span></span>
  
<span data-ttu-id="bacce-102">Określa zachowanie punktu końcowego, które włącza usługę wysłać odpowiedzi asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="bacce-102">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>  
  
<span data-ttu-id="bacce-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="bacce-103">\<system.serviceModel></span></span>  
<span data-ttu-id="bacce-104">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="bacce-104">\<behaviors></span></span>  
<span data-ttu-id="bacce-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="bacce-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="bacce-106">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="bacce-106">\<behavior></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bacce-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="bacce-107">Syntax</span></span>  
  
```xml  
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean"
                                   maxPendingReceives="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="bacce-108">Typ</span><span class="sxs-lookup"><span data-stu-id="bacce-108">Type</span></span>  
  
`Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bacce-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="bacce-109">Attributes and elements</span></span>  
  
<span data-ttu-id="bacce-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="bacce-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bacce-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bacce-111">Attributes</span></span>

| <span data-ttu-id="bacce-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="bacce-112">Attribute</span></span>               | <span data-ttu-id="bacce-113">Opis</span><span class="sxs-lookup"><span data-stu-id="bacce-113">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="bacce-114">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="bacce-114">asynchronousSendEnabled</span></span> | <span data-ttu-id="bacce-115">Wartość logiczna określająca czy zachowanie przesyłu asynchronicznego jest włączone.</span><span class="sxs-lookup"><span data-stu-id="bacce-115">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="bacce-116">Liczba całkowita, która określa liczbę równoczesnych pobrań, które mogą być wystawiane na kanale.</span><span class="sxs-lookup"><span data-stu-id="bacce-116">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="bacce-117">Tę wartość należy skonfigurować tylko wtedy, gdy zachowanie ograniczania przepływności usługi zostało poprawnie skonfigurowane.</span><span class="sxs-lookup"><span data-stu-id="bacce-117">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="bacce-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="bacce-118">Child elements</span></span>

<span data-ttu-id="bacce-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="bacce-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bacce-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bacce-120">Parent elements</span></span>

| <span data-ttu-id="bacce-121">Element</span><span class="sxs-lookup"><span data-stu-id="bacce-121">Element</span></span> | <span data-ttu-id="bacce-122">Opis</span><span class="sxs-lookup"><span data-stu-id="bacce-122">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="bacce-123">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="bacce-123">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="bacce-124">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="bacce-124">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="bacce-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bacce-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement>
- <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>
