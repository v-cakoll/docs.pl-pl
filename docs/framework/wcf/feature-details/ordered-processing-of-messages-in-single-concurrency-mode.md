---
title: Uporządkowane przetwarzanie komunikatów w trybie pojedynczej współbieżności
ms.date: 03/30/2017
ms.assetid: a90f5662-a796-46cd-ae33-30a4072838af
ms.openlocfilehash: bbbc1f62931abda438c3d06b514518b1199b649e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ordered-processing-of-messages-in-single-concurrency-mode"></a>Uporządkowane przetwarzanie komunikatów w trybie pojedynczej współbieżności
Usługi WCF sprawia, że żadnych gwarancji dotyczących kolejności, w jakiej są przetwarzane wiadomości, chyba że zamykania kanału źródłowego.  Dla wystąpienia usługi WCF, który używa MsmqInputChannel, który nie jest podczas zamykania kanału sesji, nie będzie można przetwarzać komunikatów w kolejności. Istnieją pewne okoliczności, w których deweloper może mają w kolejności przetwarzania zachowanie, ale nie mają być używane sesje. W tym temacie opisano sposób skonfigurowania tego zachowania, gdy usługa jest uruchomiona w trybie równoległym pojedynczego.  
  
## <a name="in-order-message-processing"></a>Przetwarzanie komunikatów w kolejności  
 Nowy atrybut o nazwie <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> został dodany do <xref:System.ServiceModel.ServiceBehaviorAttribute>. Gdy <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> jest ustawiona na wartość true i <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> ustawiono <xref:System.ServiceModel.ConcurrencyMode.Single> komunikaty wysyłane do usługi będą przetwarzane w kolejności. Poniższy fragment kodu przedstawia sposób ustawiania tych atrybutów.  
  
```  
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, EnsureOrderedDispatch = true )]  
    class Service : IService  
    {  
         // ...  
    }  
```  
  
 Jeśli <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> ma ustawioną wartość inną wartość <xref:System.InvalidOperationException> jest generowany.  
  
## <a name="see-also"></a>Zobacz też  
 [Sesje, tworzenie wystąpień i współbieżność](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
 [Współbieżność](../../../../docs/framework/wcf/samples/concurrency.md)
