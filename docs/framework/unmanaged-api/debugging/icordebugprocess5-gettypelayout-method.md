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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ee556f559a7dc4c271f110f7bba4c86b675c3511
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736497"
---
# <a name="icordebugprocess5gettypelayout-method"></a>ICorDebugProcess5::GetTypeLayout — Metoda
Pobiera informacje o układ obiektu w pamięci na podstawie jego identyfikatora typu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetTypeLayout(    [in] COR_TYPEID id,     [out] COR_TYPE_LAYOUT *pLayout);  
```  
  
## <a name="parameters"></a>Parametry  
 `id`  
 [in] A [cor_typeid —](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token, który określa typ, którego układ jest pożądane.  
  
 `pLayout`  
 [out] Wskaźnik do [cor_type_layout —](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) strukturę, która zawiera informacje na temat układu obiektu w pamięci.  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugProcess5::GetTypeLayout` Metoda zawiera informacje dotyczące obiektu, na podstawie jego [cor_typeid —](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), która jest zwracana przez szereg innych [icordebugprocess5 —](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md) metody. Informacje są udostępniane przez [cor_type_layout —](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) strukturę, która jest wypełniana przez metodę.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [COR_TYPE_LAYOUT, struktura](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)
- [ICorDebugProcess5, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
