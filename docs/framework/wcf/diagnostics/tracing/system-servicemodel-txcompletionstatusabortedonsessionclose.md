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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 695ebb2089147093601f2d51f11f11ca45861590
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodeltxcompletionstatusabortedonsessionclose"></a><span data-ttu-id="424cf-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="424cf-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span></span>
<span data-ttu-id="424cf-103">Określona transakcja została przerwana, ponieważ była niezakończona podczas zamykania sesji i TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute została ustawiona na false.</span><span class="sxs-lookup"><span data-stu-id="424cf-103">The specified transaction was aborted because it was uncompleted when the session was closed and the TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute was set to false.</span></span>  
  
## <a name="description"></a><span data-ttu-id="424cf-104">Opis</span><span class="sxs-lookup"><span data-stu-id="424cf-104">Description</span></span>  
 <span data-ttu-id="424cf-105">Śledzone, jeśli bieżąca aktywna sesja została zamknięta i transakcja nie została ukończona, a ma ustawioną wartość TransactionAutoCompleteOnSessionClose `false`.</span><span class="sxs-lookup"><span data-stu-id="424cf-105">Traced if the current active session was closed, and the transaction was not completed, and TransactionAutoCompleteOnSessionClose is set to `false`.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="424cf-106">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="424cf-106">Troubleshooting</span></span>  
 <span data-ttu-id="424cf-107">Ślad wskazuje potencjalnych błędów aplikacji, które należy zbadać.</span><span class="sxs-lookup"><span data-stu-id="424cf-107">This trace indicates a potential application bug that should be investigated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="424cf-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="424cf-108">See Also</span></span>  
 [<span data-ttu-id="424cf-109">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="424cf-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="424cf-110">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="424cf-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="424cf-111">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="424cf-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
