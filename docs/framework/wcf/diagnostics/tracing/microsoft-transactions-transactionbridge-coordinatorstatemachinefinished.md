---
title: Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished
ms.date: 03/30/2017
ms.assetid: 16cb428d-d886-4789-a961-6fded4b0dbba
ms.openlocfilehash: 8cc32e7b38bfd1bdafd2377ad759f98b248d722e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710459"
---
# <a name="microsofttransactionstransactionbridgecoordinatorstatemachinefinished"></a><span data-ttu-id="1e7cb-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="1e7cb-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span></span>
<span data-ttu-id="1e7cb-103">Automatu stanów dla rejestracji koordynatora została wprowadzona w stan zakończenia.</span><span class="sxs-lookup"><span data-stu-id="1e7cb-103">The state machine for a coordinator enlistment has entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="1e7cb-104">Opis</span><span class="sxs-lookup"><span data-stu-id="1e7cb-104">Description</span></span>  
 <span data-ttu-id="1e7cb-105">Śledzone, gdy lokalny Menedżer transakcji uważa, że rejestracja przełożonego koordynatora zakończeniu przetwarzania 2pc.</span><span class="sxs-lookup"><span data-stu-id="1e7cb-105">Traced when the local Transaction Manager believes a superior coordinator enlistment has completed 2pc processing.</span></span> <span data-ttu-id="1e7cb-106">Wynik dla rejestracji może być przydzielony, Aborted lub zapomnianych.</span><span class="sxs-lookup"><span data-stu-id="1e7cb-106">The outcome for the enlistment can be Committed or Aborted or Forgotten.</span></span> <span data-ttu-id="1e7cb-107">Również śledzona jest, gdy lokalny Menedżer transakcji głosów tylko do odczytu podczas przygotowywania.</span><span class="sxs-lookup"><span data-stu-id="1e7cb-107">It is also traced if the local Transaction Manager votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e7cb-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1e7cb-108">See also</span></span>
- [<span data-ttu-id="1e7cb-109">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="1e7cb-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="1e7cb-110">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="1e7cb-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="1e7cb-111">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="1e7cb-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
