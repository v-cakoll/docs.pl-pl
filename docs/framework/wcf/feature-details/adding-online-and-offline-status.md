---
title: Dodawanie stanu online i offline
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 05e5f51d-81b6-4c17-b364-9dda447a5fce
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5d5b6c858b5aa5918498ba8fccee41f7392ac32e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="adding-online-and-offline-status"></a><span data-ttu-id="3ef55-102">Dodawanie stanu online i offline</span><span class="sxs-lookup"><span data-stu-id="3ef55-102">Adding Online and Offline Status</span></span>
<span data-ttu-id="3ef55-103">W wielu przypadkach jest ważna w przypadku aplikacji do monitorowania konkretne szczegółowe informacje o stanie połączenia kanał elementu równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="3ef55-103">In many cases, it is important for an application to monitor specific details about the status of a Peer Channel connection.</span></span> <span data-ttu-id="3ef55-104">Te informacje można uzyskać przez wywołanie metody `GetProperty` metody wykonania <xref:System.ServiceModel.IOnlineStatus> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="3ef55-104">You can obtain this information by calling the `GetProperty` method on an implementation of the <xref:System.ServiceModel.IOnlineStatus> interface.</span></span> <span data-ttu-id="3ef55-105">Obiekt o implementację tego interfejsu można monitorować stan połączenia lub Zarejestruj się w celu obsługi zdarzeń, takich jak `OnOnline` i `OnOffline`i reagowania natychmiast wystąpienia zmian do stanu online.</span><span class="sxs-lookup"><span data-stu-id="3ef55-105">An object with an implementation of this interface can monitor connection status or register for event handlers, such as `OnOnline` and `OnOffline`, and react immediately as changes to online status occur.</span></span>  
  
 <span data-ttu-id="3ef55-106">W infrastrukturze kanału równorzędnego klienta uważa się być w trybie online, jeśli jest dołączona do przynajmniej jednego równorzędnego i w trybie offline w przeciwnym razie wartość.</span><span class="sxs-lookup"><span data-stu-id="3ef55-106">In the Peer Channel infrastructure, a client is considered to be online if it is connected to at least one other peer and offline otherwise.</span></span> <span data-ttu-id="3ef55-107">Może to być szczególnie przydatne w zarówno debugowanie tworzenie aplikacji lub wyświetlanie szczegółowych informacji dla użytkownika końcowego.</span><span class="sxs-lookup"><span data-stu-id="3ef55-107">This can be particularly useful in both debugging a developing applications or displaying detailed information to the end user.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3ef55-108">Program obsługi zdarzeń w trybie online należy najpierw upewnić się czy węzeł jest otwarte przed wysłaniem komunikaty.</span><span class="sxs-lookup"><span data-stu-id="3ef55-108">An online event handler should first ensure that the node is open before sending any messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ef55-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3ef55-109">See Also</span></span>  
 [<span data-ttu-id="3ef55-110">Tworzenie aplikacji kanału równorzędnego</span><span class="sxs-lookup"><span data-stu-id="3ef55-110">Building a Peer Channel Application</span></span>](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
