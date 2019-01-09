---
title: '&lt;dispatcherSynchronization&gt;'
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: 86660620113b162a9a5260b7026a64455284d184
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151465"
---
# <a name="ltdispatchersynchronizationgt"></a>&lt;dispatcherSynchronization&gt;
  
Określa zachowanie punktu końcowego, które włącza usługę wysłać odpowiedzi asynchronicznie.  
  
\<system.serviceModel>  
\<zachowania >  
\<endpointBehaviors>  
\<zachowanie >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean"
                                   maxPendingReceives="Integer" />
```  
  
## <a name="type"></a>Typ  
  
`Type`  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
  
W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty

| Atrybut               | Opis       |
| ----------------------- | ----------------- |
| asynchronousSendEnabled | Wartość logiczna określająca czy zachowanie przesyłu asynchronicznego jest włączone. |
| `maxPendingReceives`    | Liczba całkowita, która określa liczbę równoczesnych pobrań, które mogą być wystawiane na kanale.<br /><br /> Tę wartość należy skonfigurować tylko wtedy, gdy zachowanie ograniczania przepływności usługi zostało poprawnie skonfigurowane. |

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |  
| ------- | ----------- |  
| [\<zachowanie >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Określa zachowanie punktu końcowego. |

## <a name="see-also"></a>Zobacz także

 <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement><xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>
