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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c71ccbc62ea026a55a7e84f6925a78850594a813
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61942522"
---
# <a name="icordebugmodule2setjitcompilerflags-method"></a>ICorDebugModule2::SetJITCompilerFlags — Metoda
Ustawia flagi, które kontrolują kompilację just-in-time (JIT) to icordebugmodule2 —.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetJITCompilerFlags (  
    [in] DWORD dwFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwFlags`  
 [in] Bitowa kombinacja [cordebugjitcompilerflags —](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) wartości wyliczenia.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `dwFlags` wartość jest nieprawidłowa, `SetJITCompilerFlags` metoda zakończy się niepowodzeniem.  
  
 `SetJITCompilerFlags` Metoda może być wywołana tylko z poziomu [ICorDebugManagedCallback::LoadModule](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md) wywołania zwrotnego dla tego modułu. Próbuje wywołać go po `ICorDebugManagedCallback::LoadModule` wywołania zwrotnego dostarczonej będą się nie powieść.  
  
 Edytuj i Kontynuuj nie jest obsługiwany w 64-bitowych lub Win9x platformach. W związku z tym jeśli wywołasz `SetJITCompilerFlags` metodę na jedną z tych dwóch platform przy użyciu flagi CORDEBUG_JIT_ENABLE_ENC w `dwFlags`, `SetJITCompilerFlags` metody i wszystkie metody określonej funkcji Edytuj i Kontynuuj, takich jak [icordebugmodule2 —:: Applychanges —](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md), zakończy się niepowodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
