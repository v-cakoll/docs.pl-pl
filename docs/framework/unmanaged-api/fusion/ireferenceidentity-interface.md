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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2bb151d7c77104d8e24acefaac2e1f109b67f168
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796360"
---
# <a name="ireferenceidentity-interface"></a>IReferenceIdentity — Interfejs
Reprezentuje odwołanie do unikatowego podpisu obiektu kodu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|Pobiera wskaźnik interfejsu do nowego `IReferenceIdentity` wystąpienia, które jest identyczne z tą `IReferenceIdentity`różnicą, z wyjątkiem określonych zmian atrybutów.|  
|`IReferenceIdentity::EnumAttributes`|Pobiera wskaźnik interfejsu do `IEnumIDENTITY_ATTRIBUTE` wystąpienia, które zawiera atrybuty skojarzone z tym `IReferenceIdentity`elementem.|  
|`IReferenceIdentity::GetAttribute`|Pobiera wartość atrybutu w określonym obszarze nazw z określoną nazwą.|  
|`IReferenceIdentity::SetAttribute`|Ustawia atrybut, który ma określoną przestrzeń nazw i określoną nazwę określonej wartości.|  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** Izolacja. h  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy łączenia](fusion-interfaces.md)
- [IEnumIDENTITY_ATTRIBUTE, interfejs](ienumidentity-attribute-interface.md)
