---
title: Odnajdywanie w programie WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], discovery
- Windows Communication Foundation [WCF], discovery
- discovery [WCF]
ms.assetid: 462c4913-f388-45a9-9042-28ae96a4e735
ms.openlocfilehash: 63c6589cb2ecff9f0a5e7c8bb61b454f6516c98c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600182"
---
# <a name="wcf-discovery"></a><span data-ttu-id="444e6-102">Odnajdywanie w programie WCF</span><span class="sxs-lookup"><span data-stu-id="444e6-102">WCF Discovery</span></span>
<span data-ttu-id="444e6-103">Windows Communication Foundation (WCF) zapewnia wsparcie umożliwiające odnajdywanie usług w środowisku uruchomieniowym w sposób współdziałający przy użyciu protokołu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="444e6-103">Windows Communication Foundation (WCF) provides support to enable services to be discoverable at runtime in an interoperable way using the WS-Discovery protocol.</span></span> <span data-ttu-id="444e6-104">Usługi WCF mogą ogłaszać swoją dostępność do sieci przy użyciu komunikatu multiemisji lub serwera proxy odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="444e6-104">WCF services can announce their availability to the network using a multicast message or to a discovery proxy server.</span></span> <span data-ttu-id="444e6-105">Aplikacje klienckie mogą przeszukiwać sieć lub serwer proxy odnajdywania, aby znaleźć usługi spełniające zestaw kryteriów.</span><span class="sxs-lookup"><span data-stu-id="444e6-105">Client applications can search the network or a discovery proxy server to find services that meet a set of criteria.</span></span> <span data-ttu-id="444e6-106">Tematy w tej sekcji zawierają omówienie i szczegółowo opisano model programowania tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="444e6-106">The topics in this section provide an overview and describe the programming model for this feature in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="444e6-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="444e6-107">In This Section</span></span>  
 [<span data-ttu-id="444e6-108">Omówienie odnajdywania WCF</span><span class="sxs-lookup"><span data-stu-id="444e6-108">WCF Discovery Overview</span></span>](wcf-discovery-overview.md)  
 <span data-ttu-id="444e6-109">Zawiera omówienie obsługi protokołu WS-Discovery zapewnianej przez program WCF.</span><span class="sxs-lookup"><span data-stu-id="444e6-109">Provides an overview of WS-Discovery support provided by WCF.</span></span>  
  
 [<span data-ttu-id="444e6-110">Model obiektów odnajdywania WCF</span><span class="sxs-lookup"><span data-stu-id="444e6-110">WCF Discovery Object Model</span></span>](wcf-discovery-object-model.md)  
 <span data-ttu-id="444e6-111">Opisuje klasy w modelu obiektów i rozszerzalność obsługi WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="444e6-111">Describes the classes in the object model and extensibility of WS-Discovery support.</span></span>  
  
 [<span data-ttu-id="444e6-112">Instrukcje: programowe dodawanie możliwości odnajdywania do usługi i klienta WCF</span><span class="sxs-lookup"><span data-stu-id="444e6-112">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>](how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)  
 <span data-ttu-id="444e6-113">Przedstawia sposób odnajdywania usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="444e6-113">Shows how to make a Windows Communication Foundation (WCF) service discoverable.</span></span>  
  
 [<span data-ttu-id="444e6-114">Implementowanie serwera proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="444e6-114">Implementing a Discovery Proxy</span></span>](implementing-a-discovery-proxy.md)  
 <span data-ttu-id="444e6-115">Opisuje kroki wymagane do zaimplementowania serwera proxy odnajdywania, usługi wykrywalnej, która rejestruje się za pomocą serwera proxy odnajdywania, i klienta korzystającego z serwera proxy odnajdywania w celu znalezienia usługi wykrywalnej.</span><span class="sxs-lookup"><span data-stu-id="444e6-115">Describes the steps required to implement a discovery proxy, a discoverable service that registers with the discovery proxy, and a client that uses the discovery proxy to find the discoverable service.</span></span>  
  
 [<span data-ttu-id="444e6-116">Przechowywanie wersji odnajdywania</span><span class="sxs-lookup"><span data-stu-id="444e6-116">Discovery Versioning</span></span>](discovery-versioning.md)  
 <span data-ttu-id="444e6-117">Zawiera krótkie omówienie implementacji prototypu niektórych nowych funkcji odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="444e6-117">Provides a brief overview of a prototype implementation of some new discovery features.</span></span> <span data-ttu-id="444e6-118">Zawiera również omówienie sposobu wybierania wersji odnajdowania do użycia.</span><span class="sxs-lookup"><span data-stu-id="444e6-118">It also gives an overview on how to select the discovery version to use.</span></span>  
  
 [<span data-ttu-id="444e6-119">Konfigurowanie odnajdywania w pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="444e6-119">Configuring Discovery in a Configuration File</span></span>](configuring-discovery-in-a-configuration-file.md)  
 <span data-ttu-id="444e6-120">Pokazuje, jak skonfigurować odnajdywanie w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="444e6-120">Shows how to configure Discovery in configuration.</span></span>  
  
 [<span data-ttu-id="444e6-121">Używanie kanału klienta odnajdywania</span><span class="sxs-lookup"><span data-stu-id="444e6-121">Using the Discovery Client Channel</span></span>](using-the-discovery-client-channel.md)  
 <span data-ttu-id="444e6-122">Pokazuje, jak używać kanału klienta odnajdywania podczas pisania aplikacji klienckiej programu WCF.</span><span class="sxs-lookup"><span data-stu-id="444e6-122">Shows how to use a Discovery Client Channel when writing a WCF client application.</span></span>
