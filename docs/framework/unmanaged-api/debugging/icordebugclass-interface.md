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
ms.openlocfilehash: 7ac588591222a1abbc7b99ec7e973284c055f95e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784170"
---
# <a name="icordebugclass-interface"></a>ICorDebugClass, interfejs

Reprezentuje typ, który może być podstawowy lub złożony (to jest zdefiniowany przez użytkownika). Jeśli typ jest ogólny, `ICorDebugClass` reprezentuje typ ogólny bez wystąpień.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetModule, metoda](icordebugclass-getmodule-method.md)|Pobiera moduł, który definiuje tę klasę.|  
|[GetStaticFieldValue, metoda](icordebugclass-getstaticfieldvalue-method.md)|Pobiera wartość określonego pola statycznego.|  
|[GetToken, metoda](icordebugclass-gettoken-method.md)|Pobiera `TypeDef` token metadanych dla tej klasy.|  
  
## <a name="remarks"></a>Uwagi  
 Interfejs `ICorDebugClass` reprezentuje typ ogólny bez wystąpień. Interfejs ICorDebugType reprezentuje typ ogólny skonkretyzowany. Na przykład `Hashtable<K, V>` byłaby reprezentowana przez `ICorDebugClass`, a `Hashtable<Int32, String>` będzie reprezentowane przez `ICorDebugType`.  
  
 Typy inne niż ogólne są reprezentowane przez `ICorDebugClass` i `ICorDebugType`. Ten ostatni interfejs został wprowadzony w .NET Framework w wersji 2,0, aby można było zająć się tworzeniem wystąpienia typu.  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](debugging-interfaces.md)
