---
title: ICorDebugType::GetType — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetType
helpviewer_keywords:
- ICorDebugType::GetType method [.NET Framework debugging]
- GetType method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: d6e64534-4d47-4ad0-a340-7590e07e2b4a
topic_type:
- apiref
ms.openlocfilehash: ac42c6254182ea775377a448a54d527b234c97dc
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379924"
---
# <a name="icordebugtypegettype-method"></a>ICorDebugType::GetType — Metoda
Pobiera wartość CorElementType —, która opisuje typ natywny środowiska uruchomieniowego języka wspólnego (CLR) <xref:System.Type> reprezentowanego przez ten ICorDebugType.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetType (  
    [out] CorElementType   *ty  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ty`  
 określoną Wskaźnik do wartości `CorElementType` wyliczenia wskazującej, że środowisko CLR <xref:System.Type> `ICorDebugType` reprezentuje.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli wartość `ty` jest ELEMENT_TYPE_CLASS lub ELEMENT_TYPE_VALUETYPE, Metoda [ICorDebugType:: GetClass](icordebugtype-getclass-method.md) może zostać wywołana w celu pobrania niewystąpienia typu dla typu ogólnego; w przeciwnym razie nie należy wywoływać `ICorDebugType::GetClass` .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
