---
title: ICorDebugClass, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass
helpviewer_keywords:
- ICorDebugClass interface [.NET Framework debugging]
ms.assetid: 03a6facb-f12f-49be-9839-e73b9c791cd5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc5099af23a2b706694bfcb655d295607c97ea8a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969280"
---
# <a name="icordebugclass-interface"></a>ICorDebugClass, interfejs

Reprezentuje typ, który może być podstawowy lub złożony (to jest zdefiniowany przez użytkownika). Jeśli typ jest ogólny, `ICorDebugClass` reprezentuje typ ogólny bez wystąpień.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetModule, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|Pobiera moduł, który definiuje tę klasę.|  
|[GetStaticFieldValue, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md)|Pobiera wartość określonego pola statycznego.|  
|[GetToken, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-gettoken-method.md)|Pobiera token `TypeDef` metadanych dla tej klasy.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugClass` Interfejs reprezentuje typ ogólny bez wystąpień. Interfejs ICorDebugType reprezentuje typ ogólny skonkretyzowany. Na przykład `Hashtable<K, V>` byłyby reprezentowane przez `ICorDebugClass`, a `Hashtable<Int32, String>` byłyby reprezentowane przez `ICorDebugType`.  
  
 Typy inne niż ogólne są reprezentowane przez `ICorDebugClass` i. `ICorDebugType` Ten ostatni interfejs został wprowadzony w .NET Framework w wersji 2,0, aby można było zająć się tworzeniem wystąpienia typu.  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** CorDebug.idl, CorDebug.h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
