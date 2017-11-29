---
title: "IReferenceAppId — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IReferenceAppId
api_location: fusion.dll
api_type: COM
f1_keywords: IReferenceAppId
helpviewer_keywords: IReferenceAppId interface [.NET Framework fusion]
ms.assetid: 8eb9e565-f358-43ce-900e-a8f8a5aa6cfb
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cac4ef63292f1bd342bb94799872b002fdcdf945
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy łączenia](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [IEnumReferenceIdentity — interfejs](../../../../docs/framework/unmanaged-api/fusion/ienumreferenceidentity-interface.md)  
 [IReferenceIdentity — interfejs](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
