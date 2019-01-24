---
title: Dodawanie stanu online i offline
ms.date: 03/30/2017
ms.assetid: 05e5f51d-81b6-4c17-b364-9dda447a5fce
ms.openlocfilehash: 6a04648e4251774538d298b35d1d655e09e03495
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54591912"
---
# <a name="adding-online-and-offline-status"></a><span data-ttu-id="ad8a2-102">Dodawanie stanu online i offline</span><span class="sxs-lookup"><span data-stu-id="ad8a2-102">Adding Online and Offline Status</span></span>
<span data-ttu-id="ad8a2-103">W wielu przypadkach jest ważne w przypadku aplikacji do monitorowania konkretne szczegółowe informacje o stan połączenia kanał elementu równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="ad8a2-103">In many cases, it is important for an application to monitor specific details about the status of a Peer Channel connection.</span></span> <span data-ttu-id="ad8a2-104">Te informacje można uzyskać przez wywołanie metody `GetProperty` metody na implementację <xref:System.ServiceModel.IOnlineStatus> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="ad8a2-104">You can obtain this information by calling the `GetProperty` method on an implementation of the <xref:System.ServiceModel.IOnlineStatus> interface.</span></span> <span data-ttu-id="ad8a2-105">Obiekt o implementację tego interfejsu można monitorować stan połączenia lub zarejestruj procedury obsługi zdarzeń, takich jak `OnOnline` i `OnOffline`i od razu wraz ze zmianami do stanu online.</span><span class="sxs-lookup"><span data-stu-id="ad8a2-105">An object with an implementation of this interface can monitor connection status or register for event handlers, such as `OnOnline` and `OnOffline`, and react immediately as changes to online status occur.</span></span>  
  
 <span data-ttu-id="ad8a2-106">W infrastrukturze kanał elementu równorzędnego klienta uznaje się być w trybie online, jeśli jest połączony co najmniej jeden innych elementów równorzędnych i w trybie offline w przeciwnym razie.</span><span class="sxs-lookup"><span data-stu-id="ad8a2-106">In the Peer Channel infrastructure, a client is considered to be online if it is connected to at least one other peer and offline otherwise.</span></span> <span data-ttu-id="ad8a2-107">Może to być szczególnie przydatne w zarówno profilowanie tworzenie aplikacji lub wyświetlanie szczegółowych informacji do użytkownika końcowego.</span><span class="sxs-lookup"><span data-stu-id="ad8a2-107">This can be particularly useful in both debugging a developing applications or displaying detailed information to the end user.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ad8a2-108">Program obsługi zdarzeń w trybie online należy najpierw upewnić się, że węzeł został otwarty przed wysłaniem komunikatów.</span><span class="sxs-lookup"><span data-stu-id="ad8a2-108">An online event handler should first ensure that the node is open before sending any messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad8a2-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ad8a2-109">See also</span></span>
- [<span data-ttu-id="ad8a2-110">Tworzenie aplikacji kanału równorzędnego</span><span class="sxs-lookup"><span data-stu-id="ad8a2-110">Building a Peer Channel Application</span></span>](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
