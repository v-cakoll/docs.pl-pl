---
title: <backupLists>
ms.date: 03/30/2017
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
ms.openlocfilehash: b65cc4d04b5304e93b70509c9db3bc2248accb7f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926435"
---
# <a name="backuplists"></a><span data-ttu-id="c969f-101">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="c969f-101">\<backupLists></span></span>
<span data-ttu-id="c969f-102">Reprezentuje sekcję konfiguracji definiującą zestaw usług kopii zapasowych używanych w obsłudze błędów.</span><span class="sxs-lookup"><span data-stu-id="c969f-102">Represents a configuration section for defining a set of backup services used in error handling.</span></span> <span data-ttu-id="c969f-103">Każdy element podrzędny to lista kopii zapasowych, która wylicza zestaw punktów końcowych, które mają być używane przez usługę routingu w przypadku, gdy podstawowy punkt końcowy nie zostanie osiągnięty.</span><span class="sxs-lookup"><span data-stu-id="c969f-103">Each child element is a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="c969f-104">Jeśli pierwszy punkt końcowy na liście nie działa, usługa routingu automatycznie przejdzie w tryb failover do kolejnej listy.</span><span class="sxs-lookup"><span data-stu-id="c969f-104">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="c969f-105">Dzięki temu można szybko dodać niezawodność do aplikacji bez konieczności uczenia się aplikacji klienckiej, jak obsługiwać złożone wzorce lub wszystkie usługi są wdrażane.</span><span class="sxs-lookup"><span data-stu-id="c969f-105">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
 <span data-ttu-id="c969f-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c969f-106">\<system.serviceModel></span></span>  
<span data-ttu-id="c969f-107">\<> routingu</span><span class="sxs-lookup"><span data-stu-id="c969f-107">\<routing></span></span>  
<span data-ttu-id="c969f-108">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="c969f-108">\<backupLists></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c969f-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="c969f-109">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c969f-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c969f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c969f-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c969f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c969f-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c969f-112">Attributes</span></span>  
 <span data-ttu-id="c969f-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="c969f-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c969f-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c969f-114">Child Elements</span></span>  
  
|<span data-ttu-id="c969f-115">Element</span><span class="sxs-lookup"><span data-stu-id="c969f-115">Element</span></span>|<span data-ttu-id="c969f-116">Opis</span><span class="sxs-lookup"><span data-stu-id="c969f-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c969f-117">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="c969f-117">\<filter></span></span>](filter.md)|<span data-ttu-id="c969f-118">Zawiera listę punktów końcowych, które mają być używane przez usługę routingu w przypadku, gdy podstawowy punkt końcowy nie zostanie osiągnięty.</span><span class="sxs-lookup"><span data-stu-id="c969f-118">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="c969f-119">.</span><span class="sxs-lookup"><span data-stu-id="c969f-119">.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c969f-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c969f-120">Parent Elements</span></span>  
  
|<span data-ttu-id="c969f-121">Element</span><span class="sxs-lookup"><span data-stu-id="c969f-121">Element</span></span>|<span data-ttu-id="c969f-122">Opis</span><span class="sxs-lookup"><span data-stu-id="c969f-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c969f-123">\<> routingu</span><span class="sxs-lookup"><span data-stu-id="c969f-123">\<routing></span></span>](routing.md)|<span data-ttu-id="c969f-124">Reprezentuje sekcję konfiguracji określającą zestaw filtrów routingu, które określają typ Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> , który ma być używany podczas oceniania wiadomości przychodzących, a także tabele routingu, które definiują docelowe punkty końcowe Wysyłaj komunikaty do, gdy filtr jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="c969f-124">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c969f-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c969f-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
