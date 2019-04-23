---
title: <backupLists>
ms.date: 03/30/2017
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
ms.openlocfilehash: 6e44dbe3c0966c6d243db343b9f9b0dec2480cb1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59134449"
---
# <a name="backuplists"></a><span data-ttu-id="23748-101">\<backupLists></span><span class="sxs-lookup"><span data-stu-id="23748-101">\<backupLists></span></span>
<span data-ttu-id="23748-102">Reprezentuje sekcję konfiguracji definiujących zestaw usług kopii zapasowych używanych do obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="23748-102">Represents a configuration section for defining a set of backup services used in error handling.</span></span> <span data-ttu-id="23748-103">Każdy element podrzędny jest listę kopii zapasowych, która wylicza zestaw punktów końcowych, które chcesz, aby usługa routingu do użycia w przypadku, gdy nie można nawiązać połączenia z podstawowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="23748-103">Each child element is a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="23748-104">Jeśli pierwszy punkt końcowy na liście nie działa, usługa routingu będzie automatycznie przełączać się kolejny na liście.</span><span class="sxs-lookup"><span data-stu-id="23748-104">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="23748-105">Dzięki temu możesz szybko dodać niezawodność do Twojej aplikacji bez konieczności nauki aplikacji klienckiej sposobu obsługi złożonych wzorów lub wszystkich usług wdrożonym.</span><span class="sxs-lookup"><span data-stu-id="23748-105">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
 <span data-ttu-id="23748-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="23748-106">\<system.serviceModel></span></span>  
<span data-ttu-id="23748-107">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="23748-107">\<routing></span></span>  
<span data-ttu-id="23748-108">\<backupLists></span><span class="sxs-lookup"><span data-stu-id="23748-108">\<backupLists></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23748-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="23748-109">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="23748-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="23748-110">Attributes and Elements</span></span>  
 <span data-ttu-id="23748-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="23748-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="23748-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="23748-112">Attributes</span></span>  
 <span data-ttu-id="23748-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="23748-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="23748-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="23748-114">Child Elements</span></span>  
  
|<span data-ttu-id="23748-115">Element</span><span class="sxs-lookup"><span data-stu-id="23748-115">Element</span></span>|<span data-ttu-id="23748-116">Opis</span><span class="sxs-lookup"><span data-stu-id="23748-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="23748-117">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="23748-117">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)|<span data-ttu-id="23748-118">Zawiera listę punktów końcowych, które chcesz, aby usługa routingu do użycia w przypadku, gdy nie można nawiązać połączenia z podstawowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="23748-118">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="23748-119">.</span><span class="sxs-lookup"><span data-stu-id="23748-119">.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="23748-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="23748-120">Parent Elements</span></span>  
  
|<span data-ttu-id="23748-121">Element</span><span class="sxs-lookup"><span data-stu-id="23748-121">Element</span></span>|<span data-ttu-id="23748-122">Opis</span><span class="sxs-lookup"><span data-stu-id="23748-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="23748-123">\<routing></span><span class="sxs-lookup"><span data-stu-id="23748-123">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="23748-124">Reprezentuje sekcję konfiguracji określającą zestaw filtrów routingu, które określają typ obiektu programu Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> używanego podczas oceniania wiadomości przychodzących, jak również routingu definiujące miejsce docelowe punktów końcowych do tabel wysyłanie komunikatów do gdy kryteria filtru.</span><span class="sxs-lookup"><span data-stu-id="23748-124">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="23748-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="23748-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
