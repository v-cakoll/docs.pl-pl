---
title: Izolacja sieci dla aplikacji Windows Store
ms.date: 03/30/2017
ms.assetid: b064497c-d956-46b8-838d-7a0223c7e200
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 4d26b6df5d26a96bb8fa41dd3a8151fcb4a08b75
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43773660"
---
# <a name="network-isolation-for-windows-store-apps"></a><span data-ttu-id="a36c5-102">Izolacja sieci dla aplikacji Windows Store</span><span class="sxs-lookup"><span data-stu-id="a36c5-102">Network Isolation for Windows Store Apps</span></span>
<span data-ttu-id="a36c5-103">Klasy w <xref:System.Net>, <xref:System.Net.Http>, i <xref:System.Net.Http.Headers> przestrzeni nazw może służyć do tworzenia aplikacji Windows Store lub aplikacjami pulpitu.</span><span class="sxs-lookup"><span data-stu-id="a36c5-103">Classes in the <xref:System.Net>,  <xref:System.Net.Http>, and <xref:System.Net.Http.Headers> namespaces can be used to develop Windows Store  apps  or desktop apps.</span></span> <span data-ttu-id="a36c5-104">W przypadku użycia w aplikacji Windows Store, klas w tych obszarach nazw dotyczy izolacji sieci, częścią modelu zabezpieczeń aplikacji, które są używane przez [!INCLUDE[win8](../../../includes/win8-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a36c5-104">When used in a Windows Store app, classes in these namespaces are affected by network isolation, part of the application security model used by the [!INCLUDE[win8](../../../includes/win8-md.md)].</span></span> <span data-ttu-id="a36c5-105">Możliwości odpowiedniej sieci musi być włączony w manifeście aplikacji dla aplikacji Windows Store dla systemu zezwolić na dostęp do sieci.</span><span class="sxs-lookup"><span data-stu-id="a36c5-105">The appropriate network capabilities must be enabled in the app manifest for a Windows Store app for the system to allow network access.</span></span>  
  
## <a name="checklist-for-network-isolation"></a><span data-ttu-id="a36c5-106">Lista kontrolna na potrzeby izolacji sieciowej</span><span class="sxs-lookup"><span data-stu-id="a36c5-106">Checklist for Network Isolation</span></span>  
 <span data-ttu-id="a36c5-107">Użyj tej listy kontrolnej, należy upewnić się, że izolacja sieciowa jest skonfigurowany dla aplikacji Windows Store.</span><span class="sxs-lookup"><span data-stu-id="a36c5-107">Use this checklist to be sure that network isolation is configured for your Windows Store app.</span></span>  
  
1.  <span data-ttu-id="a36c5-108">Określ kierunek żądań dostępu do sieci wymagane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="a36c5-108">Determine the direction of network access requests needed by the app.</span></span> <span data-ttu-id="a36c5-109">Może to być wychodzącego zainicjowane przez klienta żądania lub żądania przychodzące niechciane lub może być kombinację obu tych typów żądań sieci.</span><span class="sxs-lookup"><span data-stu-id="a36c5-109">This can be either outbound client-initiated requests or inbound unsolicited requests or it could be a combination of both of these network request types.</span></span>  
  
2.  <span data-ttu-id="a36c5-110">Określanie typu zasobów sieciowych, które ta aplikacja będzie komunikować się z.</span><span class="sxs-lookup"><span data-stu-id="a36c5-110">Determine the type of network resources that that app will communicate with.</span></span> <span data-ttu-id="a36c5-111">Aplikacja może być konieczne do komunikowania się z zaufanych zasobów w domu lub pracy sieci.</span><span class="sxs-lookup"><span data-stu-id="a36c5-111">An app may need to communicate with trusted resources on a Home or Work network.</span></span> <span data-ttu-id="a36c5-112">Aplikacja może być konieczne do komunikowania się z zasobami przez Internet.</span><span class="sxs-lookup"><span data-stu-id="a36c5-112">An app might need to communicate with resources on the Internet.</span></span> <span data-ttu-id="a36c5-113">Aplikacja może potrzebować dostępu do obu rodzajów zasobów sieciowych.</span><span class="sxs-lookup"><span data-stu-id="a36c5-113">An app might need access to both types of network resources.</span></span>  
  
3.  <span data-ttu-id="a36c5-114">Skonfiguruj minimalną wymaganą możliwości izolacji sieci w manifeście aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a36c5-114">Configure the minimum-required networking isolation capabilities in the app manifest.</span></span>  
  
4.  <span data-ttu-id="a36c5-115">Wdrażanie i uruchamianie aplikacji, aby przetestować go za pomocą narzędzia izolacji sieci, które są dostarczane do rozwiązywania problemów.</span><span class="sxs-lookup"><span data-stu-id="a36c5-115">Deploy and run your app to test it using the network isolation tools provided for troubleshooting.</span></span>  
  
 <span data-ttu-id="a36c5-116">Aby uzyskać bardziej szczegółowe informacje dotyczące sposobu konfigurowania funkcji sieciowych i izolacji narzędzi używanych do rozwiązywania problemów izolacji sieci, zobacz [sposobu konfigurowania możliwości izolacji sieci](https://go.microsoft.com/fwlink/?LinkID=228265) w [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] dla deweloperów dokumentacja.</span><span class="sxs-lookup"><span data-stu-id="a36c5-116">For more detailed information on how to configure network capabilities and isolation tools used for troubleshooting network isolation, see [How to configure network isolation capabilities](https://go.microsoft.com/fwlink/?LinkID=228265) in the [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] developer documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a36c5-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a36c5-117">See Also</span></span>  
 [<span data-ttu-id="a36c5-118">Łączenie z usługą sieci web</span><span class="sxs-lookup"><span data-stu-id="a36c5-118">Connecting to a web service</span></span>](https://go.microsoft.com/fwlink/?LinkID=245696)  
 [<span data-ttu-id="a36c5-119">Wskazówki i listy kontrolne do izolacji sieci</span><span class="sxs-lookup"><span data-stu-id="a36c5-119">Guidelines and checklist for network isolation</span></span>](https://go.microsoft.com/fwlink/?LinkID=228265)  
 [<span data-ttu-id="a36c5-120">Szybki Start: Łączenie za pomocą elementu HttpClient</span><span class="sxs-lookup"><span data-stu-id="a36c5-120">Quickstart: Connecting using HttpClient</span></span>](https://go.microsoft.com/fwlink/?LinkId=245697)  
 [<span data-ttu-id="a36c5-121">Jak używać klasy HttpClient obsługi</span><span class="sxs-lookup"><span data-stu-id="a36c5-121">How to use HttpClient handlers</span></span>](https://go.microsoft.com/fwlink/?LinkId=245699)  
 [<span data-ttu-id="a36c5-122">Jak zabezpieczyć HttpClient połączeń</span><span class="sxs-lookup"><span data-stu-id="a36c5-122">How to secure HttpClient connections</span></span>](https://go.microsoft.com/fwlink/?LinkId=245698)  
 [<span data-ttu-id="a36c5-123">Przykładowe klasy HttpClient</span><span class="sxs-lookup"><span data-stu-id="a36c5-123">HttpClient Sample</span></span>](https://go.microsoft.com/fwlink/?LinkId=242550)
