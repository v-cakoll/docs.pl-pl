---
title: Microsoft.Transactions.TransactionBridge.ReplayMessageRetry
ms.date: 03/30/2017
ms.assetid: e5b820ae-504d-405a-926a-9effa41d2369
ms.openlocfilehash: 0c9e79709f5929e1fa123a8d1695ca720046e9e3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61997526"
---
# <a name="microsofttransactionstransactionbridgereplaymessageretry"></a><span data-ttu-id="be0ac-102">Microsoft.Transactions.TransactionBridge.ReplayMessageRetry</span><span class="sxs-lookup"><span data-stu-id="be0ac-102">Microsoft.Transactions.TransactionBridge.ReplayMessageRetry</span></span>
<span data-ttu-id="be0ac-103">Ponowna próba komunikat powtarzania została wysłana do koordynator nie odpowiada.</span><span class="sxs-lookup"><span data-stu-id="be0ac-103">A replay message retry was sent to an unresponsive coordinator.</span></span>  
  
## <a name="description"></a><span data-ttu-id="be0ac-104">Opis</span><span class="sxs-lookup"><span data-stu-id="be0ac-104">Description</span></span>  
 <span data-ttu-id="be0ac-105">Śledzone w razie potrzeby lokalny Menedżer transakcji do wysłania wiadomości powtarzania koordynatorem wyższego poziomu, ponieważ nie otrzymała odpowiedzi w określonym czasie.</span><span class="sxs-lookup"><span data-stu-id="be0ac-105">Traced if the local Transaction Manager needed to resend a Replay message to a superior coordinator because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="be0ac-106">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="be0ac-106">Troubleshooting</span></span>  
 <span data-ttu-id="be0ac-107">Badania potencjalnych sieci lub problemy z produktu, które uniemożliwiają są dostarczane na czas odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="be0ac-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="be0ac-108">Jeśli wiele z tych komunikatów są widoczne, może to wskazywać problemy z infrastrukturą lub nieprawidłowo długich czasów odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="be0ac-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="be0ac-109">Zarówno w przypadku problemów znacznie skróci przepływność transakcji w ramach systemu.</span><span class="sxs-lookup"><span data-stu-id="be0ac-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be0ac-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="be0ac-110">See also</span></span>

- [<span data-ttu-id="be0ac-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="be0ac-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="be0ac-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="be0ac-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="be0ac-113">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="be0ac-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
