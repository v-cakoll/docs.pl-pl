---
title: System.ServiceModel.TxCompletionStatusAbortedOnSessionClose
ms.date: 03/30/2017
ms.assetid: 7e142e9d-e81b-4309-974a-02e9cc064ea0
ms.openlocfilehash: 7b1f6a2f4a344b566c76d0095942b84a8a4e76f6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991630"
---
# <a name="systemservicemodeltxcompletionstatusabortedonsessionclose"></a><span data-ttu-id="7a5e9-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="7a5e9-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span></span>
<span data-ttu-id="7a5e9-103">Określony transakcja została przerwana, ponieważ był niezakończonych modyfikacji, gdy sesja została zamknięta, a gdy TransactionAutoCompleteOnSessionClose została ustawiona na wartość false.</span><span class="sxs-lookup"><span data-stu-id="7a5e9-103">The specified transaction was aborted because it was uncompleted when the session was closed and the TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute was set to false.</span></span>  
  
## <a name="description"></a><span data-ttu-id="7a5e9-104">Opis</span><span class="sxs-lookup"><span data-stu-id="7a5e9-104">Description</span></span>  
 <span data-ttu-id="7a5e9-105">Śledzone bieżącej aktywnej sesji zostało zamknięte, transakcja nie została ukończona i jest równa TransactionAutoCompleteOnSessionClose `false`.</span><span class="sxs-lookup"><span data-stu-id="7a5e9-105">Traced if the current active session was closed, and the transaction was not completed, and TransactionAutoCompleteOnSessionClose is set to `false`.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="7a5e9-106">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="7a5e9-106">Troubleshooting</span></span>  
 <span data-ttu-id="7a5e9-107">Ślad wskazuje potencjalny błąd aplikacji, które należy zbadać.</span><span class="sxs-lookup"><span data-stu-id="7a5e9-107">This trace indicates a potential application bug that should be investigated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a5e9-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7a5e9-108">See also</span></span>

- [<span data-ttu-id="7a5e9-109">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="7a5e9-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="7a5e9-110">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="7a5e9-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="7a5e9-111">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="7a5e9-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
