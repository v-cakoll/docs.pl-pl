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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7c9a456e668560cb2172de80295b731a6103aa7a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgecoordinatorstatemachinefinished"></a><span data-ttu-id="2c236-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="2c236-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span></span>
<span data-ttu-id="2c236-103">Komputer stanu dla rejestracji koordynatora przeszedł w stan zakończenia.</span><span class="sxs-lookup"><span data-stu-id="2c236-103">The state machine for a coordinator enlistment has entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="2c236-104">Opis</span><span class="sxs-lookup"><span data-stu-id="2c236-104">Description</span></span>  
 <span data-ttu-id="2c236-105">Śledzone podczas lokalnego Menedżera transakcji uznaje się, że rejestracja koordynatora wyższego poziomu przetworzył 2pc.</span><span class="sxs-lookup"><span data-stu-id="2c236-105">Traced when the local Transaction Manager believes a superior coordinator enlistment has completed 2pc processing.</span></span> <span data-ttu-id="2c236-106">Wynik dla rejestracji mogą być zatwierdzone lub anulowane lub Forgotten.</span><span class="sxs-lookup"><span data-stu-id="2c236-106">The outcome for the enlistment can be Committed or Aborted or Forgotten.</span></span> <span data-ttu-id="2c236-107">Również śledzonego, gdy lokalnego Menedżera transakcji głosów tylko do odczytu podczas przygotowania.</span><span class="sxs-lookup"><span data-stu-id="2c236-107">It is also traced if the local Transaction Manager votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c236-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2c236-108">See Also</span></span>  
 [<span data-ttu-id="2c236-109">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="2c236-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="2c236-110">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="2c236-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="2c236-111">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="2c236-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
