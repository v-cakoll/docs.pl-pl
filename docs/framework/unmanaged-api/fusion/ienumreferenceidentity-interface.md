---
title: IEnumReferenceIdentity — Interfejs
ms.date: 03/30/2017
api_name:
- IEnumReferenceIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumReferenceIdentity
helpviewer_keywords:
- IEnumReferenceIdentity interface [.NET Framework fusion]
ms.assetid: a17b3155-7216-4e16-8c9f-abce21f549e7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4c5d4bc1fa82f7623168050f4ee36f0ea3cd171e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796431"
---
# <a name="ienumreferenceidentity-interface"></a>IEnumReferenceIdentity — Interfejs
Służy jako moduł wyliczający dla kolekcji `IReferenceIdentity` obiektów.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|Pobiera wskaźnik interfejsu do nowego `IEnumReferenceIdentity` , który zawiera te same składowe. `IEnumReferenceIdentity`|  
|`IEnumReferenceIdentity::Next`|Pobiera określoną liczbę `IReferenceIdentity` obiektów, rozpoczynając od bieżącego położenia.|  
|`IEnumReferenceIdentity::Reset`|Przenosi wskaźnik instrukcji na początek tego `IEnumReferenceIdentity`elementu.|  
|`IEnumReferenceIdentity::Skip`|Przesuwa wskaźnik instrukcji do przodu o określoną liczbę elementów, rozpoczynając od bieżącego położenia.|  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** Izolacja. h  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy łączenia](fusion-interfaces.md)
- [IReferenceIdentity, interfejs](ireferenceidentity-interface.md)
