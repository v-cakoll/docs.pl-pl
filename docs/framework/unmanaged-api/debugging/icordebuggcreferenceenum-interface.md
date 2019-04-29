---
title: ICorDebugGCReferenceEnum — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugGCReferenceEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGCReferenceEnum
helpviewer_keywords:
- ICorDebugGCReferenceEnum interface [.NET Framework debugging]
ms.assetid: 5f3c91c9-c035-454f-96cc-011cab1ea06b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8f83d2ac9ca96145fa89b283fec42c71858097f6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651626"
---
# <a name="icordebuggcreferenceenum-interface"></a>ICorDebugGCReferenceEnum — Interfejs
Dostarcza moduł wyliczający dla obiektów, które zostaną usunięte jako elementy bezużyteczne.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Next, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md)|Pobiera określoną liczbę [cor_gc_reference —](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) wystąpień, które zawierają informacje o obiektach, których będzie jesdnostką zbierającą śmieci.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugGCReferenceEnum` Interfejsu implementuje interfejs "ICorDebugEnum".  
  
 `ICorDebugGCReferenceEnum` Wystąpień jest wypełniana przy użyciu [cor_gc_reference —](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) wystąpień, wywołując [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) metody. [Cor_gc_reference —](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) obiekty mogą być wyliczane przez wywołanie metody [ICorDebugGCReference::Next](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md) metody.  
  
 [Cor_gc_reference —](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) obiektów kolekcji wypełnione przez tę metodę reprezentowania trzy rodzaje obiektów:  
  
- Obiekty z wszystkie stosy zarządzane. Obejmuje to odwołań na żywo w kodzie zarządzanym, a także obiekty utworzone przez środowisko uruchomieniowe języka wspólnego.  
  
- Obiekty z tabeli dojście. Obejmuje to odwołań do silnych (`HNDTYPE_STRONG` i `HNDTYPE_REFCOUNT`) i zmiennych statycznych w module.  
  
- Obiekty z; kolejka finalizatorów. Elementy główne obiektów; kolejka finalizatorów, aż finalizator zostało uruchomione.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
