---
title: PiiLoggingNotAllowed
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc34a0b6-fee7-4da4-b146-b0c1c8b7519a
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0c96da5fe16c468e6ba4dedcdf377c23ba437f47
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="piiloggingnotallowed"></a><span data-ttu-id="e3b4e-102">PiiLoggingNotAllowed</span><span class="sxs-lookup"><span data-stu-id="e3b4e-102">PiiLoggingNotAllowed</span></span>
<span data-ttu-id="e3b4e-103">Identyfikator: 108</span><span class="sxs-lookup"><span data-stu-id="e3b4e-103">Id: 108</span></span>  
  
 <span data-ttu-id="e3b4e-104">Ważność: błąd</span><span class="sxs-lookup"><span data-stu-id="e3b4e-104">Severity: Error</span></span>  
  
 <span data-ttu-id="e3b4e-105">Kategoria: śledzenie</span><span class="sxs-lookup"><span data-stu-id="e3b4e-105">Category: Tracing</span></span>  
  
## <a name="description"></a><span data-ttu-id="e3b4e-106">Opis</span><span class="sxs-lookup"><span data-stu-id="e3b4e-106">Description</span></span>  
 <span data-ttu-id="e3b4e-107">To zdarzenie oznacza, że żadne znane dane osobowe nie są rejestrowane.</span><span class="sxs-lookup"><span data-stu-id="e3b4e-107">This event indicates that no known PII is being logged.</span></span> <span data-ttu-id="e3b4e-108">Rejestrowanie znanych danych nie jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="e3b4e-108">Logging of known PII is not allowed.</span></span> <span data-ttu-id="e3b4e-109">Aby zezwolić na rejestrowanie znanych danych osobowych, Ustaw "element enableLoggingKnownPii" `true` w pliku Machine.config. Zdarzenie Wyświetla nazwę procesu i identyfikatora procesu.</span><span class="sxs-lookup"><span data-stu-id="e3b4e-109">To allow logging of known PII, set "enableLoggingKnownPii" to `true` in Machine.config. The event lists the process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3b4e-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e3b4e-110">See Also</span></span>  
 [<span data-ttu-id="e3b4e-111">Rejestrowanie zdarzeń</span><span class="sxs-lookup"><span data-stu-id="e3b4e-111">Event Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)  
 [<span data-ttu-id="e3b4e-112">Informacje ogólne o zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="e3b4e-112">Events General Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
