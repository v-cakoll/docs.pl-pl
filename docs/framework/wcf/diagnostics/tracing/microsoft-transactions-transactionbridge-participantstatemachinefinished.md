---
title: Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54b677f7-03ad-40f2-9c5d-297a8ad9bf90
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 53ac142c8c7d8004020210ffb3c0dcb2355a5b61
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgeparticipantstatemachinefinished"></a><span data-ttu-id="8c05e-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="8c05e-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span></span>
<span data-ttu-id="8c05e-103">Komputer stanu dla rejestracji uczestnika przeszedł w stan zakończenia.</span><span class="sxs-lookup"><span data-stu-id="8c05e-103">The state machine for a participant enlistment entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="8c05e-104">Opis</span><span class="sxs-lookup"><span data-stu-id="8c05e-104">Description</span></span>  
 <span data-ttu-id="8c05e-105">Śledzone po zakończeniu przetwarzania 2pc podrzędnego rejestracji uczestnika.</span><span class="sxs-lookup"><span data-stu-id="8c05e-105">Traced when a subordinate participant enlistment has completed 2pc processing.</span></span> <span data-ttu-id="8c05e-106">Wynik dla rejestracji mogą być zatwierdzone lub anulowane.</span><span class="sxs-lookup"><span data-stu-id="8c05e-106">The outcome for the enlistment can be Committed or Aborted.</span></span> <span data-ttu-id="8c05e-107">Również śledzonego, jeśli każdy uczestnik głosów tylko do odczytu podczas przygotowania.</span><span class="sxs-lookup"><span data-stu-id="8c05e-107">It is also traced if any participant votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c05e-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8c05e-108">See Also</span></span>  
 [<span data-ttu-id="8c05e-109">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="8c05e-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="8c05e-110">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="8c05e-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="8c05e-111">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="8c05e-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
