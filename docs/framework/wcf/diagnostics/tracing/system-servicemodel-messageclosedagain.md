---
title: System.ServiceModel.MessageClosedAgain
ms.date: 03/30/2017
ms.assetid: 24c274d4-65cd-4c91-9869-bc6eb34ef979
ms.openlocfilehash: a18355d55359df665d0e936ce95da34bf07aec6a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761510"
---
# <a name="systemservicemodelmessageclosedagain"></a><span data-ttu-id="8f7d2-102">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="8f7d2-102">System.ServiceModel.MessageClosedAgain</span></span>
<span data-ttu-id="8f7d2-103">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="8f7d2-103">System.ServiceModel.MessageClosedAgain</span></span>  
  
## <a name="description"></a><span data-ttu-id="8f7d2-104">Opis</span><span class="sxs-lookup"><span data-stu-id="8f7d2-104">Description</span></span>  
 <span data-ttu-id="8f7d2-105">Wiadomość została zamknięta, ponownie.</span><span class="sxs-lookup"><span data-stu-id="8f7d2-105">A message was closed again.</span></span>  
  
 <span data-ttu-id="8f7d2-106">Komunikat powinien zostać zamknięty, tylko raz.</span><span class="sxs-lookup"><span data-stu-id="8f7d2-106">A message should be closed only once.</span></span> <span data-ttu-id="8f7d2-107">Ta śledzenia jest emitowane w kodzie rozszerzenia użytkownika, wskazuje, że kod rozszerzenia użytkownika dobiega końca komunikat, który został już zamknięty.</span><span class="sxs-lookup"><span data-stu-id="8f7d2-107">If this trace is being emitted in user extension code, it indicates that the user extension code is closing a message that has already been closed.</span></span> <span data-ttu-id="8f7d2-108">Tego śledzenia jest emitowane przy użyciu kodu produktu, wskazuje, że kod rozszerzenia użytkownika może potencjalnie zamykać komunikat zbyt wczesny.</span><span class="sxs-lookup"><span data-stu-id="8f7d2-108">If this trace is being emitted through product code, it indicates that the user extension code could potentially be closing a message too early.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f7d2-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8f7d2-109">See also</span></span>

- [<span data-ttu-id="8f7d2-110">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="8f7d2-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="8f7d2-111">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="8f7d2-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="8f7d2-112">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="8f7d2-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
