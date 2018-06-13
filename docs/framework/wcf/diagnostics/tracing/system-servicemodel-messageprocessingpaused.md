---
title: System.ServiceModel.MessageProcessingPaused
ms.date: 03/30/2017
ms.assetid: 36b5302a-93cc-478a-9bb2-8a1601fba1df
ms.openlocfilehash: 6fb1463b811d985f54b9a99e59d1280eaa040256
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33482817"
---
# <a name="systemservicemodelmessageprocessingpaused"></a><span data-ttu-id="e2401-102">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="e2401-102">System.ServiceModel.MessageProcessingPaused</span></span>
<span data-ttu-id="e2401-103">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="e2401-103">System.ServiceModel.MessageProcessingPaused</span></span>  
  
## <a name="description"></a><span data-ttu-id="e2401-104">Opis</span><span class="sxs-lookup"><span data-stu-id="e2401-104">Description</span></span>  
 <span data-ttu-id="e2401-105">Wątki były włączane podczas przetwarzania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="e2401-105">The threads were switched while processing a message.</span></span>  
  
 <span data-ttu-id="e2401-106">Przetwarzanie komunikatów może być wstrzymana przez następujących powodów:</span><span class="sxs-lookup"><span data-stu-id="e2401-106">Message processing can be paused by the following reasons:</span></span>  
  
-   <span data-ttu-id="e2401-107">Właściwość ConcurrencyMode jest pojedyncza lub współużytkowane i usługa przetwarza kolejną wiadomość.</span><span class="sxs-lookup"><span data-stu-id="e2401-107">ConcurrencyMode is single or reentrant, and the service is processing another message.</span></span>  
  
-   <span data-ttu-id="e2401-108">Transakcja jest włączona i usługa przetwarza obecnie inną transakcję.</span><span class="sxs-lookup"><span data-stu-id="e2401-108">Transaction is enabled and the service is processing another transaction.</span></span>  
  
-   <span data-ttu-id="e2401-109">Kontekst synchronizacji jest nieaktualna.</span><span class="sxs-lookup"><span data-stu-id="e2401-109">Synchronization context is not current.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2401-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e2401-110">See Also</span></span>  
 [<span data-ttu-id="e2401-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="e2401-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="e2401-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="e2401-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="e2401-113">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="e2401-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
