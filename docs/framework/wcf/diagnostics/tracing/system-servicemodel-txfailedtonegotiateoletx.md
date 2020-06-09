---
title: System.ServiceModel.TxFailedToNegotiateOleTx
ms.date: 03/30/2017
ms.assetid: 3f0f0b4b-a1ad-4704-8329-455daf54892d
ms.openlocfilehash: 2c9ea77cdd76d4593c2ee5b09a4b917677b8925f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601416"
---
# <a name="systemservicemodeltxfailedtonegotiateoletx"></a><span data-ttu-id="5b228-102">System.ServiceModel.TxFailedToNegotiateOleTx</span><span class="sxs-lookup"><span data-stu-id="5b228-102">System.ServiceModel.TxFailedToNegotiateOleTx</span></span>
<span data-ttu-id="5b228-103">Nie można ukończyć negocjacji protokołu OleTransactions dla określonego kontekstu koordynacji.</span><span class="sxs-lookup"><span data-stu-id="5b228-103">The OleTransactions protocol negotiation failed to complete for the specified coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="5b228-104">Opis</span><span class="sxs-lookup"><span data-stu-id="5b228-104">Description</span></span>  
 <span data-ttu-id="5b228-105">Śledzone w przypadku, gdy transakcja przychodząca z informacjami OleTx nie może używać dołączonych informacji OleTx i zostanie przywrócona w zamian przy użyciu protokołu WS-AT.</span><span class="sxs-lookup"><span data-stu-id="5b228-105">Traced when an incoming transaction with OleTx information is unable to use the attached OleTx information, and will fall-back to using WS-AT instead.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="5b228-106">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="5b228-106">Troubleshooting</span></span>  
 <span data-ttu-id="5b228-107">Wskazuje potencjalny problem z komunikacją RPC usługi MSDTC między maszynami.</span><span class="sxs-lookup"><span data-stu-id="5b228-107">Indicates a potential problem with MSDTC RPC communication between the machines.</span></span> <span data-ttu-id="5b228-108">Jeśli wiele z tych śladów jest wyświetlanych w dzienniku, może wynikać drastyczne zmniejszenie wydajności.</span><span class="sxs-lookup"><span data-stu-id="5b228-108">If many of these traces appear in the log, a drastic decrease in performance can result.</span></span>  <span data-ttu-id="5b228-109">Jeśli OleTx nie jest wymagana, ustaw wartość `OleTxUpgradeEnabled` 0 w konfiguracji rejestru WS-AT.</span><span class="sxs-lookup"><span data-stu-id="5b228-109">If OleTx is not desired, set `OleTxUpgradeEnabled` to 0 in the WS-AT registry configuration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b228-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5b228-110">See also</span></span>

- [<span data-ttu-id="5b228-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="5b228-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="5b228-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="5b228-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="5b228-113">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="5b228-113">Administration and Diagnostics</span></span>](../index.md)
