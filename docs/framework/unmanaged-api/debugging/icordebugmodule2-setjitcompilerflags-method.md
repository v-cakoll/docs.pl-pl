---
title: "ICorDebugModule2::SetJITCompilerFlags — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule2.SetJITCompilerFlags
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule2::SetJITCompilerFlags
helpviewer_keywords:
- ICorDebugModule2::SetJITCompilerFlags method [.NET Framework debugging]
- SetJITCompilerFlags method [.NET Framework debugging]
ms.assetid: ea574c84-c622-4589-9a14-b55771af5e06
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 42eea356214fedb22a2f60842f6007f3eb6a0e2a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmodule2setjitcompilerflags-method"></a>ICorDebugModule2::SetJITCompilerFlags — Metoda
Ustawia flagi sterujące kompilacji to ICorDebugModule2 just-in-time (JIT).  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetJITCompilerFlags (  
    [in] DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwFlags`  
 [in] Bitowe połączenie [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) wartości wyliczenia.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `dwFlags` wartość jest nieprawidłowa, `SetJITCompilerFlags` metoda zakończy się niepowodzeniem.  
  
 `SetJITCompilerFlags` Metodę można wywołać tylko z poziomu [ICorDebugManagedCallback::LoadModule](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md) wywołania zwrotnego dla tego modułu. Próby wywołania je po `ICorDebugManagedCallback::LoadModule` wywołania zwrotnego został dostarczony spowoduje niepowodzenie.  
  
 Edytuj i Kontynuuj nie jest obsługiwana na 64-bitowym lub platformach Win9x. W związku z tym jeśli wywołujesz `SetJITCompilerFlags` metodę na jedną z tych dwóch platform z flagą CORDEBUG_JIT_ENABLE_ENC w `dwFlags`, `SetJITCompilerFlags` — metoda i wszystkie metody określonej Edytuj i Kontynuuj, takich jak [ICorDebugModule2:: ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md), zakończy się niepowodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
