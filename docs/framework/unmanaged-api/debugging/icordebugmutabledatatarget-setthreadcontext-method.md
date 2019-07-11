---
title: ICorDebugMutableDataTarget::SetThreadContext Method
ms.date: 03/30/2017
ms.assetid: 8c0d01d5-67e5-4522-9ccf-c8f3a78cb4fd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6629af393eeadb68292f8f2360ecb60c09a0cd03
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764615"
---
# <a name="icordebugmutabledatatargetsetthreadcontext-method"></a>ICorDebugMutableDataTarget::SetThreadContext Method
Ustawia kontekst (wartości rejestru) dla wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetThreadContext(  
   [in] DWORD dwThreadID,  
   [in] ULONG32 contextSize,   [in, size_is(contextSize)] const BYTE * pContext);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwThreadID`  
 [in] Identyfikator wątku zdefiniowaną przez system operacyjny.  
  
 `contextSize`  
 [in] Rozmiar `pContext` bufor do zapisania.  
  
 `pContext`  
 [in] Wskaźnik do bajtów do zapisania.  
  
## <a name="remarks"></a>Uwagi  
 `SetThreadContext` Metody aktualizacji bieżący kontekst wątku określonego przez system operacyjny zdefiniowane `dwThreadID` argumentu. Format rekordu kontekstu jest określana przez platformę, wskazywanym przez [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) metody. W przypadku Windows, jest to [KONTEKSTU](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context) struktury.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugMutableDataTarget, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
