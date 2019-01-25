---
title: Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished
ms.date: 03/30/2017
ms.assetid: 54b677f7-03ad-40f2-9c5d-297a8ad9bf90
ms.openlocfilehash: 56eb40d4e8b2580ba094e67552872cf558c8a617
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54642298"
---
# <a name="microsofttransactionstransactionbridgeparticipantstatemachinefinished"></a><span data-ttu-id="ff05b-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="ff05b-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span></span>
<span data-ttu-id="ff05b-103">Automatu stanów dla uczestnika rejestracji została zakończona stanu.</span><span class="sxs-lookup"><span data-stu-id="ff05b-103">The state machine for a participant enlistment entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ff05b-104">Opis</span><span class="sxs-lookup"><span data-stu-id="ff05b-104">Description</span></span>  
 <span data-ttu-id="ff05b-105">Śledzone, gdy podrzędny rejestracji uczestnika zakończy przetwarzanie 2pc.</span><span class="sxs-lookup"><span data-stu-id="ff05b-105">Traced when a subordinate participant enlistment has completed 2pc processing.</span></span> <span data-ttu-id="ff05b-106">Wynik dla rejestracji może być przydzielony lub Aborted.</span><span class="sxs-lookup"><span data-stu-id="ff05b-106">The outcome for the enlistment can be Committed or Aborted.</span></span> <span data-ttu-id="ff05b-107">Również śledzona jest, gdy każdy uczestnik głosów tylko do odczytu podczas przygotowywania.</span><span class="sxs-lookup"><span data-stu-id="ff05b-107">It is also traced if any participant votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff05b-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ff05b-108">See also</span></span>
- [<span data-ttu-id="ff05b-109">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="ff05b-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="ff05b-110">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="ff05b-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="ff05b-111">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="ff05b-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
