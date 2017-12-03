---
title: System.ServiceModel.MessageProcessingPaused
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 36b5302a-93cc-478a-9bb2-8a1601fba1df
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 33d05eaa94ec0efdf6d18d03d9d38bda6f0c9eb7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelmessageprocessingpaused"></a><span data-ttu-id="32831-102">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="32831-102">System.ServiceModel.MessageProcessingPaused</span></span>
<span data-ttu-id="32831-103">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="32831-103">System.ServiceModel.MessageProcessingPaused</span></span>  
  
## <a name="description"></a><span data-ttu-id="32831-104">Opis</span><span class="sxs-lookup"><span data-stu-id="32831-104">Description</span></span>  
 <span data-ttu-id="32831-105">Wątki były włączane podczas przetwarzania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="32831-105">The threads were switched while processing a message.</span></span>  
  
 <span data-ttu-id="32831-106">Przetwarzanie komunikatów może być wstrzymana przez następujących powodów:</span><span class="sxs-lookup"><span data-stu-id="32831-106">Message processing can be paused by the following reasons:</span></span>  
  
-   <span data-ttu-id="32831-107">Właściwość ConcurrencyMode jest pojedyncza lub współużytkowane i usługa przetwarza kolejną wiadomość.</span><span class="sxs-lookup"><span data-stu-id="32831-107">ConcurrencyMode is single or reentrant, and the service is processing another message.</span></span>  
  
-   <span data-ttu-id="32831-108">Transakcja jest włączona i usługa przetwarza obecnie inną transakcję.</span><span class="sxs-lookup"><span data-stu-id="32831-108">Transaction is enabled and the service is processing another transaction.</span></span>  
  
-   <span data-ttu-id="32831-109">Kontekst synchronizacji jest nieaktualna.</span><span class="sxs-lookup"><span data-stu-id="32831-109">Synchronization context is not current.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32831-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="32831-110">See Also</span></span>  
 [<span data-ttu-id="32831-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="32831-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="32831-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="32831-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="32831-113">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="32831-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
