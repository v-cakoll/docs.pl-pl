---
title: Dodawanie stanu online i offline
ms.date: 03/30/2017
ms.assetid: 05e5f51d-81b6-4c17-b364-9dda447a5fce
ms.openlocfilehash: fb19614c1975c5634a81ca2f40edb145b724cd1d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488107"
---
# <a name="adding-online-and-offline-status"></a><span data-ttu-id="f1708-102">Dodawanie stanu online i offline</span><span class="sxs-lookup"><span data-stu-id="f1708-102">Adding Online and Offline Status</span></span>
<span data-ttu-id="f1708-103">W wielu przypadkach jest ważna w przypadku aplikacji do monitorowania konkretne szczegółowe informacje o stanie połączenia kanał elementu równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="f1708-103">In many cases, it is important for an application to monitor specific details about the status of a Peer Channel connection.</span></span> <span data-ttu-id="f1708-104">Te informacje można uzyskać przez wywołanie metody `GetProperty` metody wykonania <xref:System.ServiceModel.IOnlineStatus> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="f1708-104">You can obtain this information by calling the `GetProperty` method on an implementation of the <xref:System.ServiceModel.IOnlineStatus> interface.</span></span> <span data-ttu-id="f1708-105">Obiekt o implementację tego interfejsu można monitorować stan połączenia lub Zarejestruj się w celu obsługi zdarzeń, takich jak `OnOnline` i `OnOffline`i reagowania natychmiast wystąpienia zmian do stanu online.</span><span class="sxs-lookup"><span data-stu-id="f1708-105">An object with an implementation of this interface can monitor connection status or register for event handlers, such as `OnOnline` and `OnOffline`, and react immediately as changes to online status occur.</span></span>  
  
 <span data-ttu-id="f1708-106">W infrastrukturze kanału równorzędnego klienta uważa się być w trybie online, jeśli jest dołączona do przynajmniej jednego równorzędnego i w trybie offline w przeciwnym razie wartość.</span><span class="sxs-lookup"><span data-stu-id="f1708-106">In the Peer Channel infrastructure, a client is considered to be online if it is connected to at least one other peer and offline otherwise.</span></span> <span data-ttu-id="f1708-107">Może to być szczególnie przydatne w zarówno debugowanie tworzenie aplikacji lub wyświetlanie szczegółowych informacji dla użytkownika końcowego.</span><span class="sxs-lookup"><span data-stu-id="f1708-107">This can be particularly useful in both debugging a developing applications or displaying detailed information to the end user.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f1708-108">Program obsługi zdarzeń w trybie online należy najpierw upewnić się czy węzeł jest otwarte przed wysłaniem komunikaty.</span><span class="sxs-lookup"><span data-stu-id="f1708-108">An online event handler should first ensure that the node is open before sending any messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1708-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f1708-109">See Also</span></span>  
 [<span data-ttu-id="f1708-110">Tworzenie aplikacji kanału równorzędnego</span><span class="sxs-lookup"><span data-stu-id="f1708-110">Building a Peer Channel Application</span></span>](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
