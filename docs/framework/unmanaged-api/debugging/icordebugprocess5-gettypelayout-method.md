---
title: ICorDebugProcess5::GetTypeLayout — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeLayout
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeLayout
helpviewer_keywords:
- ICorDebugProcess5::GetTypeLayout method [.NET Framework debugging]
- GetTypeLayout method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: bd62f5d1-e874-41f1-81e5-a29a7572c15d
topic_type:
- apiref
ms.openlocfilehash: a348c3b2ad33a5d68b1bc46e9a284f2d2a9c7304
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121285"
---
# <a name="icordebugprocess5gettypelayout-method"></a>ICorDebugProcess5::GetTypeLayout — Metoda
Pobiera informacje o układzie obiektu w pamięci na podstawie jego identyfikatora typu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetTypeLayout(    [in] COR_TYPEID id,     [out] COR_TYPE_LAYOUT *pLayout);  
```  
  
## <a name="parameters"></a>Parametry  
 `id`  
 podczas Token [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) , który określa typ, którego układ jest żądany.  
  
 `pLayout`  
 określoną Wskaźnik do struktury [COR_TYPE_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) , który zawiera informacje o układzie obiektu w pamięci.  
  
## <a name="remarks"></a>Uwagi  
 Metoda `ICorDebugProcess5::GetTypeLayout` zawiera informacje o obiekcie opartym na jego [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), który jest zwracany przez wiele innych metod [ICorDebugProcess5](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md) . Informacje są dostarczane przez strukturę [COR_TYPE_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) , która jest wypełniana przez metodę.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [COR_TYPE_LAYOUT, struktura](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)
- [ICorDebugProcess5, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
