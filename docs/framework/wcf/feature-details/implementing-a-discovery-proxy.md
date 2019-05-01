---
title: Implementowanie serwera proxy odnajdywania
ms.date: 03/30/2017
ms.assetid: dda20e79-8df3-438e-a281-69d779d978ec
ms.openlocfilehash: 5d9296d8ba70d4c9e8d8339fa3a032d9c4c62826
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62047064"
---
# <a name="implementing-a-discovery-proxy"></a><span data-ttu-id="12662-102">Implementowanie serwera proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="12662-102">Implementing a Discovery Proxy</span></span>
<span data-ttu-id="12662-103">W tej sekcji opisano kroki wymagane do wdrożenia serwera proxy odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="12662-103">This section describes the steps required to implement a discovery proxy.</span></span> <span data-ttu-id="12662-104">Serwera proxy odnajdywania to autonomiczna usługa, który zawiera repozytorium usług.</span><span class="sxs-lookup"><span data-stu-id="12662-104">A discovery proxy is a standalone service that contains a repository of services.</span></span> <span data-ttu-id="12662-105">Klienci mogą wysyłać zapytania serwera proxy odnajdywania można znaleźć wykrywalny usług, które ma informacje o serwerze proxy.</span><span class="sxs-lookup"><span data-stu-id="12662-105">Clients can query a discovery proxy to find discoverable services that the proxy is aware of.</span></span> <span data-ttu-id="12662-106">Jak serwer proxy jest wypełniana przy użyciu usługi zależy od implementujący.</span><span class="sxs-lookup"><span data-stu-id="12662-106">How a proxy is populated with services is up to the implementer.</span></span> <span data-ttu-id="12662-107">Na przykład serwera proxy odnajdywania można nawiązać połączenie z istniejącym repozytorium usługi i stał się wykrywalny, administrator może użyć interfejsu API zarządzania nad dodaniem usług wykrywalny do serwera proxy lub serwera proxy odnajdywania może korzystać z funkcji anons, aby te informacje aktualizowanie swojej wewnętrznej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="12662-107">For example, a discovery proxy can connect to an existing service repository and make that information discoverable, an administrator can use a management API to add discoverable services to a proxy, or a discovery proxy can use the announcement functionality to update its internal cache.</span></span>  
  
 <span data-ttu-id="12662-108">Implementacja programu WCF zapewnia klas bazowych, które umożliwiają łatwe tworzenie serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="12662-108">The WCF implementation provides base classes that allow you to easily build a proxy.</span></span> <span data-ttu-id="12662-109">Korzystanie z tych interfejsów API do tworzenia serwera Proxy odnajdywania na podstawie istniejącego repozytorium.</span><span class="sxs-lookup"><span data-stu-id="12662-109">You can utilize these APIs to build a Discovery Proxy on top of your existing repository.</span></span>  
  
 <span data-ttu-id="12662-110">Serwera proxy odnajdywania zaimplementowane w tym miejscu jest podobnie jak inne usługi WCF, możesz również stał się wykrywalny serwera proxy odnajdywania i klienci mogą zlokalizować jego punkty końcowe.</span><span class="sxs-lookup"><span data-stu-id="12662-110">The discovery proxy implemented here is like any other WCF services, in that you can also make the discovery proxy discoverable and have the clients locate its endpoints.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="12662-111">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="12662-111">In This Section</span></span>  
 [<span data-ttu-id="12662-112">Instrukcje: Wdrażanie serwera Proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="12662-112">How to: Implement a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 <span data-ttu-id="12662-113">W tym artykule opisano sposób wdrażania serwera proxy odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="12662-113">Describes how to implement a discovery proxy.</span></span>  
  
 [<span data-ttu-id="12662-114">Instrukcje: Implementowanie Odnajdywanej usługi rejestrowanej za pomocą serwera Proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="12662-114">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 <span data-ttu-id="12662-115">Opisuje sposób Implementowanie odnajdywanej usługi WCF, rejestrowanej za pomocą serwera proxy odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="12662-115">Describes how to implement a discoverable WCF service that registers with the discovery proxy.</span></span>  
  
 [<span data-ttu-id="12662-116">Instrukcje: Wdrażanie aplikacji klienta, który używa serwera Proxy odnajdywania można znaleźć usługi</span><span class="sxs-lookup"><span data-stu-id="12662-116">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)  
 <span data-ttu-id="12662-117">W tym artykule opisano, jak wdrożyć aplikację kliencką usługi WCF, która używa serwera proxy odnajdywania do wyszukiwania dla usługi.</span><span class="sxs-lookup"><span data-stu-id="12662-117">Describes how to implement a WCF client application that uses the discovery proxy to search for a service.</span></span>  
  
 [<span data-ttu-id="12662-118">Instrukcje: Testowanie serwera Proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="12662-118">How to: Test the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-test-the-discovery-proxy.md)  
 <span data-ttu-id="12662-119">Zawiera opis sposobu testowania kodu napisanego w poprzednich tematach trzy.</span><span class="sxs-lookup"><span data-stu-id="12662-119">Describes how to test the code written in the previous three topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12662-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="12662-120">See also</span></span>

- [<span data-ttu-id="12662-121">Odnajdywanie w programie WCF</span><span class="sxs-lookup"><span data-stu-id="12662-121">WCF Discovery</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery.md)
- [<span data-ttu-id="12662-122">Instrukcje: Programowe Dodawanie możliwości odnajdywania do usługi i klienta WCF</span><span class="sxs-lookup"><span data-stu-id="12662-122">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)
