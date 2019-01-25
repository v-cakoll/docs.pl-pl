---
title: System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort
ms.date: 03/30/2017
ms.assetid: 155c3203-2e17-4709-b896-2254e22da45e
ms.openlocfilehash: 3d43524b7141a134b9560e92da66ef2349b8119a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54631288"
---
# <a name="systemservicemodeltxcompletionstatuscompletedforasyncabort"></a><span data-ttu-id="5f4a9-102">System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="5f4a9-102">System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort</span></span>
<span data-ttu-id="5f4a9-103">Określonej transakcji dla określonej operacji zostało zakończone z powodu przerwania asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="5f4a9-103">The specified transaction for the specified operation was completed due to asynchronous abort.</span></span>  
  
## <a name="description"></a><span data-ttu-id="5f4a9-104">Opis</span><span class="sxs-lookup"><span data-stu-id="5f4a9-104">Description</span></span>  
 <span data-ttu-id="5f4a9-105">Bieżąca transakcja została przerwana z powodu innej uczestnika oddanie głosu na przerwanie, limity czasu wystąpienia lub inny błąd wewnątrz uczestnika transakcji.</span><span class="sxs-lookup"><span data-stu-id="5f4a9-105">The current transaction was aborted due to another participant voting for Abort, time-outs occurring, or another error inside the participant of a transaction.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="5f4a9-106">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="5f4a9-106">Troubleshooting</span></span>  
 <span data-ttu-id="5f4a9-107">Jeśli to przerwania jest nieoczekiwana, sprawdź wszystkie dzienniki systemu, aby określić rzeczywistą powód przerwania.</span><span class="sxs-lookup"><span data-stu-id="5f4a9-107">If this abort is unexpected, check all system logs to determine the real reason for the abort.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f4a9-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5f4a9-108">See also</span></span>
- [<span data-ttu-id="5f4a9-109">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="5f4a9-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="5f4a9-110">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="5f4a9-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="5f4a9-111">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="5f4a9-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
