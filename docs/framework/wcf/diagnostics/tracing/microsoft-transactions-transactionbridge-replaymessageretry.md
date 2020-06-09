---
title: Microsoft.Transactions.TransactionBridge.ReplayMessageRetry
ms.date: 03/30/2017
ms.assetid: e5b820ae-504d-405a-926a-9effa41d2369
ms.openlocfilehash: 162452d5d12859571d78ef19cf1d838953ee7acd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596210"
---
# <a name="microsofttransactionstransactionbridgereplaymessageretry"></a><span data-ttu-id="7b21b-102">Microsoft.Transactions.TransactionBridge.ReplayMessageRetry</span><span class="sxs-lookup"><span data-stu-id="7b21b-102">Microsoft.Transactions.TransactionBridge.ReplayMessageRetry</span></span>
<span data-ttu-id="7b21b-103">Do koordynatora, który nie odpowiada, wysłano ponowną próbę komunikatu powtórzenia.</span><span class="sxs-lookup"><span data-stu-id="7b21b-103">A replay message retry was sent to an unresponsive coordinator.</span></span>  
  
## <a name="description"></a><span data-ttu-id="7b21b-104">Opis</span><span class="sxs-lookup"><span data-stu-id="7b21b-104">Description</span></span>  
 <span data-ttu-id="7b21b-105">Śledzony, jeśli lokalny Menedżer transakcji jest wymagany do ponownego wysłania komunikatu powtarzania do koordynatora wyższego, ponieważ nie otrzymał odpowiedzi w danym czasie.</span><span class="sxs-lookup"><span data-stu-id="7b21b-105">Traced if the local Transaction Manager needed to resend a Replay message to a superior coordinator because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="7b21b-106">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="7b21b-106">Troubleshooting</span></span>  
 <span data-ttu-id="7b21b-107">Zbadaj potencjalne problemy z siecią lub produktem, które uniemożliwiają dostarczenie odpowiedzi na czas.</span><span class="sxs-lookup"><span data-stu-id="7b21b-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="7b21b-108">Jeśli jest widocznych wiele z tych komunikatów, może to oznaczać problemy z infrastrukturą lub czasy nietypowej odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="7b21b-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="7b21b-109">Oba problemy znacząco zmniejszają przepływność transakcji w ramach systemu.</span><span class="sxs-lookup"><span data-stu-id="7b21b-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b21b-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7b21b-110">See also</span></span>

- [<span data-ttu-id="7b21b-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="7b21b-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="7b21b-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="7b21b-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="7b21b-113">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="7b21b-113">Administration and Diagnostics</span></span>](../index.md)
