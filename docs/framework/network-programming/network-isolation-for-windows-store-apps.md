---
title: Izolacja sieci dla aplikacji ze Sklepu Windows
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b064497c-d956-46b8-838d-7a0223c7e200
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b6c0665a379f02a74bd0f3631aa26b41dd6ece5a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="network-isolation-for-windows-store-apps"></a><span data-ttu-id="5aac9-102">Izolacja sieci dla aplikacji ze Sklepu Windows</span><span class="sxs-lookup"><span data-stu-id="5aac9-102">Network Isolation for Windows Store Apps</span></span>
<span data-ttu-id="5aac9-103">Klasy w <xref:System.Net>, <xref:System.Net.Http>, i <xref:System.Net.Http.Headers> przestrzeni nazw może służyć do tworzenia aplikacji ze Sklepu Windows lub aplikacji klasycznych.</span><span class="sxs-lookup"><span data-stu-id="5aac9-103">Classes in the <xref:System.Net>,  <xref:System.Net.Http>, and <xref:System.Net.Http.Headers> namespaces can be used to develop Windows Store  apps  or desktop apps.</span></span> <span data-ttu-id="5aac9-104">Gdy są używane w aplikacji ze Sklepu Windows, klas w tych obszarach nazw dotyczy izolacji sieci, część używany przez model zabezpieczeń aplikacji [!INCLUDE[win8](../../../includes/win8-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5aac9-104">When used in a Windows Store app, classes in these namespaces are affected by network isolation, part of the application security model used by the [!INCLUDE[win8](../../../includes/win8-md.md)].</span></span> <span data-ttu-id="5aac9-105">Możliwości odpowiedniej sieci musi być włączony w manifeście aplikacji dla aplikacji ze Sklepu Windows dla systemu w celu umożliwienia dostępu do sieci.</span><span class="sxs-lookup"><span data-stu-id="5aac9-105">The appropriate network capabilities must be enabled in the app manifest for a Windows Store app for the system to allow network access.</span></span>  
  
## <a name="checklist-for-network-isolation"></a><span data-ttu-id="5aac9-106">Lista kontrolna dotycząca izolacji sieci</span><span class="sxs-lookup"><span data-stu-id="5aac9-106">Checklist for Network Isolation</span></span>  
 <span data-ttu-id="5aac9-107">Użyj tej listy kontrolnej, należy upewnić się, że izolacja sieci jest skonfigurowany dla aplikacji ze Sklepu Windows.</span><span class="sxs-lookup"><span data-stu-id="5aac9-107">Use this checklist to be sure that network isolation is configured for your Windows Store app.</span></span>  
  
1.  <span data-ttu-id="5aac9-108">Określ kierunek wymagane przez aplikację żądań dostępu do sieci.</span><span class="sxs-lookup"><span data-stu-id="5aac9-108">Determine the direction of network access requests needed by the app.</span></span> <span data-ttu-id="5aac9-109">Może to być żądań wychodzących inicjowanej przez klienta lub niechciane żądania przychodzące lub może być kombinację obu typów sieci żądania.</span><span class="sxs-lookup"><span data-stu-id="5aac9-109">This can be either outbound client-initiated requests or inbound unsolicited requests or it could be a combination of both of these network request types.</span></span>  
  
2.  <span data-ttu-id="5aac9-110">Określ typ tej aplikacji będą komunikować się z zasobów sieciowych.</span><span class="sxs-lookup"><span data-stu-id="5aac9-110">Determine the type of network resources that that app will communicate with.</span></span> <span data-ttu-id="5aac9-111">Aplikacja może być konieczne do komunikowania się z zaufanych zasobów w sieci w domu lub pracy.</span><span class="sxs-lookup"><span data-stu-id="5aac9-111">An app may need to communicate with trusted resources on a Home or Work network.</span></span> <span data-ttu-id="5aac9-112">Aplikacja może być konieczne do komunikowania się z zasobami przez Internet.</span><span class="sxs-lookup"><span data-stu-id="5aac9-112">An app might need to communicate with resources on the Internet.</span></span> <span data-ttu-id="5aac9-113">Aplikacja może potrzebować dostępu do obu typów zasobów sieciowych.</span><span class="sxs-lookup"><span data-stu-id="5aac9-113">An app might need access to both types of network resources.</span></span>  
  
3.  <span data-ttu-id="5aac9-114">Minimalna wymagana możliwości izolacji sieci należy skonfigurować w manifeście aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5aac9-114">Configure the minimum-required networking isolation capabilities in the app manifest.</span></span>  
  
4.  <span data-ttu-id="5aac9-115">Wdrażanie i uruchamianie aplikacji w taki sposób, aby przetestować go przy użyciu narzędzia izolacji sieci, które są dostępne w celu rozwiązywania problemów.</span><span class="sxs-lookup"><span data-stu-id="5aac9-115">Deploy and run your app to test it using the network isolation tools provided for troubleshooting.</span></span>  
  
 <span data-ttu-id="5aac9-116">Aby uzyskać bardziej szczegółowe informacje na temat konfigurowania funkcji sieciowych i izolacja narzędzi używanych do rozwiązywania problemów w przypadku izolacji sieci, zobacz [sposobu konfigurowania możliwości izolacji sieci](http://go.microsoft.com/fwlink/?LinkID=228265) w [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] developer dokumentacja.</span><span class="sxs-lookup"><span data-stu-id="5aac9-116">For more detailed information on how to configure network capabilities and isolation tools used for troubleshooting network isolation, see [How to configure network isolation capabilities](http://go.microsoft.com/fwlink/?LinkID=228265) in the [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] developer documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5aac9-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5aac9-117">See Also</span></span>  
 [<span data-ttu-id="5aac9-118">Łączenie z usługą sieci web</span><span class="sxs-lookup"><span data-stu-id="5aac9-118">Connecting to a web service</span></span>](http://go.microsoft.com/fwlink/?LinkID=245696)  
 [<span data-ttu-id="5aac9-119">Wskazówki i Lista kontrolna dotycząca izolacji sieci</span><span class="sxs-lookup"><span data-stu-id="5aac9-119">Guidelines and checklist for network isolation</span></span>](http://go.microsoft.com/fwlink/?LinkID=228265)  
 [<span data-ttu-id="5aac9-120">Szybki Start: Łączenie za pomocą elementu HttpClient</span><span class="sxs-lookup"><span data-stu-id="5aac9-120">Quickstart: Connecting using HttpClient</span></span>](http://go.microsoft.com/fwlink/?LinkId=245697)  
 [<span data-ttu-id="5aac9-121">Jak używać HttpClient obsługi</span><span class="sxs-lookup"><span data-stu-id="5aac9-121">How to use HttpClient handlers</span></span>](http://go.microsoft.com/fwlink/?LinkId=245699)  
 [<span data-ttu-id="5aac9-122">Jak zabezpieczyć połączenia HttpClient</span><span class="sxs-lookup"><span data-stu-id="5aac9-122">How to secure HttpClient connections</span></span>](http://go.microsoft.com/fwlink/?LinkId=245698)  
 [<span data-ttu-id="5aac9-123">Przykładowe HttpClient</span><span class="sxs-lookup"><span data-stu-id="5aac9-123">HttpClient Sample</span></span>](http://go.microsoft.com/fwlink/?LinkId=242550)
