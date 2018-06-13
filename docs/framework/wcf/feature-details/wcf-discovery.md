---
title: Odnajdywanie w programie WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], discovery
- Windows Communication Foundation [WCF], discovery
- discovery [WCF]
ms.assetid: 462c4913-f388-45a9-9042-28ae96a4e735
ms.openlocfilehash: 175f79096d2bbda81a602d38e027d5a6d871fa12
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497961"
---
# <a name="wcf-discovery"></a><span data-ttu-id="e4667-102">Odnajdywanie w programie WCF</span><span class="sxs-lookup"><span data-stu-id="e4667-102">WCF Discovery</span></span>
<span data-ttu-id="e4667-103">Windows Communication Foundation (WCF) obsługuje Włączanie usług będzie wykrywalny w czasie wykonywania w sposób interoperacyjne za pomocą protokołu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="e4667-103">Windows Communication Foundation (WCF) provides support to enable services to be discoverable at runtime in an interoperable way using the WS-Discovery protocol.</span></span> <span data-ttu-id="e4667-104">Usługi WCF można poinformować o ich dostępności sieci za pomocą komunikatu multiemisji lub serwera proxy odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="e4667-104">WCF services can announce their availability to the network using a multicast message or to a discovery proxy server.</span></span> <span data-ttu-id="e4667-105">Aplikacje klienckie można znaleźć sieci lub serwera proxy odnajdywania można znaleźć usługi, które spełniają określone kryteria.</span><span class="sxs-lookup"><span data-stu-id="e4667-105">Client applications can search the network or a discovery proxy server to find services that meet a set of criteria.</span></span> <span data-ttu-id="e4667-106">Tematy w tej sekcji omówiono i modelu programowania dla tej funkcji, które szczegółowo opisano.</span><span class="sxs-lookup"><span data-stu-id="e4667-106">The topics in this section provide an overview and describe the programming model for this feature in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e4667-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="e4667-107">In This Section</span></span>  
 [<span data-ttu-id="e4667-108">Omówienie odnajdywania WCF</span><span class="sxs-lookup"><span data-stu-id="e4667-108">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 <span data-ttu-id="e4667-109">Omówienie obsługi protokołu WS-Discovery udostępniane przez usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="e4667-109">Provides an overview of WS-Discovery support provided by WCF.</span></span>  
  
 [<span data-ttu-id="e4667-110">Model obiektów odnajdywania WCF</span><span class="sxs-lookup"><span data-stu-id="e4667-110">WCF Discovery Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-object-model.md)  
 <span data-ttu-id="e4667-111">Zawiera opis klas w modelu obiektów i rozszerzalność obsługi protokołu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="e4667-111">Describes the classes in the object model and extensibility of WS-Discovery support.</span></span>  
  
 [<span data-ttu-id="e4667-112">Instrukcje: programowe dodawanie możliwości odnajdywania do usługi i klienta WCF</span><span class="sxs-lookup"><span data-stu-id="e4667-112">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)  
 <span data-ttu-id="e4667-113">Pokazuje sposób wprowadzania wykrywalny usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="e4667-113">Shows how to make a Windows Communication Foundation (WCF) service discoverable.</span></span>  
  
 [<span data-ttu-id="e4667-114">Implementowanie serwera proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="e4667-114">Implementing a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md)  
 <span data-ttu-id="e4667-115">W tym artykule opisano kroki wymagane do wdrożenia serwera proxy odnajdywania, wykrywalnej usługi, który rejestruje przy użyciu serwera proxy odnajdywania i klienta, który używa serwera proxy odnajdywania można znaleźć wykrywalnej usługi.</span><span class="sxs-lookup"><span data-stu-id="e4667-115">Describes the steps required to implement a discovery proxy, a discoverable service that registers with the discovery proxy, and a client that uses the discovery proxy to find the discoverable service.</span></span>  
  
 [<span data-ttu-id="e4667-116">Przechowywanie wersji odnajdywania</span><span class="sxs-lookup"><span data-stu-id="e4667-116">Discovery Versioning</span></span>](../../../../docs/framework/wcf/feature-details/discovery-versioning.md)  
 <span data-ttu-id="e4667-117">Krótki przegląd prototypu stosowania niektórych nowych funkcji odnajdowania.</span><span class="sxs-lookup"><span data-stu-id="e4667-117">Provides a brief overview of a prototype implementation of some new discovery features.</span></span> <span data-ttu-id="e4667-118">Również zawiera omówienie dotyczące wybierz wersję odnajdywania do użycia.</span><span class="sxs-lookup"><span data-stu-id="e4667-118">It also gives an overview on how to select the discovery version to use.</span></span>  
  
 [<span data-ttu-id="e4667-119">Konfigurowanie odnajdywania w pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e4667-119">Configuring Discovery in a Configuration File</span></span>](../../../../docs/framework/wcf/feature-details/configuring-discovery-in-a-configuration-file.md)  
 <span data-ttu-id="e4667-120">Pokazano, jak skonfigurować odnajdywanie w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e4667-120">Shows how to configure Discovery in configuration.</span></span>  
  
 [<span data-ttu-id="e4667-121">Używanie kanału klienta odnajdywania</span><span class="sxs-lookup"><span data-stu-id="e4667-121">Using the Discovery Client Channel</span></span>](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)  
 <span data-ttu-id="e4667-122">Przedstawia sposób korzystania z kanału klienta odnajdowania, podczas pisania aplikacji klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="e4667-122">Shows how to use a Discovery Client Channel when writing a WCF client application.</span></span>
