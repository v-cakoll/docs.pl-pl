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
ms.openlocfilehash: f73919634ba15dfd16694676d1389875fc2d79bc
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210192"
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
 Jeśli `dwFlags` wartość jest nieprawidłowa, metoda zakończy `SetJITCompilerFlags` się niepowodzeniem.  
  
 `SetJITCompilerFlags`Metodę można wywołać tylko z poziomu wywołania zwrotnego [ICorDebugManagedCallback:: LoadModule](icordebugmanagedcallback-loadmodule-method.md) dla tego modułu. Próbuje wywołać ją po `ICorDebugManagedCallback::LoadModule` dostarczeniu wywołania zwrotnego zakończy się niepowodzeniem.  
  
 Edytuj i Kontynuuj nie są obsługiwane na platformach 64-bitowych i Win9x. W związku z tym, jeśli wywołasz `SetJITCompilerFlags` metodę na jednej z tych dwóch platform z flagą CORDEBUG_JIT_ENABLE_ENC ustawioną w `dwFlags` , `SetJITCompilerFlags` Metoda i wszystkie metody specyficzne dla opcji Edytuj i Kontynuuj, takie jak [ICorDebugModule2:: ApplyChanges —](icordebugmodule2-applychanges-method.md), zakończą się niepowodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
