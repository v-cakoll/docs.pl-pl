---
title: System.ServiceModel.TxCompletionStatusAbortedOnSessionClose
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e142e9d-e81b-4309-974a-02e9cc064ea0
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1e9ab5af359b833452664f534e3627f477246fa6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodeltxcompletionstatusabortedonsessionclose"></a><span data-ttu-id="70f7d-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="70f7d-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span></span>
<span data-ttu-id="70f7d-103">Określona transakcja została przerwana, ponieważ była niezakończona podczas zamykania sesji i TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute została ustawiona na false.</span><span class="sxs-lookup"><span data-stu-id="70f7d-103">The specified transaction was aborted because it was uncompleted when the session was closed and the TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute was set to false.</span></span>  
  
## <a name="description"></a><span data-ttu-id="70f7d-104">Opis</span><span class="sxs-lookup"><span data-stu-id="70f7d-104">Description</span></span>  
 <span data-ttu-id="70f7d-105">Śledzone, jeśli bieżąca aktywna sesja została zamknięta i transakcja nie została ukończona, a ma ustawioną wartość TransactionAutoCompleteOnSessionClose `false`.</span><span class="sxs-lookup"><span data-stu-id="70f7d-105">Traced if the current active session was closed, and the transaction was not completed, and TransactionAutoCompleteOnSessionClose is set to `false`.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="70f7d-106">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="70f7d-106">Troubleshooting</span></span>  
 <span data-ttu-id="70f7d-107">Ślad wskazuje potencjalnych błędów aplikacji, które należy zbadać.</span><span class="sxs-lookup"><span data-stu-id="70f7d-107">This trace indicates a potential application bug that should be investigated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70f7d-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="70f7d-108">See Also</span></span>  
 [<span data-ttu-id="70f7d-109">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="70f7d-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="70f7d-110">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="70f7d-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="70f7d-111">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="70f7d-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
