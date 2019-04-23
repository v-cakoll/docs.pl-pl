---
title: Microsoft.Transactions.TransactionBridge.PrepareMessageRetry
ms.date: 03/30/2017
ms.assetid: ada4baa5-b60d-46b8-ad46-4d69f8d8a9fa
ms.openlocfilehash: 02e275fa212128c65beda4bc3703949e75ea5092
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59220893"
---
# <a name="microsofttransactionstransactionbridgepreparemessageretry"></a><span data-ttu-id="8e099-102">Microsoft.Transactions.TransactionBridge.PrepareMessageRetry</span><span class="sxs-lookup"><span data-stu-id="8e099-102">Microsoft.Transactions.TransactionBridge.PrepareMessageRetry</span></span>
<span data-ttu-id="8e099-103">Ponowna próba przygotowania wiadomość została wysłana do uczestnika, który nie odpowiada.</span><span class="sxs-lookup"><span data-stu-id="8e099-103">A prepare message retry was sent to an unresponsive participant.</span></span>  
  
## <a name="description"></a><span data-ttu-id="8e099-104">Opis</span><span class="sxs-lookup"><span data-stu-id="8e099-104">Description</span></span>  
 <span data-ttu-id="8e099-105">Śledzone w razie potrzeby lokalny Menedżer transakcji próba wysłania wiadomości przygotowania do podrzędnego uczestnika, ponieważ nie otrzymała odpowiedzi w określonym czasie.</span><span class="sxs-lookup"><span data-stu-id="8e099-105">Traced if the local Transaction Manager needed to resend a Prepare message to a subordinate participant because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="8e099-106">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="8e099-106">Troubleshooting</span></span>  
 <span data-ttu-id="8e099-107">Badania potencjalnych sieci lub problemy z produktu, które uniemożliwiają są dostarczane na czas odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="8e099-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="8e099-108">Jeśli wiele z tych komunikatów są widoczne, może to wskazywać problemy z infrastrukturą lub nieprawidłowo długich czasów odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="8e099-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="8e099-109">Zarówno w przypadku problemów może znacząco zmniejszyć przepływność transakcji w ramach systemu.</span><span class="sxs-lookup"><span data-stu-id="8e099-109">Both issues can drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e099-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8e099-110">See also</span></span>

- [<span data-ttu-id="8e099-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="8e099-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="8e099-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="8e099-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="8e099-113">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="8e099-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
