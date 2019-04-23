---
title: System.ServiceModel.TxCompletionStatusAbortedOnSessionClose
ms.date: 03/30/2017
ms.assetid: 7e142e9d-e81b-4309-974a-02e9cc064ea0
ms.openlocfilehash: 7b1f6a2f4a344b566c76d0095942b84a8a4e76f6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59166507"
---
# <a name="systemservicemodeltxcompletionstatusabortedonsessionclose"></a><span data-ttu-id="60fb3-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="60fb3-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span></span>
<span data-ttu-id="60fb3-103">Określony transakcja została przerwana, ponieważ był niezakończonych modyfikacji, gdy sesja została zamknięta, a gdy TransactionAutoCompleteOnSessionClose została ustawiona na wartość false.</span><span class="sxs-lookup"><span data-stu-id="60fb3-103">The specified transaction was aborted because it was uncompleted when the session was closed and the TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute was set to false.</span></span>  
  
## <a name="description"></a><span data-ttu-id="60fb3-104">Opis</span><span class="sxs-lookup"><span data-stu-id="60fb3-104">Description</span></span>  
 <span data-ttu-id="60fb3-105">Śledzone bieżącej aktywnej sesji zostało zamknięte, transakcja nie została ukończona i jest równa TransactionAutoCompleteOnSessionClose `false`.</span><span class="sxs-lookup"><span data-stu-id="60fb3-105">Traced if the current active session was closed, and the transaction was not completed, and TransactionAutoCompleteOnSessionClose is set to `false`.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="60fb3-106">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="60fb3-106">Troubleshooting</span></span>  
 <span data-ttu-id="60fb3-107">Ślad wskazuje potencjalny błąd aplikacji, które należy zbadać.</span><span class="sxs-lookup"><span data-stu-id="60fb3-107">This trace indicates a potential application bug that should be investigated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60fb3-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="60fb3-108">See also</span></span>

- [<span data-ttu-id="60fb3-109">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="60fb3-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="60fb3-110">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="60fb3-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="60fb3-111">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="60fb3-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
