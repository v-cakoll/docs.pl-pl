---
title: Wystąpienia
ms.date: 03/30/2017
ms.assetid: c8cf3460-0ca1-4411-8262-e9ecaf7f0a31
ms.openlocfilehash: e0be9c93b5efe17235dbccd426cdd73fbb739361
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651832"
---
# <a name="instances"></a>Wystąpienia
Nazwa komputera: wystąpienia.  
  
## <a name="description"></a>Opis  
 Liczba kontekstów wystąpienia, które zawiera obecnie usługi.  
  
 W większości przypadków, liczbę kontekstów wystąpienia jest taka sama jak liczba wystąpień. Jednak poniższe scenariusze są wyjątkiem od tej reguły.  
  
- Wywołuje metody usługi <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> metoda jawnie.  
  
- A <xref:System.ServiceModel.ReleaseInstanceMode> jest stosowany do <xref:System.ServiceModel.OperationBehaviorAttribute> wystąpienia.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.OperationBehaviorAttribute>
