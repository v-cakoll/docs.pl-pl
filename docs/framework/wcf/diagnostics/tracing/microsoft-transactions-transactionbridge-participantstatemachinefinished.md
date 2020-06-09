---
title: Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished
ms.date: 03/30/2017
ms.assetid: 54b677f7-03ad-40f2-9c5d-297a8ad9bf90
ms.openlocfilehash: 0652b3b76c155431b68c5ee0dc8f83977f9845a5
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594364"
---
# <a name="microsofttransactionstransactionbridgeparticipantstatemachinefinished"></a><span data-ttu-id="cc107-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="cc107-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span></span>
<span data-ttu-id="cc107-103">Komputer stanu dla rejestracji uczestnika przeszedł w stan zakończenia.</span><span class="sxs-lookup"><span data-stu-id="cc107-103">The state machine for a participant enlistment entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="cc107-104">Opis</span><span class="sxs-lookup"><span data-stu-id="cc107-104">Description</span></span>  
 <span data-ttu-id="cc107-105">Śledzone, gdy Rejestracja uczestnika podrzędnego zakończyła przetwarzanie 2PC.</span><span class="sxs-lookup"><span data-stu-id="cc107-105">Traced when a subordinate participant enlistment has completed 2pc processing.</span></span> <span data-ttu-id="cc107-106">Wynik rejestracji można zatwierdzić lub przerwać.</span><span class="sxs-lookup"><span data-stu-id="cc107-106">The outcome for the enlistment can be Committed or Aborted.</span></span> <span data-ttu-id="cc107-107">Jest on także śledzony, jeśli którykolwiek uczestnik odgłosów w trakcie przygotowania.</span><span class="sxs-lookup"><span data-stu-id="cc107-107">It is also traced if any participant votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc107-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cc107-108">See also</span></span>

- [<span data-ttu-id="cc107-109">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="cc107-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="cc107-110">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="cc107-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="cc107-111">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="cc107-111">Administration and Diagnostics</span></span>](../index.md)
