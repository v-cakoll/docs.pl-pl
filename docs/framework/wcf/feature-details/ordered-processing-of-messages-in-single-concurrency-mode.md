---
title: Uporządkowane przetwarzanie komunikatów w trybie pojedynczej współbieżności
ms.date: 03/30/2017
ms.assetid: a90f5662-a796-46cd-ae33-30a4072838af
ms.openlocfilehash: ecabb9a6e838b0137c538d76c554646356ea87f5
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991501"
---
# <a name="ordered-processing-of-messages-in-single-concurrency-mode"></a>Uporządkowane przetwarzanie komunikatów w trybie pojedynczej współbieżności
Funkcja WCF nie gwarantuje kolejności, w której przetwarzane są komunikaty, chyba że źródłowy kanał to sesja.  Na przykład usługa WCF korzystająca z MsmqInputChannel, która nie jest kanałem sesji, nie przetwarza komunikatów w określonej kolejności. Istnieją pewne sytuacje, w których deweloper może chcieć wykonać przetwarzanie w kolejności, ale nie chce używać sesji. W tym temacie opisano sposób konfigurowania tego zachowania, gdy usługa jest uruchomiona w trybie pojedynczego współbieżności.  
  
## <a name="in-order-message-processing"></a>Przetwarzanie komunikatów w porządku  
 <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> Dodano<xref:System.ServiceModel.ServiceBehaviorAttribute>nowy atrybut o nazwie. Gdy <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> jest ustawiona na wartość true <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> i jest ustawiona <xref:System.ServiceModel.ConcurrencyMode.Single> na komunikaty wysyłane do usługi, zostanie przetworzona w kolejności. Poniższy fragment kodu ilustruje sposób ustawiania tych atrybutów.  
  
```csharp
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, EnsureOrderedDispatch = true )]  
    class Service : IService  
    {  
         // ...  
    }  
```  
  
 Jeśli <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> jest ustawiona na inną wartość <xref:System.InvalidOperationException> , zostanie zgłoszony.  
  
## <a name="see-also"></a>Zobacz także

- [Sesje, tworzenie wystąpień i współbieżność](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)
- [Współbieżność](../../../../docs/framework/wcf/samples/concurrency.md)
