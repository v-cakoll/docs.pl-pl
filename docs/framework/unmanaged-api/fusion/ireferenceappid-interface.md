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
ms.openlocfilehash: 522ed80f161f114af25e1fa7ad041c8238073d6f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796369"
---
# <a name="ireferenceappid-interface"></a>IReferenceAppId — Interfejs
Reprezentuje odwołanie do unikatowego identyfikatora aplikacji w bieżącym zakresie.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|Pobiera wskaźnik do ciągu reprezentującego identyfikator kodu dla aplikacji, do której się odwołuje `IReferenceAppId`.|  
|`IReferenceAppId::put_CodeBase`|Ustawia identyfikator kodu dla aplikacji, do której się odwołuje `IReferenceAppId`.|  
|`IReferenceAppId::EnumAppPath`|Pobiera wskaźnik interfejsu do `IEnumReferenceIdentity` wystąpienia `IReferenceIdentity` zawierającego wystąpienia, które reprezentują elementy członkowskie tego `IReferenceAppId`elementu.|  
|`IReferenceAppId::get_SubscriptionId`|Pobiera wskaźnik do ciągu reprezentującego Identyfikator tokenu dla subskrypcji `IReferenceAppId`.|  
|`IReferenceAppId::put_SubscriptionId`|Ustawia identyfikator tokenu dla subskrypcji `IReferenceAppId` na wartość określonej wartości ciągu.|  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** Izolacja. h  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy łączenia](fusion-interfaces.md)
- [IEnumReferenceIdentity, interfejs](ienumreferenceidentity-interface.md)
- [IReferenceIdentity, interfejs](ireferenceidentity-interface.md)
