---
title: <dispatcherSynchronization>
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: 7336c9f7d8a117f9a9bfd338e47941eeb648fa51
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925846"
---
# <a name="dispatchersynchronization"></a>\<dispatcherSynchronization>
  
Określa zachowanie punktu końcowego, które umożliwia usłudze wysyłanie odpowiedzi asynchronicznie.  
  
\<system.serviceModel>  
\<> zachowań  
\<endpointBehaviors>  
\<> zachowania  
  
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
| asynchronousSendEnabled | Wartość logiczna określająca, czy jest włączone asynchroniczne wysyłanie. |
| `maxPendingReceives`    | Liczba całkowita określająca liczbę współbieżnych odbiorów, które mogą być wystawiane w kanale.<br /><br /> Ta wartość powinna być skonfigurowana tylko po poprawnym skonfigurowaniu zachowania ograniczania usługi. |

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |  
| ------- | ----------- |  
| [\<> zachowania](behavior-of-endpointbehaviors.md)|Określa zachowanie punktu końcowego. |

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement>
- <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>
