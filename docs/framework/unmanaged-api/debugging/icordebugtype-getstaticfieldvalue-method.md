---
title: ICorDebugType::GetStaticFieldValue — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetStaticFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetStaticFieldValue
helpviewer_keywords:
- GetStaticFieldValue method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::GetStaticFieldValue method [.NET Framework debugging]
ms.assetid: 62eb5d55-53ee-4fb3-8d47-7b6c96808f9e
topic_type:
- apiref
ms.openlocfilehash: 37bf5abf66b613d8432af84c7d73aff60e9127cb
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791273"
---
# <a name="icordebugtypegetstaticfieldvalue-method"></a>ICorDebugType::GetStaticFieldValue — Metoda
Pobiera wskaźnik interfejsu do obiektu ICorDebugValue, który zawiera wartość pola statycznego, do którego odwołuje się określony token pola w określonej ramce stosu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef        fieldDef,  
    [in]  ICorDebugFrame    *pFrame,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `fieldDef`  
 podczas Token `mdFieldDef`, który określa pole statyczne.  
  
 `pFrame`  
 podczas Wskaźnik do elementu ICorDebugFrame, który reprezentuje ramkę stosu.  
  
 `ppValue`  
 określoną Wskaźnik do adresu `ICorDebugValue`, który zawiera wartość pola statycznego.  
  
## <a name="remarks"></a>Uwagi  
 Metody `GetStaticFieldValue` można używać tylko wtedy, gdy typ jest ELEMENT_TYPE_CLASS lub ELEMENT_TYPE_VALUETYPE, jak wskazano w metodzie [ICorDebugType:: GetType](icordebugtype-gettype-method.md) .  
  
 W przypadku typów innych niż ogólne Operacja wykonywana przez `GetStaticFieldValue` jest taka sama jak wywołanie [ICorDebugClass:: GetStaticFieldValue](icordebugclass-getstaticfieldvalue-method.md) w obiekcie ICorDebugClass, który jest zwracany przez [ICorDebugType:: GetClass](icordebugtype-getclass-method.md).  
  
 W przypadku typów ogólnych wartość pola statycznego będzie określana względem konkretnego wystąpienia. Ponadto, jeśli pole statyczne może być powiązane z wątkiem, kontekstem lub domeną aplikacji, Ramka stosu pomoże debugerowi określić odpowiednią wartość.  
  
## <a name="remarks"></a>Uwagi  
 `GetStaticFieldValue` można używać tylko wtedy, gdy wywołanie `ICorDebugType::GetType` zwraca wartość ELEMENT_TYPE_CLASS lub ELEMENT_TYPE_VALUETYPE.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
