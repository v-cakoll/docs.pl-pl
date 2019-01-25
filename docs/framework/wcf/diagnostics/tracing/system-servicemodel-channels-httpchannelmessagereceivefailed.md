---
title: System.ServiceModel.Channels.HttpChannelMessageReceiveFailed
ms.date: 03/30/2017
ms.assetid: 9eb311da-fdcc-4dd3-9d85-05b3280dfdda
ms.openlocfilehash: 22730ef8a0c0b4706f9e267fef251014a70a58fb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54720174"
---
# <a name="systemservicemodelchannelshttpchannelmessagereceivefailed"></a><span data-ttu-id="24385-102">System.ServiceModel.Channels.HttpChannelMessageReceiveFailed</span><span class="sxs-lookup"><span data-stu-id="24385-102">System.ServiceModel.Channels.HttpChannelMessageReceiveFailed</span></span>
<span data-ttu-id="24385-103">Nie może odebrać komunikatu za pośrednictwem kanału protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="24385-103">Failed to receive a message over an HTTP channel.</span></span>  
  
## <a name="description"></a><span data-ttu-id="24385-104">Opis</span><span class="sxs-lookup"><span data-stu-id="24385-104">Description</span></span>  
 <span data-ttu-id="24385-105">Ślad może być emitowana jako ostrzeżenia lub błędu.</span><span class="sxs-lookup"><span data-stu-id="24385-105">This trace can be emitted as a warning or an error.</span></span> <span data-ttu-id="24385-106">W obu przypadkach śledzenia jest emitowane, gdy nie znaleziono niezgodny odbiornik dla przychodzących żądań HTTP i odrzucenia żądania HTTP.</span><span class="sxs-lookup"><span data-stu-id="24385-106">In both cases, the trace is emitted when a compatible listener is not found for an incoming HTTP request and the HTTP request is discarded.</span></span> <span data-ttu-id="24385-107">Może się to zdarzyć, ponieważ czasownik HTTP żądania nie został rozpoznany przez dowolnego odbiornika protokołu HTTP lub ponieważ brak odbiornika prowadził nasłuchiwanie na adresie żądania był przeznaczony dla.</span><span class="sxs-lookup"><span data-stu-id="24385-107">This could happen because the request’s HTTP verb was not recognized by any HTTP listener, or because no listener was listening on the address the request was targeted for.</span></span> <span data-ttu-id="24385-108">Śledzenia jest emitowane ostrzeżenie w przypadku Self-Hosted, jak i błąd, gdy usługa jest hostowana w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="24385-108">The trace is emitted as a warning in the self-hosted case, and as an error when the service is hosted in IIS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24385-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="24385-109">See also</span></span>
- [<span data-ttu-id="24385-110">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="24385-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="24385-111">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="24385-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="24385-112">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="24385-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
