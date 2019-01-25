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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0af820b590271e16cbfb443c193fd0afb4ed3358
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54604127"
---
# <a name="icordebugevalcreatevalue-method"></a>ICorDebugEval::CreateValue — Metoda
Tworzy wartość określonego typu o wartości początkowej zero lub wartość null.  
  
 Ta metoda jest przestarzała w programie .NET Framework 2.0. Użyj [ICorDebugEval2::CreateValueForType](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) zamiast tego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CreateValue (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `elementType`  
 [in] Wartość [corelementtype —](../../../../docs/framework/unmanaged-api/metadata/corelementtype-enumeration.md) wyliczenie, który określa typ wartości.  
  
 `pElementClass`  
 [in] Wskaźnik do [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md) obiekt, który określa klasę wartości, jeśli typ nie jest typem pierwotnym.  
  
 `ppValue`  
 [out] Wskaźnik na adres obiektu "ICorDebugValue", który reprezentuje wartość.  
  
## <a name="remarks"></a>Uwagi  
 `CreateValue` Tworzy `ICorDebugValue` obiekt danego typu wyłącznie w celu korzystania z niego Obliczanie funkcji. Ten obiekt wartość może służyć do przekazywania stałe użytkownika jako parametry.  
  
 Jeśli typ wartości jest typu podstawowego, jej wartość początkową wynosi zero lub wartość null. Użyj [ICorDebugGenericValue::SetValue](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md) można ustawić wartości typu podstawowego.  
  
 Jeśli wartość `elementType` jest ELEMENT_TYPE_CLASS, możesz uzyskać "ICorDebugReferenceValue" (zwracane w `ppValue`) reprezentujący odwołanie do obiektu o wartości null. Ten obiekt jest używany do przekazywania wartości null do obliczania funkcji, z parametrami odwołanie do obiektu. Nie można ustawić `ICorDebugValue` miejscem; zawsze pozostaje o wartości null.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** 1.1, 1.0  
  
## <a name="see-also"></a>Zobacz także

- [Createvaluefortype — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) ICorDebugValue
