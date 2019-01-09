---
title: '&lt;backupLists&gt;'
ms.date: 03/30/2017
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
ms.openlocfilehash: ff363f97b25496dc9bb3a691de7c8abf77c0dc9d
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149127"
---
# <a name="ltbackuplistsgt"></a><span data-ttu-id="19895-102">&lt;backupLists&gt;</span><span class="sxs-lookup"><span data-stu-id="19895-102">&lt;backupLists&gt;</span></span>
<span data-ttu-id="19895-103">Reprezentuje sekcję konfiguracji definiujących zestaw usług kopii zapasowych używanych do obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="19895-103">Represents a configuration section for defining a set of backup services used in error handling.</span></span> <span data-ttu-id="19895-104">Każdy element podrzędny jest listę kopii zapasowych, która wylicza zestaw punktów końcowych, które chcesz, aby usługa routingu do użycia w przypadku, gdy nie można nawiązać połączenia z podstawowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="19895-104">Each child element is a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="19895-105">Jeśli pierwszy punkt końcowy na liście nie działa, usługa routingu będzie automatycznie przełączać się kolejny na liście.</span><span class="sxs-lookup"><span data-stu-id="19895-105">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="19895-106">Dzięki temu możesz szybko dodać niezawodność do Twojej aplikacji bez konieczności nauki aplikacji klienckiej sposobu obsługi złożonych wzorów lub wszystkich usług wdrożonym.</span><span class="sxs-lookup"><span data-stu-id="19895-106">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
 <span data-ttu-id="19895-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="19895-107">\<system.serviceModel></span></span>  
<span data-ttu-id="19895-108">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="19895-108">\<routing></span></span>  
<span data-ttu-id="19895-109">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="19895-109">\<backupLists></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19895-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="19895-110">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="19895-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="19895-111">Attributes and Elements</span></span>  
 <span data-ttu-id="19895-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="19895-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="19895-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="19895-113">Attributes</span></span>  
 <span data-ttu-id="19895-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="19895-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="19895-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="19895-115">Child Elements</span></span>  
  
|<span data-ttu-id="19895-116">Element</span><span class="sxs-lookup"><span data-stu-id="19895-116">Element</span></span>|<span data-ttu-id="19895-117">Opis</span><span class="sxs-lookup"><span data-stu-id="19895-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="19895-118">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="19895-118">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)|<span data-ttu-id="19895-119">Zawiera listę punktów końcowych, które chcesz, aby usługa routingu do użycia w przypadku, gdy nie można nawiązać połączenia z podstawowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="19895-119">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="19895-120">.</span><span class="sxs-lookup"><span data-stu-id="19895-120">.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="19895-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="19895-121">Parent Elements</span></span>  
  
|<span data-ttu-id="19895-122">Element</span><span class="sxs-lookup"><span data-stu-id="19895-122">Element</span></span>|<span data-ttu-id="19895-123">Opis</span><span class="sxs-lookup"><span data-stu-id="19895-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="19895-124">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="19895-124">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="19895-125">Reprezentuje sekcję konfiguracji określającą zestaw filtrów routingu, które określają typ obiektu programu Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> używanego podczas oceniania wiadomości przychodzących, jak również routingu definiujące miejsce docelowe punktów końcowych do tabel wysyłanie komunikatów do gdy kryteria filtru.</span><span class="sxs-lookup"><span data-stu-id="19895-125">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="19895-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="19895-126">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>    
