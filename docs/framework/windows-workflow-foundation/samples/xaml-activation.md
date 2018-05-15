---
title: Aktywacja XAML
ms.date: 03/30/2017
ms.assetid: 486760e2-bb10-4ed5-8c02-fe7472498d2d
ms.openlocfilehash: 8621b0ea7b390c81e76ac7eeedb0b547b44320d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="xaml-activation"></a><span data-ttu-id="bb9d0-102">Aktywacja XAML</span><span class="sxs-lookup"><span data-stu-id="bb9d0-102">XAML Activation</span></span>
<span data-ttu-id="bb9d0-103">W tym przykładzie pokazano, jak udostępniać deklaracyjnego przepływu pracy w programie IIS.</span><span class="sxs-lookup"><span data-stu-id="bb9d0-103">This sample demonstrates how to host a declarative workflow in IIS.</span></span> <span data-ttu-id="bb9d0-104">Próbka jest podstawowy przepływ pracy o nazwie `EchoService` mający jednej operacji.</span><span class="sxs-lookup"><span data-stu-id="bb9d0-104">The sample is a basic workflow called `EchoService` that has one operation.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bb9d0-105">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="bb9d0-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="bb9d0-106">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="bb9d0-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="bb9d0-107">Jeśli ten katalog nie istnieje, przejdź do (stronę pobierania) można pobrać wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="bb9d0-107">If this directory does not exist, go to (download page) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bb9d0-108">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="bb9d0-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\XAMLActivation`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="bb9d0-109">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="bb9d0-109">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="bb9d0-110">Otwórz rozwiązanie XAMLActivation.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bb9d0-110">Open the XAMLActivation.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="bb9d0-111">Skompiluj rozwiązanie, naciskając klawisz **F5**.</span><span class="sxs-lookup"><span data-stu-id="bb9d0-111">Build the solution by pressing **F5**.</span></span>  
  
3.  <span data-ttu-id="bb9d0-112">Uruchom WcfTestClient.exe.</span><span class="sxs-lookup"><span data-stu-id="bb9d0-112">Run WcfTestClient.exe.</span></span> <span data-ttu-id="bb9d0-113">W wierszu polecenia wpisz następujące:</span><span class="sxs-lookup"><span data-stu-id="bb9d0-113">From a command prompt, type in the following:</span></span>  
  
    1.  <span data-ttu-id="bb9d0-114">CD %SystemDrive%\Program Files\Microsoft 10.0\Common7\IDE programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bb9d0-114">cd %SystemDrive%\Program Files\Microsoft Visual Studio 10.0\Common7\IDE</span></span>  
  
    2.  <span data-ttu-id="bb9d0-115">Uruchom WcfTestClient.exe.</span><span class="sxs-lookup"><span data-stu-id="bb9d0-115">Run WcfTestClient.exe.</span></span>  
  
4.  <span data-ttu-id="bb9d0-116">Ustaw adres usługi na WcfTestClient.exe naciskając klawisz CTRL + SHIFT + A, a ustawienie adresu usługi http://localhost:56133/Service.xamlx.</span><span class="sxs-lookup"><span data-stu-id="bb9d0-116">Set the address of the service on WcfTestClient.exe by pressing CTRL+SHIFT+A and setting the service address to http://localhost:56133/Service.xamlx.</span></span>  
  
5.  <span data-ttu-id="bb9d0-117">Operacja echo testować usługę.</span><span class="sxs-lookup"><span data-stu-id="bb9d0-117">Perform the echo operation to test the service.</span></span>  
  
6.  <span data-ttu-id="bb9d0-118">Wdrażanie usługi w usługach IIS przy użyciu DeployToIIS.Bat w wierszu polecenia z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="bb9d0-118">Deploy the Service in IIS using DeployToIIS.Bat in a command prompt with administrator privileges.</span></span>  
  
7.  <span data-ttu-id="bb9d0-119">Zaktualizuj adres usługi w kliencie programu http://localhost/XAMLActivation/Service.xamlx i testować usługę ponownie, używając WcfTestClient.exe.</span><span class="sxs-lookup"><span data-stu-id="bb9d0-119">Update the service address in the client to http://localhost/XAMLActivation/Service.xamlx and test the service again using WcfTestClient.exe.</span></span>
