---
title: 'Najlepsze praktyki: Elementy pośredniczące'
ms.date: 03/30/2017
ms.assetid: 2d41b337-8132-4ac2-bea2-6e9ae2f00f8d
ms.openlocfilehash: 8b0e0e635c0e790b342115b988905ba29a6b8ad1
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2018
ms.locfileid: "52296407"
---
# <a name="best-practices-intermediaries"></a><span data-ttu-id="3fb28-102">Najlepsze praktyki: Elementy pośredniczące</span><span class="sxs-lookup"><span data-stu-id="3fb28-102">Best Practices: Intermediaries</span></span>
<span data-ttu-id="3fb28-103">Należy uważać, aby poprawnie obsługi błędów podczas wywoływania pośredników, aby upewnić się, że kanały po stronie usługi na pośrednika są prawidłowo zamknięte.</span><span class="sxs-lookup"><span data-stu-id="3fb28-103">Care must be taken to handle faults correctly when calling intermediaries to make sure service side channels on the intermediary are closed properly.</span></span>  
  
 <span data-ttu-id="3fb28-104">Rozważmy następujący scenariusz.</span><span class="sxs-lookup"><span data-stu-id="3fb28-104">Consider the following scenario.</span></span> <span data-ttu-id="3fb28-105">Klient wysyła wywołania pośrednika, która następnie wywołuje usługi zaplecza.</span><span class="sxs-lookup"><span data-stu-id="3fb28-105">A client makes a call to an intermediary which then calls a back-end service.</span></span>  <span data-ttu-id="3fb28-106">Usługi zaplecza definiuje kontrakt nie błędów, więc żadnych błędów zgłaszane z tej usługi będzie traktowane jako błąd bez.</span><span class="sxs-lookup"><span data-stu-id="3fb28-106">The back-end service defines no fault contract, so any fault thrown from that service will be treated as an un-typed fault.</span></span>  <span data-ttu-id="3fb28-107">Zgłasza usługi zaplecza <xref:System.ApplicationException> i WCF poprawnie przerywa kanału po stronie usługi.</span><span class="sxs-lookup"><span data-stu-id="3fb28-107">The back-end service throws an <xref:System.ApplicationException> and WCF correctly aborts the service-side channel.</span></span> <span data-ttu-id="3fb28-108"><xref:System.ApplicationException> Następnie powierzchnie <xref:System.ServiceModel.FaultException> , jest zgłaszany do pośrednik.</span><span class="sxs-lookup"><span data-stu-id="3fb28-108">The <xref:System.ApplicationException> then surfaces as a <xref:System.ServiceModel.FaultException> that is thrown to the intermediary.</span></span> <span data-ttu-id="3fb28-109">Generuje ponownie pośrednik <xref:System.ApplicationException>.</span><span class="sxs-lookup"><span data-stu-id="3fb28-109">The intermediary re-throws the <xref:System.ApplicationException>.</span></span> <span data-ttu-id="3fb28-110">Usługi WCF interpretuje to jako bez błędów, z pośrednik i przekazuje go do klienta.</span><span class="sxs-lookup"><span data-stu-id="3fb28-110">WCF interprets this as an un-typed fault from the intermediary and forwards it on to the client.</span></span> <span data-ttu-id="3fb28-111">Po odebraniu usterki, zarówno klient, jak i pośrednik błędów ich kanały po stronie klienta.</span><span class="sxs-lookup"><span data-stu-id="3fb28-111">Upon receiving the fault, both the intermediary and the client fault their client-side channels.</span></span> <span data-ttu-id="3fb28-112">Kanału po stronie usługi pośrednika jednak pozostaje otwarty, ponieważ usługi WCF nie wie, że błąd jest krytyczny.</span><span class="sxs-lookup"><span data-stu-id="3fb28-112">The intermediary’s service-side channel however remains open because WCF doesn’t know the fault is fatal.</span></span>  
  
 <span data-ttu-id="3fb28-113">Najlepszym rozwiązaniem, w tym scenariuszu jest wykryć, czy błędów pochodzące z usługi jest krytyczny, a jeśli więc pośrednik powinien błędów kanału po stronie usługi, jak pokazano w poniższym fragmencie kodu.</span><span class="sxs-lookup"><span data-stu-id="3fb28-113">The best practice in this scenario is to detect if the fault coming from the service is fatal and if so the intermediary should fault its service-side channel as shown in the following code snippet.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3fb28-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3fb28-114">See Also</span></span>  
 [<span data-ttu-id="3fb28-115">Obsługa błędów programu WCF</span><span class="sxs-lookup"><span data-stu-id="3fb28-115">WCF Error Handling</span></span>](../../../docs/framework/wcf/wcf-error-handling.md)  
 [<span data-ttu-id="3fb28-116">Określanie i obsługa błędów w kontraktach i usługach</span><span class="sxs-lookup"><span data-stu-id="3fb28-116">Specifying and Handling Faults in Contracts and Services</span></span>](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
