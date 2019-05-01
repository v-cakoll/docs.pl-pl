---
title: Przechowywanie wersji odnajdywania
ms.date: 03/30/2017
ms.assetid: f91c6d0a-3af2-45c5-9a5c-e75390619836
ms.openlocfilehash: 18c160e5e08ed9b6733bed9d5e40a4dde00dfd1c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61856651"
---
# <a name="discovery-versioning"></a><span data-ttu-id="fac47-102">Przechowywanie wersji odnajdywania</span><span class="sxs-lookup"><span data-stu-id="fac47-102">Discovery Versioning</span></span>
<span data-ttu-id="fac47-103">Ten temat zawiera krótkie omówienie wdrożenia niektóre nowe funkcje odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="fac47-103">This topic provides a brief overview of the implementation of some new discovery features.</span></span> <span data-ttu-id="fac47-104">Daje ona również przegląd informacji na temat sposobu wybierz wersję odnajdywania do użycia.</span><span class="sxs-lookup"><span data-stu-id="fac47-104">It also gives an overview on how to select the discovery version to use.</span></span>  
  
## <a name="discovery-versioning"></a><span data-ttu-id="fac47-105">Przechowywanie wersji odnajdywania</span><span class="sxs-lookup"><span data-stu-id="fac47-105">Discovery Versioning</span></span>  
 <span data-ttu-id="fac47-106">Funkcja odnajdowania obsługuje trzy wersje protokołu WS_Discovery.</span><span class="sxs-lookup"><span data-stu-id="fac47-106">The discovery feature includes support for three versions of the WS_Discovery protocol.</span></span> <span data-ttu-id="fac47-107">Odnajdywanie interfejsy API pozwalają na wybór wersji protokołu, którego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="fac47-107">The discovery APIs allow you to select which version of the protocol you want to use.</span></span> <span data-ttu-id="fac47-108">W tym dokumencie krótko opisano ustawienia dotyczące przechowywania wersji.</span><span class="sxs-lookup"><span data-stu-id="fac47-108">This document briefly describes the versioning-related settings.</span></span>  
  
 <span data-ttu-id="fac47-109">Następujące klasy odnajdywania powstał <xref:System.ServiceModel.Discovery.DiscoveryVersion> właściwości i podejmij <xref:System.ServiceModel.Discovery.DiscoveryVersion> argumentu w ich konstruktory:</span><span class="sxs-lookup"><span data-stu-id="fac47-109">The following Discovery classes now have a <xref:System.ServiceModel.Discovery.DiscoveryVersion> property and take a <xref:System.ServiceModel.Discovery.DiscoveryVersion> argument in their constructors:</span></span>  
  
- <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
  
- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
  
- <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
  
- <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
  
### <a name="discoveryversionwsdiscoveryapril2005"></a><span data-ttu-id="fac47-110">DiscoveryVersion.WSDiscoveryApril2005</span><span class="sxs-lookup"><span data-stu-id="fac47-110">DiscoveryVersion.WSDiscoveryApril2005</span></span>  
 <span data-ttu-id="fac47-111">Zapewnianie <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryApril2005> jako Konstruktor parametru powoduje, że implementacja przy użyciu wersji April2005 protokołu WS Discovery.</span><span class="sxs-lookup"><span data-stu-id="fac47-111">Providing <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryApril2005> as a constructor parameter makes the implementation use the April2005 version of the WS-Discovery protocol.</span></span> <span data-ttu-id="fac47-112">Ta wersja odnosi się do opublikowanej wersji specyfikacji protokołu WS Discovery.</span><span class="sxs-lookup"><span data-stu-id="fac47-112">This version corresponds to the published version of the WS-Discovery protocol specification.</span></span> <span data-ttu-id="fac47-113">Na potrzeby współdziałania z starszych aplikacji wykorzystujących April2005 wersję protokołu WS Discovery, można używać tej wersji.</span><span class="sxs-lookup"><span data-stu-id="fac47-113">This version should be used to interoperate with legacy application utilizing the April2005 version of WS-Discovery.</span></span>  
  
### <a name="discoveryversionwsdiscovery11"></a><span data-ttu-id="fac47-114">DiscoveryVersion.WSDiscovery11</span><span class="sxs-lookup"><span data-stu-id="fac47-114">DiscoveryVersion.WSDiscovery11</span></span>  
 <span data-ttu-id="fac47-115">Domyślna wersja odnajdywania używany przez interfejsy API to <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscovery11>.</span><span class="sxs-lookup"><span data-stu-id="fac47-115">The default discovery version used by the APIs is <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscovery11>.</span></span> <span data-ttu-id="fac47-116">Jest to standardowy bieżącą wersję protokołu WS Discovery.</span><span class="sxs-lookup"><span data-stu-id="fac47-116">This is the current standardized version of the WS-Discovery protocol.</span></span>  
  
## <a name="discoveryversionwsdiscoverycd1"></a><span data-ttu-id="fac47-117">DiscoveryVersion.WSDiscoveryCD1</span><span class="sxs-lookup"><span data-stu-id="fac47-117">DiscoveryVersion.WSDiscoveryCD1</span></span>  
 <span data-ttu-id="fac47-118">Zapewnianie <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryCD1> jako parametr konstruktora sprawia, że implementacja Użyj Komitet wersję roboczą 1 wersję protokołu WS Discovery.</span><span class="sxs-lookup"><span data-stu-id="fac47-118">Providing <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryCD1> as a constructor parameter makes the implementation use the committee draft 1 version of the WS-Discovery protocol.</span></span> <span data-ttu-id="fac47-119">Ta wersja protokołu powinna służyć pod kątem współdziałania z implementacjami dysku CD 1 wersję protokołu WS Discovery.</span><span class="sxs-lookup"><span data-stu-id="fac47-119">This version of the protocol should be used to interoperate with implementations running the CD1 version of the WS-Discovery protocol.</span></span>  
  
## <a name="supporting-multiple-udp-discovery-endpoints-for-different-discovery-versions-on-a-single-service-host"></a><span data-ttu-id="fac47-120">Obsługa wielu punktów końcowych odnajdywania protokołu UDP dla wersji odnajdywania inny na hoście pojedynczą usługę</span><span class="sxs-lookup"><span data-stu-id="fac47-120">Supporting Multiple UDP Discovery Endpoints for Different Discovery Versions on a Single Service Host</span></span>  
 <span data-ttu-id="fac47-121">Można udostępnić wiele punktów końcowych odnajdywania protokołu UDP dla wersji odnajdywania inny na hoście jednej usługi.</span><span class="sxs-lookup"><span data-stu-id="fac47-121">You may want to expose multiple UDP Discovery Endpoints for different discovery versions on a single service host.</span></span> <span data-ttu-id="fac47-122">W tym celu należy określić unikatowy adres dla każdego punktu końcowego odnajdywania protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="fac47-122">To do this you must specify a unique address for each UDP discovery endpoint.</span></span> <span data-ttu-id="fac47-123">W przykładzie poniżej pokazano, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="fac47-123">The following example shows how to do this.</span></span>  
  
```  
UdpDiscoveryEndpoint newVersionUdpEndpoint = new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscovery11);  
UdpDiscoveryEndpoint oldVersionUdpEndpoint = new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscoveryApril2005);  
  
newVersionUdpEndpoint.Address = new EndpointAddress(newVersionUdpEndpoint.Address.Uri.ToString() + "/version11");  
oldVersionUdpEndpoint.Address = new EndpointAddress(oldVersionUdpEndpoint.Address.Uri.ToString() + "/versionAril2005");  
  
serviceHost.AddServiceEndpoint(newVersionUdpEndpoint);  
serviceHost.AddServiceEndpoint(oldVersionUdpEndpoint);  
```
