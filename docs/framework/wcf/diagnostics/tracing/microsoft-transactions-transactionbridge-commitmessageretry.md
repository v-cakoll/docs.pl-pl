---
title: Microsoft.Transactions.TransactionBridge.CommitMessageRetry
ms.date: 03/30/2017
ms.assetid: 4abe01f0-6398-4fba-b2f3-c054b7f7e971
ms.openlocfilehash: f37bc252e12aef94d77c0745d36b5c8232a169eb
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599740"
---
# <a name="microsofttransactionstransactionbridgecommitmessageretry"></a><span data-ttu-id="e1c54-102">Microsoft.Transactions.TransactionBridge.CommitMessageRetry</span><span class="sxs-lookup"><span data-stu-id="e1c54-102">Microsoft.Transactions.TransactionBridge.CommitMessageRetry</span></span>
<span data-ttu-id="e1c54-103">Do uczestnika, który nie odpowiada, wysłano ponowną próbę komunikatu zatwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="e1c54-103">A commit message retry was sent to an unresponsive participant.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e1c54-104">Opis</span><span class="sxs-lookup"><span data-stu-id="e1c54-104">Description</span></span>  
 <span data-ttu-id="e1c54-105">Śledzony, jeśli lokalny Menedżer transakcji jest wymagany do ponownego wysłania komunikatu zatwierdzenia do uczestnika podrzędnego, ponieważ nie otrzymał odpowiedzi w danym czasie.</span><span class="sxs-lookup"><span data-stu-id="e1c54-105">Traced if the local Transaction Manager needed to resend a Commit message to a subordinate participant because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="e1c54-106">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="e1c54-106">Troubleshooting</span></span>  
 <span data-ttu-id="e1c54-107">Zbadaj potencjalne problemy z siecią lub produktem, które uniemożliwiają dostarczenie odpowiedzi na czas.</span><span class="sxs-lookup"><span data-stu-id="e1c54-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="e1c54-108">Jeśli jest widocznych wiele z tych komunikatów, może to oznaczać problemy z infrastrukturą lub czasy nietypowej odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="e1c54-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="e1c54-109">Oba problemy znacząco zmniejszają przepływność transakcji w ramach systemu.</span><span class="sxs-lookup"><span data-stu-id="e1c54-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1c54-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e1c54-110">See also</span></span>

- [<span data-ttu-id="e1c54-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="e1c54-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="e1c54-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="e1c54-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="e1c54-113">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="e1c54-113">Administration and Diagnostics</span></span>](../index.md)
