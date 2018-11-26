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
# <a name="best-practices-intermediaries"></a>Najlepsze praktyki: Elementy pośredniczące
Należy uważać, aby poprawnie obsługi błędów podczas wywoływania pośredników, aby upewnić się, że kanały po stronie usługi na pośrednika są prawidłowo zamknięte.  
  
 Rozważmy następujący scenariusz. Klient wysyła wywołania pośrednika, która następnie wywołuje usługi zaplecza.  Usługi zaplecza definiuje kontrakt nie błędów, więc żadnych błędów zgłaszane z tej usługi będzie traktowane jako błąd bez.  Zgłasza usługi zaplecza <xref:System.ApplicationException> i WCF poprawnie przerywa kanału po stronie usługi. <xref:System.ApplicationException> Następnie powierzchnie <xref:System.ServiceModel.FaultException> , jest zgłaszany do pośrednik. Generuje ponownie pośrednik <xref:System.ApplicationException>. Usługi WCF interpretuje to jako bez błędów, z pośrednik i przekazuje go do klienta. Po odebraniu usterki, zarówno klient, jak i pośrednik błędów ich kanały po stronie klienta. Kanału po stronie usługi pośrednika jednak pozostaje otwarty, ponieważ usługi WCF nie wie, że błąd jest krytyczny.  
  
 Najlepszym rozwiązaniem, w tym scenariuszu jest wykryć, czy błędów pochodzące z usługi jest krytyczny, a jeśli więc pośrednik powinien błędów kanału po stronie usługi, jak pokazano w poniższym fragmencie kodu.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa błędów programu WCF](../../../docs/framework/wcf/wcf-error-handling.md)  
 [Określanie i obsługa błędów w kontraktach i usługach](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
