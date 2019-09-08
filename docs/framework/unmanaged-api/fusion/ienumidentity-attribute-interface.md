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
ms.openlocfilehash: dbb3ac150ebfe9fe3698427d8bb2bfb3e3347c07
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796466"
---
# <a name="ienumidentity_attribute-interface"></a>IEnumIDENTITY_ATTRIBUTE — Interfejs
Służy jako moduł wyliczający dla atrybutów obiektu kodu w bieżącym zakresie.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|`IEnumIDENTITY_ATTRIBUTE::Clone`|Pobiera wskaźnik interfejsu do nowego `IEnumIDENTITY_ATTRIBUTE` , który zawiera te same składowe. `IEnumIDENTITY_ATTRIBUTE`|  
|`IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer`|Zapisuje dane zawarte w elementach tego `IEnumIDENTITY_ATTRIBUTE` obiektu do określonego buforu danych.|  
|`IEnumIDENTITY_ATTRIBUTE::Next`|Pobiera określoną liczbę atrybutów, rozpoczynając od bieżącego położenia.|  
|`IEnumIDENTITY_ATTRIBUTE::Reset`|Przenosi wskaźnik instrukcji na początek tego `IEnumIDENTITY_ATTRIBUTE`elementu.|  
|`IEnumIDENTITY_ATTRIBUTE::Skip`|Przesuwa wskaźnik instrukcji do przodu o określoną liczbę elementów, rozpoczynając od bieżącego położenia.|  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** Izolacja. h  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy łączenia](fusion-interfaces.md)
