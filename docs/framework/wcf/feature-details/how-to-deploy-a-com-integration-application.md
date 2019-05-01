---
title: 'Instrukcje: wdrażanie aplikacji integracji modelu COM+'
ms.date: 03/30/2017
ms.assetid: 2e5a0510-db3c-4988-a09c-696285836650
ms.openlocfilehash: fcf525943e6e453253c6f4d3bcfa8a1a08df6909
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778329"
---
# <a name="how-to-deploy-a-com-integration-application"></a><span data-ttu-id="ed5b9-102">Instrukcje: wdrażanie aplikacji integracji modelu COM+</span><span class="sxs-lookup"><span data-stu-id="ed5b9-102">How to: Deploy a COM+ Integration Application</span></span>
<span data-ttu-id="ed5b9-103">Po napisaniu aplikacji COM +, integracja, warto wdrożyć ją na innym komputerze.</span><span class="sxs-lookup"><span data-stu-id="ed5b9-103">Once you have written a COM+ integration application, you may want to deploy it on another machine.</span></span> <span data-ttu-id="ed5b9-104">W tym temacie opisano sposób przenoszenia aplikacji integracji modelu COM + z jednego komputera na inny.</span><span class="sxs-lookup"><span data-stu-id="ed5b9-104">This topic describes how to move a COM+ integration application from one machine to another.</span></span>  
  
### <a name="moving-a-com-hosted-integration-app"></a><span data-ttu-id="ed5b9-105">Przenoszenie modelu COM + hostowanych integracji aplikacji</span><span class="sxs-lookup"><span data-stu-id="ed5b9-105">Moving a COM+ hosted Integration App</span></span>  
  
1. <span data-ttu-id="ed5b9-106">Upewnij się, że WCF jest zainstalowany na obu komputerach.</span><span class="sxs-lookup"><span data-stu-id="ed5b9-106">Ensure that WCF is installed on both machines.</span></span>  
  
2. <span data-ttu-id="ed5b9-107">Eksportowanie aplikacji z komputera A.</span><span class="sxs-lookup"><span data-stu-id="ed5b9-107">Export the application from machine A.</span></span>  
  
3. <span data-ttu-id="ed5b9-108">Importuj aplikację na komputerze B.</span><span class="sxs-lookup"><span data-stu-id="ed5b9-108">Import the application on machine B.</span></span>  
  
4. <span data-ttu-id="ed5b9-109">Ustaw katalog główny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ed5b9-109">Set the Application Root Directory.</span></span> <span data-ttu-id="ed5b9-110">Według Konwencji jest to aplikacje %PROGRAMFILES%/ComPlus / {AppGUID}.</span><span class="sxs-lookup"><span data-stu-id="ed5b9-110">By convention, this is %PROGRAMFILES%/ComPlus Applications/{AppGUID}.</span></span>  
  
5. <span data-ttu-id="ed5b9-111">Skopiuj pliki Application.config i Application.manifest z katalogu głównego aplikacji na maszynie, A do katalogu głównego aplikacji na maszynie B.</span><span class="sxs-lookup"><span data-stu-id="ed5b9-111">Copy the Application.config and Application.manifest files from the application root directory on machine A to the application root directory on machine B.</span></span>  
  
6. <span data-ttu-id="ed5b9-112">Edytuj adresy punktów końcowych usługi w pliku Application.config na komputerze B, aby zidentyfikować odpowiedni komputer.</span><span class="sxs-lookup"><span data-stu-id="ed5b9-112">Edit the service endpoint addresses in the Application.config file on machine B to identify the appropriate machine.</span></span> <span data-ttu-id="ed5b9-113">Na przykład zmienić `http://machineA/MyService` do `http://machineB/MyService`.</span><span class="sxs-lookup"><span data-stu-id="ed5b9-113">For example, change `http://machineA/MyService` to `http://machineB/MyService`.</span></span>  
  
### <a name="moving-a-web-hosted-integration-application"></a><span data-ttu-id="ed5b9-114">Przenoszenie aplikacji hostowanej w sieci Web integracji</span><span class="sxs-lookup"><span data-stu-id="ed5b9-114">Moving a Web-hosted integration application</span></span>  
  
1. <span data-ttu-id="ed5b9-115">Upewnij się, że WCF jest zainstalowany na obu komputerach.</span><span class="sxs-lookup"><span data-stu-id="ed5b9-115">Ensure that WCF is installed on both machines.</span></span>  
  
2. <span data-ttu-id="ed5b9-116">Eksportowanie aplikacji z komputera A.</span><span class="sxs-lookup"><span data-stu-id="ed5b9-116">Export the application from machine A.</span></span>  
  
3. <span data-ttu-id="ed5b9-117">Importuj aplikację na komputerze B.</span><span class="sxs-lookup"><span data-stu-id="ed5b9-117">Import the application on machine B.</span></span>  
  
4. <span data-ttu-id="ed5b9-118">Tworzenie vroot usług IIS na maszynie B.</span><span class="sxs-lookup"><span data-stu-id="ed5b9-118">Create an IIS vroot on machine B.</span></span>  
  
5. <span data-ttu-id="ed5b9-119">Skopiuj plik .svc (componentName.svc) i plik Web.config z głównego katalogu wirtualnego na maszynie, A do nowo utworzonego głównego katalogu wirtualnego na maszynie B.</span><span class="sxs-lookup"><span data-stu-id="ed5b9-119">Copy the .svc file (componentName.svc) and the Web.config file from the vroot on machine A to the newly created vroot on machine B.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed5b9-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ed5b9-120">See also</span></span>

- [<span data-ttu-id="ed5b9-121">Przegląd integrowania z aplikacjami COM+</span><span class="sxs-lookup"><span data-stu-id="ed5b9-121">Integrating with COM+ Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)
- [<span data-ttu-id="ed5b9-122">Instrukcje: Konfigurowanie ustawień usługi COM +</span><span class="sxs-lookup"><span data-stu-id="ed5b9-122">How to: Configure COM+ Service Settings</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
- [<span data-ttu-id="ed5b9-123">Instrukcje: Używanie narzędzia konfiguracji modelu usług COM +</span><span class="sxs-lookup"><span data-stu-id="ed5b9-123">How to: Use the COM+ Service Model Configuration Tool</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)
