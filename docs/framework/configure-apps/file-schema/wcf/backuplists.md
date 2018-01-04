---
title: '&lt;backupLists&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5fee9e455189d5be1c81fb950eff3882aa8222b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltbackuplistsgt"></a><span data-ttu-id="44439-102">&lt;backupLists&gt;</span><span class="sxs-lookup"><span data-stu-id="44439-102">&lt;backupLists&gt;</span></span>
<span data-ttu-id="44439-103">Reprezentuje sekcję konfiguracji definiujących zestaw usług kopii zapasowych używanych do obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="44439-103">Represents a configuration section for defining a set of backup services used in error handling.</span></span> <span data-ttu-id="44439-104">Każdy element podrzędny jest listy kopii zapasowych, który wylicza zestaw punktów końcowych, które chcesz usługa routingu do użycia w przypadku, gdy podstawowy punkt końcowy jest nieosiągalny.</span><span class="sxs-lookup"><span data-stu-id="44439-104">Each child element is a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="44439-105">Jeśli pierwszy punkt końcowy na liście nie działa, usługa routingu zostanie automatycznie awaryjnej do następnego w liście.</span><span class="sxs-lookup"><span data-stu-id="44439-105">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="44439-106">Dzięki temu można szybko dodać niezawodność do aplikacji bez konieczności nauki aplikacji klienckiej sposobu obsługi złożonych wzorów lub wszystkich usług wdrożonym.</span><span class="sxs-lookup"><span data-stu-id="44439-106">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
 <span data-ttu-id="44439-107">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="44439-107">\<system.serviceModel></span></span>  
<span data-ttu-id="44439-108">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="44439-108">\<routing></span></span>  
<span data-ttu-id="44439-109">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="44439-109">\<backupLists></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44439-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="44439-110">Syntax</span></span>  
  
```xml
   <routing>  <backupLists>    <backupList name="String">      <add endpointName="String" />    </backupList>    </backupLists></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="44439-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="44439-111">Attributes and Elements</span></span>  
 <span data-ttu-id="44439-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="44439-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44439-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="44439-113">Attributes</span></span>  
 <span data-ttu-id="44439-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="44439-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="44439-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="44439-115">Child Elements</span></span>  
  
|<span data-ttu-id="44439-116">Element</span><span class="sxs-lookup"><span data-stu-id="44439-116">Element</span></span>|<span data-ttu-id="44439-117">Opis</span><span class="sxs-lookup"><span data-stu-id="44439-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="44439-118">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="44439-118">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md)|<span data-ttu-id="44439-119">Zawiera listę punktów końcowych, które chcesz usługa routingu do użycia w przypadku, gdy podstawowy punkt końcowy jest nieosiągalny.</span><span class="sxs-lookup"><span data-stu-id="44439-119">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="44439-120">.</span><span class="sxs-lookup"><span data-stu-id="44439-120">.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="44439-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="44439-121">Parent Elements</span></span>  
  
|<span data-ttu-id="44439-122">Element</span><span class="sxs-lookup"><span data-stu-id="44439-122">Element</span></span>|<span data-ttu-id="44439-123">Opis</span><span class="sxs-lookup"><span data-stu-id="44439-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="44439-124">\<Routing ></span><span class="sxs-lookup"><span data-stu-id="44439-124">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="44439-125">Reprezentuje sekcję konfiguracji określającą zestaw filtrów routingu, które określają typ [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> używanego podczas oceniania wiadomości przychodzących, jak również routingu tabel docelowych punktów końcowych do wysyłania komunikatów do podczas definiowania kryteria filtru.</span><span class="sxs-lookup"><span data-stu-id="44439-125">Represents a configuration section for defining a set of routing filters, which determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="44439-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="44439-126">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>    
