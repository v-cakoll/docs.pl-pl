---
title: System.ServiceModel.TxFailedToNegotiateOleTx
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f0f0b4b-a1ad-4704-8329-455daf54892d
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6c0e688e1f24171494b4adaae964ac1fc2be2309
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodeltxfailedtonegotiateoletx"></a><span data-ttu-id="57b1c-102">System.ServiceModel.TxFailedToNegotiateOleTx</span><span class="sxs-lookup"><span data-stu-id="57b1c-102">System.ServiceModel.TxFailedToNegotiateOleTx</span></span>
<span data-ttu-id="57b1c-103">Nie negocjacji protokołu OleTransactions dla kontekstu koordynacji określony.</span><span class="sxs-lookup"><span data-stu-id="57b1c-103">The OleTransactions protocol negotiation failed to complete for the specified coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="57b1c-104">Opis</span><span class="sxs-lookup"><span data-stu-id="57b1c-104">Description</span></span>  
 <span data-ttu-id="57b1c-105">Śledzone podczas transakcji przychodzącej z informacjami o OleTx nie może użyć dołączone informacje OleTx i będzie awaryjne można zamiast niego protokołu WS-AT.</span><span class="sxs-lookup"><span data-stu-id="57b1c-105">Traced when an incoming transaction with OleTx information is unable to use the attached OleTx information, and will fall-back to using WS-AT instead.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="57b1c-106">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="57b1c-106">Troubleshooting</span></span>  
 <span data-ttu-id="57b1c-107">Wskazuje potencjalny problem z RPC usługi MSDTC komunikacji między komputerami.</span><span class="sxs-lookup"><span data-stu-id="57b1c-107">Indicates a potential problem with MSDTC RPC communication between the machines.</span></span> <span data-ttu-id="57b1c-108">Jeśli wiele z tych śladów pojawiają się w dzienniku, może spowodować radykalne spadek wydajności.</span><span class="sxs-lookup"><span data-stu-id="57b1c-108">If many of these traces appear in the log, a drastic decrease in performance can result.</span></span>  <span data-ttu-id="57b1c-109">Jeśli OleTx nie jest wymagana, ustaw `OleTxUpgradeEnabled` na 0 w konfiguracji rejestru WS-AT.</span><span class="sxs-lookup"><span data-stu-id="57b1c-109">If OleTx is not desired, set `OleTxUpgradeEnabled` to 0 in the WS-AT registry configuration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57b1c-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="57b1c-110">See Also</span></span>  
 [<span data-ttu-id="57b1c-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="57b1c-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="57b1c-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="57b1c-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="57b1c-113">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="57b1c-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
