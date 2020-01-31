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
ms.openlocfilehash: 306d881c05c2fcdb15a53a439bfce6eff3afffa8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792314"
---
# <a name="icordebugprocess5gettypelayout-method"></a>ICorDebugProcess5::GetTypeLayout — Metoda
Pobiera informacje o układzie obiektu w pamięci na podstawie jego identyfikatora typu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetTypeLayout(    [in] COR_TYPEID id,     [out] COR_TYPE_LAYOUT *pLayout);  
```  
  
## <a name="parameters"></a>Parametry  
 `id`  
 podczas Token [COR_TYPEID](cor-typeid-structure.md) , który określa typ, którego układ jest żądany.  
  
 `pLayout`  
 określoną Wskaźnik do struktury [COR_TYPE_LAYOUT](cor-type-layout-structure.md) , która zawiera informacje o układzie obiektu w pamięci.  
  
## <a name="remarks"></a>Uwagi  
 Metoda `ICorDebugProcess5::GetTypeLayout` zapewnia informacje o obiekcie na podstawie jego [COR_TYPEID](cor-typeid-structure.md), który jest zwracany przez wiele innych metod [ICorDebugProcess5](icordebugprocess5-interface.md) . Informacje są dostarczane przez strukturę [COR_TYPE_LAYOUT](cor-type-layout-structure.md) , która jest wypełniana przez metodę.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [COR_TYPE_LAYOUT, struktura](cor-type-layout-structure.md)
- [ICorDebugProcess5, interfejs](icordebugprocess5-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
