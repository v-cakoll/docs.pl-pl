---
title: "ICorDebugCode::GetILToNativeMapping — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f4477ff22d08d5f7ef291c27c00b8985f89ebebd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcodegetiltonativemapping-method"></a>ICorDebugCode::GetILToNativeMapping — Metoda
Pobiera tablicę wystąpień "cor_debug_il_to_native_map —", które reprezentują mapowania od przesunięcia języka pośredniego (MSIL) firmy Microsoft do natywnej przesunięcia.  
  
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
 [out] Wskaźnik do rzeczywistą liczbę zwracanych w elementów `map` tablicy.  
  
 `map`  
 [out] Tablica `COR_DEBUG_IL_TO_NATIVE_MAP` stuctures, z których każdy reprezentuje mapowanie z przesunięciem MSIL do natywnej przesunięcie.  
  
 Nie ma żadnych porządkowanie tablicy zwracane elementy.  
  
## <a name="remarks"></a>Uwagi  
 `GetILToNativeMapping` Metoda zwraca wyniki znaczenie tylko wtedy, gdy to wystąpienie "ICorDebugCode" reprezentuje kodu macierzystego, który był just-in-time (JIT) skompilowana z kodu MSIL.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugCode, interfejs1](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)
