---
title: IEnumIDENTITY_ATTRIBUTE — Interfejs
ms.date: 03/30/2017
api_name:
- IEnumIDENTITY_ATTRIBUTE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumIDENTITY_ATTRIBUTE
helpviewer_keywords:
- IEnumIDENTITY_ATTRIBUTE interface [.NET Framework fusion]
ms.assetid: c2ec2748-e9ae-4e1b-80db-6fcec5cb81a1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d725228f2a7359d415673fdcb90d0cabae1a40be
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59175529"
---
# <a name="ienumidentityattribute-interface"></a>IEnumIDENTITY_ATTRIBUTE — Interfejs
Służy jako moduł wyliczający dla atrybutów obiektu kodu w bieżącym zakresie.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|`IEnumIDENTITY_ATTRIBUTE::Clone`|Pobiera wskaźnik interfejsu do nowego `IEnumIDENTITY_ATTRIBUTE` zawiera te same elementy członkowskie, ponieważ `IEnumIDENTITY_ATTRIBUTE`.|  
|`IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer`|Zapisuje dane zawarte w elementach to `IEnumIDENTITY_ATTRIBUTE` do określonych danych buforu.|  
|`IEnumIDENTITY_ATTRIBUTE::Next`|Pobiera określoną liczbę atrybutów, zaczynając od bieżącej pozycji.|  
|`IEnumIDENTITY_ATTRIBUTE::Reset`|Przesuwa wskaźnik instrukcji na początku `IEnumIDENTITY_ATTRIBUTE`.|  
|`IEnumIDENTITY_ATTRIBUTE::Skip`|Przesuwa wskaźnik instrukcji do przodu o określoną liczbę elementów, zaczynając od bieżącej pozycji.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Isolation.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy łączenia](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
