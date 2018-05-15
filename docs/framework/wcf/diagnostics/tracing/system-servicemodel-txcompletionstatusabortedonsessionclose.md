---
title: System.ServiceModel.TxCompletionStatusAbortedOnSessionClose
ms.date: 03/30/2017
ms.assetid: 7e142e9d-e81b-4309-974a-02e9cc064ea0
ms.openlocfilehash: 7ecc70f1c4d7184401dd29908968f628f2e6792a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="systemservicemodeltxcompletionstatusabortedonsessionclose"></a><span data-ttu-id="e2ecc-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="e2ecc-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span></span>
<span data-ttu-id="e2ecc-103">Określona transakcja została przerwana, ponieważ była niezakończona podczas zamykania sesji i TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute została ustawiona na false.</span><span class="sxs-lookup"><span data-stu-id="e2ecc-103">The specified transaction was aborted because it was uncompleted when the session was closed and the TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute was set to false.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e2ecc-104">Opis</span><span class="sxs-lookup"><span data-stu-id="e2ecc-104">Description</span></span>  
 <span data-ttu-id="e2ecc-105">Śledzone, jeśli bieżąca aktywna sesja została zamknięta i transakcja nie została ukończona, a ma ustawioną wartość TransactionAutoCompleteOnSessionClose `false`.</span><span class="sxs-lookup"><span data-stu-id="e2ecc-105">Traced if the current active session was closed, and the transaction was not completed, and TransactionAutoCompleteOnSessionClose is set to `false`.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="e2ecc-106">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="e2ecc-106">Troubleshooting</span></span>  
 <span data-ttu-id="e2ecc-107">Ślad wskazuje potencjalnych błędów aplikacji, które należy zbadać.</span><span class="sxs-lookup"><span data-stu-id="e2ecc-107">This trace indicates a potential application bug that should be investigated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2ecc-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e2ecc-108">See Also</span></span>  
 [<span data-ttu-id="e2ecc-109">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="e2ecc-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="e2ecc-110">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="e2ecc-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="e2ecc-111">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="e2ecc-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
