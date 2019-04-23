---
title: System.ServiceModel.TxFailedToNegotiateOleTx
ms.date: 03/30/2017
ms.assetid: 3f0f0b4b-a1ad-4704-8329-455daf54892d
ms.openlocfilehash: 2de1aa51d58d9d86f953e027fd3f7f172e3887d3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59097567"
---
# <a name="systemservicemodeltxfailedtonegotiateoletx"></a><span data-ttu-id="ce40f-102">System.ServiceModel.TxFailedToNegotiateOleTx</span><span class="sxs-lookup"><span data-stu-id="ce40f-102">System.ServiceModel.TxFailedToNegotiateOleTx</span></span>
<span data-ttu-id="ce40f-103">Negocjacji protokołu OleTransactions nie można ukończyć dla kontekstu określonego koordynacji.</span><span class="sxs-lookup"><span data-stu-id="ce40f-103">The OleTransactions protocol negotiation failed to complete for the specified coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ce40f-104">Opis</span><span class="sxs-lookup"><span data-stu-id="ce40f-104">Description</span></span>  
 <span data-ttu-id="ce40f-105">Śledzone transakcji przychodzących z informacjami o OleTx nie może użyć dołączone informacje OleTx, gdy będzie awaryjne za pomocą WS-AT zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="ce40f-105">Traced when an incoming transaction with OleTx information is unable to use the attached OleTx information, and will fall-back to using WS-AT instead.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="ce40f-106">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="ce40f-106">Troubleshooting</span></span>  
 <span data-ttu-id="ce40f-107">Wskazuje potencjalny problem za pomocą usługi MSDTC RPC łączności między maszynami.</span><span class="sxs-lookup"><span data-stu-id="ce40f-107">Indicates a potential problem with MSDTC RPC communication between the machines.</span></span> <span data-ttu-id="ce40f-108">Jeśli wiele ślady te pojawiają się w dzienniku, może to skutkować drastycznym spadku wydajności.</span><span class="sxs-lookup"><span data-stu-id="ce40f-108">If many of these traces appear in the log, a drastic decrease in performance can result.</span></span>  <span data-ttu-id="ce40f-109">Jeśli OleTx jest niepożądany, należy ustawić `OleTxUpgradeEnabled` na 0 w konfiguracji rejestru WS-AT.</span><span class="sxs-lookup"><span data-stu-id="ce40f-109">If OleTx is not desired, set `OleTxUpgradeEnabled` to 0 in the WS-AT registry configuration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce40f-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ce40f-110">See also</span></span>

- [<span data-ttu-id="ce40f-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="ce40f-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="ce40f-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="ce40f-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="ce40f-113">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="ce40f-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
