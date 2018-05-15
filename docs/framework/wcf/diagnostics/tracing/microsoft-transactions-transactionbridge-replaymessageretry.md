---
title: Microsoft.Transactions.TransactionBridge.ReplayMessageRetry
ms.date: 03/30/2017
ms.assetid: e5b820ae-504d-405a-926a-9effa41d2369
ms.openlocfilehash: d000447245d973916dfe0df9af5c46b6fa822e32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="microsofttransactionstransactionbridgereplaymessageretry"></a><span data-ttu-id="3104b-102">Microsoft.Transactions.TransactionBridge.ReplayMessageRetry</span><span class="sxs-lookup"><span data-stu-id="3104b-102">Microsoft.Transactions.TransactionBridge.ReplayMessageRetry</span></span>
<span data-ttu-id="3104b-103">Do koordynatora, który nie odpowiada, wysłano ponowną próbę komunikatu powtarzania.</span><span class="sxs-lookup"><span data-stu-id="3104b-103">A replay message retry was sent to an unresponsive coordinator.</span></span>  
  
## <a name="description"></a><span data-ttu-id="3104b-104">Opis</span><span class="sxs-lookup"><span data-stu-id="3104b-104">Description</span></span>  
 <span data-ttu-id="3104b-105">Śledzone w razie potrzeby lokalnego Menedżera transakcji do wysłania wiadomości powtarzania koordynatorem wyższego poziomu, ponieważ nie otrzymano odpowiedzi w określonym czasie.</span><span class="sxs-lookup"><span data-stu-id="3104b-105">Traced if the local Transaction Manager needed to resend a Replay message to a superior coordinator because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="3104b-106">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="3104b-106">Troubleshooting</span></span>  
 <span data-ttu-id="3104b-107">Badania potencjalnych sieci lub produktu problemy, które uniemożliwiają dostarczanie na czas odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="3104b-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="3104b-108">Jeśli wiele z tych wiadomości są widoczne, może to oznaczać problemy związane z infrastrukturą lub nieprawidłowo długich czasów odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="3104b-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="3104b-109">Problemy z obu znacząco zmniejsza przepływność transakcji w systemie.</span><span class="sxs-lookup"><span data-stu-id="3104b-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3104b-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3104b-110">See Also</span></span>  
 [<span data-ttu-id="3104b-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="3104b-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="3104b-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="3104b-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="3104b-113">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="3104b-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
