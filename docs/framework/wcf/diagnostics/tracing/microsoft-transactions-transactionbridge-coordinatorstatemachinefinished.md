---
title: Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished
ms.date: 03/30/2017
ms.assetid: 16cb428d-d886-4789-a961-6fded4b0dbba
ms.openlocfilehash: 3b9a3703e49c3932f62fcfb6994c9028b074bbe8
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594416"
---
# <a name="microsofttransactionstransactionbridgecoordinatorstatemachinefinished"></a><span data-ttu-id="f91d1-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="f91d1-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span></span>
<span data-ttu-id="f91d1-103">Komputer stanu dla rejestracji koordynatora przeszedł w stan zakończenia.</span><span class="sxs-lookup"><span data-stu-id="f91d1-103">The state machine for a coordinator enlistment has entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="f91d1-104">Opis</span><span class="sxs-lookup"><span data-stu-id="f91d1-104">Description</span></span>  
 <span data-ttu-id="f91d1-105">Śledzenie, gdy lokalny Menedżer transakcji uważa, że funkcja rejestracji wyższej koordynatora zakończyła przetwarzanie 2PC.</span><span class="sxs-lookup"><span data-stu-id="f91d1-105">Traced when the local Transaction Manager believes a superior coordinator enlistment has completed 2pc processing.</span></span> <span data-ttu-id="f91d1-106">Wynik rejestracji można zatwierdzić lub przerwać lub zazapominać.</span><span class="sxs-lookup"><span data-stu-id="f91d1-106">The outcome for the enlistment can be Committed or Aborted or Forgotten.</span></span> <span data-ttu-id="f91d1-107">Jest on także śledzony, jeśli lokalny Menedżer transakcji odnosi wartość ReadOnly podczas przygotowywania.</span><span class="sxs-lookup"><span data-stu-id="f91d1-107">It is also traced if the local Transaction Manager votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f91d1-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f91d1-108">See also</span></span>

- [<span data-ttu-id="f91d1-109">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="f91d1-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="f91d1-110">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="f91d1-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="f91d1-111">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="f91d1-111">Administration and Diagnostics</span></span>](../index.md)
