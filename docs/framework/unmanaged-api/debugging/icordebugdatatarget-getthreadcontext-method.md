---
title: ICorDebugDataTarget::GetThreadContext — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.GetThreadContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::GetThreadContext
helpviewer_keywords:
- ICorDebugDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: c8954268-1821-4b23-b665-dbb55f2af31b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ab2fbf6bb08a33158ea450f0f19eca50e280d8c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412883"
---
# <a name="icordebugdatatargetgetthreadcontext-method"></a>ICorDebugDataTarget::GetThreadContext — Metoda
Zwraca bieżący kontekst wątku określonego wątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetThreadContext(  
       [in] DWORD dwThreadID,  
       [in] ULONG32 contextFlags,  
       [in] ULONG32 contextSize,  
       [out, size_is(contextSize)] BYTE * pContext);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwThreadID`  
 [in] Identyfikator wątku, w którego kontekście ma być pobrana. Identyfikator jest zdefiniowany przez system operacyjny.  
  
 `contextFlags`  
 [in] Bitowe połączenie flag zależny od platformy, które wskazują części kontekście powinny być do odczytu.  
  
 `contextSize`  
 [in] Rozmiar `pContext`.  
  
 `pContext`  
 [out] Bufor przechowywania kontekst wątku.  
  
## <a name="remarks"></a>Uwagi  
 Na platformach Windows `pContext` musi być `CONTEXT` Struktura (zdefiniowane w pliku WinNT.h), która jest odpowiednia dla typu maszyny, określony przez [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) metody. `contextFlags` musi mieć takie same wartości jak `ContextFlags` pole `CONTEXT` struktury. `CONTEXT` Struktura jest specyficznych dla procesora, zobacz szczegóły w pliku pliku WinNT.h.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugDataTarget, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
