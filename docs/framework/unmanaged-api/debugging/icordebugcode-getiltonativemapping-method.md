---
title: ICorDebugCode::GetILToNativeMapping — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetILToNativeMapping
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetILToNativeMapping
helpviewer_keywords:
- GetILToNativeMapping method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetILToNativeMapping method [.NET Framework debugging]
ms.assetid: a8ecd8c8-9627-4356-9c6f-bd05e24637c0
topic_type:
- apiref
ms.openlocfilehash: 98709c0ce7469db1d0365d71e10d2d021cd3b3f0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777889"
---
# <a name="icordebugcodegetiltonativemapping-method"></a>ICorDebugCode::GetILToNativeMapping — Metoda
Pobiera tablicę wystąpień "COR_DEBUG_IL_TO_NATIVE_MAP", które reprezentują mapowania z przesunięcia języka pośredniego firmy Microsoft (MSIL) do natywnych przesunięć.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetILToNativeMapping (  
    [in]  ULONG32    cMap,  
    [out] ULONG32    *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `cMap`  
 podczas Rozmiar tablicy `map`.  
  
 `pcMap`  
 określoną Wskaźnik do rzeczywistej liczby elementów zwracanych w tablicy `map`.  
  
 `map`  
 określoną Tablica struktur `COR_DEBUG_IL_TO_NATIVE_MAP`, z których każdy reprezentuje mapowanie z przesunięcia MSIL do natywnego przesunięcia.  
  
 Nie istnieje porządkowanie do tablicy zwracanych elementów.  
  
## <a name="remarks"></a>Uwagi  
 Metoda `GetILToNativeMapping` zwraca znaczące wyniki tylko wtedy, gdy to wystąpienie "ICorDebugCode" reprezentuje kod natywny, który był wcześniej (JIT) skompilowany na podstawie kodu MSIL.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugCode, interfejs](icordebugcode-interface1.md)
