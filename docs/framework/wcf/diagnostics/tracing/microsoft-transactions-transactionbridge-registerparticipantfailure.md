---
title: Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
ms.date: 03/30/2017
ms.assetid: 3a4ead79-8550-4037-84e3-fd70ff56e001
ms.openlocfilehash: e56a9ed1d837af27d481282e0e106d537ec41ee3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59164297"
---
# <a name="microsofttransactionstransactionbridgeregisterparticipantfailure"></a><span data-ttu-id="b7116-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span><span class="sxs-lookup"><span data-stu-id="b7116-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span></span>
<span data-ttu-id="b7116-103">Nie można zarejestrować uczestnika dla protokołu kontroli usługi protokołu WS-AT.</span><span class="sxs-lookup"><span data-stu-id="b7116-103">The WS-AT protocol service failed to register a participant for a control protocol.</span></span>  
  
## <a name="description"></a><span data-ttu-id="b7116-104">Opis</span><span class="sxs-lookup"><span data-stu-id="b7116-104">Description</span></span>  
 <span data-ttu-id="b7116-105">Śledzone, jeśli usługa MSDTC wykrywa nieprawidłowe żądanie rejestracji.</span><span class="sxs-lookup"><span data-stu-id="b7116-105">Traced if MSDTC detects an invalid Registration request.</span></span> <span data-ttu-id="b7116-106">Może to być spowodowane przez wiele żądań rejestracji uzupełniania i wewnętrzne błędy.</span><span class="sxs-lookup"><span data-stu-id="b7116-106">This can be caused by  multiple Completion registration requests and internal errors.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="b7116-107">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="b7116-107">Troubleshooting</span></span>  
 <span data-ttu-id="b7116-108">Nie należy próbować Zarejestruj się w celu ukończenia więcej niż jeden raz.</span><span class="sxs-lookup"><span data-stu-id="b7116-108">Do not try to Register for Completion more than once.</span></span>  <span data-ttu-id="b7116-109">Ponadto sprawdź, czy ciąg stanu w ramach komunikat śledzenia do ustalenia, czy istnieje dowolny element informacje z możliwością działania.</span><span class="sxs-lookup"><span data-stu-id="b7116-109">Also, inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7116-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b7116-110">See also</span></span>

- [<span data-ttu-id="b7116-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="b7116-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="b7116-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="b7116-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="b7116-113">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="b7116-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
