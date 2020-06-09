---
title: Dodawanie stanu online i offline
ms.date: 03/30/2017
ms.assetid: 05e5f51d-81b6-4c17-b364-9dda447a5fce
ms.openlocfilehash: da170bbc22d04dcbf5f7cd4ac084a004bb4b026e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597686"
---
# <a name="adding-online-and-offline-status"></a><span data-ttu-id="6a03a-102">Dodawanie stanu online i offline</span><span class="sxs-lookup"><span data-stu-id="6a03a-102">Adding Online and Offline Status</span></span>
<span data-ttu-id="6a03a-103">W wielu przypadkach ważne jest, aby aplikacja monitorowała szczegółowe informacje o stanie połączenia kanału równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="6a03a-103">In many cases, it is important for an application to monitor specific details about the status of a Peer Channel connection.</span></span> <span data-ttu-id="6a03a-104">Te informacje można uzyskać, wywołując `GetProperty` metodę dla implementacji <xref:System.ServiceModel.IOnlineStatus> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="6a03a-104">You can obtain this information by calling the `GetProperty` method on an implementation of the <xref:System.ServiceModel.IOnlineStatus> interface.</span></span> <span data-ttu-id="6a03a-105">Obiekt z implementacją tego interfejsu może monitorować stan połączenia lub rejestr dla programów obsługi zdarzeń, takich jak i i `OnOnline` `OnOffline` reagować natychmiast po wystąpieniu zmian stanu online.</span><span class="sxs-lookup"><span data-stu-id="6a03a-105">An object with an implementation of this interface can monitor connection status or register for event handlers, such as `OnOnline` and `OnOffline`, and react immediately as changes to online status occur.</span></span>  
  
 <span data-ttu-id="6a03a-106">W infrastrukturze kanału równorzędnego klient jest traktowany jako w trybie online, jeśli jest połączony z co najmniej jednym innym węzłem równorzędnym i w przeciwnym razie w trybie offline.</span><span class="sxs-lookup"><span data-stu-id="6a03a-106">In the Peer Channel infrastructure, a client is considered to be online if it is connected to at least one other peer and offline otherwise.</span></span> <span data-ttu-id="6a03a-107">Może to być szczególnie przydatne w przypadku debugowania aplikacji tworzących lub wyświetlania szczegółowych informacji dla użytkownika końcowego.</span><span class="sxs-lookup"><span data-stu-id="6a03a-107">This can be particularly useful in both debugging a developing applications or displaying detailed information to the end user.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6a03a-108">Procedura obsługi zdarzeń online powinna najpierw upewnić się, że węzeł jest otwarty przed wysłaniem jakichkolwiek komunikatów.</span><span class="sxs-lookup"><span data-stu-id="6a03a-108">An online event handler should first ensure that the node is open before sending any messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a03a-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6a03a-109">See also</span></span>

- [<span data-ttu-id="6a03a-110">Tworzenie aplikacji kanału równorzędnego</span><span class="sxs-lookup"><span data-stu-id="6a03a-110">Building a Peer Channel Application</span></span>](building-a-peer-channel-application.md)
