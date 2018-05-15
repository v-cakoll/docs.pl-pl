---
title: System.ServiceModel.MessageClosedAgain
ms.date: 03/30/2017
ms.assetid: 24c274d4-65cd-4c91-9869-bc6eb34ef979
ms.openlocfilehash: 3a73834888ae4a8945bd71492d787e23868fa5e8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="systemservicemodelmessageclosedagain"></a><span data-ttu-id="c09c9-102">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="c09c9-102">System.ServiceModel.MessageClosedAgain</span></span>
<span data-ttu-id="c09c9-103">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="c09c9-103">System.ServiceModel.MessageClosedAgain</span></span>  
  
## <a name="description"></a><span data-ttu-id="c09c9-104">Opis</span><span class="sxs-lookup"><span data-stu-id="c09c9-104">Description</span></span>  
 <span data-ttu-id="c09c9-105">Zamknięto wiadomość ponownie.</span><span class="sxs-lookup"><span data-stu-id="c09c9-105">A message was closed again.</span></span>  
  
 <span data-ttu-id="c09c9-106">Komunikat powinien zostać zamknięty, tylko raz.</span><span class="sxs-lookup"><span data-stu-id="c09c9-106">A message should be closed only once.</span></span> <span data-ttu-id="c09c9-107">Trwa wysyłanego tego śledzenia w kodzie użytkownika rozszerzenia wskazuje, że kod rozszerzenia użytkownika zostanie zamknięty komunikat, który został już zamknięty.</span><span class="sxs-lookup"><span data-stu-id="c09c9-107">If this trace is being emitted in user extension code, it indicates that the user extension code is closing a message that has already been closed.</span></span> <span data-ttu-id="c09c9-108">Ślad jest są emitowane przez kod produktu, wskazuje, że kod rozszerzenia użytkownika może potencjalnie można zamknięcia komunikat zbyt wcześnie.</span><span class="sxs-lookup"><span data-stu-id="c09c9-108">If this trace is being emitted through product code, it indicates that the user extension code could potentially be closing a message too early.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c09c9-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c09c9-109">See Also</span></span>  
 [<span data-ttu-id="c09c9-110">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="c09c9-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="c09c9-111">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="c09c9-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="c09c9-112">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="c09c9-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
