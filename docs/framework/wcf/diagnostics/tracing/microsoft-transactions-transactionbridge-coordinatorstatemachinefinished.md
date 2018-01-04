---
title: Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16cb428d-d886-4789-a961-6fded4b0dbba
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 960166c7c1d91bcab8420a55e633b461bf37c626
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="microsofttransactionstransactionbridgecoordinatorstatemachinefinished"></a><span data-ttu-id="db91c-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="db91c-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span></span>
<span data-ttu-id="db91c-103">Komputer stanu dla rejestracji koordynatora przeszedł w stan zakończenia.</span><span class="sxs-lookup"><span data-stu-id="db91c-103">The state machine for a coordinator enlistment has entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="db91c-104">Opis</span><span class="sxs-lookup"><span data-stu-id="db91c-104">Description</span></span>  
 <span data-ttu-id="db91c-105">Śledzone podczas lokalnego Menedżera transakcji uznaje się, że rejestracja koordynatora wyższego poziomu przetworzył 2pc.</span><span class="sxs-lookup"><span data-stu-id="db91c-105">Traced when the local Transaction Manager believes a superior coordinator enlistment has completed 2pc processing.</span></span> <span data-ttu-id="db91c-106">Wynik dla rejestracji mogą być zatwierdzone lub anulowane lub Forgotten.</span><span class="sxs-lookup"><span data-stu-id="db91c-106">The outcome for the enlistment can be Committed or Aborted or Forgotten.</span></span> <span data-ttu-id="db91c-107">Również śledzonego, gdy lokalnego Menedżera transakcji głosów tylko do odczytu podczas przygotowania.</span><span class="sxs-lookup"><span data-stu-id="db91c-107">It is also traced if the local Transaction Manager votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db91c-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="db91c-108">See Also</span></span>  
 [<span data-ttu-id="db91c-109">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="db91c-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="db91c-110">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="db91c-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="db91c-111">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="db91c-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
