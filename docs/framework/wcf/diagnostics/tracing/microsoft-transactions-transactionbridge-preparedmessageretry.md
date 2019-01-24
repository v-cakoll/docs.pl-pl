---
title: Microsoft.Transactions.TransactionBridge.PreparedMessageRetry
ms.date: 03/30/2017
ms.assetid: 2194292d-bf5f-4aef-9336-cd3c4795cb71
ms.openlocfilehash: e5735596f1b724e47cdaadd30f07629ea6b772eb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54585932"
---
# <a name="microsofttransactionstransactionbridgepreparedmessageretry"></a><span data-ttu-id="3b055-102">Microsoft.Transactions.TransactionBridge.PreparedMessageRetry</span><span class="sxs-lookup"><span data-stu-id="3b055-102">Microsoft.Transactions.TransactionBridge.PreparedMessageRetry</span></span>
<span data-ttu-id="3b055-103">Ponowna próba przygotowano komunikat został wysłany do koordynator nie odpowiada.</span><span class="sxs-lookup"><span data-stu-id="3b055-103">A prepared message retry was sent to an unresponsive coordinator.</span></span>  
  
## <a name="description"></a><span data-ttu-id="3b055-104">Opis</span><span class="sxs-lookup"><span data-stu-id="3b055-104">Description</span></span>  
 <span data-ttu-id="3b055-105">Śledzone w razie potrzeby lokalny Menedżer transakcji do ponownego wysłania komunikatu przygotowania do wyższego poziomu koordynatora, ponieważ nie otrzymała odpowiedzi w określonym czasie /</span><span class="sxs-lookup"><span data-stu-id="3b055-105">Traced if the local Transaction Manager needed to resend a Prepared message to a superior coordinator because it did not receive a response in a given amount of time/</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="3b055-106">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="3b055-106">Troubleshooting</span></span>  
 <span data-ttu-id="3b055-107">Badania potencjalnych sieci lub problemy z produktu, które uniemożliwiają są dostarczane na czas odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="3b055-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="3b055-108">Jeśli wiele z tych komunikatów są widoczne, może to wskazywać problemy z infrastrukturą lub nieprawidłowo długich czasów odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="3b055-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="3b055-109">Zarówno w przypadku problemów znacznie skróci przepływność transakcji w ramach systemu.</span><span class="sxs-lookup"><span data-stu-id="3b055-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b055-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3b055-110">See also</span></span>
- [<span data-ttu-id="3b055-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="3b055-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="3b055-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="3b055-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="3b055-113">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="3b055-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
