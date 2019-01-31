---
title: <backupLists>
ms.date: 03/30/2017
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
ms.openlocfilehash: 6ac7ff19c76097cb54e7b77db21cad50b49513c0
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55280751"
---
# <a name="backuplists"></a><span data-ttu-id="d33eb-101">\<backupLists></span><span class="sxs-lookup"><span data-stu-id="d33eb-101">\<backupLists></span></span>
<span data-ttu-id="d33eb-102">Reprezentuje sekcję konfiguracji definiujących zestaw usług kopii zapasowych używanych do obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="d33eb-102">Represents a configuration section for defining a set of backup services used in error handling.</span></span> <span data-ttu-id="d33eb-103">Każdy element podrzędny jest listę kopii zapasowych, która wylicza zestaw punktów końcowych, które chcesz, aby usługa routingu do użycia w przypadku, gdy nie można nawiązać połączenia z podstawowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="d33eb-103">Each child element is a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="d33eb-104">Jeśli pierwszy punkt końcowy na liście nie działa, usługa routingu będzie automatycznie przełączać się kolejny na liście.</span><span class="sxs-lookup"><span data-stu-id="d33eb-104">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="d33eb-105">Dzięki temu możesz szybko dodać niezawodność do Twojej aplikacji bez konieczności nauki aplikacji klienckiej sposobu obsługi złożonych wzorów lub wszystkich usług wdrożonym.</span><span class="sxs-lookup"><span data-stu-id="d33eb-105">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
 <span data-ttu-id="d33eb-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d33eb-106">\<system.serviceModel></span></span>  
<span data-ttu-id="d33eb-107">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="d33eb-107">\<routing></span></span>  
<span data-ttu-id="d33eb-108">\<backupLists></span><span class="sxs-lookup"><span data-stu-id="d33eb-108">\<backupLists></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d33eb-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="d33eb-109">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d33eb-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d33eb-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d33eb-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d33eb-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d33eb-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d33eb-112">Attributes</span></span>  
 <span data-ttu-id="d33eb-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="d33eb-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d33eb-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d33eb-114">Child Elements</span></span>  
  
|<span data-ttu-id="d33eb-115">Element</span><span class="sxs-lookup"><span data-stu-id="d33eb-115">Element</span></span>|<span data-ttu-id="d33eb-116">Opis</span><span class="sxs-lookup"><span data-stu-id="d33eb-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d33eb-117">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="d33eb-117">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)|<span data-ttu-id="d33eb-118">Zawiera listę punktów końcowych, które chcesz, aby usługa routingu do użycia w przypadku, gdy nie można nawiązać połączenia z podstawowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="d33eb-118">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="d33eb-119">.</span><span class="sxs-lookup"><span data-stu-id="d33eb-119">.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d33eb-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d33eb-120">Parent Elements</span></span>  
  
|<span data-ttu-id="d33eb-121">Element</span><span class="sxs-lookup"><span data-stu-id="d33eb-121">Element</span></span>|<span data-ttu-id="d33eb-122">Opis</span><span class="sxs-lookup"><span data-stu-id="d33eb-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d33eb-123">\<routing></span><span class="sxs-lookup"><span data-stu-id="d33eb-123">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="d33eb-124">Reprezentuje sekcję konfiguracji określającą zestaw filtrów routingu, które określają typ obiektu programu Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> używanego podczas oceniania wiadomości przychodzących, jak również routingu definiujące miejsce docelowe punktów końcowych do tabel wysyłanie komunikatów do gdy kryteria filtru.</span><span class="sxs-lookup"><span data-stu-id="d33eb-124">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d33eb-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d33eb-125">See also</span></span>
- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
