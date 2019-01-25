---
title: Wystąpienia
ms.date: 03/30/2017
ms.assetid: c8cf3460-0ca1-4411-8262-e9ecaf7f0a31
ms.openlocfilehash: 1b2801b5df3a5d2ca6d7fd03299ecdf4b7df426a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54520278"
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
