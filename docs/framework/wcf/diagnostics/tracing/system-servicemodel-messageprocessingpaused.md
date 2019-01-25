---
title: System.ServiceModel.MessageProcessingPaused
ms.date: 03/30/2017
ms.assetid: 36b5302a-93cc-478a-9bb2-8a1601fba1df
ms.openlocfilehash: ba067303d861bbd7d88c67f6fd868bd808e07dfd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54528683"
---
# <a name="systemservicemodelmessageprocessingpaused"></a><span data-ttu-id="d6ff7-102">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="d6ff7-102">System.ServiceModel.MessageProcessingPaused</span></span>
<span data-ttu-id="d6ff7-103">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="d6ff7-103">System.ServiceModel.MessageProcessingPaused</span></span>  
  
## <a name="description"></a><span data-ttu-id="d6ff7-104">Opis</span><span class="sxs-lookup"><span data-stu-id="d6ff7-104">Description</span></span>  
 <span data-ttu-id="d6ff7-105">Wątki były przełączane podczas przetwarzania komunikatu.</span><span class="sxs-lookup"><span data-stu-id="d6ff7-105">The threads were switched while processing a message.</span></span>  
  
 <span data-ttu-id="d6ff7-106">Przetwarzanie komunikatów może być wstrzymana przez następujących przyczyn:</span><span class="sxs-lookup"><span data-stu-id="d6ff7-106">Message processing can be paused by the following reasons:</span></span>  
  
-   <span data-ttu-id="d6ff7-107">Procedura jest pojedynczym lub współużytkowane, a usługa przetwarza kolejną wiadomość.</span><span class="sxs-lookup"><span data-stu-id="d6ff7-107">ConcurrencyMode is single or reentrant, and the service is processing another message.</span></span>  
  
-   <span data-ttu-id="d6ff7-108">Transakcja jest włączona, a usługa przetwarza inną transakcję.</span><span class="sxs-lookup"><span data-stu-id="d6ff7-108">Transaction is enabled and the service is processing another transaction.</span></span>  
  
-   <span data-ttu-id="d6ff7-109">Kontekst synchronizacji jest nieaktualna.</span><span class="sxs-lookup"><span data-stu-id="d6ff7-109">Synchronization context is not current.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6ff7-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d6ff7-110">See also</span></span>
- [<span data-ttu-id="d6ff7-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="d6ff7-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="d6ff7-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="d6ff7-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="d6ff7-113">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="d6ff7-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
