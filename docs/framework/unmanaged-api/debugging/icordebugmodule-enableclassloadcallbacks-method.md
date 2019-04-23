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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 22a838748414f9d89cdc7ff469f7f5cc5e11b9d4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59108306"
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a>ICorDebugModule::EnableClassLoadCallbacks — Metoda
Formanty czy [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) i [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) wywołania zwrotne są wywoływane dla tego modułu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `bClassLoadCallbacks`  
 [in] Ustaw tę wartość na `true` Aby włączyć środowisko uruchomieniowe języka wspólnego (CLR), aby wywołać `ICorDebugManagedCallback::LoadClass` i `ICorDebugManagedCallback::UnloadClass` metody, gdy wystąpią ich powiązanych zdarzeń.  
  
 Wartość domyślna to `false` dla modułów nie dynamicznych. Wartość jest zawsze `true` dla modułów dynamicznych i nie można zmienić.  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugManagedCallback::LoadClass` i `ICorDebugManagedCallback::UnloadClass` wywołania zwrotne są zawsze włączone dla modułów dynamicznych i nie może być wyłączony.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
