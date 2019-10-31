---
title: ICorDebugModule::EnableClassLoadCallbacks — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.EnableClassLoadCallbacks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::EnableClassLoadCallbacks
helpviewer_keywords:
- ICorDebugModule::EnableClassLoadCallbacks method [.NET Framework debugging]
- EnableClassLoadCallbacks method [.NET Framework debugging]
ms.assetid: 78dad5e4-8e2e-400f-bec3-92ff0205cd82
topic_type:
- apiref
ms.openlocfilehash: c18ed781d44c873b4cd1957bf0102a4ce0cccad4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139219"
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a>ICorDebugModule::EnableClassLoadCallbacks — Metoda
Określa, czy wywołania zwrotne [ICorDebugManagedCallback:: LoadClass —](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) i [ICorDebugManagedCallback:: UnloadClass —](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) są wywoływane dla tego modułu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `bClassLoadCallbacks`  
 podczas Ustaw tę wartość na `true`, aby umożliwić programowi uruchomieniowemu języka wspólnego (CLR) wywoływanie metod `ICorDebugManagedCallback::LoadClass` i `ICorDebugManagedCallback::UnloadClass` w przypadku wystąpienia skojarzonych z nimi zdarzeń.  
  
 Wartość domyślna to `false` modułów niedynamicznych. Wartość jest zawsze `true` dla modułów dynamicznych i nie można jej zmienić.  
  
## <a name="remarks"></a>Uwagi  
 Wywołania zwrotne `ICorDebugManagedCallback::LoadClass` i `ICorDebugManagedCallback::UnloadClass` są zawsze włączone dla modułów dynamicznych i nie można ich wyłączyć.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
