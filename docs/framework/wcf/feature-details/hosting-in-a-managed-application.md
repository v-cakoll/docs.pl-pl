---
title: Hosting w aplikacji zarządzanej
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af70132d-e9e1-4f32-b20f-f0014629758a
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1e81a8eb27725edeccf3e5c7489109ba47b70dec
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="hosting-in-a-managed-application"></a><span data-ttu-id="421bb-102">Hosting w aplikacji zarządzanej</span><span class="sxs-lookup"><span data-stu-id="421bb-102">Hosting in a Managed Application</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="421bb-103"> usługi mogą być hostowane w dowolnym [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="421bb-103"> services can be hosted in any [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] application.</span></span> <span data-ttu-id="421bb-104">Usługi hostingowe własnym jest najbardziej elastycznego opcja hostingu, ponieważ wymaga co najmniej infrastruktury do wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="421bb-104">Self-hosting services is the most flexible hosting option because it requires the least infrastructure to deploy.</span></span> <span data-ttu-id="421bb-105">Jednak jest również opcji hostingu najmniej niezawodne, ponieważ zarządzane aplikacje nie udostępniają zaawansowane funkcje obsługi i zarządzania inne opcje hostingu w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], takie jak usługi Internet Information Services (IIS) i usług systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="421bb-105">However, it is also the least robust hosting option, because managed applications do not provide the advanced hosting and management features of other hosting options in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], such as Internet Information Services (IIS) and Windows services.</span></span>  
  
 <span data-ttu-id="421bb-106">Aby utworzyć samodzielnie hostowana usługa, Utwórz i otwórz wystąpienie <xref:System.ServiceModel.ServiceHost>, która uruchamia usługę nasłuchiwania dla wiadomości.</span><span class="sxs-lookup"><span data-stu-id="421bb-106">To create a self-hosted service, create and open an instance of the <xref:System.ServiceModel.ServiceHost>, which starts a service listening for messages.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="421bb-107"> [Porady: hostowanie usługi WCF w zarządzanej aplikacji](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md).</span><span class="sxs-lookup"><span data-stu-id="421bb-107"> [How to: Host a WCF Service in a Managed Application](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md).</span></span>  
  
 <span data-ttu-id="421bb-108">Pełny przykład na temat Definiowanie kontraktu, zaimplementować kontrakt i obsługiwać usługę wewnątrz zarządzanej aplikacji zobacz [Wprowadzenie — samouczek](../../../../docs/framework/wcf/getting-started-tutorial.md) i [hosta samodzielnego](../../../../docs/framework/wcf/samples/self-host.md).</span><span class="sxs-lookup"><span data-stu-id="421bb-108">For a complete example on how to define a contract, implement the contract, and host a service inside of a managed application see the [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md) and the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md).</span></span>  
  
 <span data-ttu-id="421bb-109">W poniższych sekcjach opisano typowe scenariusze, które używają tej opcji hostingu.</span><span class="sxs-lookup"><span data-stu-id="421bb-109">The following sections describe common scenarios that use this hosting option.</span></span>  
  
## <a name="console-applications"></a><span data-ttu-id="421bb-110">Aplikacje konsoli</span><span class="sxs-lookup"><span data-stu-id="421bb-110">Console Applications</span></span>  
 <span data-ttu-id="421bb-111">Typowe scenariusze, które są własnym hostingu umożliwia [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług uruchomionych w konsoli aplikacji.</span><span class="sxs-lookup"><span data-stu-id="421bb-111">Common scenarios that self-hosting enables are [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services running inside console applications.</span></span> <span data-ttu-id="421bb-112">Hosting [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługa wewnątrz aplikacji konsoli jest zazwyczaj przydatne w fazie projektowania usługi.</span><span class="sxs-lookup"><span data-stu-id="421bb-112">Hosting a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service inside a console application is typically useful during the development phase of the service.</span></span> <span data-ttu-id="421bb-113">Z tego powodu łatwy do debugowania, łatwo uzyskać informacje o śledzeniu na, aby dowiedzieć się, co dzieje się wewnątrz aplikacji i łatwo przenosić, kopiując je do nowej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="421bb-113">This makes them easy to debug, easy to get trace information from to find out what is happening inside of the application, and easy to move around by copying them to new locations.</span></span>  
  
## <a name="rich-client-applications"></a><span data-ttu-id="421bb-114">Aplikacje wzbogaconego klienta</span><span class="sxs-lookup"><span data-stu-id="421bb-114">Rich Client Applications</span></span>  
 <span data-ttu-id="421bb-115">Inne typowe scenariusze, które umożliwia hostingu samodzielnego są zaawansowanych aplikacji klienckich, takich jak zasoby oparte na Windows Presentation Foundation (WPF) lub program Windows Forms (WinForms).</span><span class="sxs-lookup"><span data-stu-id="421bb-115">Other common scenarios that self-hosting enables are rich client applications, such as those based on Windows Presentation Foundation (WPF) or Windows Forms (WinForms).</span></span> <span data-ttu-id="421bb-116">Ta opcja hostingu ułatwia także dla zaawansowanych aplikacji klienckich, takich jak [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] i WinForms aplikacji, aby komunikować się na zewnątrz.</span><span class="sxs-lookup"><span data-stu-id="421bb-116">This hosting option also makes it easy for rich client applications, such as [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] and WinForms applications, to communicate with the outside world.</span></span> <span data-ttu-id="421bb-117">Na przykład klient współpracy peer-to-peer, który używa [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] dla jego interfejsu użytkownika, a także hostów [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi, która umożliwia innym klientom nawiązania połączenia i udostępnianie informacji.</span><span class="sxs-lookup"><span data-stu-id="421bb-117">For example, a peer-to-peer collaboration client that uses [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] for its user interface and also hosts a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service that allows other clients to connect to it and share information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="421bb-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="421bb-118">See Also</span></span>  
 [<span data-ttu-id="421bb-119">Usługi hostingowe</span><span class="sxs-lookup"><span data-stu-id="421bb-119">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)  
 [<span data-ttu-id="421bb-120">Wprowadzenie — samouczek</span><span class="sxs-lookup"><span data-stu-id="421bb-120">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)
