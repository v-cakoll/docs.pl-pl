---
title: Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
ms.date: 03/30/2017
ms.assetid: 3a4ead79-8550-4037-84e3-fd70ff56e001
ms.openlocfilehash: 1819a269a6775c8541f38f4aa5d733002e3c1e9f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599685"
---
# <a name="microsofttransactionstransactionbridgeregisterparticipantfailure"></a><span data-ttu-id="73f46-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span><span class="sxs-lookup"><span data-stu-id="73f46-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span></span>
<span data-ttu-id="73f46-103">Usługa protokołu WS-AT nie może zarejestrować uczestnika dla protokołu kontroli.</span><span class="sxs-lookup"><span data-stu-id="73f46-103">The WS-AT protocol service failed to register a participant for a control protocol.</span></span>  
  
## <a name="description"></a><span data-ttu-id="73f46-104">Opis</span><span class="sxs-lookup"><span data-stu-id="73f46-104">Description</span></span>  
 <span data-ttu-id="73f46-105">Śledzone, jeśli usługa MSDTC wykryje Nieprawidłowe żądanie rejestracji.</span><span class="sxs-lookup"><span data-stu-id="73f46-105">Traced if MSDTC detects an invalid Registration request.</span></span> <span data-ttu-id="73f46-106">Przyczyną może być wiele żądań rejestracji ukończenia i błędy wewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="73f46-106">This can be caused by  multiple Completion registration requests and internal errors.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="73f46-107">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="73f46-107">Troubleshooting</span></span>  
 <span data-ttu-id="73f46-108">Nie próbuj rejestrować się w celu ukończenia więcej niż raz.</span><span class="sxs-lookup"><span data-stu-id="73f46-108">Do not try to Register for Completion more than once.</span></span>  <span data-ttu-id="73f46-109">Sprawdź również ciąg stanu w komunikacie śledzenia, aby określić, czy istnieje jakikolwiek element możliwy do wykonania.</span><span class="sxs-lookup"><span data-stu-id="73f46-109">Also, inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73f46-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="73f46-110">See also</span></span>

- [<span data-ttu-id="73f46-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="73f46-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="73f46-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="73f46-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="73f46-113">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="73f46-113">Administration and Diagnostics</span></span>](../index.md)
