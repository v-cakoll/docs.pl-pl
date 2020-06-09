---
title: System.ServiceModel.MessageProcessingPaused
ms.date: 03/30/2017
ms.assetid: 36b5302a-93cc-478a-9bb2-8a1601fba1df
ms.openlocfilehash: 85bec8255e0d20d6e76ea354e5b8c42b83d7d8e6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598154"
---
# <a name="systemservicemodelmessageprocessingpaused"></a><span data-ttu-id="11c64-102">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="11c64-102">System.ServiceModel.MessageProcessingPaused</span></span>
<span data-ttu-id="11c64-103">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="11c64-103">System.ServiceModel.MessageProcessingPaused</span></span>  
  
## <a name="description"></a><span data-ttu-id="11c64-104">Opis</span><span class="sxs-lookup"><span data-stu-id="11c64-104">Description</span></span>  
 <span data-ttu-id="11c64-105">Wątki zostały przełączone podczas przetwarzania komunikatu.</span><span class="sxs-lookup"><span data-stu-id="11c64-105">The threads were switched while processing a message.</span></span>  
  
 <span data-ttu-id="11c64-106">Przetwarzanie komunikatów można wstrzymać z następujących powodów:</span><span class="sxs-lookup"><span data-stu-id="11c64-106">Message processing can be paused by the following reasons:</span></span>  
  
- <span data-ttu-id="11c64-107">Właściwość ConcurrencyMode jest pojedyncza lub współużytkowana, a usługa przetwarza inną wiadomość.</span><span class="sxs-lookup"><span data-stu-id="11c64-107">ConcurrencyMode is single or reentrant, and the service is processing another message.</span></span>  
  
- <span data-ttu-id="11c64-108">Transakcja jest włączona, a usługa przetwarza inną transakcję.</span><span class="sxs-lookup"><span data-stu-id="11c64-108">Transaction is enabled and the service is processing another transaction.</span></span>  
  
- <span data-ttu-id="11c64-109">Kontekst synchronizacji nie jest bieżący.</span><span class="sxs-lookup"><span data-stu-id="11c64-109">Synchronization context is not current.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11c64-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="11c64-110">See also</span></span>

- [<span data-ttu-id="11c64-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="11c64-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="11c64-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="11c64-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="11c64-113">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="11c64-113">Administration and Diagnostics</span></span>](../index.md)
