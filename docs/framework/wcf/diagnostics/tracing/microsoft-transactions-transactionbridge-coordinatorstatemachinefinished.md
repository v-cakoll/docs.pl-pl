---
title: Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished
ms.date: 03/30/2017
ms.assetid: 16cb428d-d886-4789-a961-6fded4b0dbba
ms.openlocfilehash: abb6a81d22da3a35c754c5d1485c5d612c9cd1e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33473136"
---
# <a name="microsofttransactionstransactionbridgecoordinatorstatemachinefinished"></a><span data-ttu-id="ab452-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="ab452-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span></span>
<span data-ttu-id="ab452-103">Komputer stanu dla rejestracji koordynatora przeszedł w stan zakończenia.</span><span class="sxs-lookup"><span data-stu-id="ab452-103">The state machine for a coordinator enlistment has entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ab452-104">Opis</span><span class="sxs-lookup"><span data-stu-id="ab452-104">Description</span></span>  
 <span data-ttu-id="ab452-105">Śledzone podczas lokalnego Menedżera transakcji uznaje się, że rejestracja koordynatora wyższego poziomu przetworzył 2pc.</span><span class="sxs-lookup"><span data-stu-id="ab452-105">Traced when the local Transaction Manager believes a superior coordinator enlistment has completed 2pc processing.</span></span> <span data-ttu-id="ab452-106">Wynik dla rejestracji mogą być zatwierdzone lub anulowane lub Forgotten.</span><span class="sxs-lookup"><span data-stu-id="ab452-106">The outcome for the enlistment can be Committed or Aborted or Forgotten.</span></span> <span data-ttu-id="ab452-107">Również śledzonego, gdy lokalnego Menedżera transakcji głosów tylko do odczytu podczas przygotowania.</span><span class="sxs-lookup"><span data-stu-id="ab452-107">It is also traced if the local Transaction Manager votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab452-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ab452-108">See Also</span></span>  
 [<span data-ttu-id="ab452-109">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="ab452-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="ab452-110">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="ab452-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="ab452-111">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="ab452-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
