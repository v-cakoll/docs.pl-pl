---
title: 'Najlepsze praktyki: Elementy pośredniczące'
ms.date: 03/30/2017
ms.assetid: 2d41b337-8132-4ac2-bea2-6e9ae2f00f8d
ms.openlocfilehash: d69baae9b4f5851f60d8d1336c40e0d18db8e77d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="best-practices-intermediaries"></a>Najlepsze praktyki: Elementy pośredniczące
Należy uważać poprawnie obsłużyć błędy podczas wywoływania metody pośredników, aby upewnić się, że kanały po stronie usługi na pośrednik zostały prawidłowo zamknięte.  
  
 Rozważmy poniższy scenariusz. Klient nawiązuje połączenie pośrednika, który wywołuje usługi zaplecza.  Usługi zaplecza definiuje kontrakt nie błędu, więc winy wyjątek od tej usługi będzie traktowana jako błąd wyrażeniami bez typu.  Zwraca usługi zaplecza <xref:System.ApplicationException> i WCF poprawnie przerywa kanału po stronie serwera. <xref:System.ApplicationException> Następnie powierzchnie <xref:System.ServiceModel.FaultException> który jest zgłaszany do pośrednika. Ponownie zgłasza wyjątek pośrednik <xref:System.ApplicationException>. Usługi WCF interpretuje jako błąd wyrażeniami bez typu z pośrednik i przekazuje je do klienta. Po odebraniu usterki, zarówno klient, jak i pośrednik fault ich kanały po stronie klienta. Kanału po stronie usługi pośrednika jednak pozostanie otwarty, ponieważ WCF nie może ustalić, czy błąd jest krytyczny.  
  
 Najlepszym rozwiązaniem w tym scenariuszu jest wykryć, czy jest krytyczny błąd przesyłanych przez usługę, a jeśli tak pośrednik powinien fault kanału po stronie serwera, jak pokazano w poniższy fragment kodu.  
  
```csharp  
catch (Exception e)  
{  
    bool faulted = service.State == CommunicationState.Faulted;  
    service.Abort();  
    if (faulted)  
    {  
        throw new ApplicationException(e.Message);  
    }  
    Else  
    {  
        throw;  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa błędów programu WCF](../../../docs/framework/wcf/wcf-error-handling.md)  
 [Określanie i obsługa błędów w kontraktach i usługach](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
