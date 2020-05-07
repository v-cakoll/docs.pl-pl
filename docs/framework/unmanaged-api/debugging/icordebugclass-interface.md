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
ms.openlocfilehash: d7417e8dc193172c77d23fe3fa72c8298d802b5c
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894041"
---
# <a name="icordebugclass-interface"></a>ICorDebugClass, interfejs

Reprezentuje typ, który może być podstawowy lub złożony (to jest zdefiniowany przez użytkownika). Jeśli typ jest ogólny, `ICorDebugClass` reprezentuje typ ogólny bez wystąpień.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetModule — Metoda](icordebugclass-getmodule-method.md)|Pobiera moduł, który definiuje tę klasę.|  
|[GetStaticFieldValue, metoda](icordebugclass-getstaticfieldvalue-method.md)|Pobiera wartość określonego pola statycznego.|  
|[GetToken — Metoda](icordebugclass-gettoken-method.md)|Pobiera token `TypeDef` metadanych dla tej klasy.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugClass` Interfejs reprezentuje typ ogólny bez wystąpień. Interfejs ICorDebugType reprezentuje typ ogólny skonkretyzowany. Na przykład `Hashtable<K, V>` byłyby reprezentowane przez `ICorDebugClass`, a `Hashtable<Int32, String>` byłyby reprezentowane przez. `ICorDebugType`  
  
 Typy inne niż ogólne są reprezentowane przez `ICorDebugClass` i. `ICorDebugType` Ten ostatni interfejs został wprowadzony w .NET Framework w wersji 2,0, aby można było zająć się tworzeniem wystąpienia typu.  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Debugowanie — Interfejsy](debugging-interfaces.md)
