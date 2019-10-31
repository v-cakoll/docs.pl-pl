---
title: ICorDebugModule2::SetJITCompilerFlags — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.SetJITCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::SetJITCompilerFlags
helpviewer_keywords:
- ICorDebugModule2::SetJITCompilerFlags method [.NET Framework debugging]
- SetJITCompilerFlags method [.NET Framework debugging]
ms.assetid: ea574c84-c622-4589-9a14-b55771af5e06
topic_type:
- apiref
ms.openlocfilehash: 2358cee1b3a9aa50fb1f0e61d558f164a39aa86c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137361"
---
# <a name="icordebugmodule2setjitcompilerflags-method"></a>ICorDebugModule2::SetJITCompilerFlags — Metoda
Ustawia flagi kontrolujące kompilację just-in-Time (JIT) tej ICorDebugModule2.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetJITCompilerFlags (  
    [in] DWORD dwFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwFlags`  
 podczas Bitowa kombinacja wartości wyliczenia [CorDebugJITCompilerFlags —](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) .  
  
## <a name="remarks"></a>Uwagi  
 Jeśli wartość `dwFlags` jest nieprawidłowa, Metoda `SetJITCompilerFlags` zakończy się niepowodzeniem.  
  
 Metodę `SetJITCompilerFlags` można wywołać tylko z poziomu wywołania zwrotnego [ICorDebugManagedCallback:: LoadModule](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md) dla tego modułu. Próbuje wywołać ją po dostarczeniu wywołania zwrotnego `ICorDebugManagedCallback::LoadModule` zakończy się niepowodzeniem.  
  
 Edytuj i Kontynuuj nie są obsługiwane na platformach 64-bitowych i Win9x. W związku z tym, jeśli wywołasz metodę `SetJITCompilerFlags` na jednej z tych dwóch platform z flagą CORDEBUG_JIT_ENABLE_ENC ustawioną w `dwFlags`, Metoda `SetJITCompilerFlags` oraz wszystkie metody specyficzne dla opcji Edytuj i Kontynuuj, takie jak [ICorDebugModule2:: ApplyChanges —](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md), zakończą się niepowodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
