---
title: Syndykacja programu WCF
ms.date: 03/30/2017
helpviewer_keywords:
- syndication [WCF]
ms.assetid: ebf80384-0fc9-4919-a1e8-23ca2a13e300
ms.openlocfilehash: 198b664ff52b42b7f393eec3e8162f3a12037d9d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59175919"
---
# <a name="wcf-syndication"></a><span data-ttu-id="8b57a-102">Syndykacja programu WCF</span><span class="sxs-lookup"><span data-stu-id="8b57a-102">WCF Syndication</span></span>
<span data-ttu-id="8b57a-103">Windows Communication Foundation (WCF) obsługuje łatwo pracować z zespolone kanały informacyjne Atom, RSS lub innych niestandardowych formatów, co pozwala na odczyt i utwórz je, a także narażają je na punkt końcowy usługi.</span><span class="sxs-lookup"><span data-stu-id="8b57a-103">Windows Communication Foundation (WCF) provides support to easily work with syndication feeds in Atom, RSS or other custom formats, which allows you to read and create them as well as expose them on a service endpoint.</span></span> <span data-ttu-id="8b57a-104">W tematach w tej sekcji opisano ten model programowania do syndykacji szczegółowo.</span><span class="sxs-lookup"><span data-stu-id="8b57a-104">The topics in this section describe this programming model for syndication in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8b57a-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="8b57a-105">In This Section</span></span>  
 [<span data-ttu-id="8b57a-106">Omówienie syndykacji WCF</span><span class="sxs-lookup"><span data-stu-id="8b57a-106">WCF Syndication Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md)  
 <span data-ttu-id="8b57a-107">Omówienie syndykacji pomoc techniczna jest świadczona przez architekturę WCF.</span><span class="sxs-lookup"><span data-stu-id="8b57a-107">Provides an overview of syndication support provided by WCF.</span></span>  
  
 [<span data-ttu-id="8b57a-108">Architektura syndykacji</span><span class="sxs-lookup"><span data-stu-id="8b57a-108">Architecture of Syndication</span></span>](../../../../docs/framework/wcf/feature-details/architecture-of-syndication.md)  
 <span data-ttu-id="8b57a-109">Opisuje klasy w modelu obiektów i rozszerzalność syndykacji.</span><span class="sxs-lookup"><span data-stu-id="8b57a-109">Describes the classes in the object model and the extensibility of syndication.</span></span>  
  
 [<span data-ttu-id="8b57a-110">Sposób mapowania modelu obiektu syndykacji programu WCF na kanały informacyjne Atom i RSS</span><span class="sxs-lookup"><span data-stu-id="8b57a-110">How the WCF Syndication Object Model Maps to Atom and RSS</span></span>](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md)  
 <span data-ttu-id="8b57a-111">W tym artykule opisano, jak źródła danych są reprezentowane w modelu obiektu syndykacji programu WCF i jak są one konwertowane na RSS i kanały informacyjne Atom.</span><span class="sxs-lookup"><span data-stu-id="8b57a-111">Describes how feeds are represented within the WCF Syndication Object Model and how they are converted to RSS and Atom feeds.</span></span>  
  
 [<span data-ttu-id="8b57a-112">Instrukcje: Tworzenie podstawowego kanału informacyjnego RSS</span><span class="sxs-lookup"><span data-stu-id="8b57a-112">How to: Create a Basic RSS Feed</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-rss-feed.md)  
 <span data-ttu-id="8b57a-113">Pokazuje, jak utworzyć usługę, która udostępnia podstawowe źródło danych RSS.</span><span class="sxs-lookup"><span data-stu-id="8b57a-113">Shows how to create a service that makes a basic RSS feed available.</span></span>  
  
 [<span data-ttu-id="8b57a-114">Instrukcje: Tworzenie podstawowego źródła danych Atom</span><span class="sxs-lookup"><span data-stu-id="8b57a-114">How to: Create a Basic Atom Feed</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-atom-feed.md)  
 <span data-ttu-id="8b57a-115">Pokazuje, jak utworzyć usługę, która udostępnia podstawowe źródło danych ATOM.</span><span class="sxs-lookup"><span data-stu-id="8b57a-115">Shows how to create a service that makes a basic ATOM feed available.</span></span>  
  
 [<span data-ttu-id="8b57a-116">Instrukcje: Udostępnianie kanału informacyjnego w formatach Atom i RSS</span><span class="sxs-lookup"><span data-stu-id="8b57a-116">How to: Expose a Feed as Both Atom and RSS</span></span>](../../../../docs/framework/wcf/feature-details/how-to-expose-a-feed-as-both-atom-and-rss.md)  
 <span data-ttu-id="8b57a-117">Pokazuje, jak utworzyć usługę, która udostępnia tego samego źródła danych ATOM i RSS.</span><span class="sxs-lookup"><span data-stu-id="8b57a-117">Shows how to create a service that makes the same feed available with ATOM and RSS.</span></span>  
  
 [<span data-ttu-id="8b57a-118">Rozszerzalność syndykacji</span><span class="sxs-lookup"><span data-stu-id="8b57a-118">Syndication Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/syndication-extensibility.md)  
 <span data-ttu-id="8b57a-119">Opisuje metody dodawania niestandardowych elementów i atrybutów do zespolonego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="8b57a-119">Describes the methods of adding custom elements and attributes to a syndication feed.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="8b57a-120">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="8b57a-120">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8b57a-121">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="8b57a-121">Related Sections</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b57a-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8b57a-122">See also</span></span>

- [<span data-ttu-id="8b57a-123">Model programowania protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="8b57a-123">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [<span data-ttu-id="8b57a-124">Zaufanie częściowe</span><span class="sxs-lookup"><span data-stu-id="8b57a-124">Partial Trust</span></span>](../../../../docs/framework/wcf/feature-details/partial-trust.md)
