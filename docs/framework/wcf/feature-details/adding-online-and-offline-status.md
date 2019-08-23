---
title: Dodawanie stanu online i offline
ms.date: 03/30/2017
ms.assetid: 05e5f51d-81b6-4c17-b364-9dda447a5fce
ms.openlocfilehash: 74b113d64003756982a6b5701d9601c3116a9046
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960645"
---
# <a name="adding-online-and-offline-status"></a><span data-ttu-id="99656-102">Dodawanie stanu online i offline</span><span class="sxs-lookup"><span data-stu-id="99656-102">Adding Online and Offline Status</span></span>
<span data-ttu-id="99656-103">W wielu przypadkach ważne jest, aby aplikacja monitorowała szczegółowe informacje o stanie połączenia kanału równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="99656-103">In many cases, it is important for an application to monitor specific details about the status of a Peer Channel connection.</span></span> <span data-ttu-id="99656-104">Te informacje można uzyskać, wywołując `GetProperty` metodę dla implementacji <xref:System.ServiceModel.IOnlineStatus> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="99656-104">You can obtain this information by calling the `GetProperty` method on an implementation of the <xref:System.ServiceModel.IOnlineStatus> interface.</span></span> <span data-ttu-id="99656-105">Obiekt z implementacją tego interfejsu może monitorować stan połączenia lub rejestr dla programów obsługi zdarzeń, takich jak `OnOnline` i `OnOffline`i reagować natychmiast po wystąpieniu zmian stanu online.</span><span class="sxs-lookup"><span data-stu-id="99656-105">An object with an implementation of this interface can monitor connection status or register for event handlers, such as `OnOnline` and `OnOffline`, and react immediately as changes to online status occur.</span></span>  
  
 <span data-ttu-id="99656-106">W infrastrukturze kanału równorzędnego klient jest traktowany jako w trybie online, jeśli jest połączony z co najmniej jednym innym węzłem równorzędnym i w przeciwnym razie w trybie offline.</span><span class="sxs-lookup"><span data-stu-id="99656-106">In the Peer Channel infrastructure, a client is considered to be online if it is connected to at least one other peer and offline otherwise.</span></span> <span data-ttu-id="99656-107">Może to być szczególnie przydatne w przypadku debugowania aplikacji tworzących lub wyświetlania szczegółowych informacji dla użytkownika końcowego.</span><span class="sxs-lookup"><span data-stu-id="99656-107">This can be particularly useful in both debugging a developing applications or displaying detailed information to the end user.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="99656-108">Procedura obsługi zdarzeń online powinna najpierw upewnić się, że węzeł jest otwarty przed wysłaniem jakichkolwiek komunikatów.</span><span class="sxs-lookup"><span data-stu-id="99656-108">An online event handler should first ensure that the node is open before sending any messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99656-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="99656-109">See also</span></span>

- [<span data-ttu-id="99656-110">Tworzenie aplikacji kanału równorzędnego</span><span class="sxs-lookup"><span data-stu-id="99656-110">Building a Peer Channel Application</span></span>](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
