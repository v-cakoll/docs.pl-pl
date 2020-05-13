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
ms.openlocfilehash: 83ac91133b226e2ac263356941c3fc3288355e7e
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379936"
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
 podczas `mdFieldDef`Token określający pole statyczne.  
  
 `pFrame`  
 podczas Wskaźnik do elementu ICorDebugFrame, który reprezentuje ramkę stosu.  
  
 `ppValue`  
 określoną Wskaźnik na adres `ICorDebugValue` , który zawiera wartość pola statycznego.  
  
## <a name="remarks"></a>Uwagi  
 `GetStaticFieldValue`Metoda może być używana tylko wtedy, gdy typ jest ELEMENT_TYPE_CLASS lub ELEMENT_TYPE_VALUETYPE, zgodnie z opisem przez metodę [ICorDebugType:: GetType](icordebugtype-gettype-method.md) .  
  
 W przypadku typów innych niż ogólne Operacja wykonywana przez `GetStaticFieldValue` jest taka sama jak wywołanie [ICorDebugClass:: GetStaticFieldValue](icordebugclass-getstaticfieldvalue-method.md) w obiekcie ICorDebugClass, który jest zwracany przez [ICorDebugType:: GetClass](icordebugtype-getclass-method.md).  
  
 W przypadku typów ogólnych wartość pola statycznego będzie określana względem konkretnego wystąpienia. Ponadto, jeśli pole statyczne może być powiązane z wątkiem, kontekstem lub domeną aplikacji, Ramka stosu pomoże debugerowi określić odpowiednią wartość.  
  
## <a name="remarks"></a>Uwagi  
 `GetStaticFieldValue`mogą być używane tylko wtedy, gdy wywołanie `ICorDebugType::GetType` zwraca wartość ELEMENT_TYPE_CLASS lub ELEMENT_TYPE_VALUETYPE.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
