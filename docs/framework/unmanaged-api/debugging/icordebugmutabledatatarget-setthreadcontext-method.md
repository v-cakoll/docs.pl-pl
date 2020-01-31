---
title: 'ICorDebugMutableDataTarget:: SetThreadContext —, Metoda'
ms.date: 03/30/2017
ms.assetid: 8c0d01d5-67e5-4522-9ccf-c8f3a78cb4fd
ms.openlocfilehash: 063c7954543174caece6f3dcbe005a4b2d059c64
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792846"
---
# <a name="icordebugmutabledatatargetsetthreadcontext-method"></a>ICorDebugMutableDataTarget:: SetThreadContext —, Metoda
Ustawia kontekst (wartości rejestru) dla wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetThreadContext(  
   [in] DWORD dwThreadID,  
   [in] ULONG32 contextSize,   [in, size_is(contextSize)] const BYTE * pContext);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwThreadID`  
 podczas Identyfikator wątku zdefiniowanego przez system operacyjny.  
  
 `contextSize`  
 podczas Rozmiar bufora `pContext`, który ma zostać zapisany.  
  
 `pContext`  
 podczas Wskaźnik do bajtów do zapisania.  
  
## <a name="remarks"></a>Uwagi  
 Metoda `SetThreadContext` aktualizuje bieżący kontekst dla wątku określonego przez argument `dwThreadID` zdefiniowanego przez system operacyjny. Format rekordu kontekstu jest określany przez platformę wskazywaną przez metodę [ICorDebugDataTarget:: GetPlatform](icordebugdatatarget-getplatform-method.md) . W systemie Windows jest to struktura [kontekstu](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugMutableDataTarget, interfejs](icordebugmutabledatatarget-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
