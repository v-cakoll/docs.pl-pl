---
title: ICorDebugEval::CreateValue — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval.CreateValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::CreateValue
helpviewer_keywords:
- ICorDebugEval::CreateValue method [.NET Framework debugging]
- CreateValue method [.NET Framework debugging]
ms.assetid: 9a1c0b47-6f10-4fcb-844a-4ab2d7990140
topic_type:
- apiref
ms.openlocfilehash: 4bb04ba090be9cab551bc39d8d9f1be974c747d3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73085132"
---
# <a name="icordebugevalcreatevalue-method"></a>ICorDebugEval::CreateValue — Metoda
Tworzy wartość określonego typu z początkową wartością zero lub null.  
  
 Ta metoda jest przestarzała w .NET Framework w wersji 2,0. Zamiast tego użyj [ICorDebugEval2:: CreateValueForType —](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CreateValue (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `elementType`  
 podczas Wartość wyliczenia [CorElementType —](../../../../docs/framework/unmanaged-api/metadata/corelementtype-enumeration.md) , która określa typ wartości.  
  
 `pElementClass`  
 podczas Wskaźnik do obiektu [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md) , który określa klasę wartości, jeśli typ nie jest typem pierwotnym.  
  
 `ppValue`  
 określoną Wskaźnik na adres obiektu "ICorDebugValue", który reprezentuje wartość.  
  
## <a name="remarks"></a>Uwagi  
 `CreateValue` tworzy obiekt `ICorDebugValue` danego typu jako jedyny cel użycia go w ocenie funkcji. Ten obiekt wartości może służyć do przekazywania stałych użytkowników jako parametrów.  
  
 Jeśli typ wartości jest typem pierwotnym, jego wartość początkowa wynosi zero lub ma wartość null. Użyj [ICorDebugGenericValue:: SetValue](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md) , aby ustawić wartość typu pierwotnego.  
  
 Jeśli wartość `elementType` to ELEMENT_TYPE_CLASS, otrzymujesz "ICorDebugReferenceValue" (zwrócony w `ppValue`) reprezentujący odwołanie do obiektu null. Można użyć tego obiektu, aby przekazać wartość null do oceny funkcji, która ma parametry odwołania obiektu. Nie można ustawić dla `ICorDebugValue` żadnych elementów. zawsze pozostaje puste.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:** 1,1, 1,0  
  
## <a name="see-also"></a>Zobacz także

- [CreateValueForType, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)
- [ICorDebugEval, interfejs](icordebugeval-interface.md)
