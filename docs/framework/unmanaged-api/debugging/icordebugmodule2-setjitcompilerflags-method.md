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
ms.openlocfilehash: b28e457ea0b51d320581c0fbe36574698081ea36
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792960"
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
 podczas Bitowa kombinacja wartości wyliczenia [CorDebugJITCompilerFlags —](cordebugjitcompilerflags-enumeration.md) .  
  
## <a name="remarks"></a>Uwagi  
 Jeśli wartość `dwFlags` jest nieprawidłowa, Metoda `SetJITCompilerFlags` zakończy się niepowodzeniem.  
  
 Metodę `SetJITCompilerFlags` można wywołać tylko z poziomu wywołania zwrotnego [ICorDebugManagedCallback:: LoadModule](icordebugmanagedcallback-loadmodule-method.md) dla tego modułu. Próbuje wywołać ją po dostarczeniu wywołania zwrotnego `ICorDebugManagedCallback::LoadModule` zakończy się niepowodzeniem.  
  
 Edytuj i Kontynuuj nie są obsługiwane na platformach 64-bitowych i Win9x. W związku z tym, jeśli wywołasz metodę `SetJITCompilerFlags` na jednej z tych dwóch platform z flagą CORDEBUG_JIT_ENABLE_ENC ustawioną w `dwFlags`, Metoda `SetJITCompilerFlags` i wszystkie metody specyficzne dla opcji Edytuj i Kontynuuj, takie jak [ICorDebugModule2:: ApplyChanges —](icordebugmodule2-applychanges-method.md), zakończą się niepowodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
