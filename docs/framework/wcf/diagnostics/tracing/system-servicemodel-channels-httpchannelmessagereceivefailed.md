---
title: System.ServiceModel.Channels.HttpChannelMessageReceiveFailed
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9eb311da-fdcc-4dd3-9d85-05b3280dfdda
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1bbad8d743ff64aea923e7fbf62871e495253aea
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelchannelshttpchannelmessagereceivefailed"></a><span data-ttu-id="f8355-102">System.ServiceModel.Channels.HttpChannelMessageReceiveFailed</span><span class="sxs-lookup"><span data-stu-id="f8355-102">System.ServiceModel.Channels.HttpChannelMessageReceiveFailed</span></span>
<span data-ttu-id="f8355-103">Nie można odebrać wiadomości kanałem HTTP.</span><span class="sxs-lookup"><span data-stu-id="f8355-103">Failed to receive a message over an HTTP channel.</span></span>  
  
## <a name="description"></a><span data-ttu-id="f8355-104">Opis</span><span class="sxs-lookup"><span data-stu-id="f8355-104">Description</span></span>  
 <span data-ttu-id="f8355-105">Ślad może być wysyłany jako ostrzeżenia lub błędu.</span><span class="sxs-lookup"><span data-stu-id="f8355-105">This trace can be emitted as a warning or an error.</span></span> <span data-ttu-id="f8355-106">W obu przypadkach dane śledzenia są emitowane po zgodne odbiornik nie został znaleziony dla przychodzącego żądania HTTP i żądania HTTP są usuwane.</span><span class="sxs-lookup"><span data-stu-id="f8355-106">In both cases, the trace is emitted when a compatible listener is not found for an incoming HTTP request and the HTTP request is discarded.</span></span> <span data-ttu-id="f8355-107">Może się to zdarzyć, ponieważ zlecenie HTTP żądania nie został rozpoznany przez dowolnego odbiornik HTTP lub ponieważ odbiornik nie nasłuchuje na adresie żądania był przeznaczony dla.</span><span class="sxs-lookup"><span data-stu-id="f8355-107">This could happen because the request’s HTTP verb was not recognized by any HTTP listener, or because no listener was listening on the address the request was targeted for.</span></span> <span data-ttu-id="f8355-108">Śledzenie jest emitowany jako ostrzeżenia w przypadku hostowania samoobsługowego i jako błąd, kiedy usługa znajduje się w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="f8355-108">The trace is emitted as a warning in the self-hosted case, and as an error when the service is hosted in IIS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8355-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f8355-109">See Also</span></span>  
 [<span data-ttu-id="f8355-110">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="f8355-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="f8355-111">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="f8355-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="f8355-112">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="f8355-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
