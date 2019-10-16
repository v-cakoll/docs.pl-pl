---
title: 'Najlepsze praktyki: Elementy pośredniczące'
ms.date: 03/30/2017
ms.assetid: 2d41b337-8132-4ac2-bea2-6e9ae2f00f8d
ms.openlocfilehash: a7c037b5942a404b1ff790638979a8e430394151
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320801"
---
# <a name="best-practices-intermediaries"></a><span data-ttu-id="bd94d-102">Najlepsze praktyki: Elementy pośredniczące</span><span class="sxs-lookup"><span data-stu-id="bd94d-102">Best Practices: Intermediaries</span></span>
<span data-ttu-id="bd94d-103">Należy zachować ostrożność w celu prawidłowego obsługi błędów podczas wywoływania pośredników, aby upewnić się, że kanały po stronie usługi na pośrednim są poprawnie zamknięte.</span><span class="sxs-lookup"><span data-stu-id="bd94d-103">Care must be taken to handle faults correctly when calling intermediaries to make sure service side channels on the intermediary are closed properly.</span></span>  
  
 <span data-ttu-id="bd94d-104">Rozważmy następujący scenariusz.</span><span class="sxs-lookup"><span data-stu-id="bd94d-104">Consider the following scenario.</span></span> <span data-ttu-id="bd94d-105">Klient wysyła wywołanie do pośrednika, które następnie wywołuje usługę zaplecza.</span><span class="sxs-lookup"><span data-stu-id="bd94d-105">A client makes a call to an intermediary which then calls a back-end service.</span></span>  <span data-ttu-id="bd94d-106">Usługa zaplecza nie definiuje kontraktu błędów, więc wszelkie błędy zgłoszone przez tę usługę będą traktowane jako błąd nieokreślony.</span><span class="sxs-lookup"><span data-stu-id="bd94d-106">The back-end service defines no fault contract, so any fault thrown from that service will be treated as an un-typed fault.</span></span>  <span data-ttu-id="bd94d-107">Usługa zaplecza zgłasza <xref:System.ApplicationException>, a funkcja WCF prawidłowo przerywa kanał po stronie usługi.</span><span class="sxs-lookup"><span data-stu-id="bd94d-107">The back-end service throws an <xref:System.ApplicationException> and WCF correctly aborts the service-side channel.</span></span> <span data-ttu-id="bd94d-108">@No__t-0 następnie powierzchnie jako <xref:System.ServiceModel.FaultException>, które są generowane do pośrednika.</span><span class="sxs-lookup"><span data-stu-id="bd94d-108">The <xref:System.ApplicationException> then surfaces as a <xref:System.ServiceModel.FaultException> that is thrown to the intermediary.</span></span> <span data-ttu-id="bd94d-109">Pośrednika zgłasza <xref:System.ApplicationException>.</span><span class="sxs-lookup"><span data-stu-id="bd94d-109">The intermediary re-throws the <xref:System.ApplicationException>.</span></span> <span data-ttu-id="bd94d-110">Funkcja WCF interpretuje ją jako błąd nieokreślony z pośrednich i przekazuje je do klienta.</span><span class="sxs-lookup"><span data-stu-id="bd94d-110">WCF interprets this as an un-typed fault from the intermediary and forwards it on to the client.</span></span> <span data-ttu-id="bd94d-111">Po otrzymaniu błędu zarówno pośrednika, jak i błąd klienta ich kanałów po stronie klienta.</span><span class="sxs-lookup"><span data-stu-id="bd94d-111">Upon receiving the fault, both the intermediary and the client fault their client-side channels.</span></span> <span data-ttu-id="bd94d-112">Kanał po stronie usług pośrednika pozostanie otwarty, ponieważ platforma WCF nie wie, że błąd jest krytyczny.</span><span class="sxs-lookup"><span data-stu-id="bd94d-112">The intermediary’s service-side channel however remains open because WCF doesn’t know the fault is fatal.</span></span>  
  
 <span data-ttu-id="bd94d-113">Najlepszym rozwiązaniem w tym scenariuszu jest wykrycie, czy błąd pochodzący z usługi jest krytyczny, a jeśli tak, pośrednik powinien spowodować błąd swojego kanału po stronie usługi, jak pokazano w poniższym fragmencie kodu.</span><span class="sxs-lookup"><span data-stu-id="bd94d-113">The best practice in this scenario is to detect if the fault coming from the service is fatal and if so the intermediary should fault its service-side channel as shown in the following code snippet.</span></span>  
  
```csharp  
catch (Exception e)  
{  
    bool faulted = service.State == CommunicationState.Faulted;  
    service.Abort();  
    if (faulted)  
    {  
        throw new ApplicationException(e.Message);  
    }  
    else  
    {  
        throw;  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="bd94d-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bd94d-114">See also</span></span>

- [<span data-ttu-id="bd94d-115">Obsługa błędów programu WCF</span><span class="sxs-lookup"><span data-stu-id="bd94d-115">WCF Error Handling</span></span>](wcf-error-handling.md)
- [<span data-ttu-id="bd94d-116">Określanie i obsługa błędów w kontraktach i usługach</span><span class="sxs-lookup"><span data-stu-id="bd94d-116">Specifying and Handling Faults in Contracts and Services</span></span>](specifying-and-handling-faults-in-contracts-and-services.md)
