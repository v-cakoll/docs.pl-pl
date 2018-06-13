---
title: ICorDebugMutableDataTarget::SetThreadContext — metoda
ms.date: 03/30/2017
ms.assetid: 8c0d01d5-67e5-4522-9ccf-c8f3a78cb4fd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 05f0c0d23b4885f2d6fd351fdf845a25c899228e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418421"
---
# <a name="icordebugmutabledatatargetsetthreadcontext-method"></a>ICorDebugMutableDataTarget::SetThreadContext — metoda
Ustawia kontekst wątku (wartości rejestru).  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetThreadContext(  
   [in] DWORD dwThreadID,  
   [in] ULONG32 contextSize,   [in, size_is(contextSize)] const BYTE * pContext);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwThreadID`  
 [in] Identyfikator wątku zdefiniowane przez system operacyjny.  
  
 `contextSize`  
 [in] Rozmiar `pContext` buforu do zapisania.  
  
 `pContext`  
 [in] Wskaźnik do bajtów do zapisania.  
  
## <a name="remarks"></a>Uwagi  
 `SetThreadContext` Metody aktualizacji bieżący kontekst wątku określony przez system operacyjny zdefiniowane `dwThreadID` argumentu. Format rekordu kontekstu jest określany przez platformy wskazywaną przez [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) metody. W systemie Windows, to [KONTEKSTU](http://msdn.microsoft.com/library/windows/desktop/ms679284.aspx) struktury.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugMutableDataTarget, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
