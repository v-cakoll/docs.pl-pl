---
title: 'Instrukcje: testowanie serwera proxy odnajdywania'
ms.date: 03/30/2017
ms.assetid: d96e3fa2-3c42-4e5d-8244-2694081bdc32
ms.openlocfilehash: 78921d0a26f1116c87c2931b1472a161d6fed145
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84592817"
---
# <a name="how-to-test-the-discovery-proxy"></a><span data-ttu-id="ee579-102">Instrukcje: testowanie serwera proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="ee579-102">How to: Test the Discovery Proxy</span></span>
<span data-ttu-id="ee579-103">Jest to czwarte z czterech tematów, w których pokazano, jak zaimplementować serwer proxy odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="ee579-103">This is the fourth of four topics that shows how to implement a discovery proxy.</span></span> <span data-ttu-id="ee579-104">W poprzednim temacie [jak: implementowanie aplikacji klienckiej, która używa serwera proxy odnajdywania w celu znalezienia usługi](client-app-discovery-proxy-to-find-a-service.md), zaimplementowano aplikację kliencką WCF, która używa serwera proxy odnajdywania do znajdowania usługi, a następnie wywołuje usługę.</span><span class="sxs-lookup"><span data-stu-id="ee579-104">In the previous topic, [How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service](client-app-discovery-proxy-to-find-a-service.md), you implemented a WCF client application that uses the discovery proxy to find a service and then calls the service.</span></span> <span data-ttu-id="ee579-105">W tym temacie opisano sposób sprawdzania, czy serwer proxy odnajdywania, usługa i aplikacja kliencka działają zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="ee579-105">This topic describes how to verify the discovery proxy, the service, and the client application work as expected.</span></span>  
  
### <a name="run-the-discovery-proxy"></a><span data-ttu-id="ee579-106">Uruchom serwer proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="ee579-106">Run the Discovery Proxy</span></span>  
  
1. <span data-ttu-id="ee579-107">Otwórz wiersz polecenia jako administrator.</span><span class="sxs-lookup"><span data-stu-id="ee579-107">Open a command prompt as an administrator.</span></span>  
  
2. <span data-ttu-id="ee579-108">Może pojawić się okno dialogowe z informacją: Zapora systemu Windows zablokowała niektóre funkcje tego programu.</span><span class="sxs-lookup"><span data-stu-id="ee579-108">You may see a dialog that says: Windows Firewall has blocked some features of this program.</span></span> <span data-ttu-id="ee579-109">Jeśli zobaczysz ten komunikat, kliknij przycisk **odblokowywanie** .</span><span class="sxs-lookup"><span data-stu-id="ee579-109">If you see this message, click the **Unblock** button.</span></span>  
  
3. <span data-ttu-id="ee579-110">W wierszu polecenia Uruchom serwer proxy odnajdywania, obiektu DiscoveryProxy. exe.</span><span class="sxs-lookup"><span data-stu-id="ee579-110">Within the command prompt, run the discovery proxy, DiscoveryProxy.exe.</span></span>  
  
4. <span data-ttu-id="ee579-111">Aplikacja powinna wyświetlać następujący tekst: `Proxy started. Hit Enter to exit` .</span><span class="sxs-lookup"><span data-stu-id="ee579-111">The application should display the following text: `Proxy started. Hit Enter to exit`.</span></span>  
  
### <a name="run-the-discoverable-service"></a><span data-ttu-id="ee579-112">Uruchamianie usługi wykrywalnej</span><span class="sxs-lookup"><span data-stu-id="ee579-112">Run the Discoverable Service</span></span>  
  
1. <span data-ttu-id="ee579-113">Otwórz wiersz polecenia jako administrator.</span><span class="sxs-lookup"><span data-stu-id="ee579-113">Open a command prompt as an administrator.</span></span>  
  
2. <span data-ttu-id="ee579-114">W wierszu polecenia Uruchom usługę wykrywalną Service. exe.</span><span class="sxs-lookup"><span data-stu-id="ee579-114">Within the command prompt, run the Service.exe discoverable service.</span></span>  
  
3. <span data-ttu-id="ee579-115">Obiektu DiscoveryProxy. exe powinien wyświetlać następujący tekst: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .</span><span class="sxs-lookup"><span data-stu-id="ee579-115">The DiscoveryProxy.exe should display the following text: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .</span></span>  
  
### <a name="run-the-client-application"></a><span data-ttu-id="ee579-116">Uruchom aplikację kliencką</span><span class="sxs-lookup"><span data-stu-id="ee579-116">Run the Client Application</span></span>  
  
1. <span data-ttu-id="ee579-117">Otwórz wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="ee579-117">Open a command prompt.</span></span>  
  
2. <span data-ttu-id="ee579-118">W wierszu polecenia Uruchom aplikację Client. exe.</span><span class="sxs-lookup"><span data-stu-id="ee579-118">Within the command prompt, run the client.exe application.</span></span>  
  
3. <span data-ttu-id="ee579-119">Po kilku sekundach aplikacja kliencka wyświetli następujący tekst: łączenie z [Service-Endpoint].</span><span class="sxs-lookup"><span data-stu-id="ee579-119">After a few seconds the client application displays the following text: Connecting to [Service-Endpoint].</span></span>  
  
4. <span data-ttu-id="ee579-120">Program Service. exe powinien następnie wyświetlić następujący tekst: Odebrano żądanie powitania.</span><span class="sxs-lookup"><span data-stu-id="ee579-120">The service.exe should then display the following text: Greeting request received, I will respond.</span></span>  
  
5. <span data-ttu-id="ee579-121">Program Client. exe powinien następnie wyświetlić następujący tekst: Hello Client!</span><span class="sxs-lookup"><span data-stu-id="ee579-121">The client.exe should then display the following text: Hello Client!</span></span>  
  
### <a name="shut-down-the-applications"></a><span data-ttu-id="ee579-122">Zamykanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="ee579-122">Shut Down the Applications</span></span>  
  
1. <span data-ttu-id="ee579-123">Zamknij aplikację kliencką.</span><span class="sxs-lookup"><span data-stu-id="ee579-123">Shut down the client application.</span></span>  
  
2. <span data-ttu-id="ee579-124">Zamknij usługę.</span><span class="sxs-lookup"><span data-stu-id="ee579-124">Shut down the service.</span></span> <span data-ttu-id="ee579-125">Serwer proxy odnajdywania wyświetla następujący tekst: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******` .</span><span class="sxs-lookup"><span data-stu-id="ee579-125">The discovery proxy displays the following text: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`.</span></span>  
  
3. <span data-ttu-id="ee579-126">Zamknij serwer proxy odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="ee579-126">Shut down the discovery proxy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee579-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ee579-127">See also</span></span>

- [<span data-ttu-id="ee579-128">Omówienie odnajdywania WCF</span><span class="sxs-lookup"><span data-stu-id="ee579-128">WCF Discovery Overview</span></span>](wcf-discovery-overview.md)
- [<span data-ttu-id="ee579-129">Instrukcje: Wdrażanie serwera proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="ee579-129">How to: Implement a Discovery Proxy</span></span>](how-to-implement-a-discovery-proxy.md)
- [<span data-ttu-id="ee579-130">Instrukcje: implementowanie odnajdywanej usługi rejestrowanej za pomocą serwera proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="ee579-130">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](discoverable-service-that-registers-with-the-discovery-proxy.md)
- [<span data-ttu-id="ee579-131">Instrukcje: wdrażanie aplikacji klienta znajdującej usługę przy użyciu serwera proxy odnajdywania</span><span class="sxs-lookup"><span data-stu-id="ee579-131">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](client-app-discovery-proxy-to-find-a-service.md)
