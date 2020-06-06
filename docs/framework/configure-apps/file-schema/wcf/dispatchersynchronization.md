---
title: <dispatcherSynchronization>
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: b95f25217c2a3558846cc7a0ef43e21aacd2ee2a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398001"
---
# \<dispatcherSynchronization>
  
<span data-ttu-id="69e26-101">Określa zachowanie punktu końcowego, które umożliwia usłudze wysyłanie odpowiedzi asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="69e26-101">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dispatcherSynchronization>**  
  
## <a name="syntax"></a><span data-ttu-id="69e26-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="69e26-102">Syntax</span></span>  
  
```xml  
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean"
                                   maxPendingReceives="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="69e26-103">Typ</span><span class="sxs-lookup"><span data-stu-id="69e26-103">Type</span></span>  
  
`Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="69e26-104">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="69e26-104">Attributes and elements</span></span>  
  
<span data-ttu-id="69e26-105">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="69e26-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="69e26-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="69e26-106">Attributes</span></span>

| <span data-ttu-id="69e26-107">Atrybut</span><span class="sxs-lookup"><span data-stu-id="69e26-107">Attribute</span></span>               | <span data-ttu-id="69e26-108">Opis</span><span class="sxs-lookup"><span data-stu-id="69e26-108">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="69e26-109">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="69e26-109">asynchronousSendEnabled</span></span> | <span data-ttu-id="69e26-110">Wartość logiczna określająca, czy jest włączone asynchroniczne wysyłanie.</span><span class="sxs-lookup"><span data-stu-id="69e26-110">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="69e26-111">Liczba całkowita określająca liczbę współbieżnych odbiorów, które mogą być wystawiane w kanale.</span><span class="sxs-lookup"><span data-stu-id="69e26-111">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="69e26-112">Ta wartość powinna być skonfigurowana tylko po poprawnym skonfigurowaniu zachowania ograniczania usługi.</span><span class="sxs-lookup"><span data-stu-id="69e26-112">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="69e26-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="69e26-113">Child elements</span></span>

<span data-ttu-id="69e26-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="69e26-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="69e26-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="69e26-115">Parent elements</span></span>

| <span data-ttu-id="69e26-116">Element</span><span class="sxs-lookup"><span data-stu-id="69e26-116">Element</span></span> | <span data-ttu-id="69e26-117">Opis</span><span class="sxs-lookup"><span data-stu-id="69e26-117">Description</span></span> |  
| ------- | ----------- |  
| [\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="69e26-118">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="69e26-118">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="69e26-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="69e26-119">See also</span></span>

- <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement>
- <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>
