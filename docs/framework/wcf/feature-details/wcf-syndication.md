---
title: Syndykacja programu WCF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: syndication [WCF]
ms.assetid: ebf80384-0fc9-4919-a1e8-23ca2a13e300
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1f7f5fd65fc298107a66e2049c059f3cc58b3d44
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-syndication"></a><span data-ttu-id="7ef9a-102">Syndykacja programu WCF</span><span class="sxs-lookup"><span data-stu-id="7ef9a-102">WCF Syndication</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="7ef9a-103">zapewnia obsługę łatwo pracować ze źródła zespolonego Atom, RSS lub innych niestandardowych formatów, dzięki czemu można odczytać i utwórz je, a także ujawniać je na punkt końcowy usługi.</span><span class="sxs-lookup"><span data-stu-id="7ef9a-103"> provides support to easily work with syndication feeds in Atom, RSS or other custom formats, which allows you to read and create them as well as expose them on a service endpoint.</span></span> <span data-ttu-id="7ef9a-104">W tematach w tej sekcji opisano ten model programowania do zespolonego szczegółowo.</span><span class="sxs-lookup"><span data-stu-id="7ef9a-104">The topics in this section describe this programming model for syndication in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7ef9a-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="7ef9a-105">In This Section</span></span>  
 [<span data-ttu-id="7ef9a-106">Omówienie syndykacji WCF</span><span class="sxs-lookup"><span data-stu-id="7ef9a-106">WCF Syndication Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md)  
 <span data-ttu-id="7ef9a-107">Zawiera omówienie pomocy technicznej zespolonego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7ef9a-107">Provides an overview of syndication support provided by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="7ef9a-108">Architektura syndykacji</span><span class="sxs-lookup"><span data-stu-id="7ef9a-108">Architecture of Syndication</span></span>](../../../../docs/framework/wcf/feature-details/architecture-of-syndication.md)  
 <span data-ttu-id="7ef9a-109">Zawiera opis klas w modelu obiektów i rozszerzalność syndykacji.</span><span class="sxs-lookup"><span data-stu-id="7ef9a-109">Describes the classes in the object model and the extensibility of syndication.</span></span>  
  
 [<span data-ttu-id="7ef9a-110">Sposób mapowania modelu obiektu syndykacji programu WCF na kanały informacyjne Atom i RSS</span><span class="sxs-lookup"><span data-stu-id="7ef9a-110">How the WCF Syndication Object Model Maps to Atom and RSS</span></span>](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md)  
 <span data-ttu-id="7ef9a-111">Opisuje sposób źródeł danych są reprezentowane w modelu obiektu syndykacji WCF i jak są konwertowane na funkcję RSS i kanały informacyjne Atom.</span><span class="sxs-lookup"><span data-stu-id="7ef9a-111">Describes how feeds are represented within the WCF Syndication Object Model and how they are converted to RSS and Atom feeds.</span></span>  
  
 [<span data-ttu-id="7ef9a-112">Instrukcje: tworzenie podstawowego kanału informacyjnego RSS</span><span class="sxs-lookup"><span data-stu-id="7ef9a-112">How to: Create a Basic RSS Feed</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-rss-feed.md)  
 <span data-ttu-id="7ef9a-113">Pokazuje, jak utworzyć usługi, która udostępnia podstawowe źródło danych RSS.</span><span class="sxs-lookup"><span data-stu-id="7ef9a-113">Shows how to create a service that makes a basic RSS feed available.</span></span>  
  
 [<span data-ttu-id="7ef9a-114">Instrukcje: tworzenie podstawowego źródła danych Atom</span><span class="sxs-lookup"><span data-stu-id="7ef9a-114">How to: Create a Basic Atom Feed</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-atom-feed.md)  
 <span data-ttu-id="7ef9a-115">Pokazuje, jak utworzyć usługi, która udostępnia podstawowe źródło danych ATOM.</span><span class="sxs-lookup"><span data-stu-id="7ef9a-115">Shows how to create a service that makes a basic ATOM feed available.</span></span>  
  
 [<span data-ttu-id="7ef9a-116">Instrukcje: udostępnianie kanału informacyjnego w formatach Atom i RSS</span><span class="sxs-lookup"><span data-stu-id="7ef9a-116">How to: Expose a Feed as Both Atom and RSS</span></span>](../../../../docs/framework/wcf/feature-details/how-to-expose-a-feed-as-both-atom-and-rss.md)  
 <span data-ttu-id="7ef9a-117">Pokazuje, jak utworzyć usługi, która udostępnia tego samego źródła danych ATOM i RSS.</span><span class="sxs-lookup"><span data-stu-id="7ef9a-117">Shows how to create a service that makes the same feed available with ATOM and RSS.</span></span>  
  
 [<span data-ttu-id="7ef9a-118">Rozszerzalność syndykacji</span><span class="sxs-lookup"><span data-stu-id="7ef9a-118">Syndication Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/syndication-extensibility.md)  
 <span data-ttu-id="7ef9a-119">Zawiera opis metod dodawania niestandardowych elementów i atrybutów do źródła zespolonego.</span><span class="sxs-lookup"><span data-stu-id="7ef9a-119">Describes the methods of adding custom elements and attributes to a syndication feed.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="7ef9a-120">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="7ef9a-120">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7ef9a-121">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="7ef9a-121">Related Sections</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ef9a-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7ef9a-122">See Also</span></span>  
 [<span data-ttu-id="7ef9a-123">Model programowania protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="7ef9a-123">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [<span data-ttu-id="7ef9a-124">Zaufanie częściowe</span><span class="sxs-lookup"><span data-stu-id="7ef9a-124">Partial Trust</span></span>](../../../../docs/framework/wcf/feature-details/partial-trust.md)
