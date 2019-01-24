---
title: Uporządkowane przetwarzanie komunikatów w trybie pojedynczej współbieżności
ms.date: 03/30/2017
ms.assetid: a90f5662-a796-46cd-ae33-30a4072838af
ms.openlocfilehash: c9f2460a1def19212d3ba866b0b443830e9b69bb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745856"
---
# <a name="ordered-processing-of-messages-in-single-concurrency-mode"></a>Uporządkowane przetwarzanie komunikatów w trybie pojedynczej współbieżności
Usługi WCF sprawia, że żadnej gwarancji dotyczącej kolejności, w jakiej komunikaty są przetwarzane, chyba że przekroczono kanału źródłowego.  Na przykład usługi WCF, która używa MsmqInputChannel, który nie jest kanału sesji, zakończy się niepowodzeniem do przetwarzania wiadomości w kolejności. Istnieją pewne okoliczności, w której deweloper może ma zachowanie za przetwarzanie zamówień w, ale nie mają być używane sesji. W tym temacie opisano sposób konfigurowania tego zachowania, gdy usługa jest uruchomiona w trybie pojedynczej współbieżności.  
  
## <a name="in-order-message-processing"></a>W określonej kolejności przetwarzania wiadomości  
 Nowy atrybut o nazwie <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> została dodana do <xref:System.ServiceModel.ServiceBehaviorAttribute>. Gdy <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> jest ustawiona na wartość true i <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> jest ustawiona na <xref:System.ServiceModel.ConcurrencyMode.Single> komunikaty wysyłane do usługi, które będą przetwarzane w kolejności. Poniższy fragment kodu przedstawia sposób ustawiania tych atrybutów.  
  
```  
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, EnsureOrderedDispatch = true )]  
    class Service : IService  
    {  
         // ...  
    }  
```  
  
 Jeśli <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> jest ustawiona na jakąkolwiek inną wartość, <xref:System.InvalidOperationException> zgłaszany.  
  
## <a name="see-also"></a>Zobacz także
- [Sesje, tworzenie wystąpień i współbieżność](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)
- [Współbieżność](../../../../docs/framework/wcf/samples/concurrency.md)
