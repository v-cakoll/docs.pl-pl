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
ms.openlocfilehash: 55888786fdd8ff2b1d5610a74ee729db0d4fcfde
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976255"
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
 podczas Wartość wyliczenia [CorElementType —](../metadata/corelementtype-enumeration.md) , która określa typ wartości.  
  
 `pElementClass`  
 podczas Wskaźnik do obiektu [ICorDebugClass](icordebugclass-interface.md) , który określa klasę wartości, jeśli typ nie jest typem pierwotnym.  
  
 `ppValue`  
 określoną Wskaźnik na adres obiektu "ICorDebugValue", który reprezentuje wartość.  
  
## <a name="remarks"></a>Uwagi  
 `CreateValue`tworzy `ICorDebugValue` obiekt danego typu jako jedyny cel użycia go w ocenie funkcji. Ten obiekt wartości może służyć do przekazywania stałych użytkowników jako parametrów.  
  
 Jeśli typ wartości jest typem pierwotnym, jego wartość początkowa wynosi zero lub ma wartość null. Użyj [ICorDebugGenericValue:: SetValue](icordebuggenericvalue-setvalue-method.md) , aby ustawić wartość typu pierwotnego.  
  
 Jeśli wartość `elementType` jest ELEMENT_TYPE_CLASS, otrzymujesz "ICorDebugReferenceValue" (zwrócony w `ppValue`) reprezentujący odwołanie do obiektu o wartości null. Można użyć tego obiektu, aby przekazać wartość null do oceny funkcji, która ma parametry odwołania obiektu. Nie można ustawić elementów `ICorDebugValue` na wszystkie; zawsze pozostaje puste.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:** 1,1, 1,0  
  
## <a name="see-also"></a>Zobacz też

- [CreateValueForType, metoda](icordebugeval2-createvaluefortype-method.md)
- [ICorDebugEval, interfejs](icordebugeval-interface.md)
