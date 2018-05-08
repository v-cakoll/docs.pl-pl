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
ms.openlocfilehash: 2484fa61c03b95e7cbdb452b92a68a2049701374
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ireferenceappid-interface"></a>IReferenceAppId — Interfejs
Reprezentuje odwołanie do Unikatowy identyfikator dla aplikacji w bieżącym zakresie.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|Pobiera wskaźnik do reprezentacji ciągu identyfikatora kodu dla aplikacji odwołuje się to `IReferenceAppId`.|  
|`IReferenceAppId::put_CodeBase`|Określa identyfikator kodu dla aplikacji odwołuje się to `IReferenceAppId`.|  
|`IReferenceAppId::EnumAppPath`|Pobiera wskaźnika interfejsu do `IEnumReferenceIdentity` zawierające wystąpienie `IReferenceIdentity` wystąpień, które reprezentują członkami to `IReferenceAppId`.|  
|`IReferenceAppId::get_SubscriptionId`|Pobiera wskaźnik do reprezentację ciągu identyfikatora tokenu dla tej subskrypcji `IReferenceAppId`.|  
|`IReferenceAppId::put_SubscriptionId`|Ustawia token identyfikator subskrypcji do tego `IReferenceAppId` wartości określonego ciągu.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Isolation.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy łączenia](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [IEnumReferenceIdentity, interfejs](../../../../docs/framework/unmanaged-api/fusion/ienumreferenceidentity-interface.md)  
 [IReferenceIdentity, interfejs](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
