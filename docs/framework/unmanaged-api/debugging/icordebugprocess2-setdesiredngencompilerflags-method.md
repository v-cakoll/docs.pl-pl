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
ms.openlocfilehash: e1cab24f949ddae55d5e699e6ad82851007504dd
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57475700"
---
# <a name="icordebugprocess2setdesiredngencompilerflags-method"></a>ICorDebugProcess2::SetDesiredNGENCompilerFlags — Metoda
Ustawia flagi, które muszą być osadzone w wstępnie skompilowanym obrazów w kolejności dla środowiska uruchomieniowego do załadowania tego obrazu do bieżącego procesu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetDesiredNGENCompilerFlags (  
    [in] DWORD    pdwFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pdwFlags`  
 [in] Wartość [cordebugjitcompilerflags —](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) wyliczenie, które określa flagi kompilatora używany do wybierania wstępnie skompilowanym prawidłowy obraz.  
  
## <a name="remarks"></a>Uwagi  
 `SetDesiredNGENCompilerFlags` Metody określa flagi, które muszą być osadzone w wstępnie skompilowanym obrazów, tak, aby środowisko uruchomieniowe będzie załadować ten obraz do tego procesu. Flag ustawionych przez tę metodę są używane tylko po to, aby wybrać prawidłowy obraz wstępnie skompilowane. Jeśli istnieje nie takich obrazów, środowisko uruchomieniowe zamiast tego obciążenia obrazu języka intermediate language (MSIL) firmy Microsoft i kompilator just-in-time (JIT). W takim przypadku należy nadal używać debugera [ICorDebugModule2::SetJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md) metodę, aby ustawić flagi zgodnie z potrzebami dla kompilacji JIT.  
  
 Jeśli obraz został załadowany, ale niektóre kompilacja JIT musi odbywać się obrazu (co będzie miało miejsce, jeśli obraz zawiera ogólne), flagi kompilatora określony przez `SetDesiredNGENCompilerFlags` metody będą stosowane dodatkowe kompilację JIT.  
  
 `SetDesiredNGENCompilerFlags` Metoda musi zostać wywołane podczas [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) wywołania zwrotnego. Próbuje wywołać `SetDesiredNGENCompilerFlags` metoda później zakończy się niepowodzeniem. Ponadto próbuje ustawić flagi, które nie są zdefiniowane w `CorDebugJITCompilerFlags` wyliczenia lub czy nie jest dozwolony dla danego procesu zakończy się niepowodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorDebug, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [ICorDebugManagedCallback, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
