---
title: Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
ms.date: 03/30/2017
ms.assetid: 3a4ead79-8550-4037-84e3-fd70ff56e001
ms.openlocfilehash: fb5e50e7332269690a200334ef936dd0d5525e9c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="microsofttransactionstransactionbridgeregisterparticipantfailure"></a><span data-ttu-id="b7b98-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span><span class="sxs-lookup"><span data-stu-id="b7b98-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span></span>
<span data-ttu-id="b7b98-103">Usługa protokołu WS-AT nie może zarejestrować uczestnika dla protokołu sterowania.</span><span class="sxs-lookup"><span data-stu-id="b7b98-103">The WS-AT protocol service failed to register a participant for a control protocol.</span></span>  
  
## <a name="description"></a><span data-ttu-id="b7b98-104">Opis</span><span class="sxs-lookup"><span data-stu-id="b7b98-104">Description</span></span>  
 <span data-ttu-id="b7b98-105">Śledzone, jeśli usługi MSDTC wykryje nieprawidłowe żądanie rejestracji.</span><span class="sxs-lookup"><span data-stu-id="b7b98-105">Traced if MSDTC detects an invalid Registration request.</span></span> <span data-ttu-id="b7b98-106">Może to być spowodowane przez wiele żądań rejestracji uzupełniania i błędy wewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="b7b98-106">This can be caused by  multiple Completion registration requests and internal errors.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="b7b98-107">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="b7b98-107">Troubleshooting</span></span>  
 <span data-ttu-id="b7b98-108">Nie należy próbować rejestrowanie się w celu ukończenia więcej niż raz.</span><span class="sxs-lookup"><span data-stu-id="b7b98-108">Do not try to Register for Completion more than once.</span></span>  <span data-ttu-id="b7b98-109">Ponadto sprawdź, czy ciągu stanu w komunikat śledzenia do ustalenia, czy istnieje dowolny element przydatnych wyników.</span><span class="sxs-lookup"><span data-stu-id="b7b98-109">Also, inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7b98-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b7b98-110">See Also</span></span>  
 [<span data-ttu-id="b7b98-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="b7b98-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="b7b98-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="b7b98-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="b7b98-113">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="b7b98-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
