---
title: Microsoft.Transactions.TransactionBridge.CommitMessageRetry
ms.date: 03/30/2017
ms.assetid: 4abe01f0-6398-4fba-b2f3-c054b7f7e971
ms.openlocfilehash: f1092dd335be793fb3d2212b7b9398cc69d2f79f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474288"
---
# <a name="microsofttransactionstransactionbridgecommitmessageretry"></a><span data-ttu-id="fe70c-102">Microsoft.Transactions.TransactionBridge.CommitMessageRetry</span><span class="sxs-lookup"><span data-stu-id="fe70c-102">Microsoft.Transactions.TransactionBridge.CommitMessageRetry</span></span>
<span data-ttu-id="fe70c-103">Ponowna próba przekazania wiadomości została wysłana do uczestnika, który nie odpowiada.</span><span class="sxs-lookup"><span data-stu-id="fe70c-103">A commit message retry was sent to an unresponsive participant.</span></span>  
  
## <a name="description"></a><span data-ttu-id="fe70c-104">Opis</span><span class="sxs-lookup"><span data-stu-id="fe70c-104">Description</span></span>  
 <span data-ttu-id="fe70c-105">Śledzone w razie potrzeby lokalnego Menedżera transakcji do wysłania wiadomości zatwierdzania do uczestnika podrzędnych, ponieważ nie otrzymano odpowiedzi w określonym czasie.</span><span class="sxs-lookup"><span data-stu-id="fe70c-105">Traced if the local Transaction Manager needed to resend a Commit message to a subordinate participant because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="fe70c-106">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="fe70c-106">Troubleshooting</span></span>  
 <span data-ttu-id="fe70c-107">Badania potencjalnych sieci lub produktu problemy, które uniemożliwiają dostarczanie na czas odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="fe70c-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="fe70c-108">Jeśli wiele z tych wiadomości są widoczne, może to oznaczać problemy związane z infrastrukturą lub nieprawidłowo długich czasów odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="fe70c-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="fe70c-109">Problemy z obu znacząco zmniejsza przepływność transakcji w systemie.</span><span class="sxs-lookup"><span data-stu-id="fe70c-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe70c-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fe70c-110">See Also</span></span>  
 [<span data-ttu-id="fe70c-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="fe70c-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="fe70c-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="fe70c-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="fe70c-113">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="fe70c-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
