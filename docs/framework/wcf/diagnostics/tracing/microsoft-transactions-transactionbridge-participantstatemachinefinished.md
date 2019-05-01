---
title: Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished
ms.date: 03/30/2017
ms.assetid: 54b677f7-03ad-40f2-9c5d-297a8ad9bf90
ms.openlocfilehash: 7f37cb5d9ee3d2d9d56519f785388f278b3333b9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61997883"
---
# <a name="microsofttransactionstransactionbridgeparticipantstatemachinefinished"></a><span data-ttu-id="a5299-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="a5299-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span></span>
<span data-ttu-id="a5299-103">Automatu stanów dla uczestnika rejestracji została zakończona stanu.</span><span class="sxs-lookup"><span data-stu-id="a5299-103">The state machine for a participant enlistment entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="a5299-104">Opis</span><span class="sxs-lookup"><span data-stu-id="a5299-104">Description</span></span>  
 <span data-ttu-id="a5299-105">Śledzone, gdy podrzędny rejestracji uczestnika zakończy przetwarzanie 2pc.</span><span class="sxs-lookup"><span data-stu-id="a5299-105">Traced when a subordinate participant enlistment has completed 2pc processing.</span></span> <span data-ttu-id="a5299-106">Wynik dla rejestracji może być przydzielony lub Aborted.</span><span class="sxs-lookup"><span data-stu-id="a5299-106">The outcome for the enlistment can be Committed or Aborted.</span></span> <span data-ttu-id="a5299-107">Również śledzona jest, gdy każdy uczestnik głosów tylko do odczytu podczas przygotowywania.</span><span class="sxs-lookup"><span data-stu-id="a5299-107">It is also traced if any participant votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5299-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a5299-108">See also</span></span>

- [<span data-ttu-id="a5299-109">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="a5299-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="a5299-110">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="a5299-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="a5299-111">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="a5299-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
