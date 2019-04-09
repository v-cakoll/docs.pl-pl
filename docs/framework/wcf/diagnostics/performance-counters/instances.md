---
title: Wystąpienia
ms.date: 03/30/2017
ms.assetid: c8cf3460-0ca1-4411-8262-e9ecaf7f0a31
ms.openlocfilehash: 668cfb3026b9ab7259665f5e53873a512b1e2238
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59118992"
---
# <a name="instances"></a>Wystąpienia
Nazwa komputera: wystąpienia.  
  
## <a name="description"></a>Opis  
 Liczba kontekstów wystąpienia, które zawiera obecnie usługi.  
  
 W większości przypadków, liczbę kontekstów wystąpienia jest taka sama jak liczba wystąpień. Jednak poniższe scenariusze są wyjątkiem od tej reguły.  
  
-   Wywołuje metody usługi <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> metoda jawnie.  
  
-   A <xref:System.ServiceModel.ReleaseInstanceMode> jest stosowany do <xref:System.ServiceModel.OperationBehaviorAttribute> wystąpienia.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.OperationBehaviorAttribute>
