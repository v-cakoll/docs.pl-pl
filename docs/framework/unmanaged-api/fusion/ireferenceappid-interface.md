---
title: IReferenceAppId — Interfejs
ms.date: 03/30/2017
api_name:
- IReferenceAppId
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IReferenceAppId
helpviewer_keywords:
- IReferenceAppId interface [.NET Framework fusion]
ms.assetid: 8eb9e565-f358-43ce-900e-a8f8a5aa6cfb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25733e459423500352595d6be0eee26ef75ca7e2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157199"
---
# <a name="ireferenceappid-interface"></a>IReferenceAppId — Interfejs
Reprezentuje odwołanie do Unikatowy identyfikator aplikacji w bieżącym zakresie.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|Pobiera wskaźnik do ciągu reprezentującego identyfikator kodu dla aplikacji odwołuje się ten `IReferenceAppId`.|  
|`IReferenceAppId::put_CodeBase`|Ustawia identyfikator kodu dla aplikacji odwołuje się ten `IReferenceAppId`.|  
|`IReferenceAppId::EnumAppPath`|Pobiera wskaźnik interfejsu do `IEnumReferenceIdentity` zawierające wystąpienie `IReferenceIdentity` wystąpień, które reprezentują elementy członkowskie tego `IReferenceAppId`.|  
|`IReferenceAppId::get_SubscriptionId`|Pobiera wskaźnik do reprezentację ciągu identyfikatora tokenu dla subskrypcji w tym `IReferenceAppId`.|  
|`IReferenceAppId::put_SubscriptionId`|Ustawia token identyfikator subskrypcji to `IReferenceAppId` wartości określonego ciągu.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Isolation.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy łączenia](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [IEnumReferenceIdentity — Interfejs](../../../../docs/framework/unmanaged-api/fusion/ienumreferenceidentity-interface.md)
- [IReferenceIdentity — Interfejs](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
