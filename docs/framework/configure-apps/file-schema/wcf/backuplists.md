---
title: '&lt;backupLists&gt;'
ms.date: 03/30/2017
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
ms.openlocfilehash: 5fb89ce5a942db40b07a65f59ddd05ab4cd624aa
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltbackuplistsgt"></a><span data-ttu-id="b2e32-102">&lt;backupLists&gt;</span><span class="sxs-lookup"><span data-stu-id="b2e32-102">&lt;backupLists&gt;</span></span>
<span data-ttu-id="b2e32-103">Reprezentuje sekcję konfiguracji definiujących zestaw usług kopii zapasowych używanych do obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="b2e32-103">Represents a configuration section for defining a set of backup services used in error handling.</span></span> <span data-ttu-id="b2e32-104">Każdy element podrzędny jest listy kopii zapasowych, który wylicza zestaw punktów końcowych, które chcesz usługa routingu do użycia w przypadku, gdy podstawowy punkt końcowy jest nieosiągalny.</span><span class="sxs-lookup"><span data-stu-id="b2e32-104">Each child element is a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="b2e32-105">Jeśli pierwszy punkt końcowy na liście nie działa, usługa routingu zostanie automatycznie awaryjnej do następnego w liście.</span><span class="sxs-lookup"><span data-stu-id="b2e32-105">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="b2e32-106">Dzięki temu można szybko dodać niezawodność do aplikacji bez konieczności nauki aplikacji klienckiej sposobu obsługi złożonych wzorów lub wszystkich usług wdrożonym.</span><span class="sxs-lookup"><span data-stu-id="b2e32-106">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
 <span data-ttu-id="b2e32-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b2e32-107">\<system.serviceModel></span></span>  
<span data-ttu-id="b2e32-108">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="b2e32-108">\<routing></span></span>  
<span data-ttu-id="b2e32-109">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="b2e32-109">\<backupLists></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2e32-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="b2e32-110">Syntax</span></span>  
  
```xml
   <routing>  <backupLists>    <backupList name="String">      <add endpointName="String" />    </backupList>    </backupLists></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b2e32-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b2e32-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b2e32-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b2e32-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b2e32-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b2e32-113">Attributes</span></span>  
 <span data-ttu-id="b2e32-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="b2e32-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b2e32-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b2e32-115">Child Elements</span></span>  
  
|<span data-ttu-id="b2e32-116">Element</span><span class="sxs-lookup"><span data-stu-id="b2e32-116">Element</span></span>|<span data-ttu-id="b2e32-117">Opis</span><span class="sxs-lookup"><span data-stu-id="b2e32-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b2e32-118">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="b2e32-118">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)|<span data-ttu-id="b2e32-119">Zawiera listę punktów końcowych, które chcesz usługa routingu do użycia w przypadku, gdy podstawowy punkt końcowy jest nieosiągalny.</span><span class="sxs-lookup"><span data-stu-id="b2e32-119">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="b2e32-120">.</span><span class="sxs-lookup"><span data-stu-id="b2e32-120">.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b2e32-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b2e32-121">Parent Elements</span></span>  
  
|<span data-ttu-id="b2e32-122">Element</span><span class="sxs-lookup"><span data-stu-id="b2e32-122">Element</span></span>|<span data-ttu-id="b2e32-123">Opis</span><span class="sxs-lookup"><span data-stu-id="b2e32-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b2e32-124">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="b2e32-124">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="b2e32-125">Reprezentuje sekcję konfiguracji określającą zestaw filtrów routingu, które określają typ obiektu Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> używanego podczas oceniania wiadomości przychodzących, jak również routingu tabel docelowych punktów końcowych, aby zdefiniować wysyłanie komunikatów do gdy kryteria filtru.</span><span class="sxs-lookup"><span data-stu-id="b2e32-125">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b2e32-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b2e32-126">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>    
