---
title: Microsoft.Transactions.TransactionBridge.PreparedMessageRetry
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2194292d-bf5f-4aef-9336-cd3c4795cb71
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 88ee90abb10e9f5e09deecb3d3d66c54dc289592
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgepreparedmessageretry"></a><span data-ttu-id="9cf09-102">Microsoft.Transactions.TransactionBridge.PreparedMessageRetry</span><span class="sxs-lookup"><span data-stu-id="9cf09-102">Microsoft.Transactions.TransactionBridge.PreparedMessageRetry</span></span>
<span data-ttu-id="9cf09-103">Do koordynatora, który nie odpowiada, wysłano ponowną próbę komunikatu przygotowania.</span><span class="sxs-lookup"><span data-stu-id="9cf09-103">A prepared message retry was sent to an unresponsive coordinator.</span></span>  
  
## <a name="description"></a><span data-ttu-id="9cf09-104">Opis</span><span class="sxs-lookup"><span data-stu-id="9cf09-104">Description</span></span>  
 <span data-ttu-id="9cf09-105">Śledzone w razie potrzeby lokalnego Menedżera transakcji do ponownego wysłania komunikatu przygotowania do koordynatora wyższego poziomu, ponieważ nie otrzymano odpowiedzi w określonym czasie /</span><span class="sxs-lookup"><span data-stu-id="9cf09-105">Traced if the local Transaction Manager needed to resend a Prepared message to a superior coordinator because it did not receive a response in a given amount of time/</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="9cf09-106">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="9cf09-106">Troubleshooting</span></span>  
 <span data-ttu-id="9cf09-107">Badania potencjalnych sieci lub produktu problemy, które uniemożliwiają dostarczanie na czas odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="9cf09-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="9cf09-108">Jeśli wiele z tych wiadomości są widoczne, może to oznaczać problemy związane z infrastrukturą lub nieprawidłowo długich czasów odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="9cf09-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="9cf09-109">Problemy z obu znacząco zmniejsza przepływność transakcji w systemie.</span><span class="sxs-lookup"><span data-stu-id="9cf09-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cf09-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9cf09-110">See Also</span></span>  
 [<span data-ttu-id="9cf09-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="9cf09-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="9cf09-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="9cf09-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="9cf09-113">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="9cf09-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
