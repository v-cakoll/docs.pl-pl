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
# <a name="best-practices-intermediaries"></a>Najlepsze praktyki: Elementy pośredniczące
Należy zachować ostrożność w celu prawidłowego obsługi błędów podczas wywoływania pośredników, aby upewnić się, że kanały po stronie usługi na pośrednim są poprawnie zamknięte.  
  
 Rozważmy następujący scenariusz. Klient wysyła wywołanie do pośrednika, które następnie wywołuje usługę zaplecza.  Usługa zaplecza nie definiuje kontraktu błędów, więc wszelkie błędy zgłoszone przez tę usługę będą traktowane jako błąd nieokreślony.  Usługa zaplecza zgłasza <xref:System.ApplicationException>, a funkcja WCF prawidłowo przerywa kanał po stronie usługi. @No__t-0 następnie powierzchnie jako <xref:System.ServiceModel.FaultException>, które są generowane do pośrednika. Pośrednika zgłasza <xref:System.ApplicationException>. Funkcja WCF interpretuje ją jako błąd nieokreślony z pośrednich i przekazuje je do klienta. Po otrzymaniu błędu zarówno pośrednika, jak i błąd klienta ich kanałów po stronie klienta. Kanał po stronie usług pośrednika pozostanie otwarty, ponieważ platforma WCF nie wie, że błąd jest krytyczny.  
  
 Najlepszym rozwiązaniem w tym scenariuszu jest wykrycie, czy błąd pochodzący z usługi jest krytyczny, a jeśli tak, pośrednik powinien spowodować błąd swojego kanału po stronie usługi, jak pokazano w poniższym fragmencie kodu.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Obsługa błędów programu WCF](wcf-error-handling.md)
- [Określanie i obsługa błędów w kontraktach i usługach](specifying-and-handling-faults-in-contracts-and-services.md)
