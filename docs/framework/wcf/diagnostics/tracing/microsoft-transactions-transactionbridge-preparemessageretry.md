---
title: Microsoft.Transactions.TransactionBridge.PrepareMessageRetry
ms.date: 03/30/2017
ms.assetid: ada4baa5-b60d-46b8-ad46-4d69f8d8a9fa
ms.openlocfilehash: 0c53c1617f3aa3c5f16ba16e8ec548e46ce22137
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594338"
---
# <a name="microsofttransactionstransactionbridgepreparemessageretry"></a><span data-ttu-id="fa6e9-102">Microsoft.Transactions.TransactionBridge.PrepareMessageRetry</span><span class="sxs-lookup"><span data-stu-id="fa6e9-102">Microsoft.Transactions.TransactionBridge.PrepareMessageRetry</span></span>
<span data-ttu-id="fa6e9-103">Do uczestnika, który nie odpowiada, wysłano ponowną próbę komunikatu przygotowania.</span><span class="sxs-lookup"><span data-stu-id="fa6e9-103">A prepare message retry was sent to an unresponsive participant.</span></span>  
  
## <a name="description"></a><span data-ttu-id="fa6e9-104">Opis</span><span class="sxs-lookup"><span data-stu-id="fa6e9-104">Description</span></span>  
 <span data-ttu-id="fa6e9-105">Śledzony, jeśli lokalny Menedżer transakcji jest wymagany do ponownego wysłania komunikatu przygotowania do uczestnika podrzędnego, ponieważ nie otrzymał odpowiedzi w danym czasie.</span><span class="sxs-lookup"><span data-stu-id="fa6e9-105">Traced if the local Transaction Manager needed to resend a Prepare message to a subordinate participant because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="fa6e9-106">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="fa6e9-106">Troubleshooting</span></span>  
 <span data-ttu-id="fa6e9-107">Zbadaj potencjalne problemy z siecią lub produktem, które uniemożliwiają dostarczenie odpowiedzi na czas.</span><span class="sxs-lookup"><span data-stu-id="fa6e9-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="fa6e9-108">Jeśli jest widocznych wiele z tych komunikatów, może to oznaczać problemy z infrastrukturą lub czasy nietypowej odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="fa6e9-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="fa6e9-109">Oba problemy mogą znacząco zmniejszyć przepływność transakcji w ramach systemu.</span><span class="sxs-lookup"><span data-stu-id="fa6e9-109">Both issues can drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa6e9-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fa6e9-110">See also</span></span>

- [<span data-ttu-id="fa6e9-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="fa6e9-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="fa6e9-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="fa6e9-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="fa6e9-113">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="fa6e9-113">Administration and Diagnostics</span></span>](../index.md)
