---
title: Microsoft.Transactions.TransactionBridge.PrepareMessageRetry
ms.date: 03/30/2017
ms.assetid: ada4baa5-b60d-46b8-ad46-4d69f8d8a9fa
ms.openlocfilehash: affa647b30dbeb9237e4c20ebb441645eda94276
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="microsofttransactionstransactionbridgepreparemessageretry"></a><span data-ttu-id="34d18-102">Microsoft.Transactions.TransactionBridge.PrepareMessageRetry</span><span class="sxs-lookup"><span data-stu-id="34d18-102">Microsoft.Transactions.TransactionBridge.PrepareMessageRetry</span></span>
<span data-ttu-id="34d18-103">Do uczestnika, który nie odpowiada, wysłano ponowną próbę komunikatu przygotowania.</span><span class="sxs-lookup"><span data-stu-id="34d18-103">A prepare message retry was sent to an unresponsive participant.</span></span>  
  
## <a name="description"></a><span data-ttu-id="34d18-104">Opis</span><span class="sxs-lookup"><span data-stu-id="34d18-104">Description</span></span>  
 <span data-ttu-id="34d18-105">Śledzone w razie potrzeby lokalnego Menedżera transakcji do wysłania wiadomości przygotowanie do uczestnika podrzędnych, ponieważ nie otrzymano odpowiedzi w określonym czasie.</span><span class="sxs-lookup"><span data-stu-id="34d18-105">Traced if the local Transaction Manager needed to resend a Prepare message to a subordinate participant because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="34d18-106">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="34d18-106">Troubleshooting</span></span>  
 <span data-ttu-id="34d18-107">Badania potencjalnych sieci lub produktu problemy, które uniemożliwiają dostarczanie na czas odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="34d18-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="34d18-108">Jeśli wiele z tych wiadomości są widoczne, może to oznaczać problemy związane z infrastrukturą lub nieprawidłowo długich czasów odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="34d18-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="34d18-109">Problemy z obu uproszczenia przepływności transakcji w systemie.</span><span class="sxs-lookup"><span data-stu-id="34d18-109">Both issues can drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34d18-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="34d18-110">See Also</span></span>  
 [<span data-ttu-id="34d18-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="34d18-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="34d18-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="34d18-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="34d18-113">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="34d18-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
