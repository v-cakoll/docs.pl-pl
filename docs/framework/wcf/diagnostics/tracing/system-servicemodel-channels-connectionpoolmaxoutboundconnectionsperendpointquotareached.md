---
title: Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b9f5139-e122-4716-9ef7-2f38e1813993
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5fa64c87bc4cd0c8dc677d8b4c59de45e31d3270
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgeenlisttransactionfailure"></a><span data-ttu-id="ebacf-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span><span class="sxs-lookup"><span data-stu-id="ebacf-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span></span>
<span data-ttu-id="ebacf-103">Usługa protokołu WS-AT nie można zarejestrować transakcji za pomocą dostępnego kontekstu koordynacji.</span><span class="sxs-lookup"><span data-stu-id="ebacf-103">The WS-AT protocol service failed to enlist on a transaction using the provided coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ebacf-104">Opis</span><span class="sxs-lookup"><span data-stu-id="ebacf-104">Description</span></span>  
 <span data-ttu-id="ebacf-105">Śledzone po nie można zarejestrować transakcji dla protokołu podanego 2pc usługi MSDTC.</span><span class="sxs-lookup"><span data-stu-id="ebacf-105">Traced when MSDTC is unable to enlist on a transaction for a given 2pc protocol.</span></span>  <span data-ttu-id="ebacf-106">Może to nastąpić, ponieważ transakcja nie istnieje, rejestrowanie nie jest dozwolony lub są już zbyt wiele rejestracji.</span><span class="sxs-lookup"><span data-stu-id="ebacf-106">This can happen because the transaction no longer exists, enlisting is no longer allowed, or too many enlistments are already present.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="ebacf-107">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="ebacf-107">Troubleshooting</span></span>  
 <span data-ttu-id="ebacf-108">Sprawdź, czy ciąg stanu w komunikat śledzenia do ustalenia, czy istnieje dowolny element przydatnych wyników.</span><span class="sxs-lookup"><span data-stu-id="ebacf-108">Inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebacf-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ebacf-109">See Also</span></span>  
 [<span data-ttu-id="ebacf-110">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="ebacf-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="ebacf-111">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="ebacf-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="ebacf-112">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="ebacf-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
