---
title: Przechowywanie wersji odnajdywania
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f91c6d0a-3af2-45c5-9a5c-e75390619836
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bb9855f590fd02cc11448568b211f85ee6a951cd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="discovery-versioning"></a><span data-ttu-id="ad126-102">Przechowywanie wersji odnajdywania</span><span class="sxs-lookup"><span data-stu-id="ad126-102">Discovery Versioning</span></span>
<span data-ttu-id="ad126-103">Ten temat zawiera krótki przegląd wdrożenia niektóre nowe funkcje odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="ad126-103">This topic provides a brief overview of the implementation of some new discovery features.</span></span> <span data-ttu-id="ad126-104">Również zawiera omówienie dotyczące wybierz wersję odnajdywania do użycia.</span><span class="sxs-lookup"><span data-stu-id="ad126-104">It also gives an overview on how to select the discovery version to use.</span></span>  
  
## <a name="discovery-versioning"></a><span data-ttu-id="ad126-105">Przechowywanie wersji odnajdywania</span><span class="sxs-lookup"><span data-stu-id="ad126-105">Discovery Versioning</span></span>  
 <span data-ttu-id="ad126-106">Funkcja odnajdowania obsługuje trzy wersje protokołu WS_Discovery.</span><span class="sxs-lookup"><span data-stu-id="ad126-106">The discovery feature includes support for three versions of the WS_Discovery protocol.</span></span> <span data-ttu-id="ad126-107">Odnajdywanie interfejsów API umożliwiają wybierz, która wersja protokołu, którego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="ad126-107">The discovery APIs allow you to select which version of the protocol you want to use.</span></span> <span data-ttu-id="ad126-108">Tym dokumencie krótko opisano ustawienia związane z kontroli wersji.</span><span class="sxs-lookup"><span data-stu-id="ad126-108">This document briefly describes the versioning-related settings.</span></span>  
  
 <span data-ttu-id="ad126-109">Następujące klasy odnajdywania teraz mają <xref:System.ServiceModel.Discovery.DiscoveryVersion> właściwości i podejmij <xref:System.ServiceModel.Discovery.DiscoveryVersion> argument w swoich konstruktorach:</span><span class="sxs-lookup"><span data-stu-id="ad126-109">The following Discovery classes now have a <xref:System.ServiceModel.Discovery.DiscoveryVersion> property and take a <xref:System.ServiceModel.Discovery.DiscoveryVersion> argument in their constructors:</span></span>  
  
-   <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
  
### <a name="discoveryversionwsdiscoveryapril2005"></a><span data-ttu-id="ad126-110">DiscoveryVersion.WSDiscoveryApril2005</span><span class="sxs-lookup"><span data-stu-id="ad126-110">DiscoveryVersion.WSDiscoveryApril2005</span></span>  
 <span data-ttu-id="ad126-111">Zapewnianie <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryApril2005> jako konstruktora parametru zapewnia wdrożenia przy użyciu wersji April2005 protokołu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="ad126-111">Providing <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryApril2005> as a constructor parameter makes the implementation use the April2005 version of the WS-Discovery protocol.</span></span> <span data-ttu-id="ad126-112">Ta wersja odpowiada opublikowana wersja specyfikacji protokołu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="ad126-112">This version corresponds to the published version of the WS-Discovery protocol specification.</span></span> <span data-ttu-id="ad126-113">Współdziałanie z starszych aplikacji przy użyciu wersji April2005 WS-Discovery należy używać tej wersji.</span><span class="sxs-lookup"><span data-stu-id="ad126-113">This version should be used to interoperate with legacy application utilizing the April2005 version of WS-Discovery.</span></span>  
  
### <a name="discoveryversionwsdiscovery11"></a><span data-ttu-id="ad126-114">DiscoveryVersion.WSDiscovery11</span><span class="sxs-lookup"><span data-stu-id="ad126-114">DiscoveryVersion.WSDiscovery11</span></span>  
 <span data-ttu-id="ad126-115">Domyślną wersję odnajdywania używanych przez interfejsy API <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscovery11>.</span><span class="sxs-lookup"><span data-stu-id="ad126-115">The default discovery version used by the APIs is <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscovery11>.</span></span> <span data-ttu-id="ad126-116">Jest to bieżąca wersja protokołu WS-Discovery standardowych.</span><span class="sxs-lookup"><span data-stu-id="ad126-116">This is the current standardized version of the WS-Discovery protocol.</span></span>  
  
## <a name="discoveryversionwsdiscoverycd1"></a><span data-ttu-id="ad126-117">DiscoveryVersion.WSDiscoveryCD1</span><span class="sxs-lookup"><span data-stu-id="ad126-117">DiscoveryVersion.WSDiscoveryCD1</span></span>  
 <span data-ttu-id="ad126-118">Zapewnianie <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryCD1> jak wdrożenia, użyj parametru konstruktora Komitetu projekt 1 wersja protokołu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="ad126-118">Providing <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryCD1> as a constructor parameter makes the implementation use the committee draft 1 version of the WS-Discovery protocol.</span></span> <span data-ttu-id="ad126-119">Współdziałanie z dysku CD 1 wersją protokołu WS-Discovery implementacje powinny używać tej wersji protokołu.</span><span class="sxs-lookup"><span data-stu-id="ad126-119">This version of the protocol should be used to interoperate with implementations running the CD1 version of the WS-Discovery protocol.</span></span>  
  
## <a name="supporting-multiple-udp-discovery-endpoints-for-different-discovery-versions-on-a-single-service-host"></a><span data-ttu-id="ad126-120">Obsługa wielu punktów końcowych odnajdywania protokołu UDP dla wersji odnajdywania inny na hoście z jednej usługi</span><span class="sxs-lookup"><span data-stu-id="ad126-120">Supporting Multiple UDP Discovery Endpoints for Different Discovery Versions on a Single Service Host</span></span>  
 <span data-ttu-id="ad126-121">Warto udostępnić wiele punktów końcowych odnajdywania protokołu UDP dla wersji odnajdywania inny na hoście z jednej usługi.</span><span class="sxs-lookup"><span data-stu-id="ad126-121">You may want to expose multiple UDP Discovery Endpoints for different discovery versions on a single service host.</span></span> <span data-ttu-id="ad126-122">W tym celu należy określić unikatowy adres dla każdego punktu końcowego odnajdywania protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="ad126-122">To do this you must specify a unique address for each UDP discovery endpoint.</span></span> <span data-ttu-id="ad126-123">W przykładzie poniżej pokazano, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="ad126-123">The following example shows how to do this.</span></span>  
  
```  
UdpDiscoveryEndpoint newVersionUdpEndpoint = new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscovery11);  
UdpDiscoveryEndpoint oldVersionUdpEndpoint = new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscoveryApril2005);  
  
newVersionUdpEndpoint.Address = new EndpointAddress(newVersionUdpEndpoint.Address.Uri.ToString() + "/version11");  
oldVersionUdpEndpoint.Address = new EndpointAddress(oldVersionUdpEndpoint.Address.Uri.ToString() + "/versionAril2005");  
  
serviceHost.AddServiceEndpoint(newVersionUdpEndpoint);  
serviceHost.AddServiceEndpoint(oldVersionUdpEndpoint);  
```
