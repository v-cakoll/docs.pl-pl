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
ms.openlocfilehash: 4708fa173725e4c91a13f5b92cdbb1fdf8a8a4d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ireferenceidentity-interface"></a>IReferenceIdentity — Interfejs
Reprezentuje odwołanie do unikatowego podpisu obiektu kodu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|Pobiera wskaźnika interfejsu na nowy `IReferenceIdentity` wystąpienia, który jest taki sam jak to `IReferenceIdentity`, z wyjątkiem zmiany określonego atrybutu.|  
|`IReferenceIdentity::EnumAttributes`|Pobiera wskaźnika interfejsu do `IEnumIDENTITY_ATTRIBUTE` wystąpienia, które zawiera atrybuty skojarzone z tym `IReferenceIdentity`.|  
|`IReferenceIdentity::GetAttribute`|Pobiera wartość atrybutu w określonej przestrzeni nazw o określonej nazwie.|  
|`IReferenceIdentity::SetAttribute`|Ustawia atrybut, który ma określonego obszaru nazw i nazwę określonego na określoną wartość.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Isolation.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy łączenia](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [IEnumIDENTITY_ATTRIBUTE, interfejs](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)
