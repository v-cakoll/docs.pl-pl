---
title: 'Usługa: Wywołania zwracające błędy'
ms.date: 03/30/2017
ms.assetid: 6da7f100-3f61-4b3c-9409-fe1360829b8a
ms.openlocfilehash: f0c50f4296003f9e1be579ac0901a989f4ce2f04
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474685"
---
# <a name="service-calls-faulted"></a>Usługa: Wywołania zwracające błędy
Nazwa licznika: Wywołania zwracające błędy.  
  
## <a name="description"></a>Opis  
 Liczba wywołań tej usługi, które zostały zwrócone błędy. W aplikacji Windows Communication Foundation (WCF) metody usługi komunikują się za pomocą protokołu SOAP komunikatów "fault" informacje o błędzie przetwarzania. Błędach SOAP są typów komunikatów, które są zawarte w metadanych dla operacji usługi i dlatego należy utworzyć kontrakt błędu, w której klienci mogą używać, aby ich wykonanie bardziej niezawodne lub interakcyjne. Ponieważ błędach SOAP są wyrażane klientom w postaci XML, są one bardzo interoperacyjne.  
  
## <a name="see-also"></a>Zobacz też  
 [Określanie i obsługa błędów w kontraktach i usługach](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
