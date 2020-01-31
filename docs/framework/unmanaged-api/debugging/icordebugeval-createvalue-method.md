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
ms.openlocfilehash: bd6f1b2153404ba4567ef8348ff128b5d475c6fe
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793494"
---
# <a name="icordebugevalcreatevalue-method"></a>ICorDebugEval::CreateValue — Metoda
Tworzy wartość określonego typu z początkową wartością zero lub null.  
  
 Ta metoda jest przestarzała w .NET Framework w wersji 2,0. Zamiast tego użyj [ICorDebugEval2:: CreateValueForType —](icordebugeval2-createvaluefortype-method.md) .  
  
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
 podczas Wskaźnik do obiektu [ICorDebugClass](icordebugclass-interface.md) , który określa klasę wartości, jeśli typ nie jest typem pierwotnym.  
  
 `ppValue`  
 określoną Wskaźnik na adres obiektu "ICorDebugValue", który reprezentuje wartość.  
  
## <a name="remarks"></a>Uwagi  
 `CreateValue` tworzy obiekt `ICorDebugValue` danego typu jako jedyny cel użycia go w ocenie funkcji. Ten obiekt wartości może służyć do przekazywania stałych użytkowników jako parametrów.  
  
 Jeśli typ wartości jest typem pierwotnym, jego wartość początkowa wynosi zero lub ma wartość null. Użyj [ICorDebugGenericValue:: SetValue](icordebuggenericvalue-setvalue-method.md) , aby ustawić wartość typu pierwotnego.  
  
 Jeśli wartość `elementType` jest ELEMENT_TYPE_CLASS, zostanie wyświetlony komunikat "ICorDebugReferenceValue" (zwrócony w `ppValue`) reprezentujący odwołanie do obiektu o wartości null. Można użyć tego obiektu, aby przekazać wartość null do oceny funkcji, która ma parametry odwołania obiektu. Nie można ustawić dla `ICorDebugValue` żadnych elementów. zawsze pozostaje puste.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:** 1,1, 1,0  
  
## <a name="see-also"></a>Zobacz także

- [CreateValueForType, metoda](icordebugeval2-createvaluefortype-method.md)
- [ICorDebugEval, interfejs](icordebugeval-interface.md)
