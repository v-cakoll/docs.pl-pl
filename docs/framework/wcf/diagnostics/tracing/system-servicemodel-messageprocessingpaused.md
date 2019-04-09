---
title: System.ServiceModel.MessageProcessingPaused
ms.date: 03/30/2017
ms.assetid: 36b5302a-93cc-478a-9bb2-8a1601fba1df
ms.openlocfilehash: ac1dacef94d6446aa407e4a390b9561d033af1bb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59087484"
---
# <a name="systemservicemodelmessageprocessingpaused"></a><span data-ttu-id="7281b-102">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="7281b-102">System.ServiceModel.MessageProcessingPaused</span></span>
<span data-ttu-id="7281b-103">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="7281b-103">System.ServiceModel.MessageProcessingPaused</span></span>  
  
## <a name="description"></a><span data-ttu-id="7281b-104">Opis</span><span class="sxs-lookup"><span data-stu-id="7281b-104">Description</span></span>  
 <span data-ttu-id="7281b-105">Wątki były przełączane podczas przetwarzania komunikatu.</span><span class="sxs-lookup"><span data-stu-id="7281b-105">The threads were switched while processing a message.</span></span>  
  
 <span data-ttu-id="7281b-106">Przetwarzanie komunikatów może być wstrzymana przez następujących przyczyn:</span><span class="sxs-lookup"><span data-stu-id="7281b-106">Message processing can be paused by the following reasons:</span></span>  
  
-   <span data-ttu-id="7281b-107">Procedura jest pojedynczym lub współużytkowane, a usługa przetwarza kolejną wiadomość.</span><span class="sxs-lookup"><span data-stu-id="7281b-107">ConcurrencyMode is single or reentrant, and the service is processing another message.</span></span>  
  
-   <span data-ttu-id="7281b-108">Transakcja jest włączona, a usługa przetwarza inną transakcję.</span><span class="sxs-lookup"><span data-stu-id="7281b-108">Transaction is enabled and the service is processing another transaction.</span></span>  
  
-   <span data-ttu-id="7281b-109">Kontekst synchronizacji jest nieaktualna.</span><span class="sxs-lookup"><span data-stu-id="7281b-109">Synchronization context is not current.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7281b-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7281b-110">See also</span></span>

- [<span data-ttu-id="7281b-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="7281b-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="7281b-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="7281b-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="7281b-113">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="7281b-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
