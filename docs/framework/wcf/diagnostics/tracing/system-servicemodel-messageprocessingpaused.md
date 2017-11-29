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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1176af676673e19eb2d8cd54cc4d2d254c7ba324
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelmessageprocessingpaused"></a><span data-ttu-id="2f7fc-102">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="2f7fc-102">System.ServiceModel.MessageProcessingPaused</span></span>
<span data-ttu-id="2f7fc-103">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="2f7fc-103">System.ServiceModel.MessageProcessingPaused</span></span>  
  
## <a name="description"></a><span data-ttu-id="2f7fc-104">Opis</span><span class="sxs-lookup"><span data-stu-id="2f7fc-104">Description</span></span>  
 <span data-ttu-id="2f7fc-105">Wątki były włączane podczas przetwarzania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="2f7fc-105">The threads were switched while processing a message.</span></span>  
  
 <span data-ttu-id="2f7fc-106">Przetwarzanie komunikatów może być wstrzymana przez następujących powodów:</span><span class="sxs-lookup"><span data-stu-id="2f7fc-106">Message processing can be paused by the following reasons:</span></span>  
  
-   <span data-ttu-id="2f7fc-107">Właściwość ConcurrencyMode jest pojedyncza lub współużytkowane i usługa przetwarza kolejną wiadomość.</span><span class="sxs-lookup"><span data-stu-id="2f7fc-107">ConcurrencyMode is single or reentrant, and the service is processing another message.</span></span>  
  
-   <span data-ttu-id="2f7fc-108">Transakcja jest włączona i usługa przetwarza obecnie inną transakcję.</span><span class="sxs-lookup"><span data-stu-id="2f7fc-108">Transaction is enabled and the service is processing another transaction.</span></span>  
  
-   <span data-ttu-id="2f7fc-109">Kontekst synchronizacji jest nieaktualna.</span><span class="sxs-lookup"><span data-stu-id="2f7fc-109">Synchronization context is not current.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f7fc-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2f7fc-110">See Also</span></span>  
 [<span data-ttu-id="2f7fc-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="2f7fc-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="2f7fc-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="2f7fc-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="2f7fc-113">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="2f7fc-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
