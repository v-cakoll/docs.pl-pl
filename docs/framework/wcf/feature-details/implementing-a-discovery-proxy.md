---
title: Implementowanie serwera proxy odnajdywania
ms.date: 03/30/2017
ms.assetid: dda20e79-8df3-438e-a281-69d779d978ec
ms.openlocfilehash: 382df95fef2108d338e4ea327da9185c856eca5a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579244"
---
# <a name="implementing-a-discovery-proxy"></a><span data-ttu-id="cd1a4-102">Implementowanie serwera proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="cd1a4-102">Implementing a Discovery Proxy</span></span>
<span data-ttu-id="cd1a4-103">W tej sekcji opisano kroki wymagane do zaimplementowania serwera proxy odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="cd1a4-103">This section describes the steps required to implement a discovery proxy.</span></span> <span data-ttu-id="cd1a4-104">Serwer proxy odnajdywania jest usługą autonomiczną, która zawiera repozytorium usług.</span><span class="sxs-lookup"><span data-stu-id="cd1a4-104">A discovery proxy is a standalone service that contains a repository of services.</span></span> <span data-ttu-id="cd1a4-105">Klienci mogą wysyłać zapytania do serwera proxy odnajdywania, aby znaleźć usługi wykrywalne, których dotyczy serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="cd1a4-105">Clients can query a discovery proxy to find discoverable services that the proxy is aware of.</span></span> <span data-ttu-id="cd1a4-106">Sposób wypełniania serwera proxy za pomocą usług jest do realizatora.</span><span class="sxs-lookup"><span data-stu-id="cd1a4-106">How a proxy is populated with services is up to the implementer.</span></span> <span data-ttu-id="cd1a4-107">Na przykład serwer proxy odnajdywania może połączyć się z istniejącym repozytorium usługi i przetworzyć te informacje, administrator może użyć interfejsu API zarządzania, aby dodać odnajdywane usługi do serwera proxy, lub serwer proxy odnajdywania może korzystać z funkcji anonsowania do aktualizowania wewnętrznej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="cd1a4-107">For example, a discovery proxy can connect to an existing service repository and make that information discoverable, an administrator can use a management API to add discoverable services to a proxy, or a discovery proxy can use the announcement functionality to update its internal cache.</span></span>  
  
 <span data-ttu-id="cd1a4-108">Implementacja programu WCF zawiera klasy podstawowe, które umożliwiają łatwe tworzenie serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="cd1a4-108">The WCF implementation provides base classes that allow you to easily build a proxy.</span></span> <span data-ttu-id="cd1a4-109">Możesz użyć tych interfejsów API, aby skompilować serwer proxy odnajdywania na podstawie istniejącego repozytorium.</span><span class="sxs-lookup"><span data-stu-id="cd1a4-109">You can utilize these APIs to build a Discovery Proxy on top of your existing repository.</span></span>  
  
 <span data-ttu-id="cd1a4-110">Serwer proxy odnajdywania wdrożony w tym miejscu jest podobny do wszystkich innych usług WCF, w tym, że można również odnajdywać serwer proxy odnajdywania i klienci lokalizują jego punkty końcowe.</span><span class="sxs-lookup"><span data-stu-id="cd1a4-110">The discovery proxy implemented here is like any other WCF services, in that you can also make the discovery proxy discoverable and have the clients locate its endpoints.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cd1a4-111">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="cd1a4-111">In This Section</span></span>  
 [<span data-ttu-id="cd1a4-112">Instrukcje: Wdrażanie serwera proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="cd1a4-112">How to: Implement a Discovery Proxy</span></span>](how-to-implement-a-discovery-proxy.md)  
 <span data-ttu-id="cd1a4-113">Opisuje sposób implementacji serwera proxy odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="cd1a4-113">Describes how to implement a discovery proxy.</span></span>  
  
 [<span data-ttu-id="cd1a4-114">Instrukcje: implementowanie odnajdywanej usługi rejestrowanej za pomocą serwera proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="cd1a4-114">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](discoverable-service-that-registers-with-the-discovery-proxy.md)  
 <span data-ttu-id="cd1a4-115">Zawiera opis sposobu implementacji odnajdywanej usługi WCF, która jest rejestrowana przy użyciu serwera proxy odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="cd1a4-115">Describes how to implement a discoverable WCF service that registers with the discovery proxy.</span></span>  
  
 [<span data-ttu-id="cd1a4-116">Instrukcje: wdrażanie aplikacji klienta znajdującej usługę przy użyciu serwera proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="cd1a4-116">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](client-app-discovery-proxy-to-find-a-service.md)  
 <span data-ttu-id="cd1a4-117">Opisuje sposób implementacji aplikacji klienckiej WCF, która używa serwera proxy odnajdywania do wyszukiwania usługi.</span><span class="sxs-lookup"><span data-stu-id="cd1a4-117">Describes how to implement a WCF client application that uses the discovery proxy to search for a service.</span></span>  
  
 [<span data-ttu-id="cd1a4-118">Instrukcje: testowanie serwera proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="cd1a4-118">How to: Test the Discovery Proxy</span></span>](how-to-test-the-discovery-proxy.md)  
 <span data-ttu-id="cd1a4-119">Opisuje, jak przetestować kod zapisany w poprzednich trzech tematach.</span><span class="sxs-lookup"><span data-stu-id="cd1a4-119">Describes how to test the code written in the previous three topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd1a4-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cd1a4-120">See also</span></span>

- [<span data-ttu-id="cd1a4-121">Odnajdywanie w programie WCF</span><span class="sxs-lookup"><span data-stu-id="cd1a4-121">WCF Discovery</span></span>](wcf-discovery.md)
- [<span data-ttu-id="cd1a4-122">Instrukcje: programowe dodawanie możliwości odnajdywania do usługi i klienta WCF</span><span class="sxs-lookup"><span data-stu-id="cd1a4-122">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>](how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)
