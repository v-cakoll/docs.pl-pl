---
title: Microsoft.Transactions.TransactionBridge.CommitMessageRetry
ms.date: 03/30/2017
ms.assetid: 4abe01f0-6398-4fba-b2f3-c054b7f7e971
ms.openlocfilehash: d939d525fd1c7e8f41cccbc3ca7af9726f22bdfc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54571434"
---
# <a name="microsofttransactionstransactionbridgecommitmessageretry"></a><span data-ttu-id="cfb22-102">Microsoft.Transactions.TransactionBridge.CommitMessageRetry</span><span class="sxs-lookup"><span data-stu-id="cfb22-102">Microsoft.Transactions.TransactionBridge.CommitMessageRetry</span></span>
<span data-ttu-id="cfb22-103">Ponowna próba komunikat zatwierdzenia została wysłana do uczestnika, który nie odpowiada.</span><span class="sxs-lookup"><span data-stu-id="cfb22-103">A commit message retry was sent to an unresponsive participant.</span></span>  
  
## <a name="description"></a><span data-ttu-id="cfb22-104">Opis</span><span class="sxs-lookup"><span data-stu-id="cfb22-104">Description</span></span>  
 <span data-ttu-id="cfb22-105">Śledzone w razie potrzeby lokalny Menedżer transakcji ponownie wysłać wiadomość dotyczącą zatwierdzenia do podrzędnego uczestnika, ponieważ nie otrzymała odpowiedzi w określonym czasie.</span><span class="sxs-lookup"><span data-stu-id="cfb22-105">Traced if the local Transaction Manager needed to resend a Commit message to a subordinate participant because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="cfb22-106">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="cfb22-106">Troubleshooting</span></span>  
 <span data-ttu-id="cfb22-107">Badania potencjalnych sieci lub problemy z produktu, które uniemożliwiają są dostarczane na czas odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="cfb22-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="cfb22-108">Jeśli wiele z tych komunikatów są widoczne, może to wskazywać problemy z infrastrukturą lub nieprawidłowo długich czasów odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="cfb22-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="cfb22-109">Zarówno w przypadku problemów znacznie skróci przepływność transakcji w ramach systemu.</span><span class="sxs-lookup"><span data-stu-id="cfb22-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfb22-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cfb22-110">See also</span></span>
- [<span data-ttu-id="cfb22-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="cfb22-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="cfb22-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="cfb22-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="cfb22-113">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="cfb22-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
