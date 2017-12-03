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
ms.openlocfilehash: 16b0261a53df29b1fc2049c25375c651735a524c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="microsofttransactionstransactionbridgeregisterparticipantfailure"></a><span data-ttu-id="ee044-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span><span class="sxs-lookup"><span data-stu-id="ee044-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span></span>
<span data-ttu-id="ee044-103">Usługa protokołu WS-AT nie może zarejestrować uczestnika dla protokołu sterowania.</span><span class="sxs-lookup"><span data-stu-id="ee044-103">The WS-AT protocol service failed to register a participant for a control protocol.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ee044-104">Opis</span><span class="sxs-lookup"><span data-stu-id="ee044-104">Description</span></span>  
 <span data-ttu-id="ee044-105">Śledzone, jeśli usługi MSDTC wykryje nieprawidłowe żądanie rejestracji.</span><span class="sxs-lookup"><span data-stu-id="ee044-105">Traced if MSDTC detects an invalid Registration request.</span></span> <span data-ttu-id="ee044-106">Może to być spowodowane przez wiele żądań rejestracji uzupełniania i błędy wewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="ee044-106">This can be caused by  multiple Completion registration requests and internal errors.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="ee044-107">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="ee044-107">Troubleshooting</span></span>  
 <span data-ttu-id="ee044-108">Nie należy próbować rejestrowanie się w celu ukończenia więcej niż raz.</span><span class="sxs-lookup"><span data-stu-id="ee044-108">Do not try to Register for Completion more than once.</span></span>  <span data-ttu-id="ee044-109">Ponadto sprawdź, czy ciągu stanu w komunikat śledzenia do ustalenia, czy istnieje dowolny element przydatnych wyników.</span><span class="sxs-lookup"><span data-stu-id="ee044-109">Also, inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee044-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ee044-110">See Also</span></span>  
 [<span data-ttu-id="ee044-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="ee044-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="ee044-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="ee044-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="ee044-113">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="ee044-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
