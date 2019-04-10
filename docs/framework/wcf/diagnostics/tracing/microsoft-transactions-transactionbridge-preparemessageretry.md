---
title: Microsoft.Transactions.TransactionBridge.PrepareMessageRetry
ms.date: 03/30/2017
ms.assetid: ada4baa5-b60d-46b8-ad46-4d69f8d8a9fa
ms.openlocfilehash: 02e275fa212128c65beda4bc3703949e75ea5092
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59220893"
---
# <a name="microsofttransactionstransactionbridgepreparemessageretry"></a><span data-ttu-id="1ebcf-102">Microsoft.Transactions.TransactionBridge.PrepareMessageRetry</span><span class="sxs-lookup"><span data-stu-id="1ebcf-102">Microsoft.Transactions.TransactionBridge.PrepareMessageRetry</span></span>
<span data-ttu-id="1ebcf-103">Ponowna próba przygotowania wiadomość została wysłana do uczestnika, który nie odpowiada.</span><span class="sxs-lookup"><span data-stu-id="1ebcf-103">A prepare message retry was sent to an unresponsive participant.</span></span>  
  
## <a name="description"></a><span data-ttu-id="1ebcf-104">Opis</span><span class="sxs-lookup"><span data-stu-id="1ebcf-104">Description</span></span>  
 <span data-ttu-id="1ebcf-105">Śledzone w razie potrzeby lokalny Menedżer transakcji próba wysłania wiadomości przygotowania do podrzędnego uczestnika, ponieważ nie otrzymała odpowiedzi w określonym czasie.</span><span class="sxs-lookup"><span data-stu-id="1ebcf-105">Traced if the local Transaction Manager needed to resend a Prepare message to a subordinate participant because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="1ebcf-106">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="1ebcf-106">Troubleshooting</span></span>  
 <span data-ttu-id="1ebcf-107">Badania potencjalnych sieci lub problemy z produktu, które uniemożliwiają są dostarczane na czas odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="1ebcf-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="1ebcf-108">Jeśli wiele z tych komunikatów są widoczne, może to wskazywać problemy z infrastrukturą lub nieprawidłowo długich czasów odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="1ebcf-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="1ebcf-109">Zarówno w przypadku problemów może znacząco zmniejszyć przepływność transakcji w ramach systemu.</span><span class="sxs-lookup"><span data-stu-id="1ebcf-109">Both issues can drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ebcf-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1ebcf-110">See also</span></span>

- [<span data-ttu-id="1ebcf-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="1ebcf-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="1ebcf-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="1ebcf-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="1ebcf-113">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="1ebcf-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
