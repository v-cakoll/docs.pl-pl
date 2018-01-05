---
title: System.ServiceModel.MessageClosedAgain
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24c274d4-65cd-4c91-9869-bc6eb34ef979
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 57500bf3c66c0aec47150bb21cc8871738d4b72d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelmessageclosedagain"></a><span data-ttu-id="eedd6-102">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="eedd6-102">System.ServiceModel.MessageClosedAgain</span></span>
<span data-ttu-id="eedd6-103">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="eedd6-103">System.ServiceModel.MessageClosedAgain</span></span>  
  
## <a name="description"></a><span data-ttu-id="eedd6-104">Opis</span><span class="sxs-lookup"><span data-stu-id="eedd6-104">Description</span></span>  
 <span data-ttu-id="eedd6-105">Zamknięto wiadomość ponownie.</span><span class="sxs-lookup"><span data-stu-id="eedd6-105">A message was closed again.</span></span>  
  
 <span data-ttu-id="eedd6-106">Komunikat powinien zostać zamknięty, tylko raz.</span><span class="sxs-lookup"><span data-stu-id="eedd6-106">A message should be closed only once.</span></span> <span data-ttu-id="eedd6-107">Trwa wysyłanego tego śledzenia w kodzie użytkownika rozszerzenia wskazuje, że kod rozszerzenia użytkownika zostanie zamknięty komunikat, który został już zamknięty.</span><span class="sxs-lookup"><span data-stu-id="eedd6-107">If this trace is being emitted in user extension code, it indicates that the user extension code is closing a message that has already been closed.</span></span> <span data-ttu-id="eedd6-108">Ślad jest są emitowane przez kod produktu, wskazuje, że kod rozszerzenia użytkownika może potencjalnie można zamknięcia komunikat zbyt wcześnie.</span><span class="sxs-lookup"><span data-stu-id="eedd6-108">If this trace is being emitted through product code, it indicates that the user extension code could potentially be closing a message too early.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eedd6-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eedd6-109">See Also</span></span>  
 [<span data-ttu-id="eedd6-110">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="eedd6-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="eedd6-111">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="eedd6-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="eedd6-112">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="eedd6-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
