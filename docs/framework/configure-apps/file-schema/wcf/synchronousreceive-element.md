---
title: <synchronousReceive>, element
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: b3f4860be6b7edac776a1c30611271b2eb36968e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399494"
---
# <a name="synchronousreceive-element"></a><span data-ttu-id="8b5b7-102">\<synchronousReceive>, element</span><span class="sxs-lookup"><span data-stu-id="8b5b7-102">\<synchronousReceive> element</span></span>
<span data-ttu-id="8b5b7-103">Ten element konfiguracji służy do określania zachowania w czasie wykonywania w przypadku otrzymywania wiadomości w usłudze lub aplikacji klienckiej.</span><span class="sxs-lookup"><span data-stu-id="8b5b7-103">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="8b5b7-104">Nie ma żadnych atrybutów ani elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="8b5b7-104">It does not have any attributes or child elements.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<synchronousReceive>**  
  
## <a name="syntax"></a><span data-ttu-id="8b5b7-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="8b5b7-105">Syntax</span></span>  
  
```xml  
<synchronousReceive />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8b5b7-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8b5b7-106">Attributes and Elements</span></span>  
 <span data-ttu-id="8b5b7-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8b5b7-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8b5b7-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8b5b7-108">Attributes</span></span>  
 <span data-ttu-id="8b5b7-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="8b5b7-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8b5b7-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8b5b7-110">Child Elements</span></span>  
 <span data-ttu-id="8b5b7-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="8b5b7-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8b5b7-112">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8b5b7-112">Parent Elements</span></span>  
  
|<span data-ttu-id="8b5b7-113">Element</span><span class="sxs-lookup"><span data-stu-id="8b5b7-113">Element</span></span>|<span data-ttu-id="8b5b7-114">Opis</span><span class="sxs-lookup"><span data-stu-id="8b5b7-114">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="8b5b7-115">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="8b5b7-115">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b5b7-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8b5b7-116">Remarks</span></span>  
 <span data-ttu-id="8b5b7-117">Użyj tego zachowania, aby nakazać odbiornikowi kanału użycie synchronicznego odbioru zamiast domyślnego, asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="8b5b7-117">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> <span data-ttu-id="8b5b7-118">Windows Communication Foundation (WCF) wystawia nowy wątek do pompy dla każdego zaakceptowanego kanału.</span><span class="sxs-lookup"><span data-stu-id="8b5b7-118">Windows Communication Foundation (WCF) issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="8b5b7-119">Jeśli istnieje wiele kanałów, istnieje możliwość uruchomienia poza wątkiem.</span><span class="sxs-lookup"><span data-stu-id="8b5b7-119">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b5b7-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8b5b7-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
