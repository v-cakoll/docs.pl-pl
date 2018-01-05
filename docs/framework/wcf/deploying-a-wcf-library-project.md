---
title: "Wdrażanie projektu biblioteki WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9f9222fe-d358-443c-9a49-12c5498e35e7
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bbbbff1d88559f8ab35caa48fcb04ff1cd7bf015
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="deploying-a-wcf-library-project"></a><span data-ttu-id="c9c27-102">Wdrażanie projektu biblioteki WCF</span><span class="sxs-lookup"><span data-stu-id="c9c27-102">Deploying a WCF Library Project</span></span>
<span data-ttu-id="c9c27-103">W tym temacie opisano sposób wdrażania [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] projektu biblioteki usługi.</span><span class="sxs-lookup"><span data-stu-id="c9c27-103">This topic describes how you can deploy a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] Service Library Project.</span></span>  
  
## <a name="deploying-a-wcf-service-library"></a><span data-ttu-id="c9c27-104">Wdrażanie biblioteki usługi WCF</span><span class="sxs-lookup"><span data-stu-id="c9c27-104">Deploying a WCF Service Library</span></span>  
 <span data-ttu-id="c9c27-105">A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] biblioteki usługi jest biblioteki dołączanej (dynamicznie DLL).</span><span class="sxs-lookup"><span data-stu-id="c9c27-105">A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service library is a dynamic-link library (DLL).</span></span> <span data-ttu-id="c9c27-106">W efekcie nie można wykonać samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="c9c27-106">As such, it cannot be executed on its own.</span></span> <span data-ttu-id="c9c27-107">Musi zostać wdrożony w środowisku macierzystym.</span><span class="sxs-lookup"><span data-stu-id="c9c27-107">It needs to be deployed into a hosting environment.</span></span> <span data-ttu-id="c9c27-108">Aby uzyskać więcej informacji o tym procesie, zobacz [hostingu i korzystanie z usługi WCF](http://go.microsoft.com/fwlink/?LinkId=99932).</span><span class="sxs-lookup"><span data-stu-id="c9c27-108">For more information about this process, see [Hosting and Consuming WCF Services](http://go.microsoft.com/fwlink/?LinkId=99932).</span></span>  
  
 <span data-ttu-id="c9c27-109">A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Biblioteka usług można wdrożyć jak każdy inny [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi.</span><span class="sxs-lookup"><span data-stu-id="c9c27-109">A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service library can be deployed like any other [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="c9c27-110">Jednak należy pamiętać, że [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] nie obsługuje konfiguracji dla bibliotek DLL.</span><span class="sxs-lookup"><span data-stu-id="c9c27-110">However, be aware that [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] does not support configuration for DLLs.</span></span> <span data-ttu-id="c9c27-111"><xref:System.Configuration>obsługuje jeden plik konfiguracji na domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c9c27-111"><xref:System.Configuration> supports one configuration file per app-domain.</span></span> <span data-ttu-id="c9c27-112">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Projektu biblioteki usługi eliminuje to ograniczenie przez zapewnienie podczas tworzenia pliku App.config dla biblioteki.</span><span class="sxs-lookup"><span data-stu-id="c9c27-112">The [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service library project alleviates this limitation by providing an App.config file for the library during development.</span></span> <span data-ttu-id="c9c27-113">Jednak po wdrożeniu nie jest rozpoznawana pliku App.config.</span><span class="sxs-lookup"><span data-stu-id="c9c27-113">However, the App.config file is not recognized after deployment.</span></span>  
  
 <span data-ttu-id="c9c27-114">Masz Przenieś swój kod konfiguracji do pliku konfiguracyjnego rozpoznaje środowisku macierzystym.</span><span class="sxs-lookup"><span data-stu-id="c9c27-114">You have to move your configuration code into the configuration file recognized by your hosting environment.</span></span> <span data-ttu-id="c9c27-115">Dla hostingu samodzielnego, należy skopiować zawartość pliku App.config w pliku App.config hostingu pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="c9c27-115">For self-hosting, you should copy the contents of the App.config file into the App.config file of the hosting executable.</span></span> <span data-ttu-id="c9c27-116">Jeśli używasz usług IIS do obsługi usługi, należy skopiować zawartość pliku App.config w pliku Web.config w katalogu wirtualnego.</span><span class="sxs-lookup"><span data-stu-id="c9c27-116">If you use IIS to host your service, you should copy the contents of the App.config file into the Web.config file of the virtual directory.</span></span>
