---
title: Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished
ms.date: 03/30/2017
ms.assetid: 16cb428d-d886-4789-a961-6fded4b0dbba
ms.openlocfilehash: bffaed4976d82202eaea9ce50f6d389548fdabfd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59144836"
---
# <a name="microsofttransactionstransactionbridgecoordinatorstatemachinefinished"></a><span data-ttu-id="9f377-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="9f377-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span></span>
<span data-ttu-id="9f377-103">Automatu stanów dla rejestracji koordynatora została wprowadzona w stan zakończenia.</span><span class="sxs-lookup"><span data-stu-id="9f377-103">The state machine for a coordinator enlistment has entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="9f377-104">Opis</span><span class="sxs-lookup"><span data-stu-id="9f377-104">Description</span></span>  
 <span data-ttu-id="9f377-105">Śledzone, gdy lokalny Menedżer transakcji uważa, że rejestracja przełożonego koordynatora zakończeniu przetwarzania 2pc.</span><span class="sxs-lookup"><span data-stu-id="9f377-105">Traced when the local Transaction Manager believes a superior coordinator enlistment has completed 2pc processing.</span></span> <span data-ttu-id="9f377-106">Wynik dla rejestracji może być przydzielony, Aborted lub zapomnianych.</span><span class="sxs-lookup"><span data-stu-id="9f377-106">The outcome for the enlistment can be Committed or Aborted or Forgotten.</span></span> <span data-ttu-id="9f377-107">Również śledzona jest, gdy lokalny Menedżer transakcji głosów tylko do odczytu podczas przygotowywania.</span><span class="sxs-lookup"><span data-stu-id="9f377-107">It is also traced if the local Transaction Manager votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f377-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9f377-108">See also</span></span>

- [<span data-ttu-id="9f377-109">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="9f377-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="9f377-110">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="9f377-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="9f377-111">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="9f377-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
