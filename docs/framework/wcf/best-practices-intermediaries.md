---
title: 'Najlepsze rozwiązania: Elementy pośredniczące'
ms.date: 03/30/2017
ms.assetid: 2d41b337-8132-4ac2-bea2-6e9ae2f00f8d
ms.openlocfilehash: 0bd553486bfb89a0ec14c42a1bb7d2ed9c4c540d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59131732"
---
# <a name="best-practices-intermediaries"></a><span data-ttu-id="fbc39-102">Najlepsze rozwiązania: Elementy pośredniczące</span><span class="sxs-lookup"><span data-stu-id="fbc39-102">Best Practices: Intermediaries</span></span>
<span data-ttu-id="fbc39-103">Należy uważać, aby poprawnie obsługi błędów podczas wywoływania pośredników, aby upewnić się, że kanały po stronie usługi na pośrednika są prawidłowo zamknięte.</span><span class="sxs-lookup"><span data-stu-id="fbc39-103">Care must be taken to handle faults correctly when calling intermediaries to make sure service side channels on the intermediary are closed properly.</span></span>  
  
 <span data-ttu-id="fbc39-104">Rozważmy następujący scenariusz.</span><span class="sxs-lookup"><span data-stu-id="fbc39-104">Consider the following scenario.</span></span> <span data-ttu-id="fbc39-105">Klient wysyła wywołania pośrednika, która następnie wywołuje usługi zaplecza.</span><span class="sxs-lookup"><span data-stu-id="fbc39-105">A client makes a call to an intermediary which then calls a back-end service.</span></span>  <span data-ttu-id="fbc39-106">Usługi zaplecza definiuje kontrakt nie błędów, więc żadnych błędów zgłaszane z tej usługi będzie traktowane jako błąd bez.</span><span class="sxs-lookup"><span data-stu-id="fbc39-106">The back-end service defines no fault contract, so any fault thrown from that service will be treated as an un-typed fault.</span></span>  <span data-ttu-id="fbc39-107">Zgłasza usługi zaplecza <xref:System.ApplicationException> i WCF poprawnie przerywa kanału po stronie usługi.</span><span class="sxs-lookup"><span data-stu-id="fbc39-107">The back-end service throws an <xref:System.ApplicationException> and WCF correctly aborts the service-side channel.</span></span> <span data-ttu-id="fbc39-108"><xref:System.ApplicationException> Następnie powierzchnie <xref:System.ServiceModel.FaultException> , jest zgłaszany do pośrednik.</span><span class="sxs-lookup"><span data-stu-id="fbc39-108">The <xref:System.ApplicationException> then surfaces as a <xref:System.ServiceModel.FaultException> that is thrown to the intermediary.</span></span> <span data-ttu-id="fbc39-109">Generuje ponownie pośrednik <xref:System.ApplicationException>.</span><span class="sxs-lookup"><span data-stu-id="fbc39-109">The intermediary re-throws the <xref:System.ApplicationException>.</span></span> <span data-ttu-id="fbc39-110">Usługi WCF interpretuje to jako bez błędów, z pośrednik i przekazuje go do klienta.</span><span class="sxs-lookup"><span data-stu-id="fbc39-110">WCF interprets this as an un-typed fault from the intermediary and forwards it on to the client.</span></span> <span data-ttu-id="fbc39-111">Po odebraniu usterki, zarówno klient, jak i pośrednik błędów ich kanały po stronie klienta.</span><span class="sxs-lookup"><span data-stu-id="fbc39-111">Upon receiving the fault, both the intermediary and the client fault their client-side channels.</span></span> <span data-ttu-id="fbc39-112">Kanału po stronie usługi pośrednika jednak pozostaje otwarty, ponieważ usługi WCF nie wie, że błąd jest krytyczny.</span><span class="sxs-lookup"><span data-stu-id="fbc39-112">The intermediary’s service-side channel however remains open because WCF doesn’t know the fault is fatal.</span></span>  
  
 <span data-ttu-id="fbc39-113">Najlepszym rozwiązaniem, w tym scenariuszu jest wykryć, czy błędów pochodzące z usługi jest krytyczny, a jeśli więc pośrednik powinien błędów kanału po stronie usługi, jak pokazano w poniższym fragmencie kodu.</span><span class="sxs-lookup"><span data-stu-id="fbc39-113">The best practice in this scenario is to detect if the fault coming from the service is fatal and if so the intermediary should fault its service-side channel as shown in the following code snippet.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fbc39-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fbc39-114">See also</span></span>

- [<span data-ttu-id="fbc39-115">Obsługa błędów programu WCF</span><span class="sxs-lookup"><span data-stu-id="fbc39-115">WCF Error Handling</span></span>](../../../docs/framework/wcf/wcf-error-handling.md)
- [<span data-ttu-id="fbc39-116">Określanie i obsługa błędów w kontraktach i usługach</span><span class="sxs-lookup"><span data-stu-id="fbc39-116">Specifying and Handling Faults in Contracts and Services</span></span>](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
