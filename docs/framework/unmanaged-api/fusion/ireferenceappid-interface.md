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
ms.openlocfilehash: 6f20fb2e9e026253fb02b47dfcd63cf655acc4ee
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131659"
---
# <a name="ireferenceappid-interface"></a>IReferenceAppId — Interfejs
Reprezentuje odwołanie do unikatowego identyfikatora aplikacji w bieżącym zakresie.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|Pobiera wskaźnik do ciągu reprezentującego identyfikator kodu dla aplikacji, do której odwołuje się ten `IReferenceAppId`.|  
|`IReferenceAppId::put_CodeBase`|Ustawia identyfikator kodu dla aplikacji, do której odwołuje się ten `IReferenceAppId`.|  
|`IReferenceAppId::EnumAppPath`|Pobiera wskaźnik interfejsu do wystąpienia `IEnumReferenceIdentity` zawierającego wystąpienia `IReferenceIdentity`, które reprezentują członków tego `IReferenceAppId`.|  
|`IReferenceAppId::get_SubscriptionId`|Pobiera wskaźnik do ciągu reprezentującego Identyfikator tokenu dla subskrypcji tej `IReferenceAppId`.|  
|`IReferenceAppId::put_SubscriptionId`|Ustawia identyfikator tokenu dla subskrypcji tej `IReferenceAppId` na określoną wartość ciągu.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Izolacja. h  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy łączenia](fusion-interfaces.md)
- [IEnumReferenceIdentity, interfejs](ienumreferenceidentity-interface.md)
- [IReferenceIdentity, interfejs](ireferenceidentity-interface.md)
