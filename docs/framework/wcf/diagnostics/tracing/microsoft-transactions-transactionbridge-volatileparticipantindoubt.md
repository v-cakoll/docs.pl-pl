---
title: Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt
ms.date: 03/30/2017
ms.assetid: 3e8fc825-9f22-47e7-9c16-d64ef291c932
ms.openlocfilehash: ab1c2c8afe3a66536810a614cc6deac12519cb9b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599636"
---
# <a name="microsofttransactionstransactionbridgevolatileparticipantindoubt"></a><span data-ttu-id="0e5c5-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span><span class="sxs-lookup"><span data-stu-id="0e5c5-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span></span>
<span data-ttu-id="0e5c5-103">Usługa protokołu WS-AT odebrała przygotowany lub powtarzający się komunikat od nierozpoznanego uczestnika trwałego.</span><span class="sxs-lookup"><span data-stu-id="0e5c5-103">The WS-AT protocol service received a Prepared or Replay message from an unrecognized volatile participant.</span></span> <span data-ttu-id="0e5c5-104">Do uczestnika został zwrócony błąd, deklaruje, że wynik transakcji jest wątpliwy.</span><span class="sxs-lookup"><span data-stu-id="0e5c5-104">A fault was returned to the participant, declares that the transaction's outcome is in doubt.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0e5c5-105">Opis</span><span class="sxs-lookup"><span data-stu-id="0e5c5-105">Description</span></span>  
 <span data-ttu-id="0e5c5-106">Śledzony, gdy lokalny Menedżer transakcji odbiera przygotowany lub powtarzający się komunikat z nietrwałej rejestracji, że już został zapomniany.</span><span class="sxs-lookup"><span data-stu-id="0e5c5-106">Traced when the local Transaction Manager receives a Prepared or Replay message from a Volatile enlistment that it has already forgotten.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="0e5c5-107">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="0e5c5-107">Troubleshooting</span></span>  
 <span data-ttu-id="0e5c5-108">Zbadaj potencjalne przyczyny późnych komunikatów pochodzących od uczestnika nietrwałego.</span><span class="sxs-lookup"><span data-stu-id="0e5c5-108">Investigate potential causes of late messages coming from the Volatile participant.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e5c5-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0e5c5-109">See also</span></span>

- [<span data-ttu-id="0e5c5-110">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="0e5c5-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="0e5c5-111">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="0e5c5-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="0e5c5-112">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="0e5c5-112">Administration and Diagnostics</span></span>](../index.md)
