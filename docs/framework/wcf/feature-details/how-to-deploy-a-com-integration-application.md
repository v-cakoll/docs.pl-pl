---
title: "Instrukcje: Wdrażanie aplikacji integracji modelu COM+"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e5a0510-db3c-4988-a09c-696285836650
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7d6d9103c2d36de81392858fedc249be9f7ae94f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-deploy-a-com-integration-application"></a><span data-ttu-id="b5bce-102">Instrukcje: Wdrażanie aplikacji integracji modelu COM+</span><span class="sxs-lookup"><span data-stu-id="b5bce-102">How to: Deploy a COM+ Integration Application</span></span>
<span data-ttu-id="b5bce-103">Raz napisano aplikacji COM + integration, warto wdrożyć ją na innym komputerze.</span><span class="sxs-lookup"><span data-stu-id="b5bce-103">Once you have written a COM+ integration application, you may want to deploy it on another machine.</span></span> <span data-ttu-id="b5bce-104">W tym temacie opisano sposób przenoszenia aplikacji integracji modelu COM + z jednego komputera na inny.</span><span class="sxs-lookup"><span data-stu-id="b5bce-104">This topic describes how to move a COM+ integration application from one machine to another.</span></span>  
  
### <a name="moving-a-com-hosted-integration-app"></a><span data-ttu-id="b5bce-105">Przenoszenie COM + hostowanej integracji aplikacji</span><span class="sxs-lookup"><span data-stu-id="b5bce-105">Moving a COM+ hosted Integration App</span></span>  
  
1.  <span data-ttu-id="b5bce-106">Upewnij się, że [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jest zainstalowany na obu komputerach.</span><span class="sxs-lookup"><span data-stu-id="b5bce-106">Ensure that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is installed on both machines.</span></span>  
  
2.  <span data-ttu-id="b5bce-107">Eksportowanie aplikacji z maszyny A.</span><span class="sxs-lookup"><span data-stu-id="b5bce-107">Export the application from machine A.</span></span>  
  
3.  <span data-ttu-id="b5bce-108">Importuj aplikację na komputerze B.</span><span class="sxs-lookup"><span data-stu-id="b5bce-108">Import the application on machine B.</span></span>  
  
4.  <span data-ttu-id="b5bce-109">Ustawianie katalogu głównego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b5bce-109">Set the Application Root Directory.</span></span> <span data-ttu-id="b5bce-110">Według Konwencji jest to aplikacje %PROGRAMFILES%/ComPlus / {AppGUID}.</span><span class="sxs-lookup"><span data-stu-id="b5bce-110">By convention, this is %PROGRAMFILES%/ComPlus Applications/{AppGUID}.</span></span>  
  
5.  <span data-ttu-id="b5bce-111">Skopiuj pliki Application.config i Application.manifest z katalogu głównego aplikacji na komputerze, A do katalogu głównego aplikacji na komputerze B.</span><span class="sxs-lookup"><span data-stu-id="b5bce-111">Copy the Application.config and Application.manifest files from the application root directory on machine A to the application root directory on machine B.</span></span>  
  
6.  <span data-ttu-id="b5bce-112">Edytuj adresy punktów końcowych usługi w pliku Application.config na komputerze B, aby zidentyfikować odpowiednią maszyny.</span><span class="sxs-lookup"><span data-stu-id="b5bce-112">Edit the service endpoint addresses in the Application.config file on machine B to identify the appropriate machine.</span></span> <span data-ttu-id="b5bce-113">Na przykład zmień http://machineA/MyService http://machineB/MyService.</span><span class="sxs-lookup"><span data-stu-id="b5bce-113">For example, change http://machineA/MyService to http://machineB/MyService.</span></span>  
  
### <a name="moving-a-web-hosted-integration-application"></a><span data-ttu-id="b5bce-114">Przenoszenie aplikacji hostowanych w sieci Web integracji</span><span class="sxs-lookup"><span data-stu-id="b5bce-114">Moving a Web-hosted integration application</span></span>  
  
1.  <span data-ttu-id="b5bce-115">Upewnij się, że [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jest zainstalowany na obu komputerach.</span><span class="sxs-lookup"><span data-stu-id="b5bce-115">Ensure that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is installed on both machines.</span></span>  
  
2.  <span data-ttu-id="b5bce-116">Eksportowanie aplikacji z maszyny A.</span><span class="sxs-lookup"><span data-stu-id="b5bce-116">Export the application from machine A.</span></span>  
  
3.  <span data-ttu-id="b5bce-117">Importuj aplikację na komputerze B.</span><span class="sxs-lookup"><span data-stu-id="b5bce-117">Import the application on machine B.</span></span>  
  
4.  <span data-ttu-id="b5bce-118">Tworzenie głównego katalogu wirtualnego usług IIS na komputerze B.</span><span class="sxs-lookup"><span data-stu-id="b5bce-118">Create an IIS vroot on machine B.</span></span>  
  
5.  <span data-ttu-id="b5bce-119">Skopiuj plik SVC (componentName.svc) i plik Web.config z głównego katalogu wirtualnego na maszynie, A do nowo utworzonej głównego katalogu wirtualnego na maszynie B.</span><span class="sxs-lookup"><span data-stu-id="b5bce-119">Copy the .svc file (componentName.svc) and the Web.config file from the vroot on machine A to the newly created vroot on machine B.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5bce-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b5bce-120">See Also</span></span>  
 [<span data-ttu-id="b5bce-121">Przegląd integrowania z modelu COM + aplikacjami</span><span class="sxs-lookup"><span data-stu-id="b5bce-121">Integrating with COM+ Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)  
 [<span data-ttu-id="b5bce-122">Porady: Konfigurowanie ustawień usług COM +</span><span class="sxs-lookup"><span data-stu-id="b5bce-122">How to: Configure COM+ Service Settings</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)  
 [<span data-ttu-id="b5bce-123">Porady: Użyj narzędzia konfiguracji modelu usług COM +</span><span class="sxs-lookup"><span data-stu-id="b5bce-123">How to: Use the COM+ Service Model Configuration Tool</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)
