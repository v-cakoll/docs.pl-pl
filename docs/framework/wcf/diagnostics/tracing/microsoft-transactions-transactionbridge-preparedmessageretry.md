---
title: Microsoft.Transactions.TransactionBridge.PreparedMessageRetry
ms.date: 03/30/2017
ms.assetid: 2194292d-bf5f-4aef-9336-cd3c4795cb71
ms.openlocfilehash: d8acdb2f94e752860025ee2963aa78682b43b079
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59216915"
---
# <a name="microsofttransactionstransactionbridgepreparedmessageretry"></a><span data-ttu-id="772bf-102">Microsoft.Transactions.TransactionBridge.PreparedMessageRetry</span><span class="sxs-lookup"><span data-stu-id="772bf-102">Microsoft.Transactions.TransactionBridge.PreparedMessageRetry</span></span>
<span data-ttu-id="772bf-103">Ponowna próba przygotowano komunikat został wysłany do koordynator nie odpowiada.</span><span class="sxs-lookup"><span data-stu-id="772bf-103">A prepared message retry was sent to an unresponsive coordinator.</span></span>  
  
## <a name="description"></a><span data-ttu-id="772bf-104">Opis</span><span class="sxs-lookup"><span data-stu-id="772bf-104">Description</span></span>  
 <span data-ttu-id="772bf-105">Śledzone w razie potrzeby lokalny Menedżer transakcji do ponownego wysłania komunikatu przygotowania do wyższego poziomu koordynatora, ponieważ nie otrzymała odpowiedzi w określonym czasie /</span><span class="sxs-lookup"><span data-stu-id="772bf-105">Traced if the local Transaction Manager needed to resend a Prepared message to a superior coordinator because it did not receive a response in a given amount of time/</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="772bf-106">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="772bf-106">Troubleshooting</span></span>  
 <span data-ttu-id="772bf-107">Badania potencjalnych sieci lub problemy z produktu, które uniemożliwiają są dostarczane na czas odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="772bf-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="772bf-108">Jeśli wiele z tych komunikatów są widoczne, może to wskazywać problemy z infrastrukturą lub nieprawidłowo długich czasów odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="772bf-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="772bf-109">Zarówno w przypadku problemów znacznie skróci przepływność transakcji w ramach systemu.</span><span class="sxs-lookup"><span data-stu-id="772bf-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="772bf-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="772bf-110">See also</span></span>

- [<span data-ttu-id="772bf-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="772bf-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="772bf-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="772bf-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="772bf-113">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="772bf-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
