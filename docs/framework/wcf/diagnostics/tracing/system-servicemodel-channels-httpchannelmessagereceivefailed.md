---
title: System.ServiceModel.Channels.HttpChannelMessageReceiveFailed
ms.date: 03/30/2017
ms.assetid: 9eb311da-fdcc-4dd3-9d85-05b3280dfdda
ms.openlocfilehash: b848963caff706ff8a886c1e358ad6688e9611c8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61666693"
---
# <a name="systemservicemodelchannelshttpchannelmessagereceivefailed"></a><span data-ttu-id="78dda-102">System.ServiceModel.Channels.HttpChannelMessageReceiveFailed</span><span class="sxs-lookup"><span data-stu-id="78dda-102">System.ServiceModel.Channels.HttpChannelMessageReceiveFailed</span></span>
<span data-ttu-id="78dda-103">Nie może odebrać komunikatu za pośrednictwem kanału protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="78dda-103">Failed to receive a message over an HTTP channel.</span></span>  
  
## <a name="description"></a><span data-ttu-id="78dda-104">Opis</span><span class="sxs-lookup"><span data-stu-id="78dda-104">Description</span></span>  
 <span data-ttu-id="78dda-105">Ślad może być emitowana jako ostrzeżenia lub błędu.</span><span class="sxs-lookup"><span data-stu-id="78dda-105">This trace can be emitted as a warning or an error.</span></span> <span data-ttu-id="78dda-106">W obu przypadkach śledzenia jest emitowane, gdy nie znaleziono niezgodny odbiornik dla przychodzących żądań HTTP i odrzucenia żądania HTTP.</span><span class="sxs-lookup"><span data-stu-id="78dda-106">In both cases, the trace is emitted when a compatible listener is not found for an incoming HTTP request and the HTTP request is discarded.</span></span> <span data-ttu-id="78dda-107">Może się to zdarzyć, ponieważ czasownik HTTP żądania nie został rozpoznany przez dowolnego odbiornika protokołu HTTP lub ponieważ brak odbiornika prowadził nasłuchiwanie na adresie żądania był przeznaczony dla.</span><span class="sxs-lookup"><span data-stu-id="78dda-107">This could happen because the request’s HTTP verb was not recognized by any HTTP listener, or because no listener was listening on the address the request was targeted for.</span></span> <span data-ttu-id="78dda-108">Śledzenia jest emitowane ostrzeżenie w przypadku Self-Hosted, jak i błąd, gdy usługa jest hostowana w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="78dda-108">The trace is emitted as a warning in the self-hosted case, and as an error when the service is hosted in IIS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78dda-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="78dda-109">See also</span></span>

- [<span data-ttu-id="78dda-110">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="78dda-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="78dda-111">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="78dda-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="78dda-112">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="78dda-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
