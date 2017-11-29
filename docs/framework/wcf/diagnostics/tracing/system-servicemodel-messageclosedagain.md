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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7f3963fe28ccaf55b3946254e395b770619c8f22
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelmessageclosedagain"></a><span data-ttu-id="cc843-102">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="cc843-102">System.ServiceModel.MessageClosedAgain</span></span>
<span data-ttu-id="cc843-103">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="cc843-103">System.ServiceModel.MessageClosedAgain</span></span>  
  
## <a name="description"></a><span data-ttu-id="cc843-104">Opis</span><span class="sxs-lookup"><span data-stu-id="cc843-104">Description</span></span>  
 <span data-ttu-id="cc843-105">Zamknięto wiadomość ponownie.</span><span class="sxs-lookup"><span data-stu-id="cc843-105">A message was closed again.</span></span>  
  
 <span data-ttu-id="cc843-106">Komunikat powinien zostać zamknięty, tylko raz.</span><span class="sxs-lookup"><span data-stu-id="cc843-106">A message should be closed only once.</span></span> <span data-ttu-id="cc843-107">Trwa wysyłanego tego śledzenia w kodzie użytkownika rozszerzenia wskazuje, że kod rozszerzenia użytkownika zostanie zamknięty komunikat, który został już zamknięty.</span><span class="sxs-lookup"><span data-stu-id="cc843-107">If this trace is being emitted in user extension code, it indicates that the user extension code is closing a message that has already been closed.</span></span> <span data-ttu-id="cc843-108">Ślad jest są emitowane przez kod produktu, wskazuje, że kod rozszerzenia użytkownika może potencjalnie można zamknięcia komunikat zbyt wcześnie.</span><span class="sxs-lookup"><span data-stu-id="cc843-108">If this trace is being emitted through product code, it indicates that the user extension code could potentially be closing a message too early.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc843-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cc843-109">See Also</span></span>  
 [<span data-ttu-id="cc843-110">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="cc843-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="cc843-111">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="cc843-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="cc843-112">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="cc843-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
