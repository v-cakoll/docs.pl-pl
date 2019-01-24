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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8614dd612fff2886c4e44a977d05a575fce74eec
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54648946"
---
# <a name="icordebugcodegetiltonativemapping-method"></a>ICorDebugCode::GetILToNativeMapping — Metoda
Pobiera tablicę wystąpień "cor_debug_il_to_native_map —", które reprezentują mapowań od przesunięcia języka pośredniego (MSIL) firmy Microsoft do natywnych przesunięć.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetILToNativeMapping (  
    [in]  ULONG32    cMap,  
    [out] ULONG32    *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cMap`  
 [in] Rozmiar `map` tablicy.  
  
 `pcMap`  
 [out] Wskaźnik do rzeczywistej liczby elementów zwracanych w `map` tablicy.  
  
 `map`  
 [out] Tablica `COR_DEBUG_IL_TO_NATIVE_MAP` stuctures, z których każdy reprezentuje mapowanie z przesunięcia MSIL na przesunięciu macierzystym.  
  
 Nie ma żadnych kolejności do tablicy elementów zwracanych.  
  
## <a name="remarks"></a>Uwagi  
 `GetILToNativeMapping` Metoda zwraca znaczące wyniki tylko wtedy, gdy to wystąpienie "ICorDebugCode" reprezentuje kodu macierzystego, który był just-in-time (JIT) skompilowane z kodu MSIL.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorDebugCode, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)
