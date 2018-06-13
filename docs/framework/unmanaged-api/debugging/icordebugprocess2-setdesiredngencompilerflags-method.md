---
title: ICorDebugProcess2::SetDesiredNGENCompilerFlags — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.SetDesiredNGENCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::SetDesiredNGENCompilerFlags
helpviewer_keywords:
- ICorDebugProcess2::SetDesiredNGENCompilerFlags method [.NET Framework debugging]
- SetDesiredNGENCompilerFlags method [.NET Framework debugging]
ms.assetid: 98320175-7c5e-4dbb-8683-86fa82e2641f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 94ba2b0cf7d88104eaadd434732edf3c1d4060e2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422704"
---
# <a name="icordebugprocess2setdesiredngencompilerflags-method"></a>ICorDebugProcess2::SetDesiredNGENCompilerFlags — Metoda
Ustawia flagi, które muszą być osadzone prekompilowany obrazu w kolejności środowiska uruchomieniowego do ładowania obrazu do bieżącego procesu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetDesiredNGENCompilerFlags (  
    [in] DWORD    pdwFlags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdwFlags`  
 [in] Wartość [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) wyliczenia, która określa flagi kompilatora użyć, aby wybrać prawidłowy obraz wstępnie skompilowanym.  
  
## <a name="remarks"></a>Uwagi  
 `SetDesiredNGENCompilerFlags` Metody określa flagi, które musi być osadzony w prekompilowany obrazu, dzięki czemu środowiska uruchomieniowego załaduje obrazu do tego procesu. Flagi ustawione przez tę metodę są używane tylko w celu wybrania prawidłowy obraz wstępnie skompilowana. Jeśli istnieje nie tych obrazów, środowiska uruchomieniowego zamiast obciążenia obrazu język pośredni (MSIL) firmy Microsoft i przy użyciu kompilatora just in time (JIT). W takim przypadku należy nadal używać debugera [ICorDebugModule2::SetJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md) metody można ustawić flagi zgodnie z potrzebami dla kompilacji JIT.  
  
 Jeśli obraz został załadowany, ale niektóre kompilacji JIT musi odbywać się do tego obrazu (co będzie miało miejsce, jeśli obraz zawiera ogólne) flagi kompilatora określony przez `SetDesiredNGENCompilerFlags` metoda będzie dotyczyć dodatkowe kompilacji JIT.  
  
 `SetDesiredNGENCompilerFlags` Metoda musi zostać wywołana podczas [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) wywołania zwrotnego. Próby wywołania `SetDesiredNGENCompilerFlags` metody później zakończy się niepowodzeniem. Ponadto próbuje ustawić flagi, które nie są zdefiniowane w `CorDebugJITCompilerFlags` wyliczenia lub czy nie jest dozwolony dla danego procesu zakończy się niepowodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebug, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [ICorDebugManagedCallback, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
