---
title: Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt
ms.date: 03/30/2017
ms.assetid: 3e8fc825-9f22-47e7-9c16-d64ef291c932
ms.openlocfilehash: 9434f2f902a50a37fb3efee22fd3b18b33af9129
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61997462"
---
# <a name="microsofttransactionstransactionbridgevolatileparticipantindoubt"></a><span data-ttu-id="94cf2-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span><span class="sxs-lookup"><span data-stu-id="94cf2-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span></span>
<span data-ttu-id="94cf2-103">Usługa protokołu WS-AT odebrała komunikat Prepared lub Replay od nierozpoznanego uczestnika nietrwałego.</span><span class="sxs-lookup"><span data-stu-id="94cf2-103">The WS-AT protocol service received a Prepared or Replay message from an unrecognized volatile participant.</span></span> <span data-ttu-id="94cf2-104">Zwrócono błąd do uczestnika oświadcza, że w razie wątpliwości wyniku transakcji.</span><span class="sxs-lookup"><span data-stu-id="94cf2-104">A fault was returned to the participant, declares that the transaction's outcome is in doubt.</span></span>  
  
## <a name="description"></a><span data-ttu-id="94cf2-105">Opis</span><span class="sxs-lookup"><span data-stu-id="94cf2-105">Description</span></span>  
 <span data-ttu-id="94cf2-106">Śledzone, gdy lokalny Menedżer transakcji odbiera komunikat Prepared lub Replay od lotnych rejestracji, który już ma zapomniano.</span><span class="sxs-lookup"><span data-stu-id="94cf2-106">Traced when the local Transaction Manager receives a Prepared or Replay message from a Volatile enlistment that it has already forgotten.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="94cf2-107">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="94cf2-107">Troubleshooting</span></span>  
 <span data-ttu-id="94cf2-108">Zbadaj możliwych przyczyn opóźnień komunikaty pochodzące z uczestnika nietrwałego.</span><span class="sxs-lookup"><span data-stu-id="94cf2-108">Investigate potential causes of late messages coming from the Volatile participant.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94cf2-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="94cf2-109">See also</span></span>

- [<span data-ttu-id="94cf2-110">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="94cf2-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="94cf2-111">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="94cf2-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="94cf2-112">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="94cf2-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
