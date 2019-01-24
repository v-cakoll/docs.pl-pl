---
title: ICorDebugManagedCallback::UpdateModuleSymbols — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UpdateModuleSymbols
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UpdateModuleSymbols
helpviewer_keywords:
- UpdateModuleSymbols method [.NET Framework debugging]
- ICorDebugManagedCallback::UpdateModuleSymbols method [.NET Framework debugging]
ms.assetid: 0863f644-58e8-45a0-b0c3-a28e99b20938
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b66cc09eda1fe5ea46a55b6239e05b5acec851c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566908"
---
# <a name="icordebugmanagedcallbackupdatemodulesymbols-method"></a>ICorDebugManagedCallback::UpdateModuleSymbols — Metoda
Powiadamia debuger zmieniono symbole dla moduł środowiska uruchomieniowego języka wspólnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT UpdateModuleSymbols (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule,  
    [in] IStream            *pSymbolStream  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pAppDomain`  
 [in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji zawierające moduł, w którym symbole zostały zmienione.  
  
 `pModule`  
 [in] Wskaźnik do obiektu ICorDebugModule, który reprezentuje moduł, w którym symbole zostały zmienione.  
  
 `pSymbolStream`  
 [in] Wskaźnik do Win32 COM `IStream` obiekt, który zawiera symbole zmodyfikowane.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zapewnia możliwość zaktualizuj widok debugera symboli dla modułu, wywołując [ISymUnmanagedReader::UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) lub [ISymUnmanagedReader::ReplaceSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md).  
  
 To wywołanie zwrotne, może wystąpić wiele razy dla tego samego modułu.  
  
 Debuger starać się powiązać niepowiązanych poziom źródła punktów przerwania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorDebugManagedCallback, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
