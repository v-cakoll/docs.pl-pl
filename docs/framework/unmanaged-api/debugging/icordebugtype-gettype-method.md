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
ms.openlocfilehash: 25ffbf73fbefbb3c584450283c3080dfc11ee598
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791241"
---
# <a name="icordebugtypegettype-method"></a>ICorDebugType::GetType — Metoda
Pobiera wartość CorElementType —, która opisuje typ natywny środowiska uruchomieniowego języka wspólnego (CLR) <xref:System.Type> reprezentowane przez ten ICorDebugType.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetType (  
    [out] CorElementType   *ty  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ty`  
 określoną Wskaźnik do wartości wyliczenia `CorElementType`, który wskazuje <xref:System.Type> CLR, który reprezentuje `ICorDebugType`.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli wartość `ty` jest ELEMENT_TYPE_CLASS lub ELEMENT_TYPE_VALUETYPE, Metoda [ICorDebugType:: GetClass](icordebugtype-getclass-method.md) może zostać wywołana w celu pobrania typu niewystąpienia dla typu ogólnego; w przeciwnym razie nie wywołuj `ICorDebugType::GetClass`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
