---
title: Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a4ead79-8550-4037-84e3-fd70ff56e001
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 02831a83103f5a6bd83fc2aed474245bdeda65d4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="microsofttransactionstransactionbridgeregisterparticipantfailure"></a><span data-ttu-id="85335-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span><span class="sxs-lookup"><span data-stu-id="85335-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span></span>
<span data-ttu-id="85335-103">Usługa protokołu WS-AT nie może zarejestrować uczestnika dla protokołu sterowania.</span><span class="sxs-lookup"><span data-stu-id="85335-103">The WS-AT protocol service failed to register a participant for a control protocol.</span></span>  
  
## <a name="description"></a><span data-ttu-id="85335-104">Opis</span><span class="sxs-lookup"><span data-stu-id="85335-104">Description</span></span>  
 <span data-ttu-id="85335-105">Śledzone, jeśli usługi MSDTC wykryje nieprawidłowe żądanie rejestracji.</span><span class="sxs-lookup"><span data-stu-id="85335-105">Traced if MSDTC detects an invalid Registration request.</span></span> <span data-ttu-id="85335-106">Może to być spowodowane przez wiele żądań rejestracji uzupełniania i błędy wewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="85335-106">This can be caused by  multiple Completion registration requests and internal errors.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="85335-107">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="85335-107">Troubleshooting</span></span>  
 <span data-ttu-id="85335-108">Nie należy próbować rejestrowanie się w celu ukończenia więcej niż raz.</span><span class="sxs-lookup"><span data-stu-id="85335-108">Do not try to Register for Completion more than once.</span></span>  <span data-ttu-id="85335-109">Ponadto sprawdź, czy ciągu stanu w komunikat śledzenia do ustalenia, czy istnieje dowolny element przydatnych wyników.</span><span class="sxs-lookup"><span data-stu-id="85335-109">Also, inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85335-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="85335-110">See Also</span></span>  
 [<span data-ttu-id="85335-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="85335-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="85335-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="85335-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="85335-113">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="85335-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
