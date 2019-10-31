---
title: IReferenceIdentity — Interfejs
ms.date: 03/30/2017
api_name:
- IReferenceIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IReferenceIdentity
helpviewer_keywords:
- IReferenceIdentity interface [.NET Framework fusion]
ms.assetid: 9180ac5a-7019-4716-9f83-8a91d157239a
topic_type:
- apiref
ms.openlocfilehash: 8f6a117d1e2fe76c271b0b014e6079370c8b4fe4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127066"
---
# <a name="ireferenceidentity-interface"></a>IReferenceIdentity — Interfejs
Reprezentuje odwołanie do unikatowego podpisu obiektu kodu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|Pobiera wskaźnik interfejsu do nowego wystąpienia `IReferenceIdentity`, który jest identyczny z tym `IReferenceIdentity`, z wyjątkiem określonych zmian atrybutów.|  
|`IReferenceIdentity::EnumAttributes`|Pobiera wskaźnik interfejsu do wystąpienia `IEnumIDENTITY_ATTRIBUTE`, które zawiera atrybuty skojarzone z tym `IReferenceIdentity`.|  
|`IReferenceIdentity::GetAttribute`|Pobiera wartość atrybutu w określonym obszarze nazw z określoną nazwą.|  
|`IReferenceIdentity::SetAttribute`|Ustawia atrybut, który ma określoną przestrzeń nazw i określoną nazwę określonej wartości.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Izolacja. h  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy łączenia](fusion-interfaces.md)
- [IEnumIDENTITY_ATTRIBUTE, interfejs](ienumidentity-attribute-interface.md)
